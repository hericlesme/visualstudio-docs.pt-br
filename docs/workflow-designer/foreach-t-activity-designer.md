---
title: ForEach&lt;T&gt; Designer de atividade | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ForEach`1.UI
ms.assetid: 67097b3a-fcf5-4a72-beb1-2c7784151a86
caps.latest.revision: 
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload:
- multiple
ms.openlocfilehash: 6016947237274d65d3b59954d783c2a31f3d2b91
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="foreachlttgt-activity-designer"></a>ForEach&lt;T&gt; Designer de atividade
A atividade de <xref:System.Activities.Statements.ForEach%601> executa a atividade contida em seu <xref:System.Activities.Statements.ForEach%601.Body%2A> para cada item em uma coleção de <xref:System.Activities.Statements.ForEach%601.Values%2A> especificada.  
  
## <a name="foreacht-properties-in-the-workflow-designer"></a>ForEach < T\> propriedades no Designer de fluxo de trabalho  
 A tabela a seguir mostra as propriedades mais úteis de atividade de <xref:System.Activities.Statements.ForEach%601> e descreve como usá-los no designer.  
  
|Nome da Propriedade|Necessária|Uso|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|O nome amigável de atividade de <xref:System.Activities.Statements.ForEach%601> . O padrão é ForEach < Int32\>. Embora o valor de <xref:System.Activities.Activity.DisplayName%2A> não é necessário restrita, é uma prática recomendada usar um.|  
|<xref:System.Activities.Statements.ForEach%601.Values%2A>|verdadeiro|A coleção de itens para iterar. Para definir o <xref:System.Activities.Statements.ForEach%601.Values%2A>, digite um [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] expressão no **valores** caixa o **ForEach < T\>**  atividade designer ou na grade de propriedades.|  
|*TypeArgument*|verdadeiro|O tipo dos itens a <xref:System.Activities.Statements.ForEach%601.Values%2A> coleção especificada pelo parâmetro genérico *T*. Por padrão, *TypeArgument* é definido como **Int32**. Para alterar o tipo, altere o valor de *TypeArgument* caixa de combinação na grade de propriedades.|  
  
 Por padrão, o iterador de loop é denominado **item**. Você pode alterar o nome da variável de iterador no designer de atividade de <xref:System.Activities.Statements.ForEach%601> . O iterador do loop pode ser usado em expressões nos filhos de atividade de <xref:System.Activities.Statements.ForEach%601> .  
  
## <a name="see-also"></a>Consulte também  
 [ParallelForEach\<T >](../workflow-designer/parallelforeach-t-activity-designer.md)   
 [Fluxo de Controle](../workflow-designer/control-flow-activity-designers.md)