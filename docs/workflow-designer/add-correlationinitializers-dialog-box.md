---
title: Designer de fluxo de trabalho - adicionar a caixa de diálogo CorrelationInitializers
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- AddCorrelationInitializers.UI
ms.assetid: c0517467-d54a-4ee6-aef0-c19b96b6f395
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dc122840607b62a966e5224662ec2d557e5c8ed5
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31975140"
---
# <a name="add-correlationinitializers-dialog-box"></a>Adicione a caixa de diálogo CorrelationInitializers

O **adicionar inicializadores de correlação** no Designer de fluxo de trabalho do Windows, a caixa de diálogo é usada para configurar o **CorrelationInitializers** propriedades do <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply>, e <xref:System.ServiceModel.Activities.ReceiveReply> atividades. Para obter mais informações sobre os designers de atividade que use essa caixa, consulte o [enviar](../workflow-designer/send-activity-designer.md), [Receive](../workflow-designer/receive-activity-designer.md), [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md), e [SendAndReceiveReply ](../workflow-designer/sendandreceivereply-template-designer.md) tópicos.

Os inicializadores de correlação na coleção especificada com essa caixa de diálogo podem inicializar as seguintes correlações entre as atividades de mensagens:

- com base em consulta
- contexto
- contexto de retorno de chamada
- solicitação-resposta

A tabela a seguir descreve os elementos de interface de usuário do **adicionar inicializadores de correlação** caixa de diálogo:

|Elemento da Interface do Usuário|Descrição|
|----------------|-----------------|
|**Adicionar um inicializador**|Clique o **adicionar inicializar** caixa para adicionar um inicializador adicional à coleção.|
|**Tipo de correlação**|Especifica o tipo de inicializador de correlação. Há quatro tipos a escolher:<br /><br /> 1. Um inicializador de correlação de retorno de chamada para especificar <xref:System.ServiceModel.Activities.CallbackCorrelationInitializer>.<br />2. Um inicializador de correlação de contexto para especificar <xref:System.ServiceModel.Activities.CorrelationInitializer>.<br />3. Um inicializador de correlação de solicitação de resposta para especificar <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>.<br />4. Um inicializador de correlação de consulta para especificar <xref:System.ServiceModel.Activities.QueryCorrelationInitializer>.<br /><br /> Para editar o **CorrelationType**<br /><br /> 1. Guia para a linha específica de **adicionar inicializador** DataGrid.<br />2. Para definir o foco para **CorrelationTypeComboBox**, pressione **Ctrl**+**guia**.<br />3. Pressione Alt + seta para baixo para pop-up de **ComboBox** e editá-lo.|
|**Consultas XPath**|Um par chave/valor que contém as consultas usadas para extrair dados de correlação das mensagens de entrada e saída. Esta lista só é válido para usar <xref:System.ServiceModel.Activities.QueryCorrelationInitializer> tipos.|

## <a name="to-launch-the-add-correlation-initializers-dialog-box"></a>Para iniciar a caixa de diálogo de inicializadores de adicionar correlação

 O **adicionar inicializadores de correlação** caixa de diálogo é usada pelo **enviar**, **Receive**, **ReceiveAndSendReply**, e  **SendAndReceiveReply** designers. Acessá-los é semelhante em cada caso e o caso que envolve o **Receive** designer é usado aqui para ilustrar o procedimento.

 O **Receive** designer de atividades pode ser arrastado do **caixa de ferramentas** e descartado para a superfície do Designer de fluxo de trabalho onde quer que as atividades são colocadas. Descartando o **Receive** designer de atividade cria um <xref:System.ServiceModel.Activities.Receive> atividade com um padrão <xref:System.Activities.Activity.DisplayName%2A> Receive. Selecione o **Receive** designer de atividade e clique no botão de reticências ao lado do texto (coleção) para o **CorrelationInitializers** propriedade na grade de propriedade para o **adicionar Inicializadores de correlação** caixa de diálogo.

## <a name="see-also"></a>Consulte também

- [Adicionar caixa de diálogo correlação](http://msdn.microsoft.com/en-us/9e41a149-e8ab-41b1-8886-ea06a63041b6)
- [Caixa de diálogo Inicializar Correlação](../workflow-designer/initialize-correlation-dialog-box.md)