---
title: Designer de atividade DoWhile | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Statements.DoWhile.UI
ms.assetid: 948deb35-d72f-462b-bea6-4b119c10a148
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 911e6d6d94090ddcdd43fcd9511624e209f7c03c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47464642"
---
# <a name="dowhile-activity-designer"></a>Designer de atividade DoWhile
O <xref:System.Activities.Statements.DoWhile> atividade executa a atividade contida em seu <xref:System.Activities.Statements.DoWhile.Body%2A> pelo menos uma vez, até que uma condição especificada for avaliada como **falso**. Se você precisar a atividade contida em um corpo de loop para ser executado zero ou mais vezes, use a atividade de <xref:System.Activities.Statements.While> em vez disso.  
  
## <a name="dowhile-properties-in-the-workflow-designer"></a>Propriedades DoWhile em Designer de Fluxo de Trabalho  
 A tabela a seguir mostra as propriedades mais úteis de atividade de <xref:System.Activities.Statements.DoWhile> e descreve como usá-los no designer.  
  
|Nome da Propriedade|Necessária|Uso|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Statements.DoWhile.Body%2A>|False|A atividade a executar quando a condição for **verdadeira**. Para adicionar o <xref:System.Activities.Statements.DoWhile.Body%2A> atividade, soltar uma atividade na caixa de ferramentas para o **corpo** caixa no **DoWhile** designer de atividade com o texto de dica "Descartar atividade aqui".|  
|<xref:System.Activities.Statements.DoWhile.Condition%2A>|verdadeiro|A condição a ser avaliada após cada iteração do loop. Para definir a <xref:System.Activities.Statements.DoWhile.Condition%2A>, digite um [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] expressão na **condição** caixa no **DoWhile** atividade designer ou na grade de propriedade.|  
  
## <a name="see-also"></a>Consulte também  
 [ao mesmo tempo](../workflow-designer/while-activity-designer.md)   
 [Fluxo de Controle](../workflow-designer/control-flow-activity-designers.md)