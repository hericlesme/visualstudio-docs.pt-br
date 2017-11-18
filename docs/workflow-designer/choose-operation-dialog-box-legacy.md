---
title: "Escolha a caixa de diálogo de operação (herdado) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.Workflow.Activities.Design.OperationPickerDialog.UI
ms.assetid: bc3ec902-7797-494e-af48-e70c97eb6779
caps.latest.revision: "10"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 320233edede13e2f33bdcb206b056bf1d0b94b8e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="choose-operation-dialog-box-legacy"></a>Escolha a caixa de diálogo da operação (o legados)
Este tópico descreve como usar o **operação escolha** caixa de diálogo no herdado [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)]. Use [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] herdado quando você precisa definir como alvo [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 O **operação escolha** caixa de diálogo é usada para selecionar uma operação para associar um <xref:System.Workflow.Activities.ReceiveActivity> atividade ou um <xref:System.Workflow.Activities.SendActivity> atividade. Para obter mais informações sobre como usar essa caixa de diálogo com essas atividades, consulte [como: implementar uma operação do WCF (legados)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md) e [como: chamar uma operação do WCF (legados)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md).  
  
 A tabela a seguir descreve os elementos de interface de usuário do **operação escolha** caixa de diálogo.  
  
|Elemento da Interface do Usuário|Descrição|  
|----------------|-----------------|  
|**Adicionar contrato**|Cria um novo contrato para você. Você pode definir novos operações no contrato. (Isso é usado com <xref:System.Workflow.Activities.ReceiveActivity> somente.)|  
|**Operação de adição**|Adiciona novas operações para um novo contrato que você criou no **operação escolha** caixa de diálogo. **Observação:** você pode adicionar novas operações somente a contratos que você criou por meio de **operação escolha** caixa de diálogo. <br /><br /> (Isso é usado com <xref:System.Workflow.Activities.ReceiveActivity> somente.)|  
|**Importe...**|Importa um contrato definido anteriormente e permite que você selecione uma operação do contrato.|  
|**Nome da operação**|Nome da operação selecionada. Essa caixa de texto está disponível para edição somente se você tiver criado uma operação por meio de **operação escolha** caixa de diálogo.|  
|**Parâmetros**|Catalogue para conter as definições de parâmetro para a operação selecionada. **Observação:** definições de parâmetro podem ser alteradas apenas se você tiver criado uma operação por meio de **operação escolha** caixa de diálogo.|  
|**Propriedades**|Catalogue para conter configurações de <xref:System.Net.Security.ProtectionLevel> para as mensagens enviadas entre o cliente e o serviço. **Observação:** essa guia é habilitada somente se você tiver criado uma operação por meio de **operação escolha** caixa de diálogo.|  
|**Permissões**|Catalogue para conter propriedades de <xref:System.Workflow.Activities.OperationInfoBase.PrincipalPermissionName%2A> e de <xref:System.Workflow.Activities.OperationInfoBase.PrincipalPermissionRole%2A> de usuários são permitidos que chamar a operação. Por exemplo, se apenas os usuários do grupo de administradores foram permissão para chamar essa operação, em seguida, você escreve "Administradores" **função** caixa de texto.<br /><br /> Essa guia é habilitada para operações criadas por meio de **ChooseOperation** caixa de diálogo e operações que foram importadas por meio do **importação** botão.|  
  
> [!NOTE]
>  O **operação escolha** caixa de diálogo mostra somente contratos ou operações que são usadas por outros <xref:System.Workflow.Activities.SendActivity> atividades no fluxo de trabalho. Da mesma forma, o **operação escolha** caixa de diálogo <xref:System.Workflow.Activities.ReceiveActivity> atividades mostra apenas contratos ou operações que são usadas por outros **ReceiveActivity** atividades no fluxo de trabalho.  
  
## <a name="see-also"></a>Consulte também  
 [Como: implementar uma operação do WCF (legados)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md)   
 [Como: chamar uma operação do WCF (legados)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md)   
 [Designer herdado para a ajuda da interface do usuário do Windows Workflow Foundation](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)