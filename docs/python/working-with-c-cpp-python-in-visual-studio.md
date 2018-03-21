---
title: Trabalhando com o C++ e o Python no Visual Studio | Microsoft Docs
description: "Os processo e as etapas para escrever uma extensão ou um módulo do C++ para o Python no Visual Studio"
ms.custom: 
ms.date: 01/16/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
dev_langs:
- python
- C++
ms.tgt_pltfrm: 
ms.topic: tutorial
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: 1b2f570a75be94c3bff4b38a6d0641e3ecbce2f2
ms.sourcegitcommit: 39c525ec200c6c4ea94815567b3fad7ab14fb7b3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/08/2018
---
# <a name="creating-a-c-extension-for-python"></a>Criando uma extensão do C++ para o Python

Os módulos escritos em C++ (ou em C) são geralmente usados para estender as funcionalidades de um interpretador do Python, bem como para permitir o acesso a funcionalidades de baixo nível do sistema operacional. Há três tipos de módulos principais:

- Módulos de acelerador: como o Python é uma linguagem interpretada, algumas partes do código podem ser escritas em C++ para um desempenho mais alto. 
- Módulos de wrapper: wrappers expõem interfaces C/C++ existentes para o código Python ou expõem uma API mais "Pythonic" fácil de usar do Python.
- Módulos de acesso de baixo nível do sistema: criados para acessar os recursos de baixo nível do tempo de execução CPython, do sistema operacional ou do hardware subjacente.

Este artigo explica como criar um módulo de extensão C++ para CPython que calcula uma tangente hiperbólica e faz uma chamada a ela do código Python. A rotina é implementada primeiro em Python para demonstrar o ganho de desempenho relativo da implementação da mesma rotina em C++.

