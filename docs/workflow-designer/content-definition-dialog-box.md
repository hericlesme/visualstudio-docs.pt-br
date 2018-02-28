---
title: "Caixa de diálogo Definição de conteúdo | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- MessageContent.UI
ms.assetid: 7e4237c3-90a1-4149-bd8a-3643d1dde0df
caps.latest.revision: 
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload:
- multiple
ms.openlocfilehash: c87180f1f1c0b2c578977021b6a9511e629d10bd
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="content-definition-dialog-box"></a>Caixa de diálogo de conteúdo da definição
O **definição de conteúdo** caixa de diálogo é usada em [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] para configurar o **conteúdo** propriedades do <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply>, e <xref:System.ServiceModel.Activities.ReceiveReply> atividades. [!INCLUDE[crabout](../test/includes/crabout_md.md)]os designers de atividade que usam essa caixa, consulte o [enviar](../workflow-designer/send-activity-designer.md), [Receive](../workflow-designer/receive-activity-designer.md), [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md), e [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) tópicos.  
  
 A tabela a seguir descreve os elementos de interface de usuário do **inicializar correlação** caixa de diálogo.  
  
|Elemento da Interface do Usuário|Descrição|  
|----------------|-----------------|  
|**Message**|Especifica a mensagem de conteúdo com o **mensagem dados** caixa de texto de expressão e o tipo usando o **tipo de mensagem** caixa de listagem suspensa. Por padrão, o **definição de conteúdo** usa o <xref:System.ServiceModel.Activities.ReceiveMessageContent>, que espera um <xref:System.ServiceModel.Channels.Message> ou uma tipo na definição do serviço de fluxo de trabalho de contrato de mensagem.|  
|**Parâmetros**|Clique o **parâmetros** botão de opção usar <xref:System.ServiceModel.Activities.ReceiveParametersContent>, que espera um contrato de dados. Use a grade de dados para definir uma coleção genérica de pares chave/valor de <xref:System.Activities.OutArgument> cujos valores são atribuídos aos parâmetros variáveis no fluxo de trabalho atual.|  
  
 O **definição de conteúdo** caixa de diálogo é usada pelo **enviar**, **Receive**, **ReceiveAndSendReply**, e  **SendAndReceiveReply** designers. Acessá-lo é semelhante em cada caso e exemplos de receptor são usados aqui para ilustrar o procedimento.  
  
 O **Receive** designer de atividades pode ser arrastado o **caixa de ferramentas** e removidos no [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] superfície onde quer que as atividades geralmente são colocadas. Isso cria uma atividade de <xref:System.ServiceModel.Activities.Receive> com <xref:System.Activities.Activity.DisplayName%2A> padrão Receive. Selecione o **Receive** designer de atividade e clique no botão de reticências ao lado do texto (conteúdo) para o **conteúdo** propriedade na grade de propriedade para o **definição de conteúdo**caixa de diálogo.  
  
 O conteúdo pode ser especificado dentro de **mensagem** seção um <xref:System.ServiceModel.Activities.ReceiveMessageContent> atividade ou no **parâmetro** seção um <xref:System.ServiceModel.Activities.ReceiveParametersContent> atividade.  
  
## <a name="see-also"></a>Consulte também  
 [Ajuda da interface do usuário do Designer de Fluxo de Trabalho](../workflow-designer/workflow-designer-ui-help.md)