---
title: Depurar o ASP.NET
description: Depurar o ASP.NET usando o depurador do Visual Studio
ms.custom: mvc
ms.date: 08/06/2018
ms.technology: vs-ide-debug
ms.topic: quickstart
helpviewer_keywords:
- debugger
ms.assetid: f4cea2e1-08dc-47ac-aba2-3b8c338e607f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: 74671401b3e3eaeae5840110dfc37c926266f98a
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39636981"
---
# <a name="quickstart-debug-aspnet-with-the-visual-studio-debugger"></a>Guia de início rápido: Depurar o ASP.NET com o depurador do Visual Studio

O depurador do Visual Studio fornece muitos recursos poderosos para ajudar a depurar seus aplicativos. Este tópico fornece uma maneira rápida de conhecer alguns dos recursos básicos.

## <a name="create-a-new-project"></a>Criar um novo projeto 

1. No Visual Studio, escolha **Arquivo > Novo Projeto**.

1. Sob **Visual c#**, escolha **Web**e, em seguida, no painel central, escolha **aplicativo Web ASP.NET Core**.

1. Digite um nome como **MyDbgApp** e clique em **Okey**.

1. Na caixa de diálogo que aparece, escolha **aplicativo Web** no painel central e clique **Okey**.

     Se você não vir as **aplicativo Web** modelo de projeto, clique no **abrir instalador do Visual Studio** link no painel esquerdo do **novo projeto** caixa de diálogo. O Instalador do Visual Studio é iniciado. Escolha a carga de trabalho **ASP.NET e desenvolvimento para a Web** e, em seguida, selecione **Modificar**.

    ![Escolha um aplicativo Web](../debugger/media/dbg-qs-aspnet-choose-web-app.png)

    O Visual Studio cria o projeto.

1. No Gerenciador de soluções, abra About.cshtml.cs (sob Pages) e substitua o código a seguir

    ```csharp
    public void OnGet()
    {
        Message = "Your application description page.";
    }
    ```

    com este código:

    ```csharp
    public void OnGet()
    {
        LinkedList<int> result = doWork();
        Message = "Result of work: " + result.First.Value + ", " + result.First.Value;
    }

    private static LinkedList<int> doWork()
    {
        LinkedList<int> c1 = new LinkedList<int>();

        c1.AddLast(10);
        c1.AddLast(20);

        LinkedList<int> c2 = new LinkedList<int>(c1);

        return c2;

    }
    ```

## <a name="set-a-breakpoint"></a>Definir um ponto de interrupção

Um *ponto de interrupção* é um marcador que indica onde o Visual Studio deve suspender sua execução de código para que você pode dar uma olhada em como os valores das variáveis ou o comportamento de memória ou se deseja ou não uma ramificação de código está sendo executada. É o recurso mais básico na depuração.

1. Para definir o ponto de interrupção, clique na medianiz à esquerda do `doWork` função (ou selecione a linha de código e pressione **F9**).

    ![Definir um ponto de interrupção](../debugger/media/dbg-qs-set-breakpoint-aspnet.png)

    O ponto de interrupção é definido para a esquerda da chave de abertura (`{`).

1. Agora pressione **F5** (ou escolha **Depurar > Iniciar depuração**).

1. Quando a página da web for carregada, clique no **sobre** link na parte superior da página da web.

    A pausa do depurador em que você definiu o ponto de interrupção. A instrução em que a execução do depurador e o aplicativo está em pausa é indicada pela seta amarela. A linha com a chave de abertura (`{`) depois que o `doWork` declaração de função ainda não foi executada.

    ![Atingir um ponto de interrupção](../debugger/media/dbg-qs-hit-breakpoint-aspnet.png)

    > [!TIP]
    > Se você tiver um ponto de interrupção em um loop ou recursão ou se você tiver muitos pontos de interrupção que percorre com frequência, use uma [ponto de interrupção condicional](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) para certificar-se de que seu código seja suspenso apenas quando condições específicas forem atendidas. Isso economiza tempo e pode também tornar mais fácil depurar os problemas que são difíceis de reproduzir.

## <a name="navigate-code"></a>Navegue pelos códigos

Há diferentes comandos para instruir o depurador para continuar. Vamos mostrar um comando de navegação de código úteis que há de novo no Visual Studio 2017.

Enquanto está em pausa no ponto de interrupção, passe o mouse sobre a instrução `return c2` até que o verde **executar com um clique** botão ![executar com um clique](../debugger/media/dbg-tour-run-to-click.png) aparece e, em seguida, pressione o **executar com um clique** botão.

![Executar com um clique](../debugger/media/dbg-qs-run-to-click-aspnet.png)

O aplicativo continua a execução e faz uma pausa na linha de código em que você clicou no botão.

Comandos de teclado comuns usados para percorrer o código inclua **F10** e **F11**. Para obter mais instruções detalhadas, consulte o [guia do Iniciante](../debugger/getting-started-with-the-debugger.md).

## <a name="inspect-variables-in-a-datatip"></a>Inspecionar variáveis em um datatip

1. Na linha atual do código (indicado pelo ponteiro de execução amarelo), passe o mouse sobre o `c2` objeto com o mouse para mostrar um datatip.

    ![Exibir um datatip](../debugger/media/dbg-qs-data-tip-aspnet.png)

    O datatip mostra o valor atual do `c2` variável e permite que você inspecione suas propriedades. Durante a depuração, se você vir um valor que não esperava, provavelmente haverá um bug nas linhas de código anteriores ou de chamada. 

2. Expanda o datatip para examinar os valores de propriedade atuais do `c2` objeto.

3. Se você deseja fixar o datatip de modo que você pode continuar a ver o valor do `c2` enquanto você executa o código, clique no ícone de pino pequeno. (Você pode mover o datatip fixado em um local conveniente.)

## <a name="edit-code-and-continue-debugging"></a>Editar o código e continuar a depuração

Se você identificar uma alteração que você deseja testar em seu código no meio de uma sessão de depuração, você pode fazer isso, muito.

1. No `OnGet` método, clique na segunda instância do `result.First.Value` e altere `result.First.Value` para `result.Last.Value`.

1. Pressione **F10** (ou **Depurar > Depuração parcial**) algumas vezes para avançar o depurador e executar o código editado.

    ![Editar e continuar](../debugger/media/dbg-qs-edit-and-continue-aspnet.png "editar e continuar")

    **F10** avança uma instrução do depurador a um tempo, mas as etapas sobre funções em vez de Avançar neles (ainda executa o código que você ignore).

Para obter mais informações sobre como usar Editar e continuar e limitações de recursos, consulte [editar e continuar](../debugger/edit-and-continue.md).

## <a name="next-steps"></a>Próximas etapas

Neste tutorial, você aprendeu como iniciar o depurador, percorrer o código e inspecionar variáveis. Você talvez queira obter uma visão detalhada de recursos do depurador, juntamente com links para obter mais informações.

> [!div class="nextstepaction"]
> [Tour dos recursos do depurador](../debugger/debugger-feature-tour.md)
