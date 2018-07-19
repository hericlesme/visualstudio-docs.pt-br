---
title: Saiba como depurar usando o depurador do Visual Studio
ms.description: Learn how to start the Visual Studio debugger, step through code, and inspect data.
ms.custom: mvc
ms.date: 06/15/2018
ms.technology: vs-ide-debug
ms.topic: tutorial
helpviewer_keywords:
- debugger
ms.assetid: 62734c0d-a75a-4576-8f73-0e97c19280e1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1144e7e33709510cb03ed02cb62020f81e8e8b62
ms.sourcegitcommit: 498e39e89a89ad7bf9dcb0617424fff999b1c3b2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/21/2018
ms.locfileid: "36303140"
---
# <a name="tutorial-learn-to-debug-using-visual-studio"></a>Tutorial: Aprenda a depurar usando o Visual Studio

Este tópico apresenta os recursos do depurador do Visual Studio no passo a passo. Se você quiser uma exibição de alto nível dos recursos do depurador, consulte [tour pelos recursos do depurador](../debugger/debugger-feature-tour.md). Quando você *depurar seu aplicativo*, isso normalmente significa que você está executando seu aplicativo com o depurador anexado. Quando você fizer isso, o depurador fornece várias maneiras de ver o que está fazendo o seu código enquanto ele é executado. Você pode percorrer seu código e examinar os valores armazenados em variáveis, você pode definir inspeções em variáveis para ver quando valores são alterados, você pode examinar o caminho de execução do seu código, et al. Se essa for a primeira vez que você tentou depurar o código, você talvez queira ler [depuração para iniciantes absolutos](../debugger/debugging-absolute-beginners.md) antes de usar este tópico.

