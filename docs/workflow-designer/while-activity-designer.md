---
title: Embora o Designer de atividade | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- System.Activities.Statements.While.UI
ms.assetid: ea008091-2e4c-4f64-bfa5-afb919552446
caps.latest.revision: 
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload:
- multiple
ms.openlocfilehash: f232d8e6c4a1dab9000b8f0e0f3037d083acbbef
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="while-activity-designer"></a>Quando designer de atividades
O <xref:System.Activities.Statements.While> atividade executa a atividade contida em seu <xref:System.Activities.Statements.While.Body%2A> enquanto especificado <xref:System.Activities.Statements.While.Condition%2A> é avaliada como **true**. A atividade contida nunca pode executar. Se você desejar que a atividade contida a ser executada pelo menos uma vez, use a atividade de <xref:System.Activities.Statements.DoWhile> em vez disso.  
  
## <a name="while-properties-in-workflow-designer"></a>Quando propriedades em Designer de Fluxo de Trabalho  
 A tabela a seguir mostra as propriedades mais úteis de atividade de <xref:System.Activities.Statements.While> e descreve como elas são usadas no designer.  
  
|Nome da Propriedade|Necessária|Uso|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Especifica o nome amigável do designer de atividade de <xref:System.Activities.Statements.While> no cabeçalho. O valor padrão é quando. O valor pode ser editado no **propriedades** janela ou diretamente no cabeçalho de designer de atividade.<br /><br /> Embora não seja necessário <xref:System.Activities.Activity.DisplayName%2A> restrita, é uma prática recomendada usar um.|  
|<xref:System.Activities.Statements.While.Body%2A>|False|Contém a atividade seja executada enquanto o <xref:System.Activities.Statements.While.Condition%2A> é avaliada como **true**.|  
|<xref:System.Activities.Statements.While.Condition%2A>|verdadeiro|Contém a expressão de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] que é avaliada para determinar se a atividade em <xref:System.Activities.Statements.While.Body%2A> deve ser executada.|  
  
## <a name="see-also"></a>Consulte também  
 [Fluxo de controle](../workflow-designer/control-flow-activity-designers.md)   
 [DoWhile](../workflow-designer/dowhile-activity-designer.md)