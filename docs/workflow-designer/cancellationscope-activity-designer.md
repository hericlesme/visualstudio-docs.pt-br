---
title: Designer de atividade de CancellationScope | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.Activities.Statements.CancellationScope.UI
ms.assetid: 2c85d663-b219-4142-9866-7693ffd46379
caps.latest.revision: "8"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4b2ad28e6b89273b5fdb55e4cfa35d1df292221a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="cancellationscope-activity-designer"></a>Designer de atividade de CancellationScope
O **CancellationScope** designer de atividade é usado para criar e configurar um <xref:System.Activities.Statements.CancellationScope> atividade.  
  
## <a name="the-cancellationscope-activity"></a>A atividade de CancellationScope  
 A atividade de <xref:System.Activities.Statements.CancellationScope> permite que você especifique uma atividade para a lógica de execução e cancelar para a atividade.  
  
### <a name="using-the-cancellationscope-activity-designer"></a>Usando o designer de atividade de CancellationScope  
 O **CancellationScope** designer de atividade pode ser encontrado no **transação** categoria do **caixa de ferramentas**, que é acessado clicando o **caixa de ferramentas**  guia o [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (como alternativa, selecione **barra de ferramentas** do **exibição** menu ou CTRL + ALT + X.)  
  
 O **CancellationScope** designer de atividades pode ser arrastado o **caixa de ferramentas** e removidos no [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] superfície onde quer que as atividades geralmente são colocados, tais como dentro um <xref:System.Activities.Statements.Sequence>. Isso cria uma atividade de <xref:System.Activities.Statements.CancellationScope> com <xref:System.Activities.Activity.DisplayName%2A> padrão de CancellationScope. O <xref:System.Activities.Activity.DisplayName%2A> valor pode ser editado no cabeçalho do **CancellationScope** designer de atividade ou o **DisplayName** caixa da grade de propriedade.  
  
### <a name="the-cancellationscope-properties"></a>As propriedades de CancellationScope  
 A tabela a seguir mostra as propriedades de <xref:System.Activities.Statements.CancellationScope> e descreve como elas são usadas no designer. A propriedade de <xref:System.Activities.Activity.DisplayName%2A> pode ser editada na grade de propriedade mas outras propriedades devem ser editadas na superfície de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] .  
  
|Nome da Propriedade|Necessária|Uso|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|O nome amigável opcional de atividade de <xref:System.Activities.Statements.CancellationScope> . O padrão é CancellationScope. Embora o valor de <xref:System.Activities.Activity.DisplayName%2A> não é necessário restrita, é uma prática recomendada usar um.|  
|<xref:System.Activities.Statements.CancellationScope.Body%2A>|verdadeiro|Especifica a atividade para que a lógica cancelar é fornecida. Para adicionar o <xref:System.Activities.Statements.CancellationScope.Body%2A> atividade, soltar uma atividade do **caixa de ferramentas** no **corpo** caixa o **CancellationScope** designer de atividade com o texto de dica "Drop Atividade aqui".|  
|<xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>|verdadeiro|Especifica a atividade que é executado no caso de cancelamento. Para adicionar o <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> atividade, soltar uma atividade do **caixa de ferramentas** no **CancellationHandler** caixa o **CancellationScope** designer de atividade com dica texto "Descartar atividade aqui".|  
  
## <a name="see-also"></a>Consulte também  
 [Transação](../workflow-designer/transaction-activity-designers.md)   
 [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)   
 [Compensar](../workflow-designer/compensate-activity-designer.md)   
 [Confirmar](../workflow-designer/confirm-activity-designer.md)   
 [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)