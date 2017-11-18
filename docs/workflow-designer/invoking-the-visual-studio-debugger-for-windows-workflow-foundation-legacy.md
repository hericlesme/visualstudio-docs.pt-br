---
title: Chamar o depurador do Visual Studio para Windows Workflow Foundation (legados) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- stepping
- Step Over command
- stepping, commands
- debugging, using workflow debugger
- workflows, debugger
- workflow debugger, starting
- Step In command
- debugger, workflow
- Step Out command
- debugging workflows, starting the debugger
ms.assetid: d6f58e35-5cce-4ff2-9afc-b2d9d0f819cf
caps.latest.revision: "6"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: f56c7926e949511d90af20ce6789fe662c08e1c3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy"></a>Chamar o depurador do Visual Studio para Windows Workflow Foundation (legados)
Este tópico descreve como usar o depurador de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] depuração de aplicativos [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] em [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)]herdado. Use [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] herdado quando você precisa definir como alvo [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 Geralmente, você depura fluxos de trabalho herdados assim como você os programas de depuração escritos em outras linguagens de programação do Visual Studio. Você pode iniciar o depurador de [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] para Windows Workflow Foundation as seguintes maneiras:  
  
-   Selecione **anexar ao processo** no **depurar** menu para selecionar uma instância de fluxo de trabalho em execução dos processos disponíveis.  
  
-   Pressione **F5** para iniciar a execução de uma instância do fluxo de trabalho, ou para continuar a executar após um ponto de interrupção foi atingido.  
  
## <a name="stepping-through-code"></a>Percorrendo o código  
 O depurador oferece suporte a um dos procedimentos de depuração mais comuns, pisando, que está executando a linha de código por vez. Há três comandos para depurar código:  
  
-   **Etapa em**: você pode entrar usando uma atividade **F11**. O depurador avança em qualquer manipulador que é definido. Se nenhum manipulador é definido, você vai sobre a atividade, ou com atividades compostas, que contém outras atividades, você vai na primeira atividade executando. Não há suporte para a depuração em manipuladores de código do designer para as seguintes atividades: **IfElseActivity**, **WhileActivity**, **ConditionedActivityGroup**, ou o **ReplicatorActivity**. Para depurar os manipuladores associados com essas atividades, você deve colocar pontos de interrupção explícitos no código.  
  
-   **Sair**: você pode sair de uma atividade usando **Shift-F11**. Depuração fora de uma atividade executa a atividade atual e todas as suas atividades irmãos para a conclusão. O depurador interrompe no pai de atividade atual. Para passar para fora de um manipulador de código, o depurador interrompe a atividade com que o manipulador está associado.  
  
-   **Passar por**: você pode passar por uma atividade usando **F10**. Para entrar em uma atividade composta. o depurador interrompe no primeiro filho executável de atividade composta. Ao depurar uma não compostas, como um **CodeActivity** atividade, o depurador executa a atividade e seus identificadores associados e quebras na próxima atividade. Se a atividade que é executada é a atividade filho a última em uma atividade de composição, então após a execução, as quebras do depurador na atividade pai.  
  
## <a name="attaching-to-a-process"></a>Anexar a um processo  
 Para depurar um fluxo de trabalho, anexando a um processo, selecione o processo disponível a partir de **processos disponíveis** caixa de listagem no **anexar ao processo** caixa de diálogo. Se **automático: código de fluxo de trabalho** não é exibido no **anexar a** texto caixa e, em seguida, clique em **selecione**. No **Selecionar tipo de código** caixa de diálogo, clique em **depurar esses tipos de código** e selecione **fluxo de trabalho**. Em seguida, clique em **Okey** e clique em **Attach**.  
  
## <a name="debugging-with-f5"></a>Depuração com F5  
 Se um aplicativo de host de fluxo de trabalho e a DLL de fluxo de trabalho estão localizados em diferentes projetos do Visual Studio, por exemplo, quando você estiver usando uma biblioteca de atividades de fluxo de trabalho, você deve definir o projeto DLL do fluxo de trabalho como o projeto de inicialização de solução do Visual Studio para depurar o fluxo de trabalho usando **F5**. Você também deve definir o caminho para o aplicativo de host do projeto de DLL de fluxo de trabalho **Iniciar programa externo** propriedade.  
  
 Para definir um projeto de inicialização no Gerenciador de soluções, clique no nome do projeto e selecione **definir como projeto de inicialização**. Para definir o caminho para o host no **Iniciar programa externo** propriedade, clique duas vezes o projeto de fluxo de trabalho **propriedades** nó no Gerenciador de soluções e selecione o **depurar** guia. Em **iniciar ação**, selecione **Iniciar programa externo** e insira o caminho para o arquivo de .exe que está hospedando o fluxo de trabalho que você deseja depurar.  
  
 Se o aplicativo host é definido como o projeto de inicialização, somente o depurador do Visual Studio é invocado depuração; o depurador de [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] para Windows Workflow Foundation não é chamado. Se o depurador do Visual Studio é usado, somente os pontos de interrupção C# ou de código Visual Basic estão batidos; os pontos de interrupção definidos no designer de fluxo de trabalho não são batidos. Por exemplo, um ponto de interrupção que você definiu em uma atividade de <xref:System.Workflow.Activities.ParallelActivity> no designer é atingido se o depurador de [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] para Windows Workflow Foundation é usado, mas não quando você usar o depurador Visual Studio.  
  
## <a name="see-also"></a>Consulte também  
 [Como: definir pontos de interrupção em fluxos de trabalho (legados)](../workflow-designer/how-to-set-breakpoints-in-workflows-legacy.md)   
 [Depurando fluxos de trabalho herdados](../workflow-designer/debugging-legacy-workflows.md)