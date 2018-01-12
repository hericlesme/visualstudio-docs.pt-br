---
title: "Como: criar uma página de aplicativo | Microsoft Docs"
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
- application pages [SharePoint development in Visual Studio], adding
- application pages [SharePoint development in Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 9429f2834997ce5ad2c3359fb04c164995dd2e12
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-create-an-application-page"></a>Como criar uma página de aplicativo
  Você pode criar uma página da web para um ou mais sites do SharePoint. No SharePoint, essas páginas são chamadas de páginas do aplicativo. Ao contrário de uma página do site, uma página de aplicativo contém código que é executado por trás da página. Para obter mais informações, consulte [criando páginas de aplicativo para o SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).  
  
### <a name="to-create-an-application-page"></a>Para criar uma página de aplicativo  
  
1.  No Visual Studio, abra ou crie um projeto do SharePoint.  
  
     Para obter mais informações, consulte [projeto do SharePoint e modelos de Item de projeto](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
2.  Em **Solution Explorer**, escolha o nó do projeto.  
  
3.  Na barra de menus, escolha **projeto**, **Adicionar Novo Item**.  
  
4.  No **Adicionar Novo Item** caixa de diálogo caixa, expanda o **SharePoint** nó e, em seguida, escolha o **2010** item.  
  
5.  Na lista de modelos do SharePoint, escolha **página de aplicativo**.  
  
6.  No **nome** caixa, especifique um nome para a página de aplicativo e, em seguida, escolha o **adicionar** botão.  
  
     O Visual Studio adiciona vários arquivos e pastas no seu projeto. Para obter mais informações sobre esses arquivos, consulte [criando páginas de aplicativo para o SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).  
  
     No **fonte** visualização do designer Visual Web Developer, o arquivo de página ASP.NET é exibida. Você pode criar a página adicionando controles a partir de **caixa de ferramentas** e colocando-os em espaços reservados de conteúdo. Para obter mais informações, consulte [exibição da fonte, o Designer de página da Web](http://msdn.microsoft.com/en-us/5911396b-fe51-4150-9ff1-b085f812862f).  
  
7.  Se você desejar tratar eventos de controle, adicione código ao arquivo de código para a página de aplicativo.  
  
     O arquivo de código será exibido se você expandir o nó para o arquivo de página ASP.NET e tem uma extensão. cs ou. vb, dependendo do idioma do projeto. Para obter um exemplo de ponta a ponta de como criar uma página de aplicativo, consulte [passo a passo: Criando uma página de aplicativo do SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md).  
  
## <a name="see-also"></a>Consulte também  
 [Criando páginas de aplicativo do SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)   
 [Instruções passo a passo: criando uma página de aplicativo do SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md)  
  
  