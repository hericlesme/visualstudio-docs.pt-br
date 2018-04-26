---
title: Designer de fluxo de trabalho - Designer de atividade de TransactedReceiveScope
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.ServiceModel.Activities.TransactedReceiveScope.UI
ms.assetid: 7ca93aad-4e83-4d81-90f4-998ee114d9b6
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c7f5c4cd48cc98d58da278ac53c1a829d15c43cd
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="transactedreceivescope-activity-designer"></a>Designer de atividade de TransactedReceiveScope

O **TransactedReceiveScope** designer é usado para criar e configurar um <xref:System.ServiceModel.Activities.TransactedReceiveScope> atividade.

## <a name="the-transactedreceivescope-activity"></a>A atividade de TransactedReceiveScope

A atividade de <xref:System.ServiceModel.Activities.TransactedReceiveScope> permite que você fluxo uma transação nas transações de servidor criadas por um fluxo de trabalho ou por um distribuidor.

### <a name="using-the-transactedreceivescope-activity-designer"></a>Usando o designer de atividade de TransactedReceiveScope
 O **TransactedReceiveScope** designer de atividade pode ser encontrado no **mensagens** categoria do **caixa de ferramentas**, que é acessado clicando o **caixa de ferramentas**  guia no Designer de fluxo de trabalho (como alternativa, selecione **barra de ferramentas** do **exibição** menu ou CTRL + ALT + X.)

 O **TransactedReceiveScope** designer de atividades pode ser arrastado do **caixa de ferramentas** e descartado para a superfície do Designer de fluxo de trabalho onde quer que as atividades geralmente são colocadas. Isso cria uma <xref:System.ServiceModel.Activities.TransactedReceiveScope> atividade com um padrão **DisplayName** de TransactedReceiveScope. O <xref:System.Activities.Activity.DisplayName%2A> pode ser editado no cabeçalho do **TransactedReceiveScope** designer de atividade ou o **DisplayName** caixa da grade de propriedade.

 O **TransactedReceiveScope** designer contém **solicitação** e **corpo** caixas. Esses são usados para configurar a propriedade de <xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A> , que especifica uma atividade de <xref:System.ServiceModel.Activities.Receive> e uma propriedade de <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> , que especifica algum outro <xref:System.Activities.Activity>. <xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A> cria uma transação. A transação é feita em ambientes para o escopo de <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> de modo que quaisquer atividades dentro desse escopo seja executado dentro desta transação.

### <a name="the-transactedreceivescope-properties"></a>As propriedades de TransactedReceiveScope
 A tabela a seguir mostra as propriedades de <xref:System.ServiceModel.Activities.TransactedReceiveScope> e descreve como elas são usadas no designer. Essas <xref:System.Activities.Activity.DisplayName%2A> propriedade pode ser editada na grade de propriedade ou na superfície do Designer de fluxo de trabalho, mas os outros devem ser editados na superfície de design.

|Nome da Propriedade|Necessária|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|O nome amigável opcional de atividade de <xref:System.ServiceModel.Activities.TransactedReceiveScope> . O padrão é TransactedReceiveScope.<br /><br /> Embora o nome de <xref:System.Activities.Activity.DisplayName%2A> não é necessário restrita, é uma prática recomendada usar um nome para exibição.|
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A>|verdadeiro|Descarta uma <xref:System.ServiceModel.Activities.Receive> atividade o **solicitação** bloco na superfície do designer de atividade.|
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A>|False|Descarta uma <xref:System.Activities.Activity> para o **corpo** bloco na superfície do designer de atividade.|

## <a name="see-also"></a>Consulte também

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Receber](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Enviar](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)