---
title: "Depuração ASP.NET - Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 03/16/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: quickstart
helpviewer_keywords:
- debugger
ms.assetid: f4cea2e1-08dc-47ac-aba2-3b8c338e607f
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- aspnet
ms.openlocfilehash: 0c6f3b0d074957ba8fabd93707e9a76f0dcd46e1
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2018
---
# <a name="debug-aspnet-with-the-visual-studio-debugger"></a>Depurar ASP.NET com o depurador do Visual Studio

O depurador do Visual Studio fornece muitos recursos poderosos para ajudá-lo a depurar seus aplicativos. Este tópico fornece uma maneira rápida de conhecer alguns dos recursos básicos.

## <a name="create-a-new-project"></a>Criar um novo projeto 

1. No Visual Studio, escolha **Arquivo > Novo Projeto**.

1. Em **Visual C#**, escolha **Web**e, em seguida, no painel central, escolha **aplicativo Web do ASP.NET Core**.

1. Digite um nome como **MyDbgApp** e clique em **Okey**.

1. Na caixa de diálogo que aparece, escolha **aplicativo Web** no painel central e clique **Okey**.

     Se você não vir o **aplicativo Web** modelo de projeto, clique no **abrir instalador do Visual Studio** link no painel esquerdo do **novo projeto** caixa de diálogo. O Instalador do Visual Studio é iniciado. Escolha o **ASP.NET** e **.NET Core** carga de trabalho, escolha **modificar**.

    ![Escolha um aplicativo Web](../debugger/media/dbg-qs-aspnet-choose-web-app.png)

    O Visual Studio cria o projeto.

1. No Solution Explorer, abra About.cshtml.cs (em Pages/About.cshtml) e substitua o código a seguir

    ```c#
    public void OnGet()
    {
        Message = "Your application description page.";
    }
    ```

    com este código:

    ```c#
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

Um *ponto de interrupção* é um marcador que indica onde o Visual Studio deve suspender a execução de código para que você pode dar uma olhada os valores das variáveis ou o comportamento de memória ou se deve ou não uma ramificação de código é obtendo executada. É o recurso mais básico na depuração.

1. Para definir o ponto de interrupção, clique na medianiz à esquerda do `doWork` função (ou selecione a linha de código e pressione **F9**).

    ![Definir um ponto de interrupção](../debugger/media/dbg-qs-set-breakpoint-aspnet.png)

    O ponto de interrupção está definido para a esquerda da chave de abertura (`{`).

1. Agora, pressione **F5** (ou escolha **Depurar > Iniciar depuração**).

1. Quando a página da web é carregada, clique no **sobre** link na parte superior da página da web.

    A pausa do depurador onde você pode definir o ponto de interrupção. A instrução em que a execução do aplicativo e o depurador é pausada é indicada pela seta amarela. A linha com a chave de abertura (`{`) após o `doWork` declaração de função ainda não foi executada.

    ![Atingir um ponto de interrupção](../debugger/media/dbg-qs-hit-breakpoint-aspnet.png)

    > [!TIP]
    > Se você tiver um ponto de interrupção em um loop ou recursão, ou se você tiver muitos pontos de interrupção que você frequentemente percorrer, use um [ponto de interrupção condicional](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) para certificar-se de que seu código está suspenso somente quando condições específicas forem atendidas. Isso economiza tempo e pode também facilitam a depurar problemas difíceis de reproduzir.

## <a name="navigate-code"></a>Navegue pelos códigos

Há diferentes comandos para instruir o depurador para continuar. Vamos mostrar um comando de navegação de código útil que há de novo no Visual Studio de 2017.

Enquanto está em pausa no ponto de interrupção, passe o mouse sobre a instrução `return c2` até que o verde **execução clique** botão ![executar em, clique em](../debugger/media/dbg-tour-run-to-click.png) aparece e, em seguida, pressione a **execução clique** botão.

![Executar, clique em](../debugger/media/dbg-qs-run-to-click-aspnet.png)

O aplicativo continua a execução e pausa na linha de código em que você clicou no botão.

Comandos comuns do teclado usados para percorrer o código incluem **F10** e **F11**. Para obter mais instruções detalhadas, consulte o [guia do Iniciante](../debugger/getting-started-with-the-debugger.md).

## <a name="inspect-variables-in-a-datatip"></a>Inspecionar variáveis em um datatip

1. Na linha atual do código (indicado pelo ponteiro de execução amarelo), passe o mouse sobre o `c2` objeto com o mouse para mostrar um datatip.

    ![Exibir um datatip](../debugger/media/dbg-qs-data-tip-aspnet.png)

    O datatip mostra o valor atual de `c2` variável e permite que você inspecione suas propriedades. Durante a depuração, se você vir um valor que você não espera, você provavelmente terá um bug nas linhas anteriores ou chamadas do código. 

2. Expanda datatip para examinar os valores de propriedade atual o `c2` objeto.

3. Se você deseja fixar o datatip para que você pode continuar a ver o valor de `c2` enquanto você executar o código, clique no ícone de pino pequeno. (Você pode mover o datatip fixado em um local conveniente.)

## <a name="edit-code-and-continue-debugging"></a>Edite o código e continuar a depuração

Se você identificar uma alteração que você deseja testar no seu código no meio de uma sessão de depuração, você pode fazer isso, muito.

1. No `OnGet` método, clique na segunda instância de `result.First.Value` e alterar `result.First.Value` para `result.Last.Value`.

1. Pressione **F10** (ou **Depurar > passar por**) algumas vezes para avançar o depurador e execute o código editado.

    ![Editar e continuar](../debugger/media/dbg-qs-edit-and-continue-aspnet.png "editar e continuar")

    **F10** avança a instrução de depurador um em uma hora, mas as etapas sobre funções em vez de avançá-los (ainda executa o código que você ignorar).

Para obter mais informações sobre como usar Editar e continuar e limitações de recursos, consulte [editar e continuar](../debugger/edit-and-continue.md).

## <a name="next-steps"></a>Próximas etapas

Neste tutorial, você aprendeu como iniciar o depurador, percorrer o código e inspecionar variáveis. Você talvez queira obter uma visão de alto nível de recursos do depurador junto com links para mais informações.

> [!div class="nextstepaction"]
> [Tour dos recursos do depurador](../debugger/debugger-feature-tour.md)
