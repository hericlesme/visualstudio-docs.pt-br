---
title: "Lançar o Designer de atividade | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Throw.UI
ms.assetid: 5e97c947-be39-4a1f-af04-000e2e09528a
caps.latest.revision: 
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload:
- multiple
ms.openlocfilehash: f9af95a8aeb509554cb613edb848c2987543f1e2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="throw-activity-designer"></a>Lance o designer de atividades
O **gerar** designer de atividade é usado para criar e configurar um <xref:System.Activities.Statements.Throw> atividade.  
  
## <a name="the-throw-activity"></a>A atividade throw  
 A atividade de <xref:System.Activities.Statements.Throw> gerencie uma exceção.  
  
### <a name="using-the-throw-activity-designer"></a>Usando o designer de atividade throw  
 O **gerar** designer de atividade pode ser encontrado no **tratamento de erros** categoria do **caixa de ferramentas**, que é acessado clicando o **ferramentas**guia no lado esquerdo do [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (como alternativa, selecione **barra de ferramentas** do **exibição** menu ou CTRL + ALT + X.)  
  
 O **gerar** designer de atividades pode ser arrastado o **caixa de ferramentas** e removidos no [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] superfície onde quer que as atividades geralmente são colocados, tais como dentro um <xref:System.Activities.Statements.Sequence>. Isso cria uma <xref:System.Activities.Statements.Throw> atividade com um padrão **DisplayName** de Throw. O <xref:System.Activities.Activity.DisplayName%2A> valor pode ser editado no cabeçalho do **lançar** designer de atividade ou o **DisplayName** caixa da grade de propriedade. A propriedade de <xref:System.Activities.Statements.Throw.Exception%2A> deve ser editada na grade de propriedade.  
  
### <a name="the-throw-properties"></a>As propriedades throw  
 A tabela a seguir mostra as propriedades de <xref:System.Activities.Statements.Throw> e descreve como elas são usadas no designer.  
  
|Nome da Propriedade|Necessária|Uso|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Especifica o nome amigável opcional de atividade de <xref:System.Activities.Statements.Throw> . O padrão é throw.|  
|<xref:System.Activities.Statements.Throw.Exception%2A>|verdadeiro|A exceção para lançar. Esta exceção deve derivar de <xref:System.Exception>. Para especificar a exceção, digite uma expressão do Visual Basic na grade de propriedade.|  
  
## <a name="see-also"></a>Consulte também  
 [Coleção](../workflow-designer/collection-activity-designers.md)   
 [Relançar](../workflow-designer/rethrow-activity-designer.md)   
 [Lançar o Designer de atividade](../workflow-designer/throw-activity-designer.md)   
 [TryCatch](../workflow-designer/trycatch-activity-designer.md)