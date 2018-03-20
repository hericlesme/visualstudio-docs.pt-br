---
title: Aprenda a depurar - Visual Studio | Microsoft Docs
ms.description: Learn how to start the Visual Studio debugger, step through code, and inspect data
ms.custom: mvc
ms.date: 03/16/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: get-started-article
helpviewer_keywords:
- debugger
ms.assetid: 62734c0d-a75a-4576-8f73-0e97c19280e1
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: e0686a4138fc2489c8a63b207e98cf7780477782
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2018
---
# <a name="learn-to-debug-using-visual-studio"></a>Aprenda a depuração usando o Visual Studio

Este tópico apresenta os recursos do depurador do Visual Studio no passo a passo. Se você desejar um modo de exibição de alto nível dos recursos do depurador, consulte [tour pelos recursos do depurador](../debugger/debugger-feature-tour.md).

Você pode ler ou ao longo para ver os recursos do depurador ou você pode baixar o exemplo completo usado em Tour pelos recursos do e siga as etapas por conta própria. Para baixar o exemplo e acompanhá-lo, vá para [foto visualizador demonstração](https://code.msdn.microsoft.com/windowsdesktop/WPF-Photo-Viewer-Demo-be75662a).

|         |         |
|---------|---------|
|  ![ícone de câmera para vídeo](../install/media/video-icon.png "Assistir a um vídeo")  |    [Assista a um vídeo](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Debugger-Feature-tour-of-Visual-studio-2017-sqwiwLD6D_1111787171) depuração que mostra etapas semelhantes. |

Embora o aplicativo de demonstração é c#, os recursos são aplicáveis ao C++, Visual Basic, JavaScript e outras linguagens com suporte pelo Visual Studio (exceto onde observado).

Neste tutorial, você irá:

> [!div class="checklist"]
> * Iniciar o depurador e atingir pontos de interrupção.
> * Saiba mais sobre comandos para percorrer o código no depurador
> * Inspecionar variáveis em dicas de dados e janelas do depurador
> * Examinar a pilha de chamadas
> * Usar o auxiliar de exceção

## <a name="start-the-debugger"></a>Inicie o depurador!

1. Para acompanhar estas etapas no Visual Studio, baixe o exemplo [nesta página](https://code.msdn.microsoft.com/windowsdesktop/WPF-Photo-Viewer-Demo-be75662a).

    > [!IMPORTANT]
    > Você precisa instalar o Visual Studio com a carga de trabalho de desenvolvimento de área de trabalho do .NET para executar o aplicativo que estamos usando na demonstração.

2. Descompacte o projeto.

3. Abra o Visual Studio e selecione o **arquivo > Abrir** menu de comando e, em seguida, escolha **projeto/solução**e, em seguida, abra a pasta onde você baixou o projeto.

     ![Abra o projeto de exemplo](../debugger/media/dbg-tour-open-project.png "Abrir projeto")

3. Abra a demonstração do Visualizador de fotos WPF > c# pasta, escolha o arquivo photoapp.sln e selecione **abrir**.

     O projeto é aberto no Visual Studio. Gerenciador de soluções no painel à direita mostra todos os arquivos de projeto.

    ![Arquivos de solução do Explorer](../debugger/media/dbg-tour-solution-explorer.png "Gerenciador de soluções")

4. Pressione F5 (**Depurar > Iniciar depuração** ou **iniciar depuração** botão ![iniciar depuração](../debugger/media/dbg-tour-start-debugging.png "iniciar depuração") na barra de ferramentas de depuração).

     ![Aplicativo de Visualizador de fotos](../debugger/media/dbg-tour-wpf-app.png "aplicativo do Visualizador de fotos")

     F5 inicia o aplicativo com o depurador anexado ao processo do aplicativo, mas direita, agora podemos ainda não tiver adicionado a qualquer ponto de interrupção ou fez nada especial para examinar o código. Portanto o aplicativo carrega apenas e você verá as imagens de foto.

     Este tour, vamos dar uma olhada mais este aplicativo usando o depurador e obter recursos de examinar o depurador.

5. Parar o depurador pressionando a parada vermelha ![parar depuração](../debugger/media/dbg-tour-stop-debugging.png "parar depuração") botão.

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Definir um ponto de interrupção e iniciar o depurador

Para depurar, você precisa iniciar seu aplicativo com o depurador anexado ao processo de aplicativo.

1. No `MainWindow` construtor MainWindow.xaml.cs, defina um ponto de interrupção clicando na margem esquerda da primeira linha de código.

     ![Definir um ponto de interrupção](../debugger/media/dbg-tour-set-a-breakpoint.gif "SetABreakPoint")

6. Pressione F5 ou **iniciar depuração** botão, o aplicativo é iniciado, e o depurador é executado para a linha de código em que você definir o ponto de interrupção.

    A seta amarela representa a instrução na qual o depurador pausa, que também suspende a execução do aplicativo no mesmo momento (essa instrução ainda não executada).

    F5 continua executando o aplicativo para o próximo ponto de interrupção. (Se o aplicativo ainda não estiver executando, F5 inicia o depurador e parar no primeiro ponto de interrupção).

    Pontos de interrupção são um recurso útil quando você sabe que a linha de código ou na seção de código que você deseja examinar detalhadamente.

## <a name="restart-your-app-quickly"></a>Reinicie seu aplicativo rapidamente

Clique o **reiniciar** ![aplicativo reiniciar](../debugger/media/dbg-tour-restart.png "RestartApp") botão na barra de ferramentas Depurar (Ctrl + Shift + F5).

Quando você pressiona **reiniciar**, economiza tempo e parar o aplicativo e reiniciar o depurador. O depurador faz uma pausa no primeiro ponto de interrupção é atingido com a execução de código.

O depurador interrompe novamente no ponto de interrupção definido no `MainWindow` construtor.

## <a name="navigate-code-in-the-debugger-using-step-commands"></a>Navegar pelo código no depurador usando os comandos de etapa

Basicamente, usamos os atalhos de teclado aqui, porque ele é uma boa maneira de obter rápido em seu aplicativo em execução no depurador (comandos equivalentes como menu comandos são mostrados entre parênteses).

1. Pressione F11 (**Depurar > intervir**) duas vezes para ir a execução do aplicativo para o `InitializeComponent()` função.

     ![Use F11 para entrar em código](../debugger/media/dbg-tour-f11.png "F11 intervir")

     F11 é o **intervir** de comando e avança no aplicativo execução uma instrução de cada vez. F11 é uma boa maneira de examinar o fluxo de execução mais detalhadamente. (Para mover mais rapidamente por meio de código, mostramos algumas outras opções também.) Por padrão, o depurador ignora código não-usuário (se você quiser obter mais detalhes, consulte [Just My Code](../debugger/just-my-code.md)).

     >[!NOTE]
     > No código gerenciado, você verá uma caixa de diálogo perguntando se você deseja ser notificado quando você percorrer automaticamente propriedades e operadores (comportamento padrão). Se você quiser alterar a configuração mais tarde, desabilitar **percorrer propriedades e operadores** definindo no **Ferramentas > Opções** menu em **depuração**.

2. Pressione F10 (**Depurar > passar por**) algumas vezes até que o depurador interrompe na primeira linha do código no `OnApplicationStartup` manipulador de eventos.

     ![Use F10 para passar por código](../debugger/media/dbg-tour-f10-step-over.png "F10 Step Over")

     F10 avança o depurador sem depuração em funções ou métodos no código do aplicativo (o código ainda é executado). Pressionando F10 o `InitializeComponent` chamada de método (em vez de F11), é ignorada sobre o código de implementação para `InitializeComponent` (quais talvez nós não estiver interessados em agora).

## <a name="step-into-a-property"></a>Etapa em uma propriedade

1. Com o depurador em pausa nesta linha de código:

    ````
    mainWindow.Photos.Path = Environment.CurrentDirectory + "\\images";
    ````

    Clique na linha de código e escolha **passo específico**, em seguida, **SDKSamples.ImageSample.PhotoCollection.Path.set**

     ![Use a etapa em um recurso específico](../debugger/media/dbg-tour-step-into-specific.png "passo específico")

    Como mencionado anteriormente, por padrão, o depurador ignora propriedades gerenciadas e campos, mas o **passo específico** comando permite substituir esse comportamento. Por enquanto, queremos examinar o que acontece quando o `Path.set` execuções de setter de propriedade. **Passo específico** obtém para o `Path.set` código aqui.

     ![resultados do passo específico](../debugger/media/dbg-tour-step-into-specific-2.png "passo específico")

     O `Update` método nesse código parece que pode ser interessante, então vamos usam o depurador para examinar o código mais de perto.

5. Passe o mouse sobre o `Update` método até que o verde **executar a clique** botão ![executar em, clique em](../debugger/media/dbg-tour-run-to-click.png "RunToClick") aparece à esquerda.

     ![Use a execução em, clique em recurso](../debugger/media/dbg-tour-run-to-click-2.png "executar em, clique em")

    >  [!NOTE] 
    > O **executar a clique** botão é novo no [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]. Se você não vir o botão de seta verde, use F11 neste exemplo para avançar o depurador.

6. Clique o **executar em, clique em** botão ![executar em, clique em](../debugger/media/dbg-tour-run-to-click.png "RunToClick").

    Com esse botão é semelhante à configuração de um ponto de interrupção temporário. **Execute a clique** é útil para obter rapidamente em torno de dentro de uma região visível do código de aplicativo (você pode clicar em qualquer arquivo aberto).

    O depurador avança para o `Update` implementação do método.

7. Pressione F11 para passar para o `Update` método.

     ![Resultados do passo a passo do método Update](../debugger/media/dbg-tour-update-method.png "etapa no método de atualização")

    Aqui, podemos encontrar um código mais que pareça interessante; o aplicativo está obtendo todos os arquivos jpg que residem em um diretório específico e, em seguida, criar um objeto de foto para cada arquivo. Esse código nos dá uma boa oportunidade para iniciar inspecionar o estado do aplicativo (variáveis) com o depurador. Faremos que nas próximas seções deste tutorial.

    Recursos que permitem que você inspecione as variáveis são um dos recursos mais úteis do depurador e há diferentes maneiras de fazer isso. Geralmente, quando você tentar depurar um problema, você está tentando descobrir se variáveis estão armazenando os valores que você espera que eles têm em um determinado momento.

## <a name="examine-the-call-stack"></a>Examinar a pilha de chamadas

Enquanto está em pausa no `Update` método, clique o **pilha de chamadas** janela, por padrão, abrir no painel inferior direito.

![Examinar a pilha de chamadas](../debugger/media/dbg-tour-call-stack.png "ExamineCallStack")

O **pilha de chamadas** janela mostra a ordem em que estão sendo chamadas funções e métodos. A linha superior mostra a função atual (o `Update` método no aplicativo do tour). A segunda linha mostra que `Update` foi chamado a partir de `Path.set` propriedade e assim por diante.

>  [!NOTE]
> O **pilha de chamadas** janela é semelhante à perspectiva de depuração em alguma IDEs como Eclipse.

A pilha de chamadas é uma boa maneira de examinar e compreender o fluxo de execução de um aplicativo.

Você pode clicar duas vezes uma linha de código para consultar esse código-fonte e que também altera o escopo atual que está sendo inspecionado pelo depurador. Esta ação não Avançar o depurador.

Você também pode usar os menus de atalho do **pilha de chamadas** janela para fazer outras coisas. Por exemplo, você pode inserir pontos de interrupção em funções especificadas, promova o depurador usando **executar até o Cursor**e examine o código-fonte. Para obter mais informações, consulte [como: examinar a pilha de chamadas](../debugger/how-to-use-the-call-stack-window.md).

## <a name="step-out"></a>Sair

Digamos que você tenha examinando o `Update` método Data.cs e você deseja obter sairá da função, mas permanecem no depurador. Você pode fazer isso usando o **sair** comando.

1. Pressione Shift + F11 (ou **Depurar > Sair**).

     Este comando retoma a execução do aplicativo (e avança o depurador) até que retorna a função atual.

     Você deve estar no `Update` chamada de método no Data.cs.

2. Pressione Shift + F11 novamente e o depurador vai a pilha de chamadas de volta para o `OnApplicationStartup` manipulador de eventos.

## <a name="run-to-cursor"></a>Executar até o cursor

1. Escolha o **parar depuração** botão vermelho ![parar depuração](../debugger/media/dbg-tour-stop-debugging.png "parar depuração") ou Shift + F5.

2. No `Update` método Data.cs, com o botão direito do `Add` método chamar e escolha **executar até o Cursor**. Esse comando inicia a depuração e define um ponto de interrupção temporário na linha atual do código.

     ![Use a execução para o recurso de Cursor](../debugger/media/dbg-tour-run-to-cursor.png "executar até o Cursor")

    Você deve ser pausado no ponto de interrupção `MainWindow` (já que é o primeiro ponto de interrupção é definido).

3. Pressione F5 para ir para o `Add` método em que você selecionou **executar até o Cursor**.

    Esse comando é útil quando você estiver editando o código e deseja definir um ponto de interrupção temporário rapidamente e iniciar o depurador.

## <a name="change-the-execution-flow"></a>Alterar o fluxo de execução

1. Com o depurador em pausa no `Add` chamada de método, use o mouse para capturar a seta amarela (o ponteiro de execução) à esquerda e mova a seta amarela para cima de uma linha para o `foreach` loop.

     ![Mova o ponteiro de execução](../debugger/media/dbg-tour-move-the-execution-pointer.gif "Move o ponteiro de execução")

    Alterando o fluxo de execução, você pode fazer coisas como caminhos de execução de código diferente de teste ou execute novamente o código sem reiniciar o depurador.

2. Agora, pressione F5.

    Você pode ver as imagens adicionadas para a janela do aplicativo. Porque são novamente o código de `foreach` loop, algumas das imagens foram adicionadas duas vezes!
    
    > [!WARNING]
    > Muitas vezes você precisa ter cuidado com esse recurso, e você ver um aviso na dica de ferramenta. Você pode ver outros avisos muito. Mover o ponteiro não é possível reverter o aplicativo para um estado anterior do aplicativo.

## <a name="inspect-variables-with-data-tips"></a>Inspecionar variáveis com dicas de dados

1. Abra Data.cs no aplicativo de demonstração do Visualizador de fotos, com o botão direito do `private void Update` declaração de função e escolha **executar até o Cursor** (parar o aplicativo primeiro se ele já está em execução).

    Isso irá pausar o aplicativo com o depurador anexado. Isso nos permite examinar seu estado.

2. Passe o mouse sobre o `Add` chamada de método e clique no **executar em, clique em** botão ![executar em, clique em](../debugger/media/dbg-tour-run-to-click.png "RunToClick").

3. Agora, passe o mouse sobre o objeto de arquivo (`f`) e você verá o valor de propriedade padrão, o nome do arquivo `market 031.jpg`.

     ![Exibir uma dica de dados](../debugger/media/dbg-tour-data-tips.gif "exibir uma dica de dados")

4. Expanda o objeto para ver todas as suas propriedades, como o `FullPath` propriedade.

    Geralmente, ao depurar, você deseja uma maneira rápida de verificar os valores de propriedade em objetos e as dicas de dados são uma boa maneira de fazer isso.

    > [!TIP]
    > Em linguagens mais com suporte, você pode editar o código no meio de uma sessão do depurador se você encontrar algo que você deseja alterar. Para obter mais informações, consulte [editar e continuar](../debugger/edit-and-continue.md). Para usar esse recurso neste aplicativo, no entanto, podemos primeiro precisa atualizar a versão do aplicativo do .NET Framework.

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>Inspecionar variáveis com o windows Autos e locais

1. Examine o **Autos** janela na parte inferior do editor de código.

     ![Inspecionar variáveis na janela Autos](../debugger/media/dbg-tour-autos-window.png "janela Autos")

    No **Autos** janela, consulte variáveis e seu valor atual. O **Autos** janela mostra todas as variáveis usadas na linha atual ou a linha precedente (em C++, a janela mostra variáveis em três linhas de código. Verifique a documentação para o comportamento específico do idioma).

    > [!NOTE]
    > No JavaScript, o **locais** janela tem suporte mas não o **Autos** janela.

2. Em seguida, examinar o **locais** janela.

    O **locais** janela mostra as variáveis que estão no escopo atual.

    ![Inspecionar variáveis na janela locais](../debugger/media/dbg-tour-locals-window.png "janela locais")

    Atualmente, o `this` objeto e o objeto de arquivo (`f`) estão no escopo atual. Para obter mais informações, consulte [inspecionar variáveis nas janelas de locais e Autos](../debugger/autos-and-locals-windows.md).

## <a name="set-a-watch"></a>Definir uma inspeção

1. Na janela do editor de código principal, clique no objeto de arquivo (`f`) e escolha **Adicionar inspeção**.

    Você pode usar um **inspecionar** janela para especificar uma variável (ou uma expressão) que você deseja acompanhar na.

    Agora, você tem uma inspeção ativada a `File` objeto e você pode ver seu valor alterar quando você percorre o depurador. Ao contrário de outras janelas variável, o **inspecionar** janela sempre mostra as variáveis que você está observando (estão esmaecidos quando fora do escopo).

2. No `Add` método, clique em verde ![executar em, clique em](../debugger/media/dbg-tour-run-to-click.png "RunToClick") novamente (ou pressione F11 algumas vezes) para percorrer o `foreach` loop.

    ![Definir uma inspeção em uma variável](../debugger/media/dbg-tour-watch-window.png "janela Inspecionar")

    Você também poderá ver a primeira imagem são adicionados à janela principal da execução amostra de aplicativo, mas isso ocorre em um thread de aplicativo diferente, assim imagens podem não estar visíveis ainda.

    Para obter mais informações, consulte [definir uma inspeção usando a observação e QuickWatch Windows](../debugger/watch-and-quickwatch-windows.md)

## <a name="examine-an-exception"></a>Examine a exceção

1. Na janela do aplicativo em execução, exclua o texto no **caminho** caixa de entrada e selecione o **alteração** botão.

     ![Fazer com que uma exceção seja lançada](../debugger/media/dbg-tour-cause-an-exception.png "causar uma exceção")

     O aplicativo gera uma exceção, e o depurador leva você para a linha de código que lançou a exceção.
     
     ![Auxiliar de exceção](../debugger/media/dbg-tour-exception-helper.png "auxiliar de exceção")

     Aqui, o **auxiliar de exceção** mostra um `System.ArgumentException` e uma mensagem de erro que afirma que o caminho não é um formato inválido. Portanto, sabemos que o erro ocorreu em um argumento de método ou função.

     Neste exemplo, o `DirectoryInfo` chamada forneceu o erro na cadeia de caracteres vazia armazenada no `value` variável. (Passe o mouse sobre `value` para ver a cadeia de caracteres vazia.)

     O auxiliar de exceção é um ótimo recurso que pode ajudá-lo a depurar erros. Você também pode fazer coisas como exibir detalhes do erro e adicione uma inspeção do auxiliar de exceção. Ou, se necessário, você pode alterar as condições para lançar a exceção específica.

    >  [!NOTE] 
    > O auxiliar de exceção substitui o Assistente de exceção no [!include[vs_dev15](../misc/includes/vs_dev15_md.md)].

2. Expanda o **configurações de exceção** nó para ver mais opções sobre como lidar com esse tipo de exceção, mas você não precisa alterar nada para este tour!

3. Pressione F5 para continuar o aplicativo.

Para saber mais sobre os recursos do depurador, consulte [depurador dicas e truques](../debugger/debugger-tips-and-tricks.md).

## <a name="next-steps"></a>Próximas etapas

Neste tutorial, você aprendeu como iniciar o depurador, percorrer o código e inspecionar variáveis. Você talvez queira obter uma visão de alto nível de recursos do depurador junto com links para mais informações.

> [!div class="nextstepaction"]
> [Tour dos recursos do depurador](../debugger/debugger-feature-tour.md)
