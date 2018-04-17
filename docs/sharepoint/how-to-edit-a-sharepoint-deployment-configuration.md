---
title: 'Como: editar uma configuração de implantação do SharePoint | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.DeploymentConfig
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deploying
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 97f6851b3d9aefee969851f355552373e7ecc7ff
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-edit-a-sharepoint-deployment-configuration"></a>Como editar uma configuração de implantação do SharePoint
  Você pode criar uma configuração de implantação ou modificar uma configuração de implantação existente. Por exemplo, você pode executar uma única etapa ou alterar a ordem das etapas no processo de implantação. Você deseja criar ou modificar configurações de implantação porque não não possível alterar as configurações internas e adicionadas de forma programática.  
  
## <a name="creating-a-sharepoint-deployment-configuration"></a>Criando uma configuração de implantação do SharePoint  
  
#### <a name="to-create-a-sharepoint-deployment-configuration"></a>Para criar uma configuração de implantação do SharePoint  
  
1.  Em **Solution Explorer**, escolha um projeto do SharePoint e, em seguida, na barra de menus, escolha **projeto**, * * ProjectName**propriedades**.  
  
2.  Sobre o **SharePoint** guia, escolha o **novo** botão.  
  
     O **adicionar nova configuração de implantação** caixa de diálogo é exibida.  
  
3.  No **nome** texto, digite um nome para a configuração de implantação.  
  
4.  No **etapas de implantação disponíveis** painel, escolha as etapas que você deseja adicionar a configuração de implantação, escolha o (**>**) botão e, em seguida, escolha o **Okey** botão.  
  
    > [!NOTE]  
    >  Se você tiver configurado um comando de pré-implantação ou pós-implantação, essas etapas executadas apenas se você adicioná-los a uma configuração de implantação personalizada.  
  
## <a name="changing-the-active-deployment-configuration"></a>Alterar a configuração de implantação ativa  
  
#### <a name="to-change-the-active-deployment-configuration"></a>Para alterar a configuração de implantação ativa  
  
1.  Em **Solution Explorer**, escolha um projeto do SharePoint e, em seguida, na barra de menus, escolha **projeto**, * * ProjectName**propriedades**.  
  
2.  Escolha o **SharePoint** guia.  
  
3.  No **configuração de implantação ativa** caixa de listagem, escolha o nome da configuração de implantação que você deseja usar.  
  
## <a name="see-also"></a>Consulte também  
 [Empacotando e implantando recursos do SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  