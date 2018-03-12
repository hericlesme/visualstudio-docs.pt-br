---
title: Designer de atividade de recebimento | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.Receive.UI
ms.assetid: f58d3c70-944d-4bb4-90a7-e68c103caddc
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: d8058b13dd488ddca2237056048673529c379256
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2018
---
# <a name="receive-activity-designer"></a>Recebe o designer de atividades
O **Receive** designer de atividade é usado para criar e configurar um <xref:System.ServiceModel.Activities.Receive> atividade. Uma atividade de <xref:System.ServiceModel.Activities.Receive> é uma atividade que receberá uma mensagem que pode ser um tipo interno como <xref:System.ServiceModel.Channels.Message>, <xref:System.IO.Stream> ou <xref:System.Xml.Linq.XElement>, ou um contrato definido de dados, o contrato de mensagem, ou a classe XML que pode ser serializada.

## <a name="the-receive-activity"></a>A atividade de receptor
 A atividade de <xref:System.ServiceModel.Activities.Receive> pode receber um item único ou vários itens dependendo do tipo de recebem o conteúdo usado. Uma atividade de <xref:System.ServiceModel.Activities.SendReply> pode ser associada a uma atividade de <xref:System.ServiceModel.Activities.Receive> que receberá uma mensagem como parte de um padrão de troca de solicitação/resposta de mensagem no serviço.

### <a name="using-the-receive-activity-designer"></a>Usando o designer de atividade de receptor
 O **Receive** designer de atividade pode ser encontrado no **mensagens** categoria do **caixa de ferramentas**, que é acessado clicando o **ferramentas**guia o [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (como alternativa, selecione **barra de ferramentas** do **exibição** menu ou CTRL + ALT + X.)

 O **Receive** designer de atividades pode ser arrastado o **caixa de ferramentas** e removidos no [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] superfície onde quer que as atividades geralmente são colocadas. Isso cria uma atividade de <xref:System.ServiceModel.Activities.Receive> com <xref:System.Activities.Activity.DisplayName%2A> padrão Receive. O <xref:System.Activities.Activity.DisplayName%2A> pode ser editado no cabeçalho do **Receive** designer de atividade ou o **DisplayName** caixa da grade de propriedade.

 Para criar um <xref:System.ServiceModel.Activities.SendReply> atividade e associá-lo a selecionado <xref:System.ServiceModel.Activities.Receive> atividade, com o botão direito a **Receive** clique em designer de atividade de **SendReply criar** item no menu de contexto e o **SendReplyToReceive** designer aparece abaixo do **Receive** designer. A atividade de <xref:System.ServiceModel.Activities.SendReply> é uma atividade que envia a mensagem de resposta como parte de um padrão de troca de solicitação/resposta de mensagem no serviço. Ele pode ser configurado com o **SendReplyToReceive** designer.

 Como alternativa, o **ReceiveAndSendReply** designer de modelo no **mensagens** categoria do **caixa de ferramentas** pode ser usado para criar um par de pré-configurado<xref:System.ServiceModel.Activities.Receive>e <xref:System.ServiceModel.Activities.SendReply> atividade. Para obter mais informações sobre o uso do **ReceiveAndSendReply** e **SendReplyToReceive** modelo, consulte o [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md) tópico.

### <a name="the-receive-activity-properties"></a>As propriedades de atividade de receptor
 A tabela a seguir mostra as propriedades de <xref:System.ServiceModel.Activities.Receive> e descreve como elas são usadas no designer. Essas propriedades podem ser editadas na grade de propriedades ou na superfície de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] . A única propriedade necessário é a propriedade de <xref:System.ServiceModel.Activities.Receive.OperationName%2A> .