Você pode ler ou ao longo para ver os recursos do depurador ou você pode baixar o exemplo completo usado em um tour pelos recursos do e siga as etapas por conta própria. Para baixar o exemplo e acompanhá-lo, vá para [demonstração do Visualizador de fotos](https://code.msdn.microsoft.com/windowsdesktop/WPF-Photo-Viewer-Demo-be75662a).

|         |         |
|---------|---------|
|  ![ícone de câmera para vídeo](../install/media/video-icon.png "Assistir a um vídeo")  |    [Assista a um vídeo](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Debugger-Feature-tour-of-Visual-studio-2017-sqwiwLD6D_1111787171) sobre depuração, que mostra etapas semelhantes. |

Embora o aplicativo de demonstração é c#, os recursos são aplicáveis ao C++, Visual Basic, JavaScript e outras linguagens com suporte pelo Visual Studio (exceto onde observado).

Neste tutorial, você irá:

> [!div class="checklist"]
> * Inicie o depurador e atingir pontos de interrupção.
> * Saiba mais sobre os comandos para percorrer o código no depurador
> * Inspecionar variáveis em dicas de dados e janelas do depurador
> * Examinar a pilha de chamadas
> * Usar o auxiliar de exceção

## <a name="prerequisites"></a>Pré-requisitos

* Você deve ter o Visual Studio 2017 instalado e o. **Desenvolvimento de área de trabalho líquido** carga de trabalho.

    Se você ainda não tiver instalado o Visual Studio, acesse a página [Downloads do Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) para instalá-lo gratuitamente.

    Se você precisar instalar a carga de trabalho, mas já tiver o Visual Studio, clique no link **Abrir Instalador do Visual Studio** no painel esquerdo da caixa de diálogo **Novo Projeto** (selecione **Arquivo** > **Novo** > **Projeto**). O Instalador do Visual Studio é iniciado. Escolha o. **Desenvolvimento de área de trabalho líquido** carga de trabalho, em seguida, escolha **modificar**.

## <a name="start-the-debugger"></a>Inicie o depurador!

1. Para acompanhar estas etapas no Visual Studio, baixe a amostra [nesta página](https://code.msdn.microsoft.com/windowsdesktop/WPF-Photo-Viewer-Demo-be75662a).

    > [!IMPORTANT]
    > Você precisa instalar o Visual Studio com a carga de trabalho de desenvolvimento de área de trabalho do .NET para executar o aplicativo que estamos usando na demonstração.

2. Descompacte o projeto.

3. Abra o Visual Studio e selecione o **arquivo > Abrir** menu de comando e, em seguida, escolha **projeto/solução**e, em seguida, abra a pasta onde você baixou o projeto.

     ![Abra o projeto de exemplo](../debugger/media/dbg-tour-open-project.png "Abrir projeto")

3. Abra a demonstração do Visualizador de fotos WPF > c# pasta, escolha o *photoapp.sln* do arquivo e selecione **abrir**.

     O projeto é aberto no Visual Studio. Gerenciador de soluções, no painel direito mostra todos os arquivos de projeto.

    ![Arquivos do Gerenciador de soluções](../debugger/media/dbg-tour-solution-explorer.png "Gerenciador de soluções")

4. Pressione **F5** (**Depurar > Iniciar depuração**) ou o **iniciar depuração** botão ![iniciar depuração](../debugger/media/dbg-tour-start-debugging.png "iniciar depuração ") na barra de ferramentas Depurar.

     ![Aplicativo de Visualizador de fotos](../debugger/media/dbg-tour-wpf-app.png "aplicativo Visualizador de fotos")

     F5 inicia o aplicativo com o depurador anexado ao processo do aplicativo, mas à direita, agora podemos ainda não adicionou nenhum ponto de interrupção ou fez nada especial para examinar o código. Portanto, o aplicativo é carregado apenas e você verá as imagens de fotos.

     Este tour, vamos dar uma olhada mais próxima este aplicativo usando o depurador e obter recursos de uma olhada no depurador.

5. Pare o depurador pressionando a parada vermelha ![parar depuração](../debugger/media/dbg-tour-stop-debugging.png "parar depuração") botão.

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Definir um ponto de interrupção e iniciar o depurador

Para depurar, você precisa iniciar seu aplicativo com o depurador anexado ao processo do aplicativo.

1. No `MainWindow` construtor de MainWindow.xaml.cs, defina um ponto de interrupção clicando na margem esquerda da primeira linha de código.

     ![Defina um ponto de interrupção](../debugger/media/dbg-tour-set-a-breakpoint.gif "SetABreakPoint")

    Pontos de interrupção são o recurso mais básico e essencial da depuração confiável. Um ponto de interrupção indica quando o Visual Studio deve suspender o código em execução para que você possa examinar os valores das variáveis ou o comportamento de memória ou se uma ramificação de código está sendo executada ou não. 

6. Pressione **F5** ou o **iniciar depuração** botão, o aplicativo é iniciado, e o depurador executa a linha de código em que você definiu o ponto de interrupção.

    A seta amarela representa a instrução na qual o depurador pausou a, que também suspende a execução de aplicativo no mesmo ponto (esta instrução ainda não foi executada).

    F5 continua executando o aplicativo para o próximo ponto de interrupção. (Se o aplicativo não está em execução ainda, F5 inicia o depurador e é interrompida no primeiro ponto de interrupção.)

    Pontos de interrupção são um recurso útil quando você sabe que a linha de código ou a seção de código que você deseja examinar em detalhes.

## <a name="optional-restart-your-app-quickly"></a>(Opcional) Reinicie o aplicativo rapidamente

Clique o **reinicie** ![aplicativo reiniciar](../debugger/media/dbg-tour-restart.png "RestartApp") botão na barra de ferramentas Depurar (**Ctrl** + **Shift**   +  **F5**).

Quando você pressiona **reiniciar**, ele economiza tempo em comparação com o aplicativo de parar e reiniciar o depurador. O depurador pausa no primeiro ponto de interrupção é atingido pela execução de código.

O depurador novamente para no ponto de interrupção definido, além de `MainWindow` construtor.

## <a name="navigate-code-in-the-debugger-using-step-commands"></a>Navegar pelo código no depurador usando comandos de etapa

Em grande parte, podemos usar os atalhos de teclado aqui, porque ele é uma boa maneira de obter rápida no seu aplicativo em execução no depurador (comandos equivalentes, como o menu de comandos são mostrados entre parênteses).

1. Pressione **F11** (**Depurar > intervir**) duas vezes para ir a execução do aplicativo para o `InitializeComponent()` função.

     ![Use F11 para entrar em código](../debugger/media/dbg-tour-f11.png "F11 intervir")

     F11 é o **intervir** de comando e avança a instrução de um de execução do aplicativo por vez. F11 é uma boa maneira para examinar o fluxo de execução em que a maioria dos detalhes. (Para mover mais rapidamente por meio de código, vamos mostrar algumas outras opções também.) Por padrão, o depurador ignora o código de não usuário (se você quiser obter mais detalhes, consulte [Just My Code](../debugger/just-my-code.md)).

     >[!NOTE]
     > No código gerenciado, você verá uma caixa de diálogo perguntando se você deseja ser notificado quando você percorrer automaticamente as propriedades e operadores (comportamento padrão). Se você quiser alterar a configuração mais tarde, desabilite **depurar parcialmente propriedades e operadores** definindo no **Ferramentas > Opções** menu sob **depuração**.

2. Pressione **F10** (**Depurar > Depuração parcial**) algumas vezes até que o depurador é interrompido na primeira linha de código no `OnApplicationStartup` manipulador de eventos.

     ![Use F10 para código Step Over](../debugger/media/dbg-tour-f10-step-over.png "F10 Step Over")

     F10 avança o depurador sem entrar em funções ou métodos no código do aplicativo (o código ainda é executado). Pressionando F10 na `InitializeComponent` chamada de método (em vez de F11), podemos ignorei o código de implementação para `InitializeComponent` (que talvez podemos não estão interessados no momento).

## <a name="step-into-a-property"></a>Entrar em uma propriedade

1. Com o depurador em pausa nesta linha de código:

    ````c#
    mainWindow.Photos.Path = Environment.CurrentDirectory + "\\images";
    ````

    Clique com botão direito na linha de código e escolha **Step Into Specific**, em seguida, **SDKSamples.ImageSample.PhotoCollection.Path.set**

     ![Use a etapa em um recurso específico](../debugger/media/dbg-tour-step-into-specific.png "passo específico")

    Como mencionado anteriormente, por padrão, o depurador ignora propriedades gerenciadas e campos, mas o **Step Into Specific** comando permite que você substitua esse comportamento. Por enquanto, queremos examinar o que acontece quando o `Path.set` execuções de setter de propriedade. **Step Into Specific** nos leva para o `Path.set` aqui, o código.

     ![resultado da etapa específico](../debugger/media/dbg-tour-step-into-specific-2.png "passo específico")

     O `Update` método nesse código parece que poderia ser interessante, vamos usam o depurador para examinar esse código mais de perto.

5. Passe o mouse sobre o `Update` método até que o verde **executar com um clique** botão ![executar com um clique](../debugger/media/dbg-tour-run-to-click.png "RunToClick") aparece à esquerda.

     ![Usar o executar para clicar recurso](../debugger/media/dbg-tour-run-to-click-2.png "executar com um clique")

    >  [!NOTE]
    > O **executar com um clique** há de novo no botão [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]. Se você não vir o botão de seta verde, use F11 neste exemplo para avançar o depurador.

6. Clique o **executar com um clique** botão ![executar com um clique](../debugger/media/dbg-tour-run-to-click.png "RunToClick").

    Usar esse botão é semelhante à configuração de um ponto de interrupção temporário. **Executar com um clique** é útil para obter rapidamente em torno de dentro de uma região visível do código do aplicativo (você pode clicar em qualquer arquivo aberto).

    O depurador avança para o `Update` implementação do método.

7. Pressione **F11** Step into a `Update` método.

     ![Resultado de depuração para o método de atualização](../debugger/media/dbg-tour-update-method.png "etapa no método de atualização")

    Aqui, podemos encontrar alguns códigos mais que pareça interessante; o aplicativo está obtendo todos os. *jpg* arquivos que residem em um diretório específico e, em seguida, criando um objeto de foto para cada arquivo. Esse código nos dá uma boa oportunidade para iniciar a inspecionar o estado do aplicativo (variáveis) com o depurador. Podemos fará isso nas próximas seções deste tutorial.

    Recursos que permitem que você inspecione as variáveis são um dos recursos mais úteis do depurador, e há diferentes maneiras de fazê-lo. Muitas vezes, quando você tenta depurar um problema, você está tentando descobrir se as variáveis são armazenar os valores que você espera que eles têm em um momento específico.

## <a name="examine-the-call-stack"></a>Examinar a pilha de chamadas

Enquanto está em pausa na `Update` método, clique em de **pilha de chamadas** janela, por padrão, abrir no painel inferior direito.

![Examinar a pilha de chamadas](../debugger/media/dbg-tour-call-stack.png "ExamineCallStack")

O **pilha de chamadas** janela mostra a ordem em que métodos e funções estão sendo chamadas. A linha superior mostra a função atual (o `Update` método no aplicativo de tour). A segunda linha mostra que `Update` foi chamado a partir de `Path.set` propriedade e assim por diante.

>  [!NOTE]
> O **pilha de chamadas** janela é semelhante à perspectiva de depuração em alguns IDEs como o Eclipse.

A pilha de chamadas é uma boa maneira para examinar e entender o fluxo de execução de um aplicativo.

Você pode clicar duas vezes uma linha de código para examinar esse código-fonte e que também altera o escopo atual que está sendo inspecionado pelo depurador. Essa ação não avance para o depurador.

Você também pode usar os menus de atalho do **pilha de chamadas** janela para fazer outras coisas. Por exemplo, você pode inserir os pontos de interrupção em funções especificadas, Avançar o depurador usando **executar até o Cursor**e examinar o código-fonte. Para obter mais informações, consulte [como: examinar a pilha de chamadas](../debugger/how-to-use-the-call-stack-window.md).

## <a name="step-out"></a>Depuração circular

Digamos que você terminar de examinar o `Update` método em Data.cs e você quiser tirar proveito de função, mas mantenha-se no depurador. Você pode fazer isso usando o **depuração circular** comando.

1. Pressione **Shift** + **F11** (ou **Depurar > Depuração circular**).

     Este comando retoma a execução do aplicativo (e avança o depurador) até que retorna a função atual.

     Você deve ter voltado a `Update` chamada de método em Data.cs.

2. Pressione **Shift** + **F11** novamente, e o depurador vai até a pilha de chamada de volta para o `OnApplicationStartup` manipulador de eventos.

## <a name="run-to-cursor"></a>Executar até o cursor

1. Escolha o **parar depuração** botão vermelho ![parar depuração](../debugger/media/dbg-tour-stop-debugging.png "parar depuração") ou **Shift** + **F5** .

2. No `Update` método no *Data.cs*, clique com botão direito a `Add` chamada de método e escolha **executar até o Cursor**. Esse comando inicia a depuração e define um ponto de interrupção temporário na linha de código atual.

     ![Use a executar ao recurso de Cursor](../debugger/media/dbg-tour-run-to-cursor.png "executar até o Cursor")

    Você deve ser pausado no ponto de interrupção no `MainWindow` (já que é o primeiro ponto de interrupção é definido).

3. Pressione **F5** para ir para o `Add` método em que você selecionou **executar até o Cursor**.

    Esse comando é útil quando você estiver editando o código e deseja definir um ponto de interrupção temporário rapidamente e iniciar o depurador.

## <a name="change-the-execution-flow"></a>Alterar o fluxo de execução

1. Com o depurador pausa sobre o `Add` chamada de método, use o mouse para captar a seta amarela (o ponteiro de execução) à esquerda e mova a seta amarela para cima de uma linha para o `foreach` loop.

     ![Mova o ponteiro de execução](../debugger/media/dbg-tour-move-the-execution-pointer.gif "mover o ponteiro de execução")

    Alterando o fluxo de execução, você pode fazer coisas como caminhos de execução de código diferente de teste ou execute novamente o código sem reiniciar o depurador.

2. Agora, pressione **F5**.

    Você pode ver as imagens adicionadas à janela do aplicativo. Porque você estará reexecutando o código no `foreach` loop, algumas imagens foram adicionadas duas vezes!

    > [!WARNING]
    > Geralmente, você precisa ter cuidado com esse recurso, e você verá um aviso na dica de ferramenta. Você pode ver outros avisos, muito. Movendo o ponteiro não é possível reverter o seu aplicativo para um estado anterior do aplicativo.

## <a name="inspect-variables-with-data-tips"></a>Inspecionar variáveis com dicas de dados

1. Abra *Data.cs* no aplicativo de demonstração do Visualizador de fotos, clique com botão direito do `private void Update` declaração de função e escolha **executar até o Cursor** (interromper o aplicativo pela primeira vez se ele já está em execução).

    Isso irá pausar o aplicativo com o depurador anexado. Isso nos permite examinar seu estado.

2. Passe o mouse sobre o `Add` método chamar e clique em de **executar com um clique** botão ![executar com um clique](../debugger/media/dbg-tour-run-to-click.png "RunToClick").

3. Agora, passe o mouse sobre o objeto de arquivo (`f`) e você verá o valor de propriedade padrão, o nome do arquivo *mercado 031. jpg*.

     ![Exibir uma dica de dados](../debugger/media/dbg-tour-data-tips.gif "exibir uma dica de dados")

4. Expanda o objeto para ver todas as suas propriedades, como o `FullPath` propriedade.

    Muitas vezes, durante a depuração, você deseja uma maneira rápida de verificar valores de propriedade em objetos e as dicas de dados são uma boa maneira de fazê-lo.

    > [!TIP]
    > Em linguagens mais com suporte, você pode editar o código no meio de uma sessão do depurador se você encontrar algo que deseja alterar. Para obter mais informações, consulte [editar e continuar](../debugger/edit-and-continue.md). Para usar esse recurso neste aplicativo, no entanto, primeiro precisamos atualizar a versão do aplicativo do .NET Framework.

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>Inspecionar variáveis com as janelas Autos e locais

1. Examine os **automóveis** janela na parte inferior do editor de código.

     ![Inspecionar variáveis na janela Autos](../debugger/media/dbg-tour-autos-window.png "janela Autos")

    No **Autos** janela, você verá as variáveis e seu valor atual. O **automóveis** janela mostra todas as variáveis usadas na linha atual ou a linha anterior (em C++, a janela mostra as variáveis nas três linhas de código anteriores. Verifique a documentação para o comportamento específico do idioma).

    > [!NOTE]
    > No JavaScript, o **Locals** janela tem suporte, mas não a **Autos** janela.

2. Em seguida, examine os **Locals** janela.

    O **Locals** janela mostra as variáveis que estão no escopo atual.

    ![Inspecionar variáveis na janela locais](../debugger/media/dbg-tour-locals-window.png "janela locais")

    Atualmente, o `this` objeto e o objeto de arquivo (`f`) estão no escopo atual. Para obter mais informações, consulte [inspecionar variáveis no Windows locais e Autos](../debugger/autos-and-locals-windows.md).

## <a name="set-a-watch"></a>Definir uma inspeção

1. Na janela do editor de código principal, clique com botão direito do objeto de arquivo (`f`) e escolha **Adicionar inspeção**.

    Você pode usar um **inspeção** janela para especificar uma variável (ou uma expressão) que você deseja que fique de olho no.

    Agora, você tem uma inspeção ativada a `File` objeto e você pode ver seu valor mudam conforme você move o depurador. Ao contrário de outras janelas variáveis, o **inspeção** janela sempre mostra as variáveis que você está observando (eles estão esmaecidos quando fora do escopo).

2. No `Add` método, clique em verde ![executar com um clique](../debugger/media/dbg-tour-run-to-click.png "RunToClick") novamente no botão (ou pressione F11 algumas vezes) para percorrer o `foreach` loop.

    ![Definir uma inspeção em uma variável](../debugger/media/dbg-tour-watch-window.png "janela Inspeção")

    Você também poderá ver da primeira imagem seja adicionado à janela principal da execução do aplicativo de exemplo, mas isso acontece em um thread de aplicativo diferente, portanto, as imagens podem não estar visíveis ainda.

    Para obter mais informações, consulte [definir uma inspeção usando a inspeção e QuickWatch Windows](../debugger/watch-and-quickwatch-windows.md)

## <a name="examine-an-exception"></a>Examinar uma exceção

1. Na janela do aplicativo em execução, exclua o texto na **caminho** caixa de entrada e selecione o **alteração** botão.

     ![Fazer com que uma exceção seja lançada](../debugger/media/dbg-tour-cause-an-exception.png "causar uma exceção")

     O aplicativo gera uma exceção, e o depurador leva você até a linha de código que lançou a exceção.

     ![Auxiliar de exceção](../debugger/media/dbg-tour-exception-helper.png "auxiliar de exceção")

     Aqui, o **auxiliar de exceção** mostra um `System.ArgumentException` e uma mensagem de erro que diz que o caminho não é um formato inválido. Portanto, sabemos que o erro ocorreu em um argumento de método ou função.

     Neste exemplo, o `DirectoryInfo` chamada forneceu o erro na cadeia de caracteres vazia armazenada em do `value` variável. (Passar o mouse sobre `value` para ver a cadeia de caracteres vazia.)

     O auxiliar de exceção é um ótimo recurso que pode ajudá-lo a depurar erros. Você também pode fazer coisas como exibir detalhes do erro e adicionar uma inspeção de auxiliar de exceção. Ou, se necessário, você pode alterar as condições para lançar a exceção específica.

    >  [!NOTE]
    > O auxiliar de exceção substitui o Assistente de exceção em [!include[vs_dev15](../misc/includes/vs_dev15_md.md)].

2. Expanda o **configurações de exceção** nó para ver mais opções sobre como lidar com esse tipo de exceção, mas você não precisa alterar nada para este tour!

3. Pressione **F5** para continuar o aplicativo.

Para saber mais sobre os recursos do depurador, consulte [depurador dicas e truques](../debugger/debugger-tips-and-tricks.md).

## <a name="next-steps"></a>Próximas etapas

Neste tutorial, você aprendeu como iniciar o depurador, percorrer o código e inspecionar variáveis. Você talvez queira obter uma visão detalhada de recursos do depurador, juntamente com links para obter mais informações.

> [!div class="nextstepaction"]
> [Tour dos recursos do depurador](../debugger/debugger-feature-tour.md)
