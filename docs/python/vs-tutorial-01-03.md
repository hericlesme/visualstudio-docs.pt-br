---
title: Trabalhando com o Python no Visual Studio, etapa 3 | Microsoft Docs
ms.custom: 
ms.date: 10/16/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: get-started-article
ms.assetid: 5d6d12e4-f06a-4c3f-8efa-f9fd9711c942
caps.latest.revision: "1"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.openlocfilehash: b8756ea30b3ca0e86f23dcad7ed4ed73826cbaaa
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="step-3-using-the-interactive-repl-window"></a>Etapa 3: usando a janela interativa REPL

**Etapa anterior: [escrevendo e executando código](vs-tutorial-01-02.md)**

A *janela interativa* do Visual Studio para Python oferece uma experiência avançada de REPL (leitura-avaliação-impressão-loop), que reduz consideravelmente o ciclo comum de edição-build-depuração. A janela interativa fornece todos os recursos da experiência de REPL da linha de comando do Python. Ela também facilita a troca de código com arquivos de origem no editor do Visual Studio, o que seria difícil com a linha de comando.

1. Abra a janela interativa clicando com o botão direito do mouse no ambiente de projeto do Python no Gerenciador de Soluções (como "Python 3.6 (32 bits)", mostrado em um gráfico anterior) e selecionando **Abrir Janela Interativa**. Como alternativa, você pode selecionar **Exibir > Outras Janelas > Janelas Interativas do Python** no menu principal do Visual Studio.

1. A janela interativa abre-se abaixo do editor com o prompt habitual `>>>` de REPL do Python. Se você quiser deixar a janela interativa maior, arraste o separador entre as duas janelas:

    ![Janela interativa Python: arrastando para redimensionar](media/vs-getting-started-python-11-interactive1b.png)

    > [!Tip]
    > Você pode redimensionar todas as janelas no Visual Studio, arrastando os separadores de bordas. Você também pode arrastar e retirar janelas para fora do quadro do Visual Studio e reorganizá-las da forma que quiser dentro do quadro. Para obter detalhes completos, consulte <a href="https://docs.microsoft.com/visualstudio/ide/customizing-window-layouts-in-visual-studio" target="_blank">Personalizando layouts de janela</a>.

1. Insira algumas instruções, como `print("Hello, Visual Studio")`, e expressões, como `123/456`, para ver resultados imediatos:

    ![Resultados imediatos da janela interativa do Python](media/vs-getting-started-python-12-interactive2.png)

1. Ao começar a escrever uma instrução de várias linhas, como uma definição de função, a janela interativa mostrará o prompt `...` do Python para linhas em continuação, o que, ao contrário do REPL de linha de comando, proporcionará recuo automático:

    ![Janela interativa do Python com continuação de instrução](media/vs-getting-started-python-13-interactive3.png)

1. A janela interativa fornece um histórico completo de tudo o que foi inserido e é uma melhoria do REPL de linha de comando com itens de histórico de várias linhas. Por exemplo, com facilidade, é possível cancelar toda a definição da função `f` como uma única unidade e alterar o nome para `make_double`, em vez de recriar a função linha por linha.

1. O Visual Studio pode enviar várias linhas de código de uma janela do editor para a janela interativa. Essa capacidade permite que você mantenha o código em um arquivo de origem e envie facilmente partes específicas dele para a janela interativa. Assim, você poderá trabalhar com esses fragmentos de código no ambiente REPL rápido em vez de ter que executar o programa inteiro. Para ver esse recurso, primeiro substitua o loop `for` no arquivo `PythonApplication1.py` pelo seguinte:

    ```python
    # Create a string with spaces proportional to a cosine of x in degrees
    def make_dot_string(x):  
        return ' ' * int(20 * cos(radians(x)) + 20) + 'o'
    ```

