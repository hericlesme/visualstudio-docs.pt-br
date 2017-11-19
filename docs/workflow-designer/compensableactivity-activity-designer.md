---
title: Designer de atividade de CompensableActivity | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.Activities.Statements.CompensableActivity.UI
ms.assetid: e0340d89-d39e-4a52-8557-13e27040d7b5
caps.latest.revision: "6"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: f7523327fe63bfd00fb5bc5ce4f98aeef61a2567
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="compensableactivity-activity-designer"></a>Designer de atividade de CompensableActivity
O **CompensableActivity** designer de atividade é usado para criar e configurar um <xref:System.Activities.Statements.CompensableActivity> atividade.  
  
## <a name="the-compensableactivity-activity"></a>A atividade de CompensableActivity  
 <xref:System.Activities.Statements.CompensableActivity> define uma unidade de trabalho que pode ser compensado confirmada ou após a conclusão com êxito.  
  
### <a name="using-the-compensableactivity-activity-designer"></a>Usando o designer de atividade de CompensableActivity  
 O **CompensableActivity** designer de atividade pode ser encontrado no **transação** categoria do **caixa de ferramentas**, que é acessado clicando o **caixa de ferramentas**  guia no lado esquerdo do [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (como alternativa, selecione **barra de ferramentas** do **exibição** menu ou CTRL + ALT + X.)  
  
 O **CompensableActivity** designer de atividades pode ser arrastado o **caixa de ferramentas** e removidos no [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] superfície onde quer que as atividades geralmente são colocados, tais como dentro um <xref:System.Activities.Statements.Sequence>. Isso cria uma atividade de <xref:System.Activities.Statements.CompensableActivity> com <xref:System.Activities.Activity.DisplayName%2A> padrão de CompensableActivity. O <xref:System.Activities.Activity.DisplayName%2A> valor pode ser editado no cabeçalho do **CompensableActivity** designer de atividade ou o **DisplayName** caixa da grade de propriedade.  
  
### <a name="the-compensableactivity-properties"></a>As propriedades de CompensableActivity  
 A tabela a seguir mostra as propriedades de <xref:System.Activities.Statements.CompensableActivity> e descreve como elas são usadas no designer. A propriedade de <xref:System.Activities.Activity.DisplayName%2A> e de <xref:System.Activities.Activity%601.Result%2A> pode ser editada na grade de propriedade mas outras propriedades devem ser editadas na superfície de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] .  
  
|Nome da Propriedade|Necessária|Uso|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|O nome amigável opcional de atividade de <xref:System.Activities.Statements.CompensableActivity> . O padrão é CompensableActivity.|  
|<xref:System.Activities.Activity%601.Result%2A>|False|Especifica o valor de retorno de <xref:System.Activities.Statements.CompensableActivity>. Esta propriedade deve ser editada na grade de propriedade.|  
|<xref:System.Activities.Statements.CompensableActivity.Body%2A>|verdadeiro|Especifica a atividade para que a compensação, cancelamento, e a lógica de confirmação são fornecidos. Para adicionar o <xref:System.Activities.Statements.CompensableActivity.Body%2A> atividade, soltar uma atividade do **caixa de ferramentas** no **corpo** caixa o **CompensableActivity** designer de atividade com o texto de dica "Drop atividade aqui".|  
|<xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>|False|Especifica a atividade que é executado no caso de cancelamento. Para adicionar a atividade, descartar seu designer do **caixa de ferramentas** para o **CancellationHandler** caixa o **CompensableActivity** designer de atividade com o texto de dica "Drop Atividade aqui".|  
|<xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>|False|Especifica a atividade a ser executada para compensar a atividade de <xref:System.Activities.Statements.CompensableActivity.Body%2A> . Esse manipulador pode ser chamado explicitamente usando a atividade de <xref:System.Activities.Statements.Compensate> .<br /><br /> Para adicionar a atividade, descartar seu designer de atividade do **caixa de ferramentas** no **CompensationHandler** caixa o **CompensableActivity** designer de atividade com o texto da dica " Descartar atividade aqui".|  
|<xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>|False|Especifica a atividade a ser executada para confirmar a atividade de <xref:System.Activities.Statements.CompensableActivity.Body%2A> . Esse manipulador pode ser chamado explicitamente usando a atividade de <xref:System.Activities.Statements.Confirm> .<br /><br /> Para adicionar a atividade, descartar seu designer de atividade do **caixa de ferramentas** no **ConfirmationHandler** caixa o **CompensableActivity** designer de atividade com o texto da dica " Descartar atividade aqui".|  
  
## <a name="see-also"></a>Consulte também  
 [Transação](../workflow-designer/transaction-activity-designers.md)   
 [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md)   
 [Compensar](../workflow-designer/compensate-activity-designer.md)   
 [Confirmar](../workflow-designer/confirm-activity-designer.md)   
 [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)