|Nome da Propriedade|Necessária|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Especifica o nome amigável de atividade de <xref:System.ServiceModel.Activities.Receive> . O valor padrão é receber.<br /><br /> Embora o uso de um valor não padrão para <xref:System.Activities.Activity.DisplayName%2A> amigável não é necessário restrita, é uma prática recomendada usar um valor.|
|<xref:System.ServiceModel.Activities.Receive.OperationName%2A>|verdadeiro|Especifica o nome da operação de serviço implementada por esta atividade de <xref:System.ServiceModel.Activities.Receive> . Esta propriedade é usada para construir o valor padrão para o **ação** propriedade se o **ação** propriedade não está definida explicitamente.|
|<xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A>|False|Especifica o nome do contrato de serviço. Essa propriedade é usada para agrupar operações de serviço em contratos de serviço individuais. Todas as atividades de <xref:System.ServiceModel.Activities.Receive> que têm mesmo <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> são agrupadas no mesmo contrato de serviço (tipo de porta de WSDL.) O valor padrão é o nome totalmente qualificado de CLR de atividade de nível superior (raiz).|
|<xref:System.ServiceModel.Activities.Receive.Content%2A>|False|Especifica o conteúdo de mensagem ou de parâmetro para receber. Pode ser uma atividade de <xref:System.ServiceModel.Activities.ReceiveMessageContent> ou uma atividade de <xref:System.ServiceModel.Activities.ReceiveParametersContent> . Editar essa propriedade clicando no botão de reticências ao lado de **conteúdo** campo na grade de propriedade ou clicando o **definir...**  botão ao lado de **conteúdo** rótulo no **Receive** superfície do designer de atividade. Ambos exibem o **definição de conteúdo** caixa de diálogo. Para obter mais informações sobre como usar essa caixa, consulte o [caixa de diálogo Definição de conteúdo](../workflow-designer/content-definition-dialog-box.md) tópico.|
|<xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A>|False|Especifica se correlaciona entre atividades de <xref:System.ServiceModel.Activities.Receive> em operações de serviço de um fluxo de trabalho com um objeto de <xref:System.ServiceModel.MessageQuerySet> . Clique no botão de reticências ao lado de <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> propriedade na grade de propriedades para abrir o **definição de CorrelatesOn** caixa de diálogo. Para obter mais informações sobre o uso dessa caixa de diálogo, consulte o [caixa de diálogo Definição de conteúdo](../workflow-designer/content-definition-dialog-box.md) tópico.|
|<xref:System.ServiceModel.Activities.Receive.CorrelatesWith%2A>|False|Especifica <xref:System.ServiceModel.Activities.CorrelationHandle> usado para rotear a mensagem à instância apropriado de fluxo de trabalho.<br /><br /> Clique no botão de reticências ao lado de <xref:System.ServiceModel.Activities.Receive.CorrelatesWith%2A> propriedade na grade de propriedades para abrir o **Editor de expressão** caixa de diálogo. Para obter mais informações sobre o uso dessa caixa de diálogo, consulte o [como: usar o Editor de expressão](../workflow-designer/how-to-use-the-expression-editor.md) tópico.|
|<xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A>|False|Especifica a coleção de objetos de <xref:System.ServiceModel.Activities.CorrelationInitializer> que inicializam vários objetos de <xref:System.ServiceModel.Activities.CorrelationHandle> que configuram esta atividade de <xref:System.ServiceModel.Activities.Receive> dentro de fluxo de trabalho. Clique no botão de reticências ao lado de <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> propriedade na grade de propriedades para abrir o **adicionar inicializadores de correlação** caixa de diálogo. Para obter mais informações sobre como usar essa caixa, consulte o [caixa de diálogo Adicionar CorrelationInitializers](../workflow-designer/add-correlationinitializers-dialog-box.md) tópico.|
|<xref:System.ServiceModel.Activities.Receive.CanCreateInstance%2A>|False|Especifica um valor que determina se uma nova instância de fluxo de trabalho é criada para processar a mensagem se a mensagem não correlaciona a uma instância existente de fluxo de trabalho. Se o valor for definido como **true**, uma nova instância de fluxo de trabalho é criada para processar a mensagem quando a mensagem não está correlacionada com uma instância de fluxo de trabalho existente.|
|<xref:System.ServiceModel.Activities.Receive.KnownTypes%2A>|False|Especifica uma coleção de tipos conhecidos para a operação de serviço implementada por esta atividade de <xref:System.ServiceModel.Activities.Receive> . Esta propriedade deve ser usada em conjunto com a propriedade de <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> definida como <xref:System.Runtime.Serialization.DataContractSerializer>. É ignorada se <xref:System.Xml.Serialization.XmlSerializer> é usado.<br /><br /> Clique no botão de reticências ao lado de **KnownTypes** campo na grade de propriedades para exibir o **Editor de coleção do tipo** caixa de diálogo com a qual você pode adicionar tipos relevantes. Para obter mais informações sobre como usar essa caixa, consulte o [caixa de diálogo do Editor de coleção de tipo](../workflow-designer/type-collection-editor-dialog-box.md) tópico.|
|<xref:System.ServiceModel.Activities.Receive.ProtectionLevel%2A>|False|Especifica <xref:System.Net.Security.ProtectionLevel> para a mensagem.<br /><br /> 1. <xref:System.Net.Security.ProtectionLevel> significa somente autenticação.<br />2. <xref:System.Net.Security.ProtectionLevel> significa assinar dados para ajudar a garantir a integridade dos dados transmitidos.<br />3. <xref:System.Net.Security.ProtectionLevel> significa criptografar e assinar os dados para ajudar a garantir a confidencialidade e a integridade dos dados transmitidos.|
|<xref:System.ServiceModel.Activities.Receive.SerializerOption%2A>|False|Especifica o tipo de serializador para usar a operação de serviço implementada pela atividade de <xref:System.ServiceModel.Activities.Receive> . O valor padrão é <xref:System.Runtime.Serialization.DataContractSerializer>, que serializa e desserializa uma instância de um tipo em um fluxo XML ou em um documento que usa um contrato fornecido de dados. <xref:System.Xml.Serialization.XmlSerializer> também pode ser usado se mais controle sobre é necessário XML.|
|<xref:System.ServiceModel.Activities.Receive.Action%2A>|False|Especifica o cabeçalho da ação de mensagem. Se ele não for definido explicitamente, seu valor padrão é: https://tempuri.org/ {namespace de contrato de serviço} / {nome do contrato de serviço} / {nome da operação}.|

## <a name="see-also"></a>Consulte também

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Enviar](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)