---
title: "Como: implementar uma operação do contrato Windows Communication Foundation (legados) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: d6aeb20e-fac8-4a9d-bd26-ae78bef96b41
caps.latest.revision: "7"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 02d6a544b660a110c618bdcb7d3b778fd82ceaaa
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-implement-a-windows-communication-foundation-contract-operation-legacy"></a>Como: Implementar uma operação do Windows Communication Foundation (o legados)
Este tópico descreve como implementar uma operação do contrato de [!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)] usando o novas [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] que direciona [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 Depois de arrastar um **ReceiveActivity** atividade da caixa de ferramentas para a superfície de design de fluxo de trabalho, você será criar uma nova [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)] de contrato ou importar um contrato existente e implementar as operações. Você selecionar e/ou criar o contrato e suas operações por meio de [escolha a caixa de diálogo da operação (herdado)](../workflow-designer/choose-operation-dialog-box-legacy.md).  
  
### <a name="to-implement-a-wcf-contract-operation"></a>Para implementar uma operação do contrato de WCF  
  
1.  Clique duas vezes no **ReceiveActivity** atividade no designer ou clique no botão de reticências ao lado de **ServiceOperationInfo** propriedade no **propriedades** painel.  
  
2.  Realize um dos seguintes procedimentos:  
  
    -   Clique em **Adicionar contrato** no canto superior direito da caixa de diálogo. Isso criará um novo contrato e operação de [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)] para você.  
  
         -ou-  
  
    -   Clique em **importação** no canto superior direito da caixa de diálogo. O [procurar e selecione uma caixa de diálogo de tipo .NET (legados)](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md) é aberto. Pesquise por um assembly ou projeto que contém o contrato que você deseja. Selecione o contrato e clique em **Okey**.  
  
     Depois que um contrato é criado ou importado, você pode adicionar novos operações ao contrato criado ou importou isso. Para adicionar uma nova operação, selecione o contrato e clique em **Adicionar operação** no canto superior direito da caixa de diálogo. Quando você tiver terminado de adicionar operações, vá para a etapa 3.  
  
3.  Selecione a operação que você deseja associar a **ReceiveActivity** atividade. Você pode manipular a definição da operação alterar o nome, parâmetros, propriedades, e as configurações de permissão da operação.  
  
     Para alterar o nome, digite o novo nome no **nome da operação** caixa de texto.  
  
     Clique o **parâmetros** guia para acessar os parâmetros da operação. Você pode alterar o nome, tipo, ou a direção de um parâmetro assim como adicionar ou excluir parâmetros da operação.  
  
     Clique o **propriedades** guia para acessar a funcionalidade do exchange operação proteção com suporte e nível de mensagem da operação.  
  
     Clique o **permissões** guia para especificar quais grupos têm permissão para implementar a operação.  
  
4.  Clique em **Okey** e **ReceiveActivity** atividade exibirá o nome da operação para a operação que está implementando.  
  
5.  Coloque as atividades de fluxo de trabalho que você pretende usar para a implementação dessa operação dentro de **ReceiveActivity** atividade.  
  
## <a name="see-also"></a>Consulte também  
 [Escolha a caixa de diálogo de operação (o legados)](../workflow-designer/choose-operation-dialog-box-legacy.md)   
 [Como: chamar uma operação do WCF (legados)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md)   
 [Atividades de fluxo de trabalho herdadas](../workflow-designer/legacy-workflow-activities.md)