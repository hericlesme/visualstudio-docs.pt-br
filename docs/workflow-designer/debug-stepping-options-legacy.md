---
title: "Opções de revisão (herdado) de depuração | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- branch stepping
- stepping, options in workflow debugging
- debugging, stepping options
- debugging workflows, stepping options
- instance stepping
ms.assetid: 3e9e3041-68c7-4f16-9bd6-da5e5144744b
caps.latest.revision: "5"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: b93226b7223272c04b7d2e6b36b82cf737cd1b86
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="debug-stepping-options-legacy"></a>Opções de avançar de depuração (legados)
Este tópico descreve como depurar aplicativos de [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] que têm atividades simultâneas em [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)]herdado. Use [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] herdado quando você precisa definir como alvo [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 Quando você está depurando atividades herdadas com execução simultânea, tais como **ParallelActivity** ou **ConditionedActivityGroup**, você pode usar uma das duas opções a seguir para depurar seu código .  
  
-   **Avançar de ramificação.** Este modo de depuração permite que você percorrer e depurar uma ramificação específica de uma atividade composta, como o **ParallelActivity** ou **ConditionalActivityGroup** atividade. Quando você usa esta opção depuração, você não irá notar que uma alteração no controle ocorre devido à execução simultânea de outras atividades no fluxo de trabalho. As etapas do depurador somente com as atividades na ramificação atualmente selecionado quando outras atividades no fluxo de trabalho podem executar simultaneamente. Por exemplo, por padrão, a ramificação mais à esquerda em um **ParallelActivity** atividade e a primeira atividade filho de um **ConditionedActivityGroup** atividade são usados para depuração. Se o usuário estiver interessado em depurar qualquer outra atividade de ramificação ou filhos, um ponto de interrupção explícito deve ser colocado na atividade de ramificação ou filho. Depuração continua naquela ramificação quando o ponto de interrupção é disparado.  
  
-   **Avançar de instância.** Este modo de avançar permite que você entrar completamente e depurar executar simultaneamente atividades no fluxo de trabalho. Com essa opção, você observará que uma alteração no controle ocorre ao executar simultaneamente atividades é executado dentro de fluxo de trabalho.  
  
 Por padrão, a opção de avançar da ramificação é selecionada, e os usuários podem alternar entre as duas opções para depurar um fluxo de trabalho herdado.  
  
 Você deve selecionar a opção de avançar da instância ao depurar fluxos de trabalho herdados do computador de estado.  
  
## <a name="see-also"></a>Consulte também  
 [Depuração de fluxos de trabalho herdados](../workflow-designer/debugging-legacy-workflows.md)   
 [Como alterar a opção de executar a depuração em etapas (herdado)](../workflow-designer/how-to-change-the-debug-stepping-option-legacy.md)