A abordagem usada aqui é a mesma usada nas extensões padrão do CPython, conforme descrito na [documentação do Python](https://docs.python.org/3/c-api/). Uma comparação entre esse e outros meios é descrita em [abordagens alternativas](#alternative-approaches) ao final deste artigo.

## <a name="prerequisites"></a>Pré-requisitos

- Visual Studio 2017 com as cargas de trabalho **Desenvolvimento para desktop com C++** e **Desenvolvimento do Python** instaladas com as opções padrão.
- Na carga de trabalho **Desenvolvimento Python**, marque também a caixa à direita para **Ferramentas de desenvolvimento nativo em Python**. Essa opção define a maior parte da configuração descrita neste artigo. (Essa opção também inclui a carga de trabalho do C++ automaticamente.)

![Selecionando a opção de ferramentas de desenvolvimento nativo do Python](media/cpp-install-native.png)

- A instalação da carga de trabalho **Aplicativos de ciência de dados e análise** também inclui o Python e a opção **Ferramentas nativas de desenvolvimento em Python** por padrão.

Para obter mais informações, consulte [Instalando o suporte do Python para Visual Studio](installing-python-support-in-visual-studio.md), incluindo o uso de outras versões do Visual Studio. Se você instalar o Python separadamente, lembre-se de selecionar **Baixar símbolos de depuração** e **Baixar binários de depuração** em **Opções Avançadas** no instalador. Essa opção garante que você terá as bibliotecas de depuração necessárias disponíveis se optar por fazer um build de depuração.

## <a name="create-the-python-application"></a>Criar o aplicativo do Python

1. Crie um novo projeto do Python no Visual Studio selecionando **Arquivo > Novo > Projeto**. Pesquise "Python", selecione o modelo **Aplicativo Python**, atribua a ele um nome e um local adequados e selecione **OK**.

1. No arquivo `.py` do projeto, cole o código a seguir que submeterá a benchmark o cálculo de uma tangente hiperbólica (implementada sem o uso da biblioteca de matemática para facilitar a comparação). Fique à vontade para inserir o código manualmente para experimentar alguns [recursos de edição do Python](editing-python-code-in-visual-studio.md).

    ```python
    from itertools import islice
    from random import random
    from time import perf_counter

    COUNT = 500000  # Change this value depending on the speed of your computer
    DATA = list(islice(iter(lambda: (random() - 0.5) * 3.0, None), COUNT))

    e = 2.7182818284590452353602874713527

    def sinh(x):
        return (1 - (e ** (-2 * x))) / (2 * (e ** -x))

    def cosh(x):
        return (1 + (e ** (-2 * x))) / (2 * (e ** -x))

    def tanh(x):
        tanh_x = sinh(x) / cosh(x)
        return tanh_x

    def sequence_tanh(data):
        '''Applies the hyperbolic tangent function to map all values in
        the sequence to a value between -1.0 and 1.0.
        '''
        result = []
        for x in data:
            result.append(tanh(x))
        return result

    def test(fn, name):
        start = perf_counter()
        result = fn(DATA)
        duration = perf_counter() - start
        print('{} took {:.3f} seconds\n\n'.format(name, duration))

        for d in result:
            assert -1 <= d <=1, " incorrect values"

    if __name__ == "__main__":
        print('Running benchmarks with COUNT = {}'.format(COUNT))
        test(sequence_tanh, 'sequence_tanh')

        test(lambda d: [tanh(x) for x in d], '[tanh(x) for x in d]')
    ```

1. Execute o programa usando **Depurar > Iniciar Sem Depurar** (Ctrl + F5) para ver os resultados. Você pode ajustar a variável `COUNT` para alterar o tempo que os parâmetros de comparação levam para serem executados. Para a finalidade deste passo a passo, defina a contagem de forma que cada parâmetro de comparação leve cerca de dois segundos.

## <a name="create-the-core-c-project"></a>Criar o projeto principal do C++

1. Clique com o botão direito do mouse na solução, no Gerenciador de Soluções e selecione **Adicionar > Novo Projeto...**. Uma solução do Visual Studio pode conter projetos do Python e do C++ juntos.

1. Pesquise "C++", selecione **Projeto vazio**, especifique um nome (este artigo usa "superfastcode") e selecione **OK**. Observação: se você tiver instalado as **ferramentas de desenvolvimento nativo do Python** com o Visual Studio 2017, poderá começar com o modelo **Módulo de Extensão do Python**, que implementa grande parte do que já foi descrito aqui. No entanto, para este passo a passo, começar com um projeto vazio demonstra o build do módulo de extensão passo a passo.

1. Crie um arquivo do C++ no novo projeto clicando com o botão direito do mouse no nó **Arquivos de Origem**, selecione **Adicionar > Novo Item…**, selecione **Arquivo do C++**, fornece a ele um nome (como `module.cpp`) e selecione **OK**. Essa etapa é necessária ativar as páginas de propriedades C++ nas etapas a seguir.

1. Clique com o botão direito do mouse no projeto C++ na solução e selecione **Propriedades**.

1. Na parte superior da caixa de diálogo **Páginas de Propriedades** exibida, defina **Configuração** para **Todas as Configurações** e **Plataforma** para **Win32**.

1. Defina as propriedades específicas, conforme descrito na tabela a seguir e, em seguida, selecione **OK**.

    | Tabulação | propriedade | Valor |
    | --- | --- | --- |
    | Geral | Geral > Nome de Destino | Especifique o nome do módulo ao qual você deseja se referir do Python nas instruções `from...import`. Você pode usar esse mesmo nome em C++ ao definir o módulo para Python. Se você quiser usar o nome do projeto como o nome do módulo, deixe o valor padrão de `$(ProjectName)`. |
    | | Geral > Extensão de Destino | .pyd |
    | | Padrões do Projeto > Tipo de Configuração | Biblioteca Dinâmica (.dll) |
    | C/C++ > Geral | Diretórios de Inclusão Adicionais | Adicione a pasta `include` do Python conforme apropriado para sua instalação, por exemplo, `c:\Python36\include`.  |
    | C/C++ > Pré-processador | Definições do Pré-processador | Adicione `Py_LIMITED_API;` ao início da cadeia de caracteres (incluindo o ponto e vírgula). Essa definição restringe algumas das funções que podem ser chamadas do Python e torna o código mais portável entre diferentes versões do Python. |
    | C/C++ > Geração de Código | Biblioteca em Tempo de Execução | DLL com multi-thread (/MD) (consulte Aviso abaixo) |
    | Vinculador > Geral | Diretórios de Biblioteca Adicionais | Adicione a pasta `libs` do Python que contém arquivos `.lib` conforme apropriado para sua instalação, por exemplo, `c:\Python36\libs`. (Lembre-se de apontar para a pasta `libs` que contém arquivos `.lib` e *não* para a pasta `Lib` que contém arquivos `.py`.) |

    > [!Tip]
    > Se a guia C/C++ não for exibida nas propriedades do projeto, isso indicará que o projeto não contém nenhum arquivo que ele identifica como arquivos de origem do C/C++. Essa condição poderá ocorrer se você criar um arquivo de origem sem uma extensão `.c` ou `.cpp`. Por exemplo, se você inseriu `module.coo` em vez de `module.cpp` acidentalmente na nova caixa de diálogo de item anteriormente, o Visual Studio criará o arquivo, mas não definirá o tipo de arquivo como “Código C/C+”, que é o que ativa a guia de propriedades do C/C++. Essa identificação incorreta continuará acontecendo mesmo se você renomear o arquivo com `.cpp`. Para configurar o tipo de arquivo corretamente, clique com o botão direito do mouse no arquivo no Gerenciador de Soluções, selecione **Propriedades** e, em seguida, defina **Tipo de Arquivo** como **Código C/C++**.

    > [!Warning]
    > Sempre defina a opção **C/C++ > Geração de Código > Biblioteca de Tempo de Execução** para "DLL multithread (/MD)", mesmo para uma configuração de depuração, porque os binários Python que não são de depuração são criados com essa configuração. Se você definir a opção "DLL de depuração multithread (/MDd)", a criação de uma configuração de depuração gerará o erro *C1189: Py_LIMITED_API é incompatível com Py_DEBUG, Py_TRACE_REFS e Py_REF_DEBUG*. Além disso, se você remover `Py_LIMITED_API` para evitar o erro de build, o Python falhará ao tentar importar o módulo. (A falha ocorre na chamada da DLL a `PyModule_Create`, conforme descrito adiante, com a mensagem de saída *Erro fatal do Python: PyThreadState_Get: nenhum thread atual*.)
    >
    > A opção /MDd é usada para criar os binários de depuração Python (como python_d.exe), mas selecioná-la para uma DLL de extensão ainda causará o erro de build com `Py_LIMITED_API`.

1. Clique com o botão direito do mouse no projeto do C++ e selecione **Compilar** para testar as configurações (Depuração e Versão). Os arquivos `.pyd` estão localizados na pasta *solução* em **Depurar** e **Versão**, não na própria pasta do projeto do C++.

1. Adicione o seguinte código ao arquivo `.cpp` principal do projeto do C++:

    ```cpp
    #include <Windows.h>
    #include <cmath>

    const double e = 2.7182818284590452353602874713527;

    double sinh_impl(double x) {
        return (1 - pow(e, (-2 * x))) / (2 * pow(e, -x));
    }

    double cosh_impl(double x) {
        return (1 + pow(e, (-2 * x))) / (2 * pow(e, -x));
    }

    double tanh_impl(double x) {
        return sinh_impl(x) / cosh_impl(x);
    }
    ```

1. Compile o projeto do C++ novamente para confirmar se o código está correto.

## <a name="convert-the-c-project-to-an-extension-for-python"></a>Converter o projeto do C++ em uma extensão para o Python

Para transformar a DLL C++ em uma extensão para Python, primeiro você precisa modificar os métodos exportados para interagir com tipos Python. Em seguida, será necessário adicionar uma função que exporte o módulo, juntamente com as definições dos métodos do módulo. Para obter informações sobre o que é mostrado aqui, consulte o [Manual de Referência de API do Python/C](https://docs.python.org/3/c-api/index.html) e, especialmente, [Objetos de módulo](https://docs.python.org/3/c-api/module.html) em python.org. (Lembre-se de selecionar sua versão do Python no controle suspenso no canto superior direito.)

> [!Note]
> Essas instruções se aplicam ao Python 3.x. Se você estiver trabalhando com o Python 2.7, veja [Estender o Python 2.7 com C ou C++](https://docs.python.org/2.7/extending/extending.html) e [Realizar a portabilidade de módulos de extensão para Python 3](https://docs.python.org/2.7/howto/cporting.html) (python.org).

1. No arquivo do C++, inclua `Python.h` na parte superior:

    ```cpp
    #include <Python.h>
    ```

    > [!Tip]
    > Se aparecer *E1696: não é possível abrir o arquivo de software livre "Python.h"* e/ou *C1083: não é possível abrir o arquivo de inclusão: "Python.h": o arquivo ou diretório não existe*, verifique se você definiu a configuração **C/C++ > Geral > Diretórios de Inclusão Adicionais** nas propriedades do projeto para a pasta `include` da instalação do Python, conforme descrito na etapa 6 em [Criar o projeto principal C++](#create-the-core-c-project).

1. Modifique o método `tanh_impl` para aceitar e retornar tipos Python (um `PyOjbect*`, que é):

    ```cpp
    PyObject* tanh_impl(PyObject *, PyObject* o) {
        double x = PyFloat_AsDouble(o);
        double tanh_x = sinh_impl(x) / cosh_impl(x);
        return PyFloat_FromDouble(tanh_x);
    }
    ```

1. Adicione uma estrutura que define como a função `tanh_impl` do C++ é apresentada ao Python:

    ```cpp
    static PyMethodDef superfastcode_methods[] = {
        // The first property is the name exposed to Python, fast_tanh, the second is the C++
        // function name that contains the implementation.
        { "fast_tanh", (PyCFunction)tanh_impl, METH_O, nullptr },

        // Terminate the array with an object containing nulls.
        { nullptr, nullptr, 0, nullptr }
    };
    ```

1. Adicionar uma estrutura que define o módulo da maneira como você deseja fazer referência a ele em seu código Python, especificamente ao usar a instrução `from...import`. (Faça com que ela corresponda ao valor nas propriedades do projeto em **Propriedades de Configuração > Geral > Nome de Destino**.) No exemplo a seguir, o nome do módulo “superfastcode” significa que você pode usar `from superfastcode import fast_tanh` em Python, porque `fast_tanh` é definido em `superfastcode_methods`. (Nomes de arquivo internos ao projeto C++, como module.cpp, são irrelevantes.)

    ```cpp
    static PyModuleDef superfastcode_module = {
        PyModuleDef_HEAD_INIT,
        "superfastcode",                        // Module name to use with Python import statements
        "Provides some functions, but faster",  // Module description
        0,
        superfastcode_methods                   // Structure that defines the methods of the module
    };
    ```

1. Adicione um método que é chamado pelo Python quando ele carrega o módulo, que deve ser nomeado `PyInit_<module-name>`, em que *&lt;module_name&gt;* corresponde exatamente à propriedade **Geral > Nome de Destino** do Projeto do C++ (ou seja, ele corresponde ao nome de arquivo do `.pyd` criado pelo projeto).

    ```cpp
    PyMODINIT_FUNC PyInit_superfastcode() {
        return PyModule_Create(&superfastcode_module);
    }
    ```

1. Defina a configuração de destino como "Versão" e crie o projeto C++ novamente para verificar o código. Se você encontrar erros, verifique os seguintes casos:
    - Não é possível localizar Python.h: verifique se o caminho em **C/C++ > Geral > Diretórios de Inclusão Adicionais** nos pontos de propriedades do projeto aponta para a pasta `include` da instalação do Python.
    - Não é possível localizar as bibliotecas Python.h: verifique se o caminho em **Vinculador > Geral > Diretórios de Inclusão Adicionais** nos pontos de propriedades do projeto aponta para a pasta `libs` da instalação do Python.
    - Erros do vinculador relacionadas à arquitetura de destino: altere a arquitetura do projeto de destino C++ para corresponder à instalação do Python. Por exemplo, se você tiver como alvo x64 com o projeto C++, mas a instalação do Python for x86, altere o projeto C++ para ter como destino x86.

## <a name="test-the-code-and-compare-the-results"></a>Testar o código e comparar os resultados

Agora que você tem a DLL estruturada como uma extensão do Python, é possível consultá-la por meio do projeto do Python, importar o módulo e usar seus métodos.

### <a name="make-the-dll-available-to-python"></a>Disponibilizar a DLL para o Python

Há duas maneiras de disponibilizar a DLL para o Python.

O primeiro método funcionará se o projeto Python e o projeto C++ estiverem na mesma solução. Acesse o Gerenciador de Soluções, clique com o botão direito do mouse no nó **Referências** no projeto Python e, em seguida, selecione **Adicionar Referência**. Na caixa de diálogo que será exibida, selecione a guia **Projetos**, selecione o projeto **superfastcode** (ou qualquer nome que você esteja usando) e, em seguida, **OK**.

O método alternativo, descrito nas etapas a seguir, instala o módulo no ambiente Python global, tornando-o disponível para outros projetos Python também. (Fazer isso normalmente requer que você atualize o banco de dados de preenchimento do IntelliSense para esse ambiente no Visual Studio 2017 versão 15.5 e anterior. A atualização também é necessária ao remover o módulo do ambiente.)

1. Se estiver usando o Visual Studio 2017, execute o instalador do Visual Studio, selecione **Modificar** e selecione **Componentes Individuais > Compiladores, ferramentas de build e tempos de execução > conjunto de ferramentas do Visual C++ 2015.3 v140**. Essa etapa é necessária porque o Python (para o Windows) foi criado com o Visual Studio 2015 (versão 14.0) e espera que essas ferramentas estejam disponíveis durante o build de uma extensão por meio do método descrito aqui. (Observe que talvez seja necessário instalar uma versão de 32 bits do Python e direcionar a DLL para o Win32 e não para o x64).

1. Crie um arquivo chamado `setup.py` em seu projeto do C++, clicando com o botão direito do mouse no projeto e selecionando **Adicionar > Novo Item...**. Em seguida, selecione "Arquivo do C++ (.cpp)", nomeie o arquivo como `setup.py` e selecione **OK** (nomear o arquivo com a extensão `.py` faz com que o Visual Studio o reconheça como Python, apesar do uso do modelo do C++). Quando o arquivo for exibido no editor, cole o seguinte código nele:

    ```python
    from distutils.core import setup, Extension, DEBUG

    sfc_module = Extension('superfastcode', sources = ['module.cpp'])

    setup(name = 'superfastcode', version = '1.0',
        description = 'Python Package with superfastcode C++ extension',
        ext_modules = [sfc_module]
        )
    ```

    Consulte [Criando extensões do C e C++](https://docs.python.org/3/extending/building.html) (python.org) para ver a documentação sobre esse script.

1. O código `setup.py` instrui o Python a compilar a extensão usando o conjunto de ferramentas do C++ no Visual Studio 2015, quando usado na linha de comando. Abra um prompt de comandos com privilégios elevados, navegue até a pasta que contém o projeto C++ (ou seja, a pasta que contém `setup.py`) e digite o seguinte comando:

    ```command
    pip install .
    ```

### <a name="call-the-dll-from-python"></a>Chamar a DLL no Python

Depois de concluir um dos métodos acima, você poderá chamar a função `fast_tanh` do código Python e comparar seu desempenho com a implementação do Python:

1. Adicione as seguintes linhas no seu arquivo `.py` para chamar o método `fast_tanh` exportado da DLL e exibir a sua saída.

    ```python
    from superfastcode import fast_tanh
    test(lambda d: [fast_tanh(x) for x in d], '[fast_tanh(x) for x in d]')
    ```

1. Execute o programa Python (**Depurar > Iniciar Sem Depuração** ou Ctrl + F5) e observe que a rotina do C++ é executada com uma rapidez cinco a 20 vezes maior do que a implementação do Python. Novamente, tente aumentar a variável `COUNT` para que as diferenças sejam mais evidentes. Observe também que um build de depuração do módulo C++ é executado mais lentamente do que um build de liberação porque o build de depuração é menos otimizado e contém várias verificações de erro. Fique à vontade para alternar entre essas configurações para comparação.

## <a name="debug-the-c-code"></a>Depurar o código C++

O Visual Studio é compatível com a depuração de código de Python e C++ juntos.

1. Clique com o botão direito do mouse no projeto do Python, no Gerenciador de Soluções, selecione **Propriedades**, a guia **Depuração** e, em seguida, a opção **Depurar > Habilitar depuração de código nativo**.

    > [!Tip]
    > Ao habilitar a depuração de código nativo, a janela de saída do Python poderá desaparecer imediatamente quando o programa tiver concluído sem fornecer a pausa comum “Pressione qualquer tecla para continuar...”. Para forçar uma pausa, adicione a opção `-i` ao campo **Executar > Argumentos do Interpretador** na guia **Depurar** ao habilitar a depuração de código nativo. Esse argumento coloca o interpretador do Python no modo interativo após a conclusão do código e, nesse ponto, ele aguarda até que você pressione Ctrl + Z, Enter para sair. (Como alternativa, se você não se importar em modificar o código do Python, poderá adicionar as instruções `import os` e `os.system("pause")` ao final do programa. Esse código duplicará o prompt de pausa original.)

1. Selecione **Arquivo > Salvar** para salvar as alterações de propriedade.

1. Defina a configuração de build como "Depurar" na barra de ferramentas do Visual Studio.

    ![Definir a configuração de build como Depuração](media/cpp-set-debug.png)

1. Como o código geralmente demora mais para ser executado no depurador, talvez seja interessante alterar a variável `COUNT` no seu arquivo `.py` para um valor que seja cerca de cinco vezes menor (por exemplo, altere-o de `500000` para `100000`).

1. No código do C++, defina um ponto de interrupção na primeira linha do método `tanh_impl` e, em seguida, inicie o depurador (F5 ou **Depurar > Iniciar Depuração**). O depurador para quando esse código é chamado. Se o ponto de interrupção não for atingido, verifique se a configuração está definida como Depuração e que você salvou o projeto (o que não acontece automaticamente ao iniciar o depurador).

    ![Parando em um ponto de interrupção no código C++](media/cpp-debugging.png)

1. Neste ponto, você poderá executar o código C++ em etapas, examinar variáveis e assim por diante. Esses recursos são detalhados em [Depuração de C++ e Python juntos](debugging-mixed-mode-c-cpp-python-in-visual-studio.md).

## <a name="alternative-approaches"></a>Abordagens alternativas

Há uma variedade de meios para criar extensões Python, conforme descrito na tabela a seguir. A primeira entrada para CPython é a que já foi discutida neste artigo.

| Abordagem | Ano | Usuários representantes | Vantagens | Desvantagens |
| --- | --- | --- | --- | --- |
| Módulos de extensão do C/C++ para o CPython | 1991 | Biblioteca Padrão | [Tutoriais e documentação abrangente](https://docs.python.org/3/c-api/). Controle total. | Compilação, portabilidade, gerenciamento de referências. Profundo conhecimento sobre o C. |
| SWIG | 1996 | [crfsuite](http://www.chokkan.org/software/crfsuite/) | Gere associações para várias linguagens de uma só vez. | Sobrecarga excessiva se o Python for o único destino. |
| ctypes | 2003 | [oscrypto](https://github.com/wbond/oscrypto) | Sem compilação, ampla disponibilidade. | O acesso e a mutação de estruturas do C são complicados e sujeitos a erros. |
| Cython | 2007 | [gevent](http://www.gevent.org/), [kivy](https://kivy.org/) | Semelhante ao Python. Altamente maduro. Alto desempenho. | Compilação, nova sintaxe, nova cadeia de ferramentas. |
| cffi | 2013 | [cryptography](https://cryptography.io/en/latest/), [pypy](http://pypy.org/) | Facilidade de integração, compatibilidade com o PyPy. | Novo, menos maduro. |
