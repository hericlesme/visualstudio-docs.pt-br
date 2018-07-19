---
title: 'Como: criar um controle de usuário para uma página de aplicativo do SharePoint ou Web Part | Microsoft Docs'
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
- user controls [SharePoint development in Visual Studio], creating
- user controls [SharePoint development in Visual Studio], adding
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 98333049f711e9d28d7adb1ad0c17cfc8514e4ad
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37118344"
---
# <a name="how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part"></a>Como: criar um controle de usuário para uma página ou web part de aplicativo do SharePoint
  Você pode criar controles de usuário personalizados que fornecem funcionalidade personalizada para sua solução do SharePoint, e você pode reutilizar essa funcionalidade dentro de seu projeto. Você pode incluir os controles de usuário em uma web part ou um aplicativo de página, adicione outros controles do ASP.NET e controles do SharePoint e definir propriedades e métodos para o controle. Para obter mais informações sobre controles de usuário, consulte [criem controles reutilizáveis para web parts ou páginas de aplicativo](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md) e [controles de usuário e controles de servidor no SharePoint](http://blogs.msdn.com/b/kaevans/archive/2011/04/28/user-controls-and-server-controls-in-sharepoint.aspx).  
  
### <a name="to-create-a-user-control-for-sharepoint"></a>Para criar um controle de usuário para o SharePoint  
  
1.  No Visual Studio, abra ou crie um projeto do SharePoint.  
  
     Ver [SharePoint modelos de item de projeto e projeto](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
2.  Na **Gerenciador de soluções**, escolha o nó do projeto.  
  
3.  Na barra de menus, escolha **Projeto** > **Adicionar Novo Item**.  
  
     A caixa de diálogo **Adicionar Novo Item** é aberta.  
  
4.  No **Installed** painel, escolha o **Office/SharePoint** nó.  
  
5.  Na lista de modelos do SharePoint, escolha **controle de usuário (somente solução de Farm)**.  
  
    > [!NOTE]  
    >  Controles de usuário funcionam somente em soluções de farm.  
  
6.  No **nome** caixa, especifique um nome para o controle de usuário e, em seguida, escolha o **Add** botão.  
  
     Visual Studio adiciona várias pastas e arquivos ao seu projeto. Para obter mais informações sobre esses arquivos, consulte [criem controles reutilizáveis para web parts ou páginas de aplicativo](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md).  
  
     Por padrão, o arquivo de controle de usuário aparece na **origem** modo de exibição de designer do Visual Web Developer. Nessa exibição, você pode editar a marcação XML do controle. Você pode alternar para **Design** exibir se você quiser criar controle visualmente arrastando controles das **caixa de ferramentas**. Ver [exibição de Design, o Designer de página da Web](http://msdn.microsoft.com/en-us/d8f2270a-357d-40a4-9b39-1a3f2366216d).  
  
7.  Se você quiser manipular eventos que ocorrem no controle, adicione código ao arquivo de código do controle de usuário.  
  
     Esse arquivo aparece na **Gerenciador de soluções** sob o arquivo de controle de usuário e tem um *. CS* ou *. vb* extensão, dependendo do idioma do projeto.  
  
## <a name="see-also"></a>Consulte também
 [Criar controles reutilizáveis para web parts ou páginas de aplicativo](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)   
 [Criar páginas de aplicativo do SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)   
 [Criar web parts para SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)  
  
