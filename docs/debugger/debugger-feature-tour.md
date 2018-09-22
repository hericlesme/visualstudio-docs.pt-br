---
title: Introdução à depuração no VS 2017
description: Introdução à depuração de aplicativos usando o depurador do Visual Studio
ms.custom: mvc
ms.date: 06/15/2018
ms.technology: vs-ide-debug
ms.topic: quickstart
helpviewer_keywords:
- debugger
ms.assetid: c763d706-3213-494f-b4d2-990b6e1ec456
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e2339dcfe80e994b8bc9062d137263d3b25d274d
ms.sourcegitcommit: a749c287ec7d54148505978e8ca55ccd406b71ee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/21/2018
ms.locfileid: "46542410"
---
# <a name="first-look-at-the-visual-studio-debugger"></a>Primeiro, examine o depurador do Visual Studio

Este tópico apresenta as ferramentas de depurador fornecidas pelo Visual Studio. O contexto do Visual Studio, quando você *depurar seu aplicativo*, isso normalmente significa que você está executando o aplicativo com o depurador anexado (ou seja, no modo de depurador). Quando você fizer isso, o depurador fornece várias maneiras de ver o que está fazendo o seu código enquanto ele é executado. Você pode percorrer seu código e examinar os valores armazenados em variáveis, você pode definir inspeções em variáveis para ver quando valores são alterados, você pode examinar o caminho de execução do seu código, et al. Se essa for a primeira vez que você tentou depurar o código, você talvez queira ler [depuração para iniciantes absolutos](../debugger/debugging-absolute-beginners.md) antes de usar este tópico.

Os recursos descritos aqui são aplicáveis a c#, C++, Visual Basic, JavaScript e outras linguagens com suporte pelo Visual Studio (exceto onde observado).

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Definir um ponto de interrupção e iniciar o depurador

Para depurar, você precisa iniciar seu aplicativo com o depurador anexado ao processo do aplicativo. **F5** (**Depurar > Iniciar depuração**) é a maneira mais comum de fazer isso. No entanto, agora você pode não ter definido em qualquer ponto de interrupção para examinar seu aplicativo de código, para que possamos será fazer isso primeiro e, em seguida, iniciar a depuração. Pontos de interrupção são o recurso mais básico e essencial da depuração confiável. Um ponto de interrupção indica quando o Visual Studio deve suspender o código em execução para que você possa examinar os valores das variáveis ou o comportamento de memória ou se uma ramificação de código está sendo executada ou não. 

Se você tiver um arquivo aberto no editor de código, você pode definir um ponto de interrupção clicando na margem à esquerda de uma linha de código.

![Defina um ponto de interrupção](../debugger/media/dbg-tour-set-a-breakpoint.gif "definir pontos de interrupção")

Pressione **F5** (**Depurar > Iniciar depuração**) ou o **iniciar depuração** botão ![iniciar depuração](../debugger/media/dbg-tour-start-debugging.png "iniciar depuração ") na barra de ferramentas de depuração e as execuções do depurador para o primeiro ponto de interrupção que encontra. Se o aplicativo não está em execução ainda, F5 inicia o depurador e é interrompida no primeiro ponto de interrupção.

Pontos de interrupção são um recurso útil quando você sabe que a linha de código ou a seção de código que você deseja examinar em detalhes.

## <a name="navigate"></a> Navegar pelo código no depurador usando comandos de etapa

Nós fornecemos os atalhos de teclado para a maioria dos comandos porque elas tornam a navegação do código do aplicativo mais rápido. (O equivalente comandos, como comandos de menu são mostrados entre parênteses.)

Para iniciar seu aplicativo com o depurador anexado, pressione **F11** (**Depurar > intervir**). F11 é o **intervir** de comando e avança a instrução de um de execução do aplicativo por vez. Quando você inicia o aplicativo com F11, o depurador interromperá na primeira instrução que é executada.

![F11 Intervir](../debugger/media/dbg-tour-f11.png "F11 intervir")

A seta amarela representa a instrução na qual o depurador pausou a, que também suspende a execução de aplicativo no mesmo ponto (esta instrução ainda não foi executada).

F11 é uma boa maneira para examinar o fluxo de execução em que a maioria dos detalhes. (Para mover mais rapidamente por meio de código, vamos mostrar algumas outras opções também.) Por padrão, o depurador ignora o código de não usuário (se você quiser obter mais detalhes, consulte [Just My Code](../debugger/just-my-code.md)).

