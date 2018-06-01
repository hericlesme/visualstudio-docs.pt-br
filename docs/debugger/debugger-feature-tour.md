---
title: Introdução ao depurador
description: Dar uma olhada rápida os diferentes recursos do depurador do Visual Studio.
ms.custom: mvc
ms.date: 03/27/2018
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
ms.openlocfilehash: de27a6b3fd5b182ac2fa0ad12ed04e4d1105d9ac
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/01/2018
ms.locfileid: "34691086"
---
# <a name="first-look-at-the-visual-studio-debugger"></a>Primeiro examinar o depurador do Visual Studio

Este tópico apresenta os recursos do depurador do Visual Studio. Se você deseja acompanhar abrindo seu próprio aplicativo no Visual Studio, você pode fazer isso ou você pode acompanhar um aplicativo de exemplo usando o [guia do Iniciante](../debugger/getting-started-with-the-debugger.md).

Os recursos descritos aqui são aplicáveis ao c#, C++, Visual Basic, JavaScript e outras linguagens com suporte pelo Visual Studio (exceto onde observado).

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Definir um ponto de interrupção e iniciar o depurador

Para depurar, você precisa iniciar seu aplicativo com o depurador anexado ao processo de aplicativo. F5 (**Depurar > Iniciar depuração**) é a maneira mais comum de fazer isso. No entanto, agora você pode não ter definido em qualquer ponto de interrupção para examinar seu aplicativo de código, portanto, será faça isso primeiro e, em seguida, iniciar a depuração.

Se você tiver um arquivo aberto no editor de código, você pode definir um ponto de interrupção clicando na margem à esquerda de uma linha de código.

![Definir um ponto de interrupção](../debugger/media/dbg-tour-set-a-breakpoint.gif "definir um ponto de interrupção")

Pressione F5 (**Depurar > Iniciar depuração**) e o depurador é executado no primeiro ponto de interrupção que encontrar. Se o aplicativo ainda não estiver executando, F5 inicia o depurador e para no primeiro ponto de interrupção.

Pontos de interrupção são um recurso útil quando você sabe que a linha de código ou na seção de código que você deseja examinar detalhadamente.

## <a name="navigate-code-in-the-debugger-using-step-commands"></a>Navegar pelo código no depurador usando os comandos de etapa

Nós fornecemos os atalhos de teclado para a maioria dos comandos porque elas tornam a navegação de código do seu aplicativo mais rápido. (Equivalente a comandos, como comandos de menu são mostrados entre parênteses.)

Para iniciar seu aplicativo com o depurador anexado, pressione F11 (**Depurar > intervir**). F11 é o **intervir** de comando e avança no aplicativo execução uma instrução de cada vez. Quando você inicia o aplicativo com F11, o depurador interromperá na primeira instrução que é executada.

![F11 Intervir](../debugger/media/dbg-tour-f11.png "F11 intervir")

A seta amarela representa a instrução na qual o depurador pausa, que também suspende a execução do aplicativo no mesmo momento (essa instrução ainda não executada).

F11 é uma boa maneira de examinar o fluxo de execução mais detalhadamente. (Para mover mais rapidamente por meio de código, mostramos algumas outras opções também.) Por padrão, o depurador ignora código não-usuário (se você quiser obter mais detalhes, consulte [Just My Code](../debugger/just-my-code.md)).

>[!NOTE]
> No código gerenciado, você verá uma caixa de diálogo perguntando se você deseja ser notificado quando você percorrer automaticamente propriedades e operadores (comportamento padrão). Se você quiser alterar a configuração mais tarde, desabilitar **percorrer propriedades e operadores** definindo no **Ferramentas > Opções** menu em **depuração**.

## <a name="step-over-code-to-skip-functions"></a>Percorrer o código para ignorar a funções

Quando você estiver em uma linha de código que é uma chamada de função ou método, você pode pressionar F10 (**Depurar > passar por**) em vez de F11.

F10 avança o depurador sem depuração em funções ou métodos no código do aplicativo (o código ainda é executado). Pressione F10, será possível ignorar código que você não estiver interessado em. Dessa forma, você pode obter rapidamente ao código que você está mais interessado.

## <a name="step-into-a-property"></a>Etapa em uma propriedade

Como mencionado anteriormente, por padrão, o depurador ignora propriedades gerenciadas e campos, mas o **passo específico** comando permite substituir esse comportamento.

Clique duas vezes em uma propriedade ou campo e escolha **passo específico**, em seguida, escolha uma das opções disponíveis.

![Etapa específico](../debugger/media/dbg-tour-step-into-specific.png "passo específico")

Neste exemplo, **passo específico** nos leva para o código para `Path.set`.

![Etapa específico](../debugger/media/dbg-tour-step-into-specific-2.png "passo específico")

## <a name="run-to-a-point-in-your-code-quickly-using-the-mouse"></a>Executar até um ponto no seu código rapidamente usando o mouse

No depurador, passe o mouse sobre uma linha de código até que o **executar em, clique em** botão (execução aqui) ![executar em, clique em](../debugger/media/dbg-tour-run-to-click.png "RunToClick") aparece à esquerda.

![Execute a clique](../debugger/media/dbg-tour-run-to-click-2.png "executar em, clique em")

> [!NOTE]
> O **executar a clique** botão (execução aqui) é novo no [!include[vs_dev15](../misc/includes/vs_dev15_md.md)].

Clique o **executar a clique** botão (execução aqui). O depurador avança para a linha de código em que você clicou.

Com esse botão é semelhante à configuração de um ponto de interrupção temporário. Esse comando também é útil para obter rapidamente em torno de dentro de uma região visível do código de aplicativo. Você pode usar **executar a clique** em qualquer arquivo aberto.

## <a name="advance-the-debugger-out-of-the-current-function"></a>Avançar o depurador sairá da função atual

Às vezes, você talvez queira continuar a sessão de depuração, mas Avançar o depurador até a função atual.

Pressione Shift + F11 (ou **Depurar > Sair**).

Este comando retoma a execução do aplicativo (e avança o depurador) até que retorna a função atual.

## <a name="run-to-cursor"></a>Executar até o cursor

Parar o depurador pressionando o **parar depuração** botão vermelho ![parar depuração](../debugger/media/dbg-tour-stop-debugging.png "parar depuração") ou Shift + F5.

Clique em uma linha de código em seu aplicativo e escolha **executar até o Cursor**. Esse comando inicia a depuração e define um ponto de interrupção temporário na linha atual do código.

![Executar até o Cursor](../debugger/media/dbg-tour-run-to-cursor.png "executar até o Cursor")

Se você tiver definido os pontos de interrupção, o depurador faz uma pausa no primeiro ponto de interrupção que ele chega.

Pressione F5 até atingir a linha de código em que você selecionou **executar até o Cursor**.

Esse comando é útil quando você estiver editando o código e deseja definir um ponto de interrupção temporário rapidamente e iniciar o depurador.

> [!NOTE]
> Você pode usar **executar até o Cursor** no **pilha de chamadas** janela enquanto você está depurando.

## <a name="restart-your-app-quickly"></a>Reinicie seu aplicativo rapidamente

Clique no **reiniciar** ![aplicativo reiniciar](../debugger/media/dbg-tour-restart.png "aplicativo reiniciar") botão na barra de ferramentas Depurar (**Ctrl + Shift + F5**).

Quando você pressiona **reiniciar**, economiza tempo e parar o aplicativo e reiniciar o depurador. O depurador faz uma pausa no primeiro ponto de interrupção é atingido com a execução de código.

Se você deseja parar o depurador e voltar para o editor de código, você pode pressionar a parada vermelha ![parar depuração](../debugger/media/dbg-tour-stop-debugging.png "parar depuração") botão em vez de **reiniciar**.

## <a name="inspect-variables-with-data-tips"></a>Inspecionar variáveis com dicas de dados

Agora que você conhece as utilidades um pouco, você tem uma boa oportunidade para iniciar inspecionar o estado do aplicativo (variáveis) com o depurador. Recursos que permitem que você inspecione as variáveis são alguns dos recursos mais úteis do depurador, e há diferentes maneiras de fazer isso. Geralmente, quando você tentar depurar um problema, você está tentando descobrir se variáveis estão armazenando os valores que você espera que eles têm em um estado de aplicativo específico.

Enquanto está em pausa no depurador, passe o mouse sobre um objeto com o mouse e consulte seu valor de propriedade padrão (neste exemplo, o nome do arquivo `market 031.jpg` é o valor da propriedade padrão).

![Exibir uma dica de dados](../debugger/media/dbg-tour-data-tips.gif "exibir uma dica de dados")

Expanda o objeto para ver todas as suas propriedades (como o `FullPath` propriedade neste exemplo).

Geralmente, ao depurar, você deseja uma maneira rápida de verificar os valores de propriedade em objetos e as dicas de dados são uma boa maneira de fazer isso.

> [!TIP]
> Em linguagens mais com suporte, você pode editar o código no meio de uma sessão de depuração. Para obter mais informações, consulte [editar e continuar](../debugger/edit-and-continue.md).

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>Inspecionar variáveis com o windows Autos e locais

Durante a depuração, examine o **Autos** janela na parte inferior do editor de código.

![Janela de automóveis](../debugger/media/dbg-tour-autos-window.png "janela Autos")

No **Autos** janela, você vê variáveis juntamente com seu valor atual e seu tipo. O **Autos** janela mostra todas as variáveis usadas na linha atual ou a linha precedente (em C++, a janela mostra variáveis em três linhas de código. Verifique a documentação para o comportamento específico do idioma).

> [!NOTE]
> No JavaScript, o **locais** janela tem suporte mas não o **Autos** janela.

Em seguida, examinar o **locais** janela. O **locais** janela mostra as variáveis que estão atualmente no escopo.

![Janela locais](../debugger/media/dbg-tour-locals-window.png "janela locais")

Neste exemplo, o `this` o objeto e `f` estão no escopo. Para obter mais informações, consulte [inspecionar variáveis nas janelas de locais e Autos](../debugger/autos-and-locals-windows.md).

## <a name="set-a-watch"></a>Definir uma inspeção

Você pode usar um **inspecionar** janela para especificar uma variável (ou uma expressão) que você deseja acompanhar na.

Durante a depuração, clique em um objeto e escolha **Adicionar inspeção**.

![Janela Inspecionar](../debugger/media/dbg-tour-watch-window.png "janela Inspecionar")

Neste exemplo, você tem uma inspeção ativada a `f` objeto e você pode ver seu valor alterar quando você percorre o depurador. Ao contrário de outras janelas variável, o **inspecionar** windows sempre mostrar as variáveis que você está observando (estão esmaecidos quando fora do escopo).

Para obter mais informações, consulte [definir uma inspeção usando a observação e QuickWatch Windows](../debugger/watch-and-quickwatch-windows.md)

## <a name="examine-the-call-stack"></a>Examinar a pilha de chamadas

Clique o **pilha de chamadas** janela enquanto você está depurando, por padrão, abrir no painel inferior direito.

![Examinar a pilha de chamadas](../debugger/media/dbg-tour-call-stack.png "examinar a pilha de chamadas")

O **pilha de chamadas** janela mostra a ordem em que estão sendo chamadas funções e métodos. A linha superior mostra a função atual (o `Update` método neste exemplo). A segunda linha mostra que `Update` foi chamado a partir de `Path.set` propriedade e assim por diante. A pilha de chamadas é uma boa maneira de examinar e compreender o fluxo de execução de um aplicativo.

> [!NOTE]
> O **pilha de chamadas** janela é semelhante à perspectiva de depuração em alguma IDEs como Eclipse.

Você pode clicar duas vezes uma linha de código para consultar esse código-fonte e que também altera o escopo atual que está sendo inspecionado pelo depurador. Isso não adiantar o depurador.

Você também pode usar os menus de atalho do **pilha de chamadas** janela para fazer outras coisas. Por exemplo, você pode inserir pontos de interrupção em funções específicas, reinicie seu aplicativo usando **executar até o Cursor**e para examinar o código-fonte. Consulte [como: examinar a pilha de chamadas](../debugger/how-to-use-the-call-stack-window.md).

## <a name="examine-an-exception"></a>Examine a exceção

Quando seu aplicativo lançará uma exceção, o depurador leva você para a linha de código que lançou a exceção.

![Auxiliar de exceção](../debugger/media/dbg-tour-exception-helper.png "auxiliar de exceção")

Neste exemplo, o **auxiliar de exceção** mostra um `System.Argument` exceção e uma mensagem de erro que afirma que o caminho não é um formato inválido. Portanto, sabemos que o erro ocorreu em um argumento de método ou função.

Neste exemplo, o `DirectoryInfo` chamada forneceu o erro na cadeia de caracteres vazia armazenada no `value` variável.

O auxiliar de exceção é um ótimo recurso que pode ajudá-lo a depurar erros. Você também pode fazer coisas como exibir detalhes do erro e adicione uma inspeção do auxiliar de exceção. Ou, se necessário, você pode alterar as condições para lançar a exceção específica.

>  [!NOTE]
> O auxiliar de exceção substitui o Assistente de exceção no [!include[vs_dev15](../misc/includes/vs_dev15_md.md)].

Expanda o **configurações de exceção** nó para ver mais opções sobre como lidar com esse tipo de exceção, mas você não precisa alterar nada para este tour!

## <a name="debug-live-aspnet-apps-in-azure-app-service"></a>Depurar aplicativos dinâmicos do ASP.NET no serviço de aplicativo do Azure

o **instantâneo depurador** tira um instantâneo de seus aplicativos em produção quando executa código que você está interessado. Para instruir o depurador a tirar um instantâneo, defina snappoints e logpoints em seu código. O depurador permite ver exatamente o que deu errado sem afetar o tráfego do seu aplicativo de produção. O Depurador de Instantâneo pode ajudar a reduzir drasticamente o tempo que leva para resolver problemas que ocorrem em ambientes de produção.

![Iniciar o depurador do instantâneo](../debugger/media/snapshot-launch.png "iniciar o depurador do instantâneo")

Coleção de instantâneo está disponível para aplicativos ASP.NET em execução no serviço de aplicativo do Azure. Aplicativos ASP.NET devem estar em execução no .NET Framework 4.6.1 ou posterior, e aplicativos ASP.NET Core devem estar em execução no .NET Core 2.0 ou posterior no Windows.

Para obter mais informações, consulte [depurar aplicativos do ASP.NET ao vivo usando o depurador do instantâneo](../debugger/debug-live-azure-applications.md).

## <a name="view-snapshots-with-intellitrace-step-back-visual-studio-enterprise"></a>Exibir instantâneos com o IntelliTrace etapa-back (Visual Studio Enterprise)

**Retorno de etapa IntelliTrace** automaticamente tira um instantâneo do seu aplicativo em cada ponto de interrupção e o depurador de evento da etapa. Os instantâneos registrados permitem retornar aos pontos de interrupção ou às etapas anteriores e exibir o estado do aplicativo como ele era no passado. O retrocesso do IntelliTrace poderá poupar seu tempo quando você desejar ver o estado do aplicativo anterior, mas não desejar reiniciar a depuração nem recriar o estado do aplicativo desejado.

É possível navegar e exibir instantâneos usando os botões **Voltar** e **Avançar** na barra de ferramentas Depurar. Esses botões navegam pelos eventos exibidos na guia **Eventos** na janela **Ferramentas de Diagnóstico**.

![Etapa para trás e frente botões](../debugger/media/intellitrace-step-back-icons-description.png  "botões etapa com versões anteriores e Avançar")

Para obter mais informações, consulte a página [View snapshots using IntelliTrace step-back](../debugger/how-to-use-intellitrace-step-back.md) (Exibir instantâneos usando o retrocesso do IntelliTrace).

## <a name="next-steps"></a>Próximas etapas

Neste tutorial, você teve uma visão geral de muitos recursos do depurador. Talvez você queira uma análise mais detalhada desses recursos usando um aplicativo de exemplo

> [!div class="nextstepaction"]
> [Aprenda a depurar usando o Visual Studio](../debugger/getting-started-with-the-debugger.md)
