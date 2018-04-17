---
title: Designer de atividade de compensar | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Compensate.UI
ms.assetid: 7347c947-bfff-4bad-becd-5cd23e7b24cd
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ef289304338ea64a72c073711a287612d39bd1a8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="compensate-activity-designer"></a>Compense o designer de atividades
O **compensar** designer de atividade é usado para criar e configurar um <xref:System.Activities.Statements.Compensate> atividade.

## <a name="the-compensate-activity"></a>A atividade de compesação
 A atividade de <xref:System.Activities.Statements.Compensate> chama explicitamente <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> para uma atividade contida em <xref:System.Activities.Statements.CompensableActivity>. Se a atividade de <xref:System.Activities.Statements.Compensate> não é usada dentro de <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>, <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>, ou <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> de <xref:System.Activities.Statements.CompensableActivity>, então você deve especificar a propriedade de <xref:System.Activities.Statements.Compensate.Target%2A> .

 <xref:System.Activities.Statements.CompensationToken> especificado por <xref:System.Activities.Statements.Compensate.Target%2A> fornece um meio para confirmar ou compensar explicitamente <xref:System.Activities.Statements.CompensableActivity> uma vez que <xref:System.Activities.Statements.CompensableActivity.Body%2A> de <xref:System.Activities.Statements.CompensableActivity> terminou com êxito.

### <a name="using-the-compensate-activity-designer"></a>Usando o designer de atividade de compesação
 O **compensar** designer de atividade pode ser encontrado no **transação** categoria do **caixa de ferramentas**, que é acessado clicando o **dacaixadeferramentas** guia no lado esquerdo do [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (como alternativa, selecione **barra de ferramentas** do **exibição** menu ou CTRL + ALT + X.)

 O **compensar** designer de atividades pode ser arrastado o **caixa de ferramentas** e removidos no [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] superfície onde quer que as atividades geralmente são colocados, tais como dentro um <xref:System.Activities.Statements.Sequence>. Isso cria uma atividade de <xref:System.Activities.Statements.Compensate> com <xref:System.Activities.Activity.DisplayName%2A> padrão Compensate. O <xref:System.Activities.Activity.DisplayName%2A> valor pode ser editado no cabeçalho do **compensar** designer de atividade ou o **DisplayName** caixa da grade de propriedade.

### <a name="the-compensate-properties"></a>As propriedades de compesação
 A tabela a seguir mostra as propriedades de <xref:System.Activities.Statements.CancellationScope> e descreve como elas são usadas no designer. A propriedade de <xref:System.Activities.Activity.DisplayName%2A> pode ser editada na grade de propriedade ou na superfície de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] , mas a propriedade de <xref:System.Activities.Statements.Compensate.Target%2A> deve ser editada na grade de propriedade.

|Nome da Propriedade|Necessária|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Especifica o nome amigável opcional de atividade de <xref:System.Activities.Statements.Compensate> . O padrão é compensa.|
|<xref:System.Activities.Statements.Compensate.Target%2A>|verdadeiro|Especifica <xref:System.Activities.InArgument%601> que contém <xref:System.Activities.Statements.CompensationToken> para esta atividade de <xref:System.Activities.Statements.Compensate> .|

## <a name="see-also"></a>Consulte também

- [Transação](../workflow-designer/transaction-activity-designers.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Designer de atividade Compensate](../workflow-designer/compensate-activity-designer.md)
- [Confirmar](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)