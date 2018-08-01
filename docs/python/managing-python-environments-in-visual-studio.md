---
title: Gerenciar ambientes e interpretadores Python
description: Use a janela Ambientes Python para gerenciar ambientes globais, virtuais e conda, para instalar interpretadores e pacotes Python e atribuir ambientes a projetos do Visual Studio.
ms.date: 07/23/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 2b134dc54e2af31bb7d9fcb3f1dcdf3d31f799b5
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/24/2018
ms.locfileid: "39232212"
---
# <a name="how-to-create-and-manage-python-environments-in-visual-studio"></a>Como criar e gerenciar ambientes Python no Visual Studio

Um *ambiente* Python é um contexto em que você executa o código Python e inclui ambientes globais, virtuais e conda. Um ambiente é composto por um interpretador, uma biblioteca (normalmente a Biblioteca Padrão do Python) e um conjunto de pacotes instalados. Juntos, esses componentes determinam quais constructos de linguagem e qual sintaxe são válidos, qual funcionalidade do sistema operacional pode ser acessada e quais pacotes podem ser usados.

No Visual Studio no Windows, a janela [Janela Ambientes do Python](#the-python-environments-window), conforme descrito neste artigo, é o local em que você gerencia esses ambientes e seleciona um como padrão para novos projetos. Para qualquer projeto, também é possível [selecionar um ambiente específico](selecting-a-python-environment-for-a-project.md), em vez de usar o padrão.

**Observação**: se você for um novo usuário do Python no Visual Studio, veja os seguintes artigos para obter as informações necessárias:

- [Trabalhando com o Python no Visual Studio](overview-of-python-tools-for-visual-studio.md)
- [Instalando o suporte do Python no Visual Studio](installing-python-support-in-visual-studio.md)

Observe também que você não pode gerenciar ambientes para código Python abertos somente como uma pasta usando o comando **Arquivo** > **Abrir** > **Pasta**. Em vez disso, [Crie um projeto em Python com o código existente](quickstart-01-python-in-visual-studio-project-from-existing-code.md) para aproveitar os recursos do ambiente do Visual Studio.

Se desejar instalar pacotes em um ambiente, confira a [referência da guia Pacotes](python-environments-window-tab-reference.md#packages-tab).

## <a name="types-of-environments"></a>Tipos de ambientes

### <a name="global-environments"></a>Ambientes globais

Cada instalação do Python (por exemplo, Python 2.7, Python 3.6, Anaconda 4.4.0 etc., confira [Selecionar e instalar interpretadores Python](installing-python-interpreters.md)) mantém seu próprio ambiente global. Cada ambiente é composto pelo interpretador do Python específico, sua biblioteca padrão e por um conjunto de pacotes pré-instalados. A instalação de um pacote em um ambiente global o torna disponível para todos os projetos que usam esse ambiente. Se o ambiente estiver em uma área de proteção do sistema de arquivos (dentro de `c:\program files`, por exemplo), a instalação de pacotes exigirá privilégios de administrador.

Os ambientes globais estão disponíveis para todos os projetos no computador. No Visual Studio, selecione um ambiente global como o padrão, que é usado para todos os projetos, a menos que você escolha especificamente um diferente para um projeto. Para saber mais, confira [Selecionar um ambiente para um projeto](selecting-a-python-environment-for-a-project.md).

### <a name="virtual-environments"></a>Ambientes virtuais

Como os pacotes instalados em um ambiente global estão disponíveis para todos os projetos que usam esse ambiente, poderão ocorrer conflitos quando dois projetos exigirem pacotes incompatíveis ou versões diferentes do mesmo pacote. Ambientes virtuais evitam esses conflitos usando o interpretador e a biblioteca padrão de um ambiente global, mas mantêm seus próprios armazenamentos de pacote em pastas isolados.

No Visual Studio, é possível criar um ambiente virtual para um projeto específico, que é armazenado em uma subpasta no projeto. O Visual Studio fornece um comando para gerar um arquivo `requirements.txt` do ambiente virtual, tornando mais fácil recriar o ambiente em outros computadores. Para saber mais, confira [Usar ambientes virtuais](selecting-a-python-environment-for-a-project.md#using-virtual-environments).

### <a name="conda-environments"></a>Ambientes do Conda

Um ambiente do conda é aquele criado usando a ferramenta `conda`, ou com o gerenciamento do conda integrado no Visual Studio 2017 versão 15.7 e superior. (Exige o Anaconda ou Miniconda; o Anaconda está disponível por meio do instalador do Visual Studio. Consulte [Instalação – Visual Studio 2017](installing-python-support-in-visual-studio.md#visual-studio-2017).)

> [!Note]
> Para obter melhores resultados com ambientes do conda, use o conda 4.4.8 ou posterior (as versões do conda são diferentes das versões do Anaconda). Instalando o Anaconda 5.1 por meio do instalador do Visual Studio 2017

Para ver a versão do conda, na qual os ambientes do conda são armazenados, bem como outras informações, execute `conda info` em um prompt de comando do Anaconda (ou seja, um prompt de comando no qual o Anaconda está no caminho):

```cli
conda info
```

As pastas de ambiente do conda são exibidas da seguinte maneira:

```output
       envs directories : c:\anaconda3\envs
                          C:\Users\user\AppData\Local\conda\conda\envs
                          C:\Users\user\.conda\envs
```

Como os ambientes do conda não são armazenados com um projeto, eles atuam da mesma forma para ambientes globais. Por exemplo, a instalação de um novo pacote em um ambiente do conda torna esse pacote disponível para todos os projetos que usam esse ambiente.

Para o Visual Studio 2017 versão 15.6 e anterior, você pode usar ambientes do conda apontando-os manualmente, conforme descrito em [Identificar manualmente um ambiente existente](#manually-identify-an-existing-environment).

O Visual Studio 2017 versão 15.7 e posterior detecta ambientes do conda automaticamente e exibe-os na janela **Ambientes do Python**, conforme descrito na próxima seção.

## <a name="the-python-environments-window"></a>A janela Ambientes do Python

Os ambientes conhecidos pelo Visual Studio são exibidos na janela **Ambientes Python**. Para abrir a janela, use um dos seguintes métodos:

- Selecione o comando de menu **Exibir** > **Outras Janelas** > **Ambientes do Python**.
- Clique com o botão direito no nó **Ambientes do Python** de um projeto no Gerenciador de Soluções e selecione **Exibir Todos os Ambientes do Python**:

    ![Comando Exibir Todos os Ambientes no Gerenciador de Soluções](media/environments-view-all.png)

Em ambos os casos, a janela **Ambientes do Python** é exibida como uma guia irmã do Gerenciador de Soluções:

![Janela Ambientes do Python](media/environments-default-view.png)

O Visual Studio segue o [PEP 514](https://www.python.org/dev/peps/pep-0514/) para identificar os ambientes instalados usando o Registro. Se um ambiente esperado na lista não for exibido, confira [Manually identify an existing environment](#manually-identify-an-existing-environment) (Identificar manualmente um ambiente existente).

Selecionar um ambiente na lista exibe várias propriedades e comandos para esse ambiente na guia **Visão geral**. Por exemplo, é possível ver na imagem acima que o local do interpretador é `C:\Python36-32`. Use a lista suspensa embaixo da lista de ambientes para alternar para diferentes guias como **Pacotes** e **IntelliSense**. Essas guias são descritas na [referência à guia da janela Ambientes do Python](python-environments-window-tab-reference.md).

Selecionar um ambiente não o ativa de nenhuma maneira. O ambiente padrão, mostrado em negrito na lista, é o ambiente ativado no momento que o Visual Studio usa para projetos novos. Para ativar um ambiente diferente, use o comando **Tornar esse o ambiente padrão para novos projetos**. Dentro do contexto de um projeto, sempre é possível ativar um ambiente diferente. Para saber mais, confira [Selecionar um ambiente para um projeto](selecting-a-python-environment-for-a-project.md).

À direita de cada ambiente listado está um controle que abre uma janela interativa para esse ambiente. (No Visual Studio 2017 15.5 e anterior, é exibido outro controle que atualiza o banco de dados do IntelliSense para esse ambiente. Confira [Environments window tab reference](python-environments-window-tab-reference.md#intellisense-tab) (Referência à guia da janela Ambientes) para obter detalhes sobre o banco de dados).

> [!Tip]
> Ao expandir a janela **Ambientes do Python** até o tamanho suficiente, você obtém uma exibição mais completa de seus ambientes que pode ser mais conveniente para trabalhar.
>
> ![Exibição expandida da janela Ambientes do Python](media/environments-expanded-view.png)

> [!Note]
> Embora o Visual Studio respeite a opção de pacotes de site do sistema, ele não fornece uma maneira de alterá-lo no próprio Visual Studio.

|   |   |
|---|---|
| ![ícone de câmera para vídeo](../install/media/video-icon.png "Assistir a um vídeo") | [Assista a um vídeo (Microsoft Virtual Academy)](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121?l=qrDmN4LWE_8305918567) sobre os ambientes do Python no Visual Studio (2min35s).|

### <a name="what-if-no-environments-appear"></a>E se nenhum ambiente aparecer?

Se nenhum ambiente aparecer, isso significa que o Visual Studio não conseguiu detectar as instalações de Python nos locais padrão. Por exemplo, você pode ter instalado o Visual Studio 2017 mas limpou todas as opções de interpretador nas opções do instalador para a carga de trabalho do Python. Da mesma forma, você pode ter instalado o Visual Studio 2015 ou anterior, mas não instalou um interpretador manualmente (confira [Como instalar interpretadores Python](installing-python-interpreters.md)).

Se você souber que tem um intérprete Python em seu computador, mas o Visual Studio (qualquer versão) não detectá-lo, use o comando **+Personalizado...**  para especificar o local manualmente. Consulte a próxima seção, [Identificar manualmente um ambiente existente](#manually-identify-an-existing-environment).

> [!Tip]
> O Visual Studio detecta atualizações para um interpretador existente, como a atualização do Python 2.7.11 para 2.7.14 usando os instaladores de python.org. Durante o processo de instalação, o ambiente mais antigo desaparece da lista **Ambientes Python** antes de a atualização aparecer em seu lugar.
>
> No entanto, se você mover manualmente um interpretador e seu ambiente usando o sistema de arquivos, o Visual Studio não saberá o novo local. Para saber mais, veja [Mover um intérprete](installing-python-interpreters.md#moving-an-interpreter).

## <a name="fix-or-delete-invalid-environments"></a>Corrigir ou excluir ambientes inválidos

Se o Visual Studio encontra entradas de Registro para um ambiente, mas o caminho para o interpretador é inválido, a janela Ambientes do Python mostra o nome com uma fonte riscada:

![A janela Ambientes do Python mostrando um ambiente inválido](media/environments-invalid-entry.png)

Para corrigir um ambiente que você deseja manter, primeiro tente usar o processo **Reparar** do instalador dele. Os instaladores para o Python 3.x padrão, por exemplo, incluem essa opção.

Para corrigir um ambiente que não tem uma opção de reparo, ou para remover um ambiente inválido, use as etapas a seguir para modificar o Registro diretamente. O Visual Studio atualiza automaticamente a janela Ambientes do Python quando você faz alterações no Registro.

1. Execute `regedit.exe`.
1. Navegue até `HKEY_LOCAL_MACHINE\SOFTWARE\Python` para interpretadores de 32 bits ou `HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Python` para interpretadores de 64 bits. Para o IronPython, procure por `IronPython`.
1. Expanda o nó que corresponde à distribuição, como `PythonCore` para o CPython ou `ContinuumAnalytics` para o Anaconda. Para o IronPython, expanda o nó de número de versão.
1. Inspecione os valores sob o nó `InstallPath`:

    ![Entradas do Registro para uma instalação típica do CPython](media/environments-registry-entries.png)

    - Se o ambiente ainda existir no computador, altere o valor de `ExecutablePath` para o local correto. Corrija também os valores `(Default)` e `WindowedExecutablePath` conforme necessário.
    - Se o ambiente não existir mais no computador e você desejar removê-lo da janela Ambientes do Python, exclua o nó pai de `InstallPath`, tais como `3.6` na imagem acima.

<a name="manually-identifying-an-existing-environment"></a>

## <a name="manually-identify-an-existing-environment"></a>Identificar manualmente um ambiente existente

Use as seguintes etapas para identificar um ambiente instalado em um local não padrão (incluindo ambientes do conda no Visual Studio 2017 versão 15.6 e posterior):

1. Selecione **+ Personalizado** na janela **Ambientes do Python**, que abre a guia **Configurar**:

    ![Exibição padrão de um novo ambiente personalizado](media/environments-custom-1.png)

1. Insira um nome para o ambiente no campo **Descrição**.

1. Insira ou procure (usando **...***) o caminho do interpretador no campo **Caminho do prefixo**.

1. Se o Visual Studio detectar um interpretador Python nessa localização (como o caminho mostrado abaixo para um ambiente de conda), ele habilitará o comando **Detecção Automática**. Selecionar **Detecção Automática* preenche os campos restantes. Você também pode preencher esses campos manualmente.

    ![Habilitar o comando Detecção Automática](media/environments-custom-2.png)

    ![Preenchimento dos campos de ambiente depois de usar a Detecção Automática](media/environments-custom-3.png)

1. Quando os campos contiverem os valores desejados, selecione **Aplicar** para salvar a configuração. Agora, você pode usar o ambiente como qualquer outro no Visual Studio.

1. Se você precisar remover um ambiente identificado manualmente, selecione o comando **Remover** na guia **Configurar**. Ambientes detectados automaticamente não oferecem essa opção. Para saber mais, confira [Guia Configurar](python-environments-window-tab-reference.md#configure-tab).

## <a name="create-a-conda-environment"></a>Criar um ambiente do conda

*Visual Studio 2017 versão 15.7 e posteriores.*

1. Selecione **+ Criar ambiente do conda** na janela **Ambientes do Python**, que abre uma guia **Criar novo ambiente do conda**:

    ![Criar uma guia para um novo ambiente do conda](media/environments-conda-1.png)

1. Insira um nome para o ambiente no campo **Nome**, selecione um interpretador base do Python no campo **Python** e selecione **Criar**.

1. A janela **Saída** mostra o progresso do novo ambiente, com algumas instruções da CLI após a conclusão da criação:

    ![Criação bem-sucedida de um ambiente do conda](media/environments-conda-2.png)

1. No Visual Studio, você pode ativar um ambiente do conda para um projeto da mesma forma como faria com qualquer outro ambiente, conforme descrito em [Selecionando um ambiente para um projeto](selecting-a-python-environment-for-a-project.md).

1. Para instalar pacotes no ambiente, use a [guia Pacotes](python-environments-window-tab-reference.md#packages-tab).

## <a name="see-also"></a>Consulte também

- [Instalar interpretadores do Python](installing-python-interpreters.md)
- [Selecionar um intérprete para um projeto](selecting-a-python-environment-for-a-project.md)
- [Usando requirements.txt para dependências](managing-required-packages-with-requirements-txt.md)
- [Caminhos de pesquisa](search-paths.md)
- [Referência à janela Ambientes do Python](python-environments-window-tab-reference.md)
