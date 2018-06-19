---
title: Designer de fluxo de trabalho - Designer de atividade de CorrelationScope
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.ServiceModel.Activities.CorrelationScope.UI
ms.assetid: 75f20664-9042-464d-8e2b-148d365a2286
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b4b7eb7586eeb746bdeb3d28dfcc5fb14fe7bd6f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31976599"
---
# <a name="correlationscope-activity-designer"></a>Designer de atividade de CorrelationScope

O **CorrelationScope** designer de atividade é usado para criar e configurar um <xref:System.ServiceModel.Activities.CorrelationScope> atividade que fornece gerenciamento implícita de atividades de mensagens filho usando um <xref:System.ServiceModel.Activities.CorrelationHandle> objeto.

## <a name="the-correlationscope-activity"></a>A atividade de CorrelationScope

A propriedade de <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> especifica <xref:System.ServiceModel.Activities.CorrelationHandle> usado para gerenciar atividades filhos de mensagem. As atividades de <xref:System.ServiceModel.Activities.Send> e de <xref:System.ServiceModel.Activities.Receive> contidas em <xref:System.ServiceModel.Activities.CorrelationScope.Body%2A> são configurados para usar a propriedade de <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> de atividade de conteúdo da <xref:System.ServiceModel.Activities.CorrelationScope> para executar correlação.

### <a name="using-the-correlationscope-activity-designer"></a>Usando o designer de atividade de CorrelationScope
 O **CorrelationScope** designer de atividade pode ser encontrado no **mensagens** categoria do **caixa de ferramentas**, que é acessado clicando o **dacaixadeferramentas** guia no lado esquerdo do Designer de fluxo de trabalho (como alternativa, selecione **barra de ferramentas** do **exibição** menu ou CTRL + ALT + X.)

 O **CorrelationScope** designer de atividades pode ser arrastado do **caixa de ferramentas** e descartado para a superfície do Designer de fluxo de trabalho. Isso cria uma <xref:System.ServiceModel.Activities.CorrelationScope> atividade com um padrão **DisplayName** de CorrelationScope. O <xref:System.Activities.Activity.DisplayName%2A> pode ser editado no cabeçalho do **CorrelationScope** designer de atividade ou o **DisplayName** caixa do **propriedades** janela.

 Para especificar o <xref:System.ServiceModel.Activities.CorrelationHandle> usado por atividades de mensagens de filho, clique no botão de reticências ao lado de **CorrelatesWith** campo **propriedades** janela para exibir o **Editor de expressão**  caixa de diálogo. Esta propriedade pode também ser definida na superfície do designer de atividade.

 As atividades no escopo dentro de correlação são especificadas por descartar seus designers dentro a **corpo** caixa dentro de **CorrelationScope** designer.

### <a name="the-correlationscope-properties"></a>As propriedades de CorrelationScope
 A tabela a seguir mostra as propriedades de <xref:System.ServiceModel.Activities.CorrelationScope> e descreve como elas são usadas no designer. Essas propriedades podem ser editados no **propriedades** janela ou na superfície de design do Designer de fluxo de trabalho e geralmente em ambos.

|Nome da Propriedade|Necessária|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|O nome amigável opcional de atividade de <xref:System.ServiceModel.Activities.InitializeCorrelation> .|
|<xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A>|False|Especifica <xref:System.ServiceModel.Activities.CorrelationHandle> usado para gerenciar atividades filhos de mensagem. Se você não definir essa propriedade, <xref:System.ServiceModel.Activities.CorrelationScope><xref:System.ServiceModel.Activities.CorrelationHandle> implícito cria automaticamente.|
|<xref:System.ServiceModel.Activities.CorrelationScope.Body%2A>|False|Especifica as atividades no escopo de correlação.|

## <a name="see-also"></a>Consulte também

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Receber](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Enviar](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)