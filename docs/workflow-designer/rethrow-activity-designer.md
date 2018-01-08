---
title: "Designer de atividade de relançar | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.Activities.Statements.Rethrow.UI
ms.assetid: 9cfa2eda-395f-4cf3-9154-83fadd4f7452
caps.latest.revision: "5"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 93315ed4028ba4ded598fd07373df43150b70aa3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="rethrow-activity-designer"></a>Designer de atividade de Relançar
O **relançar** designer de atividade é usado para criar e configurar um <xref:System.Activities.Statements.Rethrow> atividade.  
  
## <a name="the-rethrow-activity"></a>A atividade de Relançar  
 A atividade de <xref:System.Activities.Statements.Rethrow> lança uma exceção lançada anteriormente. Esta atividade somente pode ser usada em um manipulador de <xref:System.Activities.Statements.Catch> na atividade de <xref:System.Activities.Statements.TryCatch> .  
  
### <a name="using-the-rethrow-activity-designer"></a>Usando o designer de atividade de Relançar  
 O **relançar** designer de atividade pode ser encontrado no **tratamento de erros** categoria do **caixa de ferramentas**, que é acessado clicando o **ferramentas**guia no lado esquerdo do [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (como alternativa, selecione **barra de ferramentas** do **exibição** menu ou CTRL + ALT + X.)  
  
 O **relançar** designer de atividades pode ser arrastado o **caixa de ferramentas** e removidos no [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] superfície onde quer que as atividades geralmente são colocados, tais como dentro um <xref:System.Activities.Statements.Sequence>. Isso cria uma <xref:System.Activities.Statements.Rethrow> atividade com um padrão **DisplayName** de Throw. O <xref:System.Activities.Activity.DisplayName%2A> valor pode ser editado no cabeçalho do **relançar** designer de atividade ou o **DisplayName** caixa da grade de propriedade.  
  
### <a name="the-rethrow-properties"></a>As propriedades de Relançar  
 A tabela a seguir mostra as propriedades de <xref:System.Activities.Statements.Rethrow> e descreve como elas são usadas no designer.  
  
|Nome da Propriedade|Necessária|Uso|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Especifica o nome amigável opcional de atividade de <xref:System.Activities.Statements.Rethrow> . O padrão é Relançar.|  
  
## <a name="see-also"></a>Consulte também  
 [Coleção](../workflow-designer/collection-activity-designers.md)   
 [Throw](../workflow-designer/throw-activity-designer.md)   
 [TryCatch](../workflow-designer/trycatch-activity-designer.md)