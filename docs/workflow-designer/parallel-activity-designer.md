---
title: Paralelo Designer de atividade | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.Activities.Statements.Parallel.UI
ms.assetid: 0306dc3b-075a-4091-ac3a-96486fbabed5
caps.latest.revision: "10"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 8be40a9cae29291951a320422755f0ff5d1f7365
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="parallel-activity-designer"></a>Designer paralelo de atividades
A atividade de <xref:System.Activities.Statements.Parallel> executa uma coleção de filhos atividades simultaneamente.  
  
## <a name="the-parallel-activity"></a>A atividade paralela  
 A atividade de <xref:System.Activities.Statements.Parallel> armazena as atividades filho em uma coleção de <xref:System.Activities.Statements.Parallel.Branches%2A> . Use a atividade de <xref:System.Activities.Statements.Parallel> em vez de atividade de <xref:System.Activities.Statements.Sequence> se algumas das atividades filho podem ir ociosa.  
  
 A atividade de <xref:System.Activities.Statements.Parallel> tem uma propriedade de <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> que contém uma expressão especificada usuário de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] . A atividade de <xref:System.Activities.Statements.Parallel> avalia essa propriedade após cada ramificação completa. Se ele for avaliada como **True**, em seguida, o <xref:System.Activities.Statements.Parallel> conclusão sem executar as outras ramificações da atividade. Se o <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> não é avaliada como **True**, em seguida, o <xref:System.Activities.Statements.Parallel> atividade é concluída quando todas as suas atividades filho forem concluídas.  
  
### <a name="using-the-parallel-activity-designer"></a>Usando o designer paralelo de atividades  
 O **paralela** designer de atividade pode ser encontrado no **fluxo de controle** categoria do **caixa de ferramentas**, que é acessado clicando o **ferramentas**guia no lado esquerdo do [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (como alternativa, selecione **barra de ferramentas** do **exibição** menu ou CTRL + ALT + X.)  
  
 O **paralela** designer de atividades pode ser arrastado o **caixa de ferramentas** e removidos no [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] superfície onde quer que os designers de atividade normalmente são colocados, por exemplo, dentro de um **Sequência** designer de atividade. Após removê-la no [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], ele cria um <xref:System.Activities.Statements.Parallel> atividade, que, por padrão, contém um <xref:System.Activities.Activity.DisplayName%2A> de **paralela**  
  
 Para adicionar uma atividade para o <xref:System.Activities.Statements.Parallel.Branches%2A> coleção de atividade paralela, arraste alguns outros designer de atividade do **caixa de ferramentas** e solte-o triângulo dentro a **paralela** designer de atividade. Os triângulos flanqueiam as atividades contidas em ramificações. As atividades adicionais podem ser adicionadas repetindo este procedimento. As atividades podem ser reordenadas arrastando e soltando dentro de **paralela** designer de atividade.  
  
### <a name="parallel-activity-properties-in-the-workflow-designer"></a>Propriedades paralelas de atividade em Designer de Fluxo de Trabalho  
 A tabela a seguir mostra as propriedades paralelas de atividade e descreve como elas são usadas no designer.  
  
|Nome da Propriedade|Necessária|Uso|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Especifica o nome amigável para exibição do designer de atividade no cabeçalho. O valor padrão é **paralela**. O valor pode ser editado no opcionalmente o **propriedades** grade ou diretamente no cabeçalho de designer de atividade.|  
|<xref:System.Activities.Statements.Parallel.Branches%2A>|verdadeiro|Contém a coleção de atividades filhos sejam executadas.|  
|<xref:System.Activities.Statements.Parallel.CompletionCondition%2A>|False|Avaliado após uma ramificação completa. Se ele for avaliada como **True**, em seguida, agendados pendentes ramificações são canceladas. Se essa propriedade não está definida ou é avaliada como **False**, a atividade é concluída quando todas as suas atividades filho forem concluídas. O valor padrão é **nulo**.|  
  
## <a name="see-also"></a>Consulte também  
 [Sequência](../workflow-designer/sequence-activity-designer.md)   
 [ParallelForEach\<T >](../workflow-designer/parallelforeach-t-activity-designer.md)   
 [Fluxo de Controle](../workflow-designer/control-flow-activity-designers.md)