>[!NOTE]
> No código gerenciado, você verá uma caixa de diálogo perguntando se você deseja ser notificado quando você percorrer automaticamente as propriedades e operadores (comportamento padrão). Se você quiser alterar a configuração mais tarde, desabilite **depurar parcialmente propriedades e operadores** definindo no **Ferramentas > Opções** menu sob **depuração**.

## <a name="step-over-code-to-skip-functions"></a>Step over no código para ignorar a funções

Quando você estiver usando uma linha de código que é uma chamada de função ou método, você poderá pressionar **F10** (**Depurar > Depuração parcial**) em vez de F11.

F10 avança o depurador sem entrar em funções ou métodos no código do aplicativo (o código ainda é executado). Pressionando F10, será possível ignorar código que você não está interessado. Dessa forma, você pode obter rapidamente para o código que você está mais interessado.

## <a name="step-into-a-property"></a>Entrar em uma propriedade

Como mencionado anteriormente, por padrão, o depurador ignora propriedades gerenciadas e campos, mas o **Step Into Specific** comando permite que você substitua esse comportamento.

Clique duas vezes em uma propriedade ou campo e escolha **Step Into Specific**, em seguida, escolha uma das opções disponíveis.

![Intervir específicas](../debugger/media/dbg-tour-step-into-specific.png "passo específico")

Neste exemplo, **Step Into Specific** nos leva ao código para `Path.set`.

![Intervir específicas](../debugger/media/dbg-tour-step-into-specific-2.png "passo específico")

## <a name="run-to-a-point-in-your-code-quickly-using-the-mouse"></a>Executar até um ponto no seu código rapidamente usando o mouse

Enquanto estiver no depurador, passe o mouse sobre uma linha de código até que o **executar com um clique** botão (realizar a execução até aqui) ![executar com um clique](../debugger/media/dbg-tour-run-to-click.png "RunToClick") aparece à esquerda.

![Executar com um clique](../debugger/media/dbg-tour-run-to-click-2.png "executar com um clique")

> [!NOTE]
> O **executar com um clique** há de novo no botão (realizar a execução até aqui) [!include[vs_dev15](../misc/includes/vs_dev15_md.md)].

Clique o **executar com um clique** botão (realizar a execução até aqui). O depurador avança para a linha de código em que você clicou.

Usar esse botão é semelhante à configuração de um ponto de interrupção temporário. Esse comando também é útil para obter rapidamente em torno de dentro de uma região visível do código do aplicativo. Você pode usar **executar com um clique** em qualquer arquivo aberto.

## <a name="advance-the-debugger-out-of-the-current-function"></a>Avançar o depurador sairá da função atual

Às vezes, talvez você queira continuar sua sessão de depuração, mas Avançar o depurador até a função atual.

Pressione **Shift + F11** (ou **Depurar > Depuração circular**).

Este comando retoma a execução do aplicativo (e avança o depurador) até que retorna a função atual.

## <a name="run-to-cursor"></a>Executar até o cursor

Pare o depurador pressionando o **parar depuração** botão vermelho ![parar depuração](../debugger/media/dbg-tour-stop-debugging.png "parar depuração") ou **Shift**  +  **F5**.

Uma linha de código em seu aplicativo com o botão direito e escolha **executar até o Cursor**. Esse comando inicia a depuração e define um ponto de interrupção temporário na linha de código atual.

![Executar até o Cursor](../debugger/media/dbg-tour-run-to-cursor.png "executar até o Cursor")

Se você tiver definido os pontos de interrupção, o depurador pausa no primeiro ponto de interrupção atinge.

Pressione **F5** até chegar a linha de código em que você selecionou **executar até o Cursor**.

Esse comando é útil quando você estiver editando o código e deseja definir um ponto de interrupção temporário rapidamente e iniciar o depurador ao mesmo tempo.

> [!NOTE]
> Você pode usar **executar até o Cursor** na **pilha de chamadas** janela enquanto você está depurando.

## <a name="restart-your-app-quickly"></a>Reinicie o aplicativo rapidamente

Clique o **reinicie** ![reiniciar o aplicativo](../debugger/media/dbg-tour-restart.png "aplicativo reiniciar") botão na barra de ferramentas Depurar (**Ctrl + Shift + F5**).

Quando você pressiona **reiniciar**, ele economiza tempo em comparação com o aplicativo de parar e reiniciar o depurador. O depurador pausa no primeiro ponto de interrupção é atingido pela execução de código.

