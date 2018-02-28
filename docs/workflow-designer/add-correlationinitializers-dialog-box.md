---
title: "Adicionar caixa de diálogo CorrelationInitializers | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- AddCorrelationInitializers.UI
ms.assetid: c0517467-d54a-4ee6-aef0-c19b96b6f395
caps.latest.revision: 
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload:
- multiple
ms.openlocfilehash: 4c4d8e07aa172aef524b4d85bda5ad8efdfb509f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="add-correlationinitializers-dialog-box"></a>Adicione a caixa de diálogo CorrelationInitializers
O **adicionar inicializadores de correlação** caixa de diálogo é usada em [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] para configurar o **CorrelationInitializers** propriedades do <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply>, e <xref:System.ServiceModel.Activities.ReceiveReply> atividades. [!INCLUDE[crabout](../test/includes/crabout_md.md)]os designers de atividade que usam essa caixa, consulte o [enviar](../workflow-designer/send-activity-designer.md), [Receive](../workflow-designer/receive-activity-designer.md), [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md), e [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) tópicos.  
  
 Inicializadores de correlação na coleção especificada com esta caixa de diálogo pode inicializar a consulta com base, o contexto, o contexto de retorno de chamada, ou se correlaciona de solicitação de resposta entre as atividades de mensagem.  
  
 A tabela a seguir descreve os elementos de interface de usuário do **adicionar inicializadores de correlação** caixa de diálogo.  
  
|Elemento da Interface do Usuário|Descrição|  
|----------------|-----------------|  
|**Adicionar um inicializador**|Clique o **adicionar inicializar** caixa para adicionar um inicializador adicional à coleção.|  
|**Tipo de correlação**|Especifica o tipo de inicializador de correlação. Há quatro tipos a escolher:<br /><br /> 1.  Um inicializador de correlação de retorno de chamada para especificar <xref:System.ServiceModel.Activities.CallbackCorrelationInitializer>.<br />2.  Um inicializador de correlação de contexto para especificar <xref:System.ServiceModel.Activities.CorrelationInitializer>.<br />3.  Um inicializador de correlação de solicitação de resposta para especificar <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>.<br />4.  Um inicializador de correlação de consulta para especificar <xref:System.ServiceModel.Activities.QueryCorrelationInitializer>.<br /><br /> Para editar o **CorrelationType**<br /><br /> 1.  Guia para a linha específica de **adicionar inicializador** DataGrid.<br />2.  Pressione Ctrl + Tab para focalizar **CorrelationTypeComboBox**<br />3.  Pressione Alt + seta para baixo para pop-up de **ComboBox** e editá-lo.|  
|**Consultas XPath**|Um par chave/valor que contém as consultas usadas para extrair dados de correlação das mensagens de entrada e saída. Esta lista só é válido para usar <xref:System.ServiceModel.Activities.QueryCorrelationInitializer> tipos.|  
  
## <a name="to-launch-the-add-correlation-initializers-dialog-box"></a>Para iniciar a caixa de diálogo de inicializadores de adicionar correlação  
 O **adicionar inicializadores de correlação** caixa de diálogo é usada pelo **enviar**, **Receive**, **ReceiveAndSendReply**, e  **SendAndReceiveReply** designers. Acessá-los é semelhante em cada caso e que envolve o **Receive** designer é usado aqui para ilustrar o procedimento.  
  
 O **Receive** designer de atividades pode ser arrastado o **caixa de ferramentas** e removidos no [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] superfície onde quer que as atividades geralmente são colocadas. Isso cria uma atividade de <xref:System.ServiceModel.Activities.Receive> com <xref:System.Activities.Activity.DisplayName%2A> padrão Receive. Selecione o **Receive** designer de atividade e clique no botão de reticências ao lado do texto (coleção) para o **CorrelationInitializers** propriedade na grade de propriedade para o **adicionar Inicializadores de correlação** caixa de diálogo.  
  
## <a name="see-also"></a>Consulte também  
 [Adicionar caixa de diálogo correlação](http://msdn.microsoft.com/en-us/9e41a149-e8ab-41b1-8886-ea06a63041b6)   
 [Caixa de diálogo Inicializar Correlação](../workflow-designer/initialize-correlation-dialog-box.md)