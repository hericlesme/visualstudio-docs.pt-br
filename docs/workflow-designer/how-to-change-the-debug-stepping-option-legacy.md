---
title: "Como: alterar a opção de Avançar de depuração (legados) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- branch stepping
- debugging, stepping options
- debugging workflows, stepping options
- stepping, changing options
- instance stepping
ms.assetid: aedc06af-d58a-44d6-aee4-f397f1f923a0
caps.latest.revision: "5"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: ff11186c82102230ec939c0c9b1c5aba69df7f3f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-change-the-debug-stepping-option-legacy"></a>Como: Altere a opção de avançar de depuração (o legados)
Este tópico descreve como modificar a opção de avançar de depuração para aplicativos de [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] em novas [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] que têm ações simultâneas. Use [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] herdado quando você precisa definir como alvo [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 Quando você está depurando atividades herdadas com execução simultânea, tais como **ParallelActivity** ou **ConditionedActivityGroup**, você pode usar uma das duas opções para depurar seu código.  
  
 Siga estas etapas para alterar a opção de avançar de depuração no seu projeto herdado de fluxo de trabalho.  
  
## <a name="procedures"></a>Procedimentos  
  
#### <a name="to-change-the-debug-stepping-option"></a>Para alterar a opção de avançar de depuração  
  
1.  Inicie o Visual Studio.  
  
2.  Abrir um projeto existente herdado de fluxo de trabalho ou criar um novo projeto que empreguem atividades simultâneas e que tem como alvo [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
3.  Sobre o **fluxo de trabalho** menu herdado [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], aponte para **depurar**e, em seguida, aponte para **opções de revisão**.  
  
4.  Selecione **instância** ou **ramificação**.  
  
## <a name="see-also"></a>Consulte também  
 [Depuração de fluxos de trabalho herdados](../workflow-designer/debugging-legacy-workflows.md)   
 [Opções de passo a passo em depuração (herdado)](../workflow-designer/debug-stepping-options-legacy.md)