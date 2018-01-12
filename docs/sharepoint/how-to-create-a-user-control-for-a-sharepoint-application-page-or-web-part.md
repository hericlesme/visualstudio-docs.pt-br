---
title: "Como: criar um controle de usuário para uma página de aplicativo do SharePoint ou da Web Part | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- user controls [SharePoint development in Visual Studio], creating
- user controls [SharePoint development in Visual Studio], adding
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 7fc51bae65f67a3810c6db208e5f7c6f04183c22
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part"></a>Como criar um controle de usuário para uma página de aplicativo do SharePoint ou Web Part
  Você pode criar controles de usuário personalizada que fornecem funcionalidade personalizada para sua solução do SharePoint, e você pode reutilizar essa funcionalidade em seu projeto. Você pode incluir os controles de usuário em um aplicativo ou a web part de página, adicione outros controles do ASP.NET e do SharePoint e definir propriedades e métodos para o controle. Para obter mais informações sobre controles de usuário, consulte [criação de controles de reutilizáveis para Web Parts ou páginas do aplicativo](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md) e [controles de usuário e servidor no SharePoint](http://blogs.msdn.com/b/kaevans/archive/2011/04/28/user-controls-and-server-controls-in-sharepoint.aspx).  
  
### <a name="to-create-a-user-control-for-sharepoint"></a>Para criar um controle de usuário do SharePoint  
  
1.  No Visual Studio, abra ou crie um projeto do SharePoint.  
  
     Consulte [modelos de Item de projeto do SharePoint e o projeto](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
2.  Em **Solution Explorer**, escolha o nó do projeto.  
  
3.  Na barra de menus, escolha **projeto**, **Adicionar Novo Item**.  
  
     A caixa de diálogo **Adicionar Novo Item** é aberta.  
  
4.  No **instalado** painel, escolha o **Office/SharePoint** nó.  
  
5.  Na lista de modelos do SharePoint, escolha **controle de usuário (solução de Farm somente)**.  
  
    > [!NOTE]  
    >  Controles de usuário funcionam somente em soluções de farm.  
  
6.  No **nome** caixa, especifique um nome para o controle de usuário e, em seguida, escolha o **adicionar** botão.  
  
     O Visual Studio adiciona vários arquivos e pastas no seu projeto. Para obter mais informações sobre esses arquivos, consulte [criação de controles de reutilizáveis para Web Parts ou páginas de aplicativo](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md).  
  
     Por padrão, o arquivo de controle de usuário é exibido no **fonte** visualização do designer Visual Web Developer. Nesta exibição, você pode editar a marcação XML do controle. Você pode alternar para **Design** exibir se você deseja criar o controle visualmente arrastando controles a partir de **caixa de ferramentas**. Consulte [exibição de Design, o Designer de página da Web](http://msdn.microsoft.com/en-us/d8f2270a-357d-40a4-9b39-1a3f2366216d).  
  
7.  Se você desejar tratar eventos que ocorrem no controle, adicione código ao arquivo de código do controle de usuário.  
  
     Esse arquivo é exibido no **Solution Explorer** no arquivo de controle de usuário e tem uma extensão. cs ou. vb, dependendo do idioma do projeto.  
  
## <a name="see-also"></a>Consulte também  
 [Criando controles reutilizáveis para Web Parts ou páginas de aplicativo](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)   
 [Criando páginas de aplicativo do SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)   
 [Criando Web Parts para o SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)  
  
  