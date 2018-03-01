---
title: Designer de atividade DoWhile | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- System.Activities.Statements.DoWhile.UI
ms.assetid: 948deb35-d72f-462b-bea6-4b119c10a148
caps.latest.revision: 
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload:
- multiple
ms.openlocfilehash: 041c63d45e70305495fd18ed595a31eee6772389
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="dowhile-activity-designer"></a>Designer de atividade DoWhile
O <xref:System.Activities.Statements.DoWhile> atividade executa a atividade contida em seu <xref:System.Activities.Statements.DoWhile.Body%2A> pelo menos uma vez, até que uma determinada condição for avaliada como **false**. Se você precisar a atividade contida em um corpo de loop para ser executado zero ou mais vezes, use a atividade de <xref:System.Activities.Statements.While> em vez disso.  
  
## <a name="dowhile-properties-in-the-workflow-designer"></a>Propriedades DoWhile em Designer de Fluxo de Trabalho  
 A tabela a seguir mostra as propriedades mais úteis de atividade de <xref:System.Activities.Statements.DoWhile> e descreve como usá-los no designer.  
  
|Nome da Propriedade|Necessária|Uso|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Statements.DoWhile.Body%2A>|False|A atividade para executar enquanto a condição é **true**. Para adicionar o <xref:System.Activities.Statements.DoWhile.Body%2A> atividade, remover uma atividade da caixa de ferramentas para a **corpo** caixa o **DoWhile** designer de atividade com o texto da dica "Descartar atividade aqui".|  
|<xref:System.Activities.Statements.DoWhile.Condition%2A>|verdadeiro|A condição a ser avaliada após cada iteração do loop. Para definir o <xref:System.Activities.Statements.DoWhile.Condition%2A>, digite um [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] expressão no **condição** caixa o **DoWhile** atividade designer ou na grade de propriedades.|  
  
## <a name="see-also"></a>Consulte também  
 [While](../workflow-designer/while-activity-designer.md)   
 [Fluxo de Controle](../workflow-designer/control-flow-activity-designers.md)