Se você quiser interromper o depurador e volte para o editor de código, você pode pressionar a parada vermelha ![parar depuração](../debugger/media/dbg-tour-stop-debugging.png "parar depuração") botão em vez de **reiniciar**.

## <a name="inspect-variables-with-data-tips"></a>Inspecionar variáveis com dicas de dados

Agora que você sabe um pouco o seu trabalho, você tem uma boa oportunidade para iniciar a inspecionar o estado do aplicativo (variáveis) com o depurador. Recursos que permitem que você inspecione as variáveis são alguns dos recursos mais úteis do depurador, e há diferentes maneiras de fazê-lo. Muitas vezes, quando você tenta depurar um problema, você está tentando descobrir se as variáveis são armazenar os valores que você espera que eles têm em um estado de aplicativo específico.

Enquanto está em pausa no depurador, passe o mouse sobre um objeto com o mouse e você verá o valor de propriedade padrão (neste exemplo, o nome do arquivo `market 031.jpg` é o valor da propriedade padrão).

![Exibir uma dica de dados](../debugger/media/dbg-tour-data-tips.gif "exibir uma dica de dados")

Expanda o objeto para ver todas as suas propriedades (como o `FullPath` propriedade neste exemplo).

Muitas vezes, durante a depuração, você deseja uma maneira rápida de verificar valores de propriedade em objetos e as dicas de dados são uma boa maneira de fazê-lo.

> [!TIP]
> Em linguagens mais com suporte, você pode editar o código no meio de uma sessão de depuração. Para obter mais informações, consulte [editar e continuar](../debugger/edit-and-continue.md).

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>Inspecionar variáveis com as janelas Autos e locais

Durante a depuração, examine os **automóveis** janela na parte inferior do editor de código.

![Janela de automóveis](../debugger/media/dbg-tour-autos-window.png "janela Autos")

No **automóveis** janela, você ver variáveis juntamente com seu valor atual e seu tipo. O **automóveis** janela mostra todas as variáveis usadas na linha atual ou a linha anterior (em C++, a janela mostra as variáveis nas três linhas de código anteriores. Verifique a documentação para o comportamento específico do idioma).

> [!NOTE]
> No JavaScript, o **Locals** janela tem suporte, mas não a **Autos** janela.

Em seguida, examine os **Locals** janela. O **Locals** janela mostra as variáveis que estão atualmente no escopo.

![Janela locais](../debugger/media/dbg-tour-locals-window.png "janela locais")

Neste exemplo, o `this` objeto e o objeto `f` estão no escopo. Para obter mais informações, consulte [inspecionar variáveis no Windows locais e Autos](../debugger/autos-and-locals-windows.md).

## <a name="set-a-watch"></a>Definir uma inspeção

Você pode usar um **inspeção** janela para especificar uma variável (ou uma expressão) que você deseja que fique de olho no.

Durante a depuração, um objeto com o botão direito e escolha **Adicionar inspeção**.

![Janela de inspeção](../debugger/media/dbg-tour-watch-window.png "janela Inspeção")

Neste exemplo, você tem uma inspeção ativada a `f` objeto e você pode ver seu valor mudam conforme você move o depurador. Ao contrário de outras janelas variáveis, o **inspeção** windows sempre mostram as variáveis que você está observando (eles estão esmaecidos quando fora do escopo).

Para obter mais informações, consulte [definir uma inspeção usando a inspeção e QuickWatch Windows](../debugger/watch-and-quickwatch-windows.md)

## <a name="examine-the-call-stack"></a>Examinar a pilha de chamadas

Clique o **pilha de chamadas** janela enquanto você estiver depurando, por padrão, abrir no painel inferior direito.

![Examinar a pilha de chamadas](../debugger/media/dbg-tour-call-stack.png "examinar a pilha de chamadas")

O **pilha de chamadas** janela mostra a ordem em que métodos e funções estão sendo chamadas. A linha superior mostra a função atual (o `Update` método neste exemplo). A segunda linha mostra que `Update` foi chamado a partir de `Path.set` propriedade e assim por diante. A pilha de chamadas é uma boa maneira para examinar e entender o fluxo de execução de um aplicativo.

> [!NOTE]
> O **pilha de chamadas** janela é semelhante à perspectiva de depuração em alguns IDEs como o Eclipse.

Você pode clicar duas vezes uma linha de código para examinar esse código-fonte e que também altera o escopo atual que está sendo inspecionado pelo depurador. Isso não Avançar o depurador.

