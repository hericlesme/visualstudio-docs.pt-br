---
title: Designer de atividade de TransactionScope | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TransactionScope.UI
ms.assetid: 8d7ebfc6-7478-4888-b3b0-b14f296096af
caps.latest.revision: 
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload:
- multiple
ms.openlocfilehash: 9c9b9ab609825a68edc4e2862d64bdd7cb830202
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="transactionscope-activity-designer"></a>Designer de atividade de TransactionScope
O **TransactionScope** designer de atividade é usado para criar e configurar um <xref:System.Activities.Statements.TransactionScope> atividade.  
  
## <a name="the-transactionscope-activity"></a>A atividade de TransactionScope  
 A atividade de <xref:System.Activities.Statements.TransactionScope> executa a atividade contida em uma única transação. As confirmações de transação quando a atividade de <xref:System.Activities.Statements.TransactionScope.Body%2A> e todos outros participantes na transação tiver terminado com êxito.  
  
### <a name="using-the-transactionscope-activity-designer"></a>Usando o designer de atividade de TransactionScope  
 O **TransactionScope** designer de atividade pode ser encontrado no **transação** categoria do **caixa de ferramentas**, que é acessado clicando o **caixa de ferramentas**  guia de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (como alternativa, selecione **barra de ferramentas** do **exibição** menu ou CTRL + ALT + X.)  
  
 O **TransactionScope** designer de atividades pode ser arrastado o **caixa de ferramentas** e removidos no [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] superfície onde quer que as atividades geralmente são colocados, tais como dentro um <xref:System.Activities.Statements.Sequence>. Isso cria uma atividade de <xref:System.Activities.Statements.TransactionScope> com <xref:System.Activities.Activity.DisplayName%2A> padrão de TransactionScope. O <xref:System.Activities.Activity.DisplayName%2A> valor pode ser editado no cabeçalho do **TransactionScope** designer de atividade ou o **DisplayName** caixa da grade de propriedade.  
  
### <a name="the-transactionscope-properties"></a>As propriedades de TransactionScope  
 A tabela a seguir mostra as propriedades de <xref:System.Activities.Statements.TransactionScope> e descreve como elas são usadas no designer. As propriedades de <xref:System.Activities.Activity.DisplayName%2A> e de <xref:System.Activities.Statements.TransactionScope.Body%2A> podem ser editadas na superfície de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] . Mas as outras propriedades devem ser editadas na grade de propriedade.  
  
|Nome da Propriedade|Necessária|Uso|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|O nome amigável opcional de atividade de <xref:System.Activities.Statements.TransactionScope> . O padrão é TransactionScope. Embora o valor de <xref:System.Activities.Activity.DisplayName%2A> não é necessário restrita, é uma prática recomendada usar um.|  
|<xref:System.Activities.Statements.TransactionScope.Body%2A>|verdadeiro|Especifica a atividade para executar em uma única transação. Para adicionar o <xref:System.Activities.Statements.TransactionScope.Body%2A> atividade, soltar uma atividade do **caixa de ferramentas** no **corpo** caixa o **TransactionScope** designer de atividade com o texto de dica "descartar atividade aqui".|  
|<xref:System.Activities.Statements.TransactionScope.IsolationLevel%2A>|verdadeiro|Especifica <xref:System.Transactions.IsolationLevel> para este <xref:System.Activities.Statements.TransactionScope>.|  
|<xref:System.Activities.Statements.TransactionScope.Timeout%2A>|False|Especifica o intervalo de tempo (formatados como o 00:00: 00, que indica horas: minutos: segundos) que a transação precisará concluir. O valor padrão é 1 (00:01 minuto: 00).|  
|[System.Activities.Statements.TransactionScope.AbortInstanceOnTransactionFailure](https://msdn.microsoft.com/library/system.activities.statements.transactionscope.abortinstanceontransactionfailure.aspx)|verdadeiro|Especifica o valor que indica se o fluxo de trabalho deve ser anuladas se a transação nulos.|  
  
## <a name="see-also"></a>Consulte também  
 [Transação](../workflow-designer/transaction-activity-designers.md)   
 [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md)   
 [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)   
 [Compensar](../workflow-designer/compensate-activity-designer.md)   
 [Confirmar](../workflow-designer/confirm-activity-designer.md)