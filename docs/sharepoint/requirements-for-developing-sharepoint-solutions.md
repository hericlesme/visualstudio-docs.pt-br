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
ms.openlocfilehash: 9c9d6a726b290bfed1c086f9fb03290a37c91490
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37118347"
---
# <a name="requirements-for-developing-sharepoint-solutions"></a>Requisitos para desenvolver soluções do SharePoint
Você deve instalar os pré-requisitos a seguir no sistema antes de usar as ferramentas de desenvolvimento de soluções do SharePoint incluídas no Visual Studio:

- Visual Studio com c# e/ou Visual Basic ou uma edição de Visual Studio Application Lifecycle Management (ALM).

- [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] instalado em 64 bits [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)] ou de 64 bits [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)] R2.

     ou

- [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] instalado em 64 bits [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)] ou de 64 bits [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)] R2.

> [!NOTE]
> Embora somente sistemas operacionais de servidor são suportados oficialmente pelo SharePoint, dois sistemas operacionais de cliente são permitidos: [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] e [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] SP1. Para obter mais informações, consulte [guia de instalação de estação de trabalho do SharePoint Server 2010 Developer](http://go.microsoft.com/fwlink/?LinkID=164557).

Tipos de projeto de modelo de conectividade de dados (BDC) de negócios exigem que [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] ser instalado no sistema.

Para desenvolver soluções do SharePoint no Visual Studio, você deve instalar o SharePoint no mesmo computador que o Visual Studio. Além disso, as ferramentas de desenvolvedor do SharePoint suportam apenas uma configuração autônoma do SharePoint; eles não oferecem suporte a uma configuração de farm (remoto).

> [!NOTE]
> Projetos do SharePoint no Visual Studio dão suporte apenas [!INCLUDE[net_v35_long](../sharepoint/includes/net-v35-long-md.md)]. Se você selecionar [!INCLUDE[net_v40_long](../sharepoint/includes/net-v40-long-md.md)] para um novo projeto do SharePoint, ele ainda será direcionada [!INCLUDE[net_v35_long](../sharepoint/includes/net-v35-long-md.md)].

Para obter mais informações sobre como instalar [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], consulte [instalar o Visual Studio](../install/install-visual-studio.md).

## <a name="vista-and-windows-7-user-account-control-uac"></a>Controle de Conta de Usuário (UAC) do Vista e do Windows 7
[!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] e [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] incorporar um recurso de segurança que é conhecido como controle de conta de usuário (UAC). Para desenvolver soluções do SharePoint no [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] na [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] e [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] sistemas, o UAC requer que você execute [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] como um administrador do sistema. Na área de trabalho, abra o menu de atalho [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]e, em seguida, escolha **executar como administrador**.

Para configurar o atalho da área de trabalho para sempre executar como administrador, abra o menu de atalho, escolha **propriedades**, escolha o **avançado** botão e, em seguida, selecione o **executar como administrador**  caixa de seleção.

Para obter mais informações, consulte [Compreendendo e configurando o controle de conta de usuário no Windows Vista](http://go.microsoft.com/fwlink/?LinkID=156476). e [controle de conta de usuário do Windows 7](http://go.microsoft.com/fwlink/?LinkId=177523).

## <a name="sharepoint-permissions-considerations"></a>Considerações sobre permissões de SharePoint
Para desenvolver soluções do SharePoint, você deve ter permissões suficientes para executar e depurar soluções do SharePoint. Antes de testar uma solução do SharePoint, execute as seguintes etapas para garantir que você tenha as permissões necessárias:

1. Adicione sua conta de usuário como um administrador do sistema.

2. Adicione sua conta de usuário como um administrador de Farm do SharePoint server.

    1. Na Administração Central do SharePoint, escolha o **gerenciar o grupo de administradores de farm** link.

    2. No **os administradores de Farm** , escolha o **New** botão.

3. Adicionar sua conta de usuário ao grupo WSS_ADMIN_WPG.

## <a name="see-also"></a>Consulte também
[Introdução ao &#40;desenvolvimento do SharePoint no Visual Studio&#41;](../sharepoint/getting-started-sharepoint-development-in-visual-studio.md)
