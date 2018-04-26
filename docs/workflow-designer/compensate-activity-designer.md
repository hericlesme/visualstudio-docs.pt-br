---
title: Designer de fluxo de trabalho - compensar Designer de atividade
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.Compensate.UI
ms.assetid: 7347c947-bfff-4bad-becd-5cd23e7b24cd
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8278066a12df0d195770391d0b2f3144ba16487d
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="compensate-activity-designer"></a>Compense o designer de atividades

O **compensar** designer de atividade é usado para criar e configurar um <xref:System.Activities.Statements.Compensate> atividade.

## <a name="the-compensate-activity"></a>A atividade de compesação
 A atividade de <xref:System.Activities.Statements.Compensate> chama explicitamente <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> para uma atividade contida em <xref:System.Activities.Statements.CompensableActivity>. Se a atividade de <xref:System.Activities.Statements.Compensate> não é usada dentro de <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>, <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>, ou <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> de <xref:System.Activities.Statements.CompensableActivity>, então você deve especificar a propriedade de <xref:System.Activities.Statements.Compensate.Target%2A> .

 <xref:System.Activities.Statements.CompensationToken> especificado por <xref:System.Activities.Statements.Compensate.Target%2A> fornece um meio para confirmar ou compensar explicitamente <xref:System.Activities.Statements.CompensableActivity> uma vez que <xref:System.Activities.Statements.CompensableActivity.Body%2A> de <xref:System.Activities.Statements.CompensableActivity> terminou com êxito.

### <a name="using-the-compensate-activity-designer"></a>Usando o designer de atividade de compesação
 O **compensar** designer de atividade pode ser encontrado no **transação** categoria do **caixa de ferramentas**. Para abrir **caixa de ferramentas**, selecione o **caixa de ferramentas** guia no lado esquerdo do Designer de fluxo de trabalho (como alternativa, selecione **barra de ferramentas** do **exibição**menu ou CTRL + ALT + X.)

 O **compensar** designer de atividades pode ser arrastado o **caixa de ferramentas** e descartado para a superfície do Designer de fluxo de trabalho onde quer que as atividades são colocados, tais como dentro um <xref:System.Activities.Statements.Sequence>. Descartar o designer de atividade cria um <xref:System.Activities.Statements.Compensate> atividade com um padrão <xref:System.Activities.Activity.DisplayName%2A> de compensar. O <xref:System.Activities.Activity.DisplayName%2A> valor pode ser editado no cabeçalho do **compensar** designer de atividade ou o **DisplayName** caixa da grade de propriedade.

### <a name="the-compensate-properties"></a>As propriedades de compesação
 A tabela a seguir mostra as propriedades de <xref:System.Activities.Statements.CancellationScope> e descreve como elas são usadas no designer. O <xref:System.Activities.Activity.DisplayName%2A> propriedade pode ser editada na grade de propriedade ou na superfície do Designer de fluxo de trabalho. Editar o <xref:System.Activities.Statements.Compensate.Target%2A> propriedade na grade de propriedade.

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