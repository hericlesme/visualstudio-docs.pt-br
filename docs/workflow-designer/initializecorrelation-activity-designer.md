---
title: Designer de fluxo de trabalho - Designer de atividade de InitializeCorrelation
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.ServiceModel.Activities.InitializeCorrelation.UI
ms.assetid: 4c54f34c-ee84-42a6-abb0-ec260c1ccb76
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 24d319af36b5d07661213edb3cff48d376bd3736
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31977530"
---
# <a name="initializecorrelation-activity-designer"></a>Designer de atividade de InitializeCorrelation

O **InitializeCorrelation** designer de atividade é usado para criar e configurar um <xref:System.ServiceModel.Activities.InitializeCorrelation> atividade que é usada para estabelecer uma correlação entre as mensagens antes de enviar ou recebê-los.

## <a name="the-initializecorrelation-activity"></a>A atividade de InitializeCorrelation

Uma atividade de <xref:System.ServiceModel.Activities.InitializeCorrelation> é usada para inicializar correlações sem enviar e receber uma mensagem. Correlação é inicializada normalmente ao enviar ou para receber uma mensagem. Se correlação deve ser estabelecida antes que uma mensagem ser enviada ou recebida, use <xref:System.ServiceModel.Activities.InitializeCorrelation> para inicializar correlação.

### <a name="using-the-initializecorrelation-activity-designer"></a>Usando o designer de atividade de InitializeCorrelation
 O **InitializeCorrelation** designer de atividade pode ser encontrado no **mensagens** categoria do **caixa de ferramentas**, que é acessado clicando o **caixa de ferramentas**  guia no Designer de fluxo de trabalho (como alternativa, selecione **barra de ferramentas** do **exibição** menu ou CTRL + ALT + X.)

 O **InitializeCorrelation** designer de atividades pode ser arrastado do **caixa de ferramentas** e descartado para a superfície do Designer de fluxo de trabalho. Isso cria uma <xref:System.ServiceModel.Activities.InitializeCorrelation> atividade com um padrão <xref:System.Activities.Activity.DisplayName%2A> de InitializeCorrelation.The <xref:System.Activities.Activity.DisplayName%2A> pode ser editado no cabeçalho do **InitializeCorrelation** designer de atividade ou o  **DisplayName** caixa do **propriedades** janela.

 O <xref:System.ServiceModel.Activities.CorrelationHandle> pode ser especifica no **correlação** campo **propriedades** janela o **InitializeCorrelation** superfície do designer de atividade.

 Clicando no botão de elipse além de **CorrelationData** campo **propriedades** janela ou o texto de dica de "Exibição …" em **InitializeCorrelation** designer de atividade superfície exibe o **inicializar correlação** caixa de diálogo na qual você pode especificar o identificador de correlação e os pares de chave-valor usados para inicializá-lo. Para obter mais informações sobre como usar essa caixa de diálogo, consulte o [caixa de diálogo do Editor de coleção de tipo](../workflow-designer/type-collection-editor-dialog-box.md) tópico.

### <a name="the-initializecorrelation-properties"></a>As propriedades de InitializeCorrelation
 A tabela a seguir mostra as propriedades de <xref:System.ServiceModel.Activities.InitializeCorrelation> e descreve como elas são usadas no designer. Essas propriedades podem ser editadas na **propriedades** janela ou na superfície do Designer de fluxo de trabalho.

|Nome da Propriedade|Necessária|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|O nome amigável de atividade de <xref:System.ServiceModel.Activities.InitializeCorrelation> . O valor padrão é InitializeCorrelation.<br /><br /> Embora o uso de um valor não padrão para <xref:System.Activities.Activity.DisplayName%2A> amigável não é necessário restrita, é uma prática recomendada usar um valor.|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.Correlation%2A>|False|<xref:System.ServiceModel.Activities.CorrelationHandle> usado para associar atividades de fluxo de trabalho em correlação.|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>|False|Um dicionário de dados de correlação que se relacionam mensagens ao fluxo de trabalho instância.<br /><br /> Use o **inicializar correlação** caixa de diálogo para configurar o <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>. Para obter mais informações sobre o uso essa caixa de diálogo, consulte o [caixa de diálogo do Editor de coleção de tipo](../workflow-designer/type-collection-editor-dialog-box.md) tópico.|

## <a name="see-also"></a>Consulte também

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [Receber](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Enviar](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)