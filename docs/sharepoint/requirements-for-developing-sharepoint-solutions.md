---
title: Requisitos para desenvolver soluções do SharePoint | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, prerequisites
- SharePoint development in Visual Studio, requirements
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 2cb92476d64abebb0dae24109e57940a19505cc1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="requirements-for-developing-sharepoint-solutions"></a>Requisitos para desenvolver soluções do SharePoint
 
Você deve instalar os pré-requisitos a seguir no sistema antes de usar as ferramentas de desenvolvimento de solução do SharePoint incluídas no Visual Studio:

- Visual Studio com c# e/ou Visual Basic ou uma edição do Visual Studio aplicativo Lifecycle Management (ALM).

- [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] instalado em 64 bits [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)] ou 64 bits [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)] R2.

     ou

- [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] instalado em 64 bits [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)] ou 64 bits [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)] R2.

> [!NOTE]
> Embora oficialmente têm suporte apenas sistemas operacionais de servidor do SharePoint, dois sistemas operacionais de cliente são permitidos: [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] e [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] SP1. Para obter mais informações, consulte [guia de instalação de estação de trabalho do SharePoint Server 2010 desenvolvedor](http://go.microsoft.com/fwlink/?LinkID=164557).

Tipos de projeto de modelo de conectividade de dados (BDC) de negócios exigem que [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] ser instalado no sistema.

Para desenvolver soluções do SharePoint no Visual Studio, você deve instalar o SharePoint no mesmo computador que o Visual Studio. Além disso, as ferramentas de desenvolvedor do SharePoint suportam apenas a uma configuração de autônomo do SharePoint; eles não dão suporte a uma configuração de farm (remoto).

> [!NOTE]
> Suportam somente a projetos do SharePoint no Visual Studio [!INCLUDE[net_v35_long](../sharepoint/includes/net-v35-long-md.md)]. Se você selecionar [!INCLUDE[net_v40_long](../sharepoint/includes/net-v40-long-md.md)] para um novo projeto do SharePoint, ele ainda será direcionada [!INCLUDE[net_v35_long](../sharepoint/includes/net-v35-long-md.md)].

Para obter mais informações sobre como instalar [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], consulte [instale o Visual Studio](../install/install-visual-studio.md).

## <a name="vista-and-windows-7-user-account-control-uac"></a>Controle de Conta de Usuário (UAC) do Vista e do Windows 7

[!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] e [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] incorporar um recurso de segurança que é conhecido como controle de conta de usuário (UAC). Para desenvolver soluções do SharePoint na [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] na [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] e [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] sistemas, o UAC exige que você execute [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] como um administrador do sistema. Na área de trabalho, abra o menu de atalho para [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]e, em seguida, escolha **executar como administrador**.

Para configurar o atalho da área de trabalho para sempre executar como administrador, abra o menu de atalho, escolha **propriedades**, escolha o **avançado** botão e, em seguida, selecione o **executar como administrador**  caixa de seleção.

Para obter mais informações, consulte [Noções básicas e configurando o controle de conta de usuário no Windows Vista](http://go.microsoft.com/fwlink/?LinkID=156476). e [controle de conta de usuário do Windows 7](http://go.microsoft.com/fwlink/?LinkId=177523).

## <a name="sharepoint-permissions-considerations"></a>Considerações das Permissões do SharePoint

Para desenvolver soluções do SharePoint, você deve ter permissões suficientes para executar e depurar soluções do SharePoint. Antes de você pode testar uma solução do SharePoint, execute as etapas a seguir para garantir que você tenha as permissões necessárias:

1. Adicione sua conta de usuário como um administrador do sistema.

2. Adicione sua conta de usuário como um administrador de Farm do SharePoint server.

    1. Na Administração Central do SharePoint, escolha o **gerenciar o grupo de administradores de farm** link.

    2. No **os administradores de Farm** página, escolha o **novo** botão.

3. Adicione sua conta de usuário para ao grupo WSS_ADMIN_WPG.

## <a name="see-also"></a>Consulte também

[Guia de Introdução &#40;desenvolvimento do SharePoint no Visual Studio&#41;](../sharepoint/getting-started-sharepoint-development-in-visual-studio.md)