Você também pode usar os menus de atalho do **pilha de chamadas** janela para fazer outras coisas. Por exemplo, você pode inserir os pontos de interrupção em funções específicas, reinicie seu aplicativo usando **executar até o Cursor**e ir examinar o código-fonte. Ver [como: examinar a pilha de chamadas](../debugger/how-to-use-the-call-stack-window.md).

## <a name="exception"></a> Examinar uma exceção

Quando seu aplicativo gera uma exceção, o depurador leva você para a linha de código que lançou a exceção.

![Auxiliar de exceção](../debugger/media/dbg-tour-exception-helper.png "auxiliar de exceção")

Neste exemplo, o **auxiliar de exceção** mostra um `System.Argument` exceção e uma mensagem de erro que diz que o caminho não é um formato inválido. Portanto, sabemos que o erro ocorreu em um argumento de método ou função.

Neste exemplo, o `DirectoryInfo` chamada forneceu o erro na cadeia de caracteres vazia armazenada em do `value` variável.

O auxiliar de exceção é um ótimo recurso que pode ajudá-lo a depurar erros. Você também pode fazer coisas como exibir detalhes do erro e adicionar uma inspeção de auxiliar de exceção. Ou, se necessário, você pode alterar as condições para lançar a exceção específica.

>  [!NOTE]
> O auxiliar de exceção substitui o Assistente de exceção em [!include[vs_dev15](../misc/includes/vs_dev15_md.md)].

Expanda o **configurações de exceção** nó para ver mais opções sobre como lidar com esse tipo de exceção, mas você não precisa alterar nada para este tour!

## <a name="debug-live-aspnet-apps-in-azure-app-service"></a>Depurar aplicativos ASP.NET dinâmicos no serviço de aplicativo do Azure

o **depurador de instantâneo** tira um instantâneo de seus aplicativos em produção quando o código que você está interessado é executado. Para instruir o depurador a tirar um instantâneo, defina snappoints e logpoints em seu código. O depurador permite ver exatamente o que deu errado sem afetar o tráfego do seu aplicativo de produção. O Depurador de Instantâneo pode ajudar a reduzir drasticamente o tempo que leva para resolver problemas que ocorrem em ambientes de produção.

![Iniciar o depurador de instantâneo](../debugger/media/snapshot-launch.png "iniciar o depurador de instantâneo")

Coleta de instantâneo está disponível para aplicativos ASP.NET em execução no serviço de aplicativo do Azure. Aplicativos ASP.NET devem estar em execução no .NET Framework 4.6.1 ou posterior, e os aplicativos ASP.NET Core devem ser executado no .NET Core 2.0 ou posterior no Windows.

Para obter mais informações, consulte [depurar aplicativos ASP.NET dinâmicos usando o depurador de instantâneo](../debugger/debug-live-azure-applications.md).

## <a name="view-snapshots-with-intellitrace-step-back-visual-studio-enterprise"></a>Exibir instantâneos com o retrocesso do IntelliTrace (Visual Studio Enterprise)

**Retrocesso do IntelliTrace** tira um instantâneo do seu aplicativo em cada ponto de interrupção e o depurador automaticamente a eventos de etapa. Os instantâneos registrados permitem retornar aos pontos de interrupção ou às etapas anteriores e exibir o estado do aplicativo como ele era no passado. O retrocesso do IntelliTrace poderá poupar seu tempo quando você desejar ver o estado do aplicativo anterior, mas não desejar reiniciar a depuração nem recriar o estado do aplicativo desejado.

É possível navegar e exibir instantâneos usando os botões **Voltar** e **Avançar** na barra de ferramentas Depurar. Esses botões navegam pelos eventos exibidos na guia **Eventos** na janela **Ferramentas de Diagnóstico**.

![Etapa para trás e para frente botões](../debugger/media/intellitrace-step-back-icons-description.png  "botões Voltar e Avançar")

Para obter mais informações, consulte o [inspecionar estados anteriores do aplicativo usando o IntelliTrace](../debugger/view-historical-application-state.md) página.

## <a name="next-steps"></a>Próximas etapas

Neste tutorial, você teve uma rápida olhada muitos recursos do depurador. Convém uma visão mais detalhada sobre esses recursos usando um aplicativo de exemplo

> [!div class="nextstepaction"]
> [Aprenda a depurar usando o Visual Studio](../debugger/getting-started-with-the-debugger.md)
