---
title: "Como: chamar uma operação do contrato Windows Communication Foundation (legados) | Microsoft Docs"
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: a9058345-708f-4fcf-8739-2a43e5285b7a
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 522db4f46486470333393ca99f384f258898e09a
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2018
---
# <a name="how-to-invoke-a-windows-communication-foundation-contract-operation-legacy"></a>Como: Chamar uma operação do Windows Communication Foundation (o legados)
Este tópico descreve como invocar um [!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)] de contrato de operação usando o Designer de fluxo de trabalho herdado do Windows que tem como alvo o [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].

 Depois de arrastar um **SendActivity** atividade da caixa de ferramentas para a superfície de design de fluxo de trabalho, você deve importar um contrato existente e determinar qual operação será invocada daquele **SendActivity** atividade. Selecione seu contrato e suas operações por meio de [escolha a caixa de diálogo da operação (herdado)](../workflow-designer/choose-operation-dialog-box-legacy.md).

 Além disso, se você estiver usando um arquivo de configuração com o serviço, você precisará especificar <xref:System.Workflow.Activities.ChannelToken>. <xref:System.Workflow.Activities.ChannelToken> identifica a configuração do ponto de extremidade a atividade de enviar usará para se conectar ao serviço de fluxo de trabalho.

### <a name="to-invoke-a-wcf-contract-operation-from-a-sendactivity-activity"></a>Para chamar a reduzir a operação de uma atividade de SendActivity

1.  Clique duas vezes no **SendActivity** atividade no designer ou clique no botão de reticências ao lado de **ServiceOperationInfo** propriedade no **propriedades** painel.

2.  Quando o **operação escolha** caixa de diálogo é aberta, clique em **importação** no canto superior direito da caixa de diálogo.

     O [procurar e selecione uma caixa de diálogo de tipo .NET (legados)](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md) é aberto.

3.  Pesquise por um assembly ou projeto que contém o contrato que você deseja.

4.  Selecione o contrato e clique em **Okey**.

5.  Em **operações disponíveis**, selecione a operação que você deseja invocar e clique em **Okey**.

### <a name="to-specify-a-channel-token"></a>Para especificar um token de canal

1.  Selecione a atividade de <xref:System.Workflow.Activities.SendActivity> no designer.

2.  No **propriedades** painel, especifique um nome para o <xref:System.Workflow.Activities.ChannelToken>. Este nome identifica unicamente o símbolo do canal.

3.  Expanda o nó simbólico do canal e especifique um nome para o ponto final de cliente que você usará no campo de <xref:System.Workflow.Activities.ChannelToken.EndpointName%2A> . A configuração de ponto de extremidade de mesmo nome no arquivo de configuração será usada para configurar o canal.

4.  Crie a configuração de ponto de extremidade no arquivo de configuração, se ele não existir. Para obter mais informações sobre como configurar seu cliente, consulte [visão geral do cliente WCF](/dotnet/framework/wcf/wcf-client-overview).

## <a name="see-also"></a>Consulte também

- [Caixa de diálogo Escolher Operação (herdado)](../workflow-designer/choose-operation-dialog-box-legacy.md)
- [Como: implementar uma operação do WCF (legados)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md)
- [Atividades de fluxo de trabalho herdadas](../workflow-designer/legacy-workflow-activities.md)