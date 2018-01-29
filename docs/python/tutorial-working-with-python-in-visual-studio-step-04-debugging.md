---
title: "Trabalhar com o Python no Visual Studio, Etapa 4, Depuração | Microsoft Docs"
description: "Etapa 4 de um tutorial básico para trabalhar com Python no Visual Studio, abordando como executar código Python no depurador."
ms.custom: 
ms.date: 01/16/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: get-started-article
caps.latest.revision: 
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: 6924f4a4b3c2f0b4319af14ab8518bf01eaab912
ms.sourcegitcommit: bd16e764134c436d2d2f46490f51234d5246ee50
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/22/2018
---
# <a name="step-4-running-code-in-the-debugger"></a>Etapa 4: executando o código no depurador

**Etapa anterior: [usando a janela interativa REPL](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md)**

Além de gerenciar projetos, fornecer uma experiência de edição avançada e a janela interativa, o Visual Studio fornece depuração completa para código do Python. No depurador, você pode executar seu código passo a passo, incluindo cada iteração de um loop. Você também pode pausar o programa sempre que determinadas condições são verdadeiras. A qualquer momento em que o programa estiver em pausa no depurador, você poderá examinar todo o estado do programa e alterar o valor de variáveis. Essas ações são essenciais para a localização de bugs do programa e também fornecem recursos muito úteis para seguir com cuidado o fluxo exato do programa.

1. Substitua o código no arquivo `PythonApplication1.py` pelo seguinte. Essa variação do código expande o `make_dot_string` para que você possa examinar as etapas distintas no depurador. Ela também coloca o loop `for` em uma função `main` e executa-o explicitamente, chamando essa função:

    ```python
    import sys
    from math import sin, cos, radians

    # Create a string with spaces proportional to a cosine of x in degrees
    def make_dot_string(x):
        rad = radians(x)                             # cos works with radians
        numspaces = int(20 * cos(radians(x)) + 20)   # scale to 0-40 spaces
        str = ' ' * numspaces + 'o'                  # place 'o' after the spaces
        return str

    def main():
        for i in range(0, 1800, 12):
            s = make_dot_string(i)
            print(s)

    main()
    ```

1. Verifique se o código funciona corretamente pressionando F5 ou selecionando o comando de menu **Depurar > Iniciar Depuração**. Esse comando executa o código no depurador, mas como você não fez nada para pausar o programa enquanto ele está em execução, ele apenas imprime um padrão de onda para algumas iterações. Pressione qualquer tecla para fechar a janela de saída.

    > [!Tip]
    > Para fechar a janela de saída automaticamente quando o programa for concluído, substitua a chamada `main()` pelo seguinte código:
    >
    > ```python
    > if __name__ == "__main__":
    >     sys.exit(int(main() or 0))
    > ```

1. Defina um ponto de interrupção na instrução `for` clicando uma vez na margem cinza próxima a essa linha ou colocando o cursor na linha e usando o comando **Depurar > Ativar/Desativar Ponto de Interrupção** (F9). Um ponto vermelho é exibido na margem cinza para indicar o ponto de interrupção (conforme indicado pela seta abaixo):

    ![Configurando um ponto de interrupção](media/vs-getting-started-python-18-debugging1.png)

1. Inicie o depurador novamente (F5) e veja que a execução do código é interrompida na linha com o ponto de interrupção. Aqui você pode inspecionar a pilha de chamadas e examinar variáveis. As variáveis que estão no escopo aparecem na janela **Autos** quando elas estão definidas. Você também pode alternar para a exibição **Locais** na parte inferior dessa janela para mostrar todas as variáveis que o Visual Studio localiza no escopo atual (incluindo funções), antes mesmo que elas sejam definidas:

    ![Experiência de interface do usuário do ponto de interrupção para o Python](media/vs-getting-started-python-19-debugging2b.png)

1. Observe a barra de ferramentas de depuração (mostrada abaixo) na parte superior da janela do Visual Studio. Essa barra de ferramentas fornece acesso rápido aos comandos de depuração mais comuns (que também podem ser encontrados no menu **Depurar**):

    ![Botões da barra de ferramentas de depuração essenciais](media/vs-getting-started-python-20-debugging3.png)

    Os botões, da esquerda para a direita, são os seguintes:
    - **Continuar** (F5) executa o programa, até o próximo ponto de interrupção ou até a conclusão do programa.
    - **Interromper Tudo** (CTRL + ALT + BREAK) pausa um programa de execução longa.
    - **Interromper a Depuração** (SHIFT + F5) interrompe o programa no ponto em que está e sai do depurador.
    - **Reiniciar** (CTRL + SHIFT + F5) interrompe o programa no ponto em que está e o reinicia no depurador.
    - **Mostrar Próxima Instrução** (ALT + NUM *) alterna para a próxima linha de código a ser executada. Isso é mais útil quando você navega em seu código durante uma sessão de depuração e deseja retornar rapidamente ao ponto em que o depurador está em pausa.
    - **Intervir** (F11) executa a próxima linha de código, entrando em funções chamadas.
    - **Contornar** (F10) executa a próxima linha de código sem entrar em funções chamadas.
    - **Sair** (SHIFT + F11) executa o restante da função atual e pausa no código de chamada.

1. Contorne a instrução `for` usando **Contornar**. *Passo a passo* significa que o depurador executa a linha de código atual, incluindo todas as chamadas de função e, em seguida, imediatamente entra em pausa outra vez. Observe como a variável `i` agora está definida nas janelas **Locais** e **Autos**.

1. Contorne a próxima linha de código, que chama `make_dot_string` e entra em pausa. Aqui o Contorno significa especificamente que o depurador executa todo o `make_dot_string` e entra em pausa ao retornar. O depurador não é interrompido dentro dessa função, a menos que exista nela outro ponto de interrupção.

1. Continue depurando o código passo a passo mais algumas vezes e observe como os valores na janela **Locais** ou **Autos** se alteram.

1. Na janela **Locais** ou **Autos**, clique duas vezes na coluna **Valor** das variáveis `i` ou `s` para editar o valor. Pressione Enter ou clique fora desse valor para aplicar as alterações.

1. Continuar percorrendo o código passo a passo, usando **Intervir**. Intervir significa que o depurador entra dentro de qualquer chamada de função para a qual ele tenha informações de depuração, como `make_dot_string`. Uma vez dentro do `make_dot_string`, você pode examinar as variáveis locais e percorrer o código especificamente.

1. Continue depurando passo a passo com Intervir e observe que, ao chegar ao fim do `make_dot_string`, a próxima etapa retorna para o loop `for` com o novo valor retornado na variável `s`. Conforme você avança novamente para a instrução `print`, observe que o Intervir em `print` não entra nessa função. Isso ocorre porque `print` não está escrita em Python, mas é código nativo dentro do tempo de execução do Python.

1. Continue usando Intervir até que você esteja novamente quase em `make_dot_string`. Então, use **Sair** e observe que você retornará ao loop `for`. Com Sair, o depurador executa o restante da função e, em seguida, faz automaticamente uma pausa no código de chamada. Isso é muito útil quando você percorreu algumas partes de uma função longa que deseja depurar, mas não deseja percorrer o restante e não quer definir um ponto de interrupção explícito no código de chamada.

1. Para continuar a execução do programa até que o próximo ponto de interrupção seja atingido, use **Continuar** (F5). Como há um ponto de interrupção no loop `for`, você interromperá na próxima iteração.

1. Percorrer centenas de iterações de um loop pode ser entediante, portanto, o Visual Studio permite que você adicione uma *condição* a um ponto de interrupção. Assim, o depurador só pausa o programa no ponto de interrupção quando a condição é satisfeita. Por exemplo, você pode usar uma condição com o ponto de interrupção na instrução `for` para que ele faça uma pausa somente quando o valor de `i` exceder 1600. Para definir essa condição, clique com o botão direito do mouse no ponto de interrupção e selecione **Condições...** (ALT + F9, C). Na janela pop-up **Configurações de Ponto de Interrupção** exibida, insira `i > 1600` como a expressão e selecione **Fechar**. Pressione F5 para continuar e observe que o programa executa muitas iterações antes da próxima interrupção.

    ![Configurando uma condição de ponto de interrupção](media/vs-getting-started-python-21-debugging4.png)

1. Para executar o programa até a conclusão, desabilite o ponto de interrupção clicando com o botão direito do mouse e selecionando **Desabilitar ponto de interrupção** (CTRL + F9). Em seguida, selecione **Continuar** (ou pressione F5) para executar o programa. Quando o programa for finalizado, o Visual Studio interromperá a sessão de depuração e retornará para o modo de edição. Observe que você também pode excluir o ponto de interrupção ao clicar em seu ponto, mas isso também excluirá qualquer condição que você definiu.

> [!Tip]
> Em algumas situações, como uma falha ao iniciar o interpretador do Python em si, a janela de saída poderá aparecer apenas rapidamente e fechar-se automaticamente, sem dar uma oportunidade de ver as mensagens de erros. Se isso acontecer, clique com botão direito do mouse no projeto no Gerenciador de Soluções, selecione **Propriedades**, selecione a guia **Depurar** e, em seguida, adicione `-i` ao campo **Argumentos do Interpretador**. Esse argumento faz com que o interpretador entre no modo interativo após a conclusão de um programa, mantendo a janela aberta até que você pressione CTRL + Z, Enter para sair.

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Instalando pacotes no ambiente do Python](tutorial-working-with-python-in-visual-studio-step-05-installing-packages.md)

### <a name="going-deeper"></a>Aprofundando-se

- [Depuração](debugging.md).
- [Depuração no Visual Studio](../debugger/debugger-feature-tour.md) oferece uma documentação completa sobre os recursos de depuração do Visual Studio.
