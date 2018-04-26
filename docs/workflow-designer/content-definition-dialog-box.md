---
title: Designer de fluxo de trabalho - caixa de diálogo Definição de conteúdo
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- MessageContent.UI
ms.assetid: 7e4237c3-90a1-4149-bd8a-3643d1dde0df
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f20a17cf7e01eafc75263bd2753d686908574752
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="content-definition-dialog-box"></a>Caixa de diálogo de conteúdo da definição

O **definição de conteúdo** no Designer de fluxo de trabalho do Windows, a caixa de diálogo é usada para configurar o **conteúdo** propriedades do <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply>, e <xref:System.ServiceModel.Activities.ReceiveReply> atividades. Para obter mais informações sobre os designers de atividade que use essa caixa, consulte o [enviar](../workflow-designer/send-activity-designer.md), [Receive](../workflow-designer/receive-activity-designer.md), [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md), e [SendAndReceiveReply ](../workflow-designer/sendandreceivereply-template-designer.md) tópicos.

A tabela a seguir descreve os elementos de interface de usuário do **inicializar correlação** caixa de diálogo:

|Elemento da Interface do Usuário|Descrição|
|----------------|-----------------|
|**Message**|Especifica a mensagem de conteúdo com o **mensagem dados** caixa de texto de expressão e o tipo usando o **tipo de mensagem** caixa de listagem suspensa. Por padrão, o **definição de conteúdo** usa o <xref:System.ServiceModel.Activities.ReceiveMessageContent>, que espera um <xref:System.ServiceModel.Channels.Message> ou uma tipo na definição do serviço de fluxo de trabalho de contrato de mensagem.|
|**Parâmetros**|Clique o **parâmetros** botão de opção usar <xref:System.ServiceModel.Activities.ReceiveParametersContent>, que espera um contrato de dados. Use a grade de dados para definir uma coleção genérica de pares chave/valor de <xref:System.Activities.OutArgument> cujos valores são atribuídos aos parâmetros variáveis no fluxo de trabalho atual.|

O **definição de conteúdo** caixa de diálogo é usada pelo **enviar**, **Receive**, **ReceiveAndSendReply**, e  **SendAndReceiveReply** designers. Acessá-lo é semelhante em cada caso e exemplos de receptor são usados aqui para ilustrar o procedimento.

O **Receive** designer de atividades pode ser arrastado do **caixa de ferramentas** e descartado para a superfície do Designer de fluxo de trabalho onde quer que as atividades geralmente são colocadas. Isso cria uma atividade de <xref:System.ServiceModel.Activities.Receive> com <xref:System.Activities.Activity.DisplayName%2A> padrão Receive. Selecione o **Receive** designer de atividade e clique no botão de reticências ao lado do texto (conteúdo) para o **conteúdo** propriedade na grade de propriedade para o **definição de conteúdo**caixa de diálogo.

O conteúdo pode ser especificado dentro de **mensagem** seção um <xref:System.ServiceModel.Activities.ReceiveMessageContent> atividade ou no **parâmetro** seção um <xref:System.ServiceModel.Activities.ReceiveParametersContent> atividade.

## <a name="see-also"></a>Consulte também

- [Ajuda da interface do usuário do Designer de Fluxo de Trabalho](../workflow-designer/workflow-designer-ui-help.md)