1. Selecione apenas as instruções `import` e `from` no arquivo `.py`, clique com o botão direito do mouse e selecione **Enviar para Interactive** (ou pressione CTRL + ENTER). O fragmento de código será imediatamente colado na janela interativa e executado. Agora selecione a função `make_dot_string` e repita o mesmo comando, que executa novamente esse fragmento de código. Como o código define uma função, é possível testar essa função rapidamente chamando-a algumas vezes:

    ![Enviando o código para a janela interativa e testando-o](media/vs-getting-started-python-14-interactive4.png)

    > [!Tip]
    > O uso de CTRL + ENTER no editor *sem* uma seleção, executará a linha de código atual na janela interativa e posicionará automaticamente o cursor na próxima linha. Com esse recurso, ao pressionar CTRL + ENTER repetidamente você terá uma maneira conveniente de percorrer o código, o que não é possível somente com a linha de comando do Python. Isso também permitirá que você percorra o código sem executar o depurador e sem, necessariamente, começar desde o início do programa.

1. Você também pode copiar e colar várias linhas de código de qualquer fonte na janela interativa, como no trecho a seguir, o que é difícil fazer com o REPL da linha de comando do Python. Ao colar, a janela interativa executa o código como se você o tivesse digitado:

    ```python
    for i in range(360):
        s = make_dot_string(i)  
        print(s) 
    ```

    ![Colando várias linhas de código usando o comando Enviar para Interativa](media/vs-getting-started-python-15-interactive5.png)

1. Como você pode ver, esse código funciona bem, mas a saída não é muito interessante. Um valor de etapa diferente no loop `for` mostraria mais da curva do cosseno. Felizmente, como todo o loop `for` está no histórico do REPL como uma única unidade, é fácil voltar e fazer as alterações desejadas e, em seguida, testar a função novamente. Pressione a seta para cima para, primeiro, recuperar o loop `for`. Em seguida, pressione as setas à esquerda ou direita para iniciar a navegação no código (até que você faça isso, as setas para baixo e para cima continuam a percorrer o histórico). Navegue até a especificação `range` e altere-a para `range(0, 360, 12)`. Em seguida, pressione CTRL + ENTER (em qualquer lugar no código) para executar toda a instrução novamente:

    ![Edição de uma declaração anterior na janela interativa](media/vs-getting-started-python-16-interactive6.png)

1. Repita o processo para fazer experiências com configurações de etapas diferentes, até encontrar um valor que você mais goste. Você também pode fazer a curva se repetir, aumentando o intervalo, por exemplo, `range(0, 1800, 12)`.
 
1. Quando estiver satisfeito com o código escrito na janela interativa, selecione-o, clique com o botão direito do mouse e selecione **Copiar Código** (CTRL+SHIFT+C) e, em seguida, cole-o no editor. Observe como esse recurso especial do Visual Studio omite automaticamente qualquer saída, bem como os prompts `>>>` e `...`. Por exemplo, a imagem abaixo mostra o uso do comando **Copiar Código** em uma seleção que inclui os prompts e a saída:

    ![Comando copiar código da janela interativa em uma seleção com prompts e saída](media/vs-getting-started-python-17-interactive7.png)

    Ao colar no editor, você obtém somente o código:

    ```python
    for i in range(0, 1800, 12):
        s = make_dot_string(i)  
        print(s) 
    ```

    Se quiser copiar o conteúdo exato da janela interativa, incluindo os prompts e a saída, basta usar o comando **Copiar** padrão.

1. O que você acabou de fazer é usar o ambiente de REPL rápido da janela interativa para trabalhar em detalhes de uma pequena parte de código e, em seguida, adicionou convenientemente esse código ao arquivo de origem do seu projeto. Agora, ao executar o código novamente com CTRL + F5 (ou **Depurar > Iniciar Sem Depurar**), você verá exatamente os resultados desejados.


## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Executando o código no depurador](vs-tutorial-01-04.md)

### <a name="going-deeper"></a>Aprofundando-se

- [Usando a Janela interativa](interactive-repl.md)
- [Usando o IPython REPL](interactive-repl-ipython.md)
