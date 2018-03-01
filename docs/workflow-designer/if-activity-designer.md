---
title: Se o Designer de atividade | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- System.Activities.Statements.If.UI
ms.assetid: 930a8fa2-db98-43e9-ad6d-a85cc7a6519a
caps.latest.revision: 
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload:
- multiple
ms.openlocfilehash: 950bff10372c9c40e047f891049e7cc387c8efc8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="if-activity-designer"></a>Se designer de atividades
A atividade de <xref:System.Activities.Statements.If> avalia uma condição e executa uma atividade dependendo dos resultados da avaliação. Esta atividade é mais útil ao usar um estilo modelando procedural de programação. Uma atividade de <xref:System.Activities.Statements.If> pode ser aninhadas dentro de uma atividade de <xref:System.Activities.Statements.Sequence> ou uma atividade de <xref:System.Activities.Statements.Parallel> , por exemplo. Se você estiver usando uma atividade de <xref:System.Activities.Statements.Flowchart> , considere usar uma atividade de <xref:System.Activities.Statements.FlowDecision> em vez disso.  
  
## <a name="if-properties-in-the-workflow-designer"></a>Se as propriedades em Designer de Fluxo de Trabalho  
 A tabela a seguir mostra as propriedades mais úteis de atividade de <xref:System.Activities.Statements.If> e descreve como usá-los no designer.  
  
|Nome da Propriedade|Necessária|Uso|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Statements.If.Condition%2A>|verdadeiro|A condição que determina que atividade filho para executar. Para definir o <xref:System.Activities.Statements.If.Condition%2A>, digite um [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] expressão no **condição** caixa o **se** atividade designer ou na grade de propriedades.|  
|<xref:System.Activities.Statements.If.Else%2A>|False|A atividade seja executada se o <xref:System.Activities.Statements.If.Condition%2A> é **false**. Para adicionar uma atividade que é executada pelo <xref:System.Activities.Statements.If.Else%2A> branch, remover uma atividade do **caixa de ferramentas** no **Else** caixa o **se** designer de atividade com o texto de dica " Descartar atividade aqui".|  
|<xref:System.Activities.Statements.If.Then%2A>|False|A atividade seja executada se o <xref:System.Activities.Statements.If.Condition%2A> é **true**. Para adicionar uma atividade que é executada pelo <xref:System.Activities.Statements.If.Then%2A> branch, remover uma atividade do **caixa de ferramentas** no **, em seguida,** caixa o **se** designer de atividade com o texto de dica " Descartar atividade aqui".|  
  
## <a name="see-also"></a>Consulte também  
 [Sequência](../workflow-designer/sequence-activity-designer.md)   
 [Paralelo](../workflow-designer/parallel-activity-designer.md)   
 [Fluxo de Controle](../workflow-designer/control-flow-activity-designers.md)