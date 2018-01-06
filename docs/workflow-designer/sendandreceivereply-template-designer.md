---
title: Designer de modelo de SendAndReceiveReply | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.SendAndReceiveReply.UI
- System.ServiceModel.Activities.ReceiveReply.UI
ms.assetid: 818a8c84-6593-416d-b016-1d91b85ffb68
caps.latest.revision: "6"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 314ff5252b426610b9a50327fe6754b2a953908c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="sendandreceivereply-template-designer"></a>Designer do modelo de SendAndReceiveReply
O **SendAndReceiveReply** modelo é usado para criar um par de pré-configurado <xref:System.ServiceModel.Activities.Send> e <xref:System.ServiceModel.Activities.ReceiveReply> atividades em um <xref:System.Activities.Statements.Sequence> atividades que são correlacionadas como parte de uma troca de mensagens de solicitação/resposta padrão no cliente.  
  
## <a name="the-sendandreceivereply-template"></a>O modelo de SendAndReceiveReply  
 Adicionando **SendAndReceiveReply** modelo faz três coisas além de criar o <xref:System.ServiceModel.Activities.Send> e <xref:System.ServiceModel.Activities.ReceiveReply> atividades em um <xref:System.Activities.Statements.Sequence> atividade:  
  
1.  Configurar <xref:System.ServiceModel.Activities.Send.OperationName%2A>, propriedades de <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> de atividade de <xref:System.ServiceModel.Activities.Send> .  
  
2.  Associa a propriedade de <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> de atividade de <xref:System.ServiceModel.Activities.ReceiveReply> a atividade de <xref:System.ServiceModel.Activities.Send> .  
  
3.  Cria <xref:System.ServiceModel.Activities.CorrelationHandle> como um variável na atividade pai.  
  
### <a name="using-the-sendandreceivereply-template-designer"></a>Usando o designer do modelo de SendAndReceiveReply  
 O **SendAndReceiveReply** designer de atividade pode ser encontrado no **mensagens** categoria do **caixa de ferramentas**, que é acessado clicando o **caixa de ferramentas**  guia [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (como alternativa, selecione **barra de ferramentas** do **exibição** menu ou CTRL + ALT + X.)  
  
 O **SendAndReceiveReply** designer de atividades pode ser arrastado o **caixa de ferramentas** e removidos no [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] superfície onde quer que as atividades geralmente são colocadas. Isso cria uma <xref:System.ServiceModel.Activities.Send> atividade que pode ser configurada com o **enviar** designer de atividade e um correlacionado <xref:System.ServiceModel.Activities.ReceiveReply> que pode ser configurado com o **ReceiveReplyForSend** designer.  
  
 [!INCLUDE[crabout](../test/includes/crabout_md.md)]usando o **enviar** designer para configurar o <xref:System.ServiceModel.Activities.Send> atividade, consulte o [enviar](../workflow-designer/send-activity-designer.md) tópico.  
  
 [!INCLUDE[crabout](../test/includes/crabout_md.md)]usando o **ReceiveReplyForSend** designer para configurar o <xref:System.ServiceModel.Activities.ReceiveReply> atividade, consulte a seção a seguir.  
  
### <a name="properties-of-receivereply"></a>Propriedades de ReceiveReply  
 A tabela a seguir mostra as propriedades de <xref:System.ServiceModel.Activities.ReceiveReply> e descreve como elas são usadas no designer. Essas propriedades podem ser editadas na grade de propriedades e alguns podem ser editados na [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]superfície do designer.  
  
|Nome da Propriedade|Necessária|Uso|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|O nome amigável opcional de atividade de <xref:System.ServiceModel.Activities.ReceiveReply> . O padrão é ReceiveReplyForSend.<br /><br /> Embora o uso de um valor não padrão para <xref:System.Activities.Activity.DisplayName%2A> amigável não é necessário restrita, é uma prática recomendada usar um valor.|  
|<xref:System.ServiceModel.Activities.ReceiveReply.Request%2A>|verdadeiro|Fazer referência a <xref:System.ServiceModel.Activities.Send> a atividade emparelhada com esta atividade de <xref:System.ServiceModel.Activities.ReceiveReply> . Essa propriedade não deve ser **nulo**. <xref:System.ServiceModel.Activities.Send> e as atividades de <xref:System.ServiceModel.Activities.ReceiveReply> são usados juntos no cliente para modelar um padrão de mensagem de solicitação/resposta. Esta propriedade especifica que a atividade de <xref:System.ServiceModel.Activities.Send> é emparelhada. No designer, você não pode editar esta propriedade como é associada automaticamente a atividade de <xref:System.ServiceModel.Activities.Send> de que você criou a atividade de <xref:System.ServiceModel.Activities.ReceiveReply> .|  
|<xref:System.ServiceModel.Activities.ReceiveReply.Content%2A>|False|Especifica o conteúdo de mensagem ou de parâmetro para receber. Pode ser uma atividade de <xref:System.ServiceModel.Activities.ReceiveMessageContent> ou uma atividade de <xref:System.ServiceModel.Activities.ReceiveParametersContent> . Editar essa propriedade clicando no botão de reticências ao lado de **conteúdo** campo na grade de propriedade ou clicando o **definir...**  botão ao lado de **conteúdo** rótulo no **Receive** superfície do designer de atividade. Ambos exibem o **definição de conteúdo** caixa de diálogo. [!INCLUDE[crabout](../test/includes/crabout_md.md)]como usar essa caixa, consulte o [caixa de diálogo Definição de conteúdo](../workflow-designer/content-definition-dialog-box.md) tópico.|  
|<xref:System.ServiceModel.Activities.ReceiveReply.CorrelationInitializers%2A>|False|Especifica a coleção de objetos de <xref:System.ServiceModel.Activities.CorrelationInitializer> que inicializam vários objetos de <xref:System.ServiceModel.Activities.CorrelationHandle> que configuram esta atividade de <xref:System.ServiceModel.Activities.Receive> dentro de fluxo de trabalho. Clique no botão de reticências ao lado de <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> propriedade na grade de propriedades para abrir o **adicionar inicializadores de correlação** caixa de diálogo. [!INCLUDE[crabout](../test/includes/crabout_md.md)]usando essa caixa, consulte o [caixa de diálogo Adicionar CorrelationInitializers](../workflow-designer/add-correlationinitializers-dialog-box.md) tópico.|  
|<xref:System.ServiceModel.Activities.ReceiveReply.Action%2A>|False|Especifica o cabeçalho da ação de mensagem. Se não é explicitamente definida, seu valor por padrão:<br /><br /> **https://tempuri.org/ {namespace de contrato de serviço} / {nome do contrato de serviço} / {nome da operação}.**|  
  
## <a name="see-also"></a>Consulte também  
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)   
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)   
 [Receber](../workflow-designer/receive-activity-designer.md)   
 [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)   
 [Enviar](../workflow-designer/send-activity-designer.md)   
 [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)