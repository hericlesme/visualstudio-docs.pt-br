---
title: Designer de fluxo de trabalho - escolha a caixa de diálogo de operação (o legados)
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Workflow.Activities.Design.OperationPickerDialog.UI
ms.assetid: bc3ec902-7797-494e-af48-e70c97eb6779
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fed4353771edc5f9cc1bb239424b0e7015acd84a
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31975576"
---
# <a name="choose-operation-dialog-box-legacy"></a>Escolha a caixa de diálogo da operação (o legados)

Este tópico descreve como usar o **operação escolha** caixa de diálogo no Designer de fluxo de trabalho herdado do Windows. Use o Designer de fluxo de trabalho herdado quando você precisa direcionar o .NET Framework versão 3.5 ou o WinFX.

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
> O **operação escolha** caixa de diálogo mostra somente contratos ou operações que são usadas por outros <xref:System.Workflow.Activities.SendActivity> atividades no fluxo de trabalho. Da mesma forma, o **operação escolha** caixa de diálogo <xref:System.Workflow.Activities.ReceiveActivity> atividades mostra apenas contratos ou operações que são usadas por outros **ReceiveActivity** atividades no fluxo de trabalho.

## <a name="see-also"></a>Consulte também

- [Como: implementar uma operação do WCF (legados)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md)
- [Como: chamar uma operação do WCF (legados)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md)
- [Designer herdado para a ajuda da interface do usuário do Windows Workflow Foundation](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)