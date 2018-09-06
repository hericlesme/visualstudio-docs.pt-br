---
title: Exibir a pilha de chamadas no depurador do Visual Studio | Microsoft Docs
ms.custom: H1Hack27Feb2017
ms.date: 04/06/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.callstack
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
- aspx
helpviewer_keywords:
- threading [Visual Studio], displaying calls to or from
- functions [debugger], viewing code on call stack
- disassembly code
- breakpoints, Call Stack window
- debugging [Visual Studio], switching to another stack frame
- debugging [Visual Studio], Call Stack window
- Call Stack window, viewing source code for functions on the call stack
- stack, switching stack frames
- Call Stack window, viewing disassembly code for functions on the call stack
ms.assetid: 5154a2a1-4729-4dbb-b675-db611a72a731
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 168f89512dee8331448db1becabdc7262b5e4744
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43774717"
---
# <a name="view-the-call-stack-and-use-the-call-stack-window-in-the-visual-studio-debugger"></a>Exibir a pilha de chamadas e usar a janela de pilha de chamadas no depurador do Visual Studio

Usando o **pilha de chamadas** janela, você pode exibir as chamadas de função ou procedimento que estão atualmente na pilha. O **pilha de chamadas** janela mostra a ordem em que métodos e funções estão sendo chamadas. A pilha de chamadas é uma boa maneira para examinar e entender o fluxo de execução de um aplicativo.
  
Quando [símbolos de depuração](#bkmk_symbols) não estão disponíveis para a parte de uma pilha de chamadas, o **pilha de chamadas** janela pode não ser capaz de exibir as informações corretas para essa parte da pilha de chamadas. Se isso ocorrer, a notação a seguir será exibida:  
  
`[Frames below may be incorrect and/or missing, no symbols loaded for name.dll]`

>  [!NOTE]
> O **pilha de chamadas** janela é semelhante à perspectiva de depuração em alguns IDEs como o Eclipse. 

> [!NOTE]
>  As caixas de diálogo e os comandos de menu vistos podem ser diferentes daqueles descritos aqui, dependendo da edição ou das configurações ativas. Para alterar suas configurações, selecione **Import and Export Settings** sobre o **ferramentas** menu.  Consulte [Personalizando o IDE](../ide/personalizing-the-visual-studio-ide.md)
  
## <a name="view-the-call-stack-while-in-the-debugger"></a>Exibir a pilha de chamadas no depurador 
  
-   Durante a depuração, o **Debug** menu, selecione **Windows > pilha de chamadas**.

 ![Janela pilha de chamadas](../debugger/media/dbg_basics_callstack_window.png "CallStackWindow")

Uma seta amarela identifica o quadro de pilha onde o ponteiro de execução está localizado atualmente. Por padrão, esse é o quadro de pilha que cujas informações aparecem na origem, **Locals**, **Autos**, **Assista**, e **desmontagem** windows . Se você quiser alterar o contexto do depurador para outro quadro na pilha, você pode fazer isso [alternar para outro quadro de pilha](#bkmk_switch).   
  
## <a name="display-non-user-code-in-the-call-stack-window"></a>Exibir o código de não usuário na janela pilha de chamadas  
  
-   Clique com botão direito do **pilha de chamadas** janela e selecione **Mostrar código externo**.

Código de não usuário é qualquer código que não é mostrado quando [Just My Code](../debugger/just-my-code.md) está habilitado. No código gerenciado, os quadros de código não-usuário ficam ocultos por padrão. A notação a seguir é exibida em vez dos quadros de código não-usuário:  
  
**[\<Código externo >]**  
  
## <a name="bkmk_switch"></a> Alternar para outro quadro de pilha (alterar o contexto do depurador)
  
1.  No **pilha de chamadas** janela, o botão direito do mouse a pilha de quadro cujos código e os dados que você deseja exibir.

    Ou, você pode clicar duas vezes em um quadro do **pilha de chamadas** janela para alternar para quadro selecionado. 
  
2.  Selecione **alternar para quadro**.  
  
     Uma seta verde com uma parte final encaracolada aparece ao lado do quadro de pilha que você selecionou. O ponteiro de execução permanece no quadro original, que ainda está marcado com a seta amarela. Se você selecionar **etapa** ou **continuar** do **depurar** menu, a execução continuará no quadro original, não no quadro selecionado.  
  
## <a name="view-the-source-code-for-a-function-on-the-call-stack"></a>Exibir o código-fonte para uma função na pilha de chamadas  
  
-   No **pilha de chamadas** janela, o botão direito do mouse na função cujo código-fonte código que você deseja ver e selecione **ir para código-fonte**.

## <a name="run-to-a-specific-function-from-the-call-stack-window"></a>Executar uma função específica da janela pilha de chamadas  
  
-  No **pilha de chamadas** janela, selecione a função, clique com botão direito e escolha **executar até o Cursor**.  
  
## <a name="set-a-breakpoint-on-the-exit-point-of-a-function-call"></a>Defina um ponto de interrupção no ponto de saída de uma chamada de função  
  
-   Ver [defina um ponto de interrupção em uma função de pilha de chamada](../debugger/using-breakpoints.md#BKMK_Set_a_breakpoint_in_the_call_stack_window).

## <a name="display-calls-to-or-from-another-thread"></a>Exibe chamadas para ou de outro thread  
  
-   Clique com botão direito do **pilha de chamadas** janela e selecione **incluem chamadas para / de outros Threads**.   
  
## <a name="visually-trace-the-call-stack"></a>Rastrear visualmente a pilha de chamadas  

Se você estiver usando o Visual Studio Enterprise (somente), você pode exibir mapas de código para a pilha de chamadas durante a depuração.

- No **pilha de chamadas** janela, abra o menu de atalho. Escolher **Mostrar pilha de chamadas no mapa de códigos**. (Teclado: **CTRL** + **SHIFT** + **`**)  
  
    Para obter informações detalhadas, consulte [mapear métodos na pilha de chamadas ao depurar](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).

![Mostrar pilha de chamadas no mapa de códigos](../debugger/media/dbg_basics_show_call_stack_on_code_map.gif "ShowCallStackOnCodeMap")
  
## <a name="view-the-disassembly-code-for-a-function-on-the-call-stack"></a>Exibir o código de desmontagem para uma função na pilha de chamadas  
  
-   No **pilha de chamadas** janela, o botão direito do mouse a função cujo código de desmontagem você deseja ver e selecione **ir para desmontagem**.    

## <a name="change-the-optional-information-displayed"></a>Alterar as informações opcionais exibidas  
  
-   Clique com botão direito do **pilha de chamadas** janela e defina ou desmarque **mostram \<**  _as informações que você deseja_ **>**.  
  
## <a name="bkmk_symbols"></a> Carregar símbolos para um módulo
No **pilha de chamadas** janela, você pode carregar símbolos de depuração para o código que não tem símbolos carregados atualmente. Esses símbolos podem ser símbolos do .NET Framework ou do sistema baixados dos servidores públicos de símbolo da Microsoft ou de símbolos em um caminho de símbolo no computador que você está depurando.  
  
Consulte [especificar símbolo (. PDB) e arquivos de origem](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)  
  
### <a name="to-load-symbols"></a>Para carregar símbolos  
  
1.  No **pilha de chamadas** janela, o botão direito do mouse quadro da pilha para o qual os símbolos não são carregados. O quadro ficará esmaecido.  
  
2.  Aponte para **Load Symbols** e, em seguida, clique em **servidores de símbolo Microsoft** (se disponível) ou navegue até o caminho do símbolo.  
  
### <a name="to-set-the-symbol-path"></a>Para definir o caminho do símbolo  
  
1.  No **pilha de chamadas** janela, escolha **configurações de símbolo** no menu de atalho.  
  
     O **opções** caixa de diálogo é aberta e o **símbolos** página é exibida.  
  
2.  Clique em **configurações de símbolo**.  
  
3.  No **opções** caixa de diálogo, clique no ícone de pasta.  
  
     No **locais de arquivo (. PDB) de símbolo** caixa, será exibido um cursor.  
  
4.  Digite um nome de caminho de diretório no local do símbolo no computador que você está depurando. Para depuração local e remota, esse é um caminho no computador local.
  
5.  Clique em **OK** para fechar a caixa de diálogo **Opções**.  
  
## <a name="see-also"></a>Consulte também  
 [Código misto e informações ausentes na janela Pilha de Chamadas](../debugger/mixed-code-and-missing-information-in-the-call-stack-window.md)  
 [Exibindo dados no depurador](../debugger/viewing-data-in-the-debugger.md)   
 [Especifique o símbolo (. PDB) e arquivos de origem](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Usando pontos de interrupção](../debugger/using-breakpoints.md)