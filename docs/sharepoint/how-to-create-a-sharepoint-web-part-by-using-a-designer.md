---
title: 'Como: criar uma Web Part do SharePoint usando um Designer | Microsoft Docs'
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
- Web Parts [SharePoint development in Visual Studio], designer
- Web Parts [SharePoint development in Visual Studio], adding
- Web Parts [SharePoint development in Visual Studio], creating
ms.assetid: 6b88f3ef-02ff-4135-80ff-b4acacf8c695
caps.latest.revision: "26"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 1b993512350e6bd27d0dce8ef359bc33fccde5ff
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-sharepoint-web-part-by-using-a-designer"></a>Como criar um Web Part do SharePoint usando um designer
  Você pode criar uma web part, adicionando um **Web Part Visual** item a qualquer projeto do SharePoint. Isso abre o designer Visual Web Developer no Visual Studio, onde você pode adicionar controles e código para a web part. Partes do Visual web funcionam da mesma maneira como partes de web. A única diferença é que você cria o visual web parts no designer do Visual Web Developer.  
  
### <a name="to-create-a-project-for-visual-web-parts"></a>Para criar um projeto para o visual web parts  
  
1.  Na barra de menus, escolha **Arquivo**, **Novo**, **Projeto**.  
  
     A caixa de diálogo **Novo Projeto** é aberta.  
  
2.  No **novo projeto** caixa de diálogo, em um **Visual C#** ou **Visual Basic**, expanda o **Office/SharePoint** nó e, em seguida, escolha o **soluções do SharePoint** categoria.  
  
3.  Na lista de modelos de projeto, escolha **SharePoint 2013 - Web Part Visual**e, em seguida, escolha o **Okey** botão.  
  
     O **Assistente de personalização do SharePoint** é exibida.  
  
4.  Sobre o **especificar o nível de site e segurança de depuração** página, especifique a URL de um site do SharePoint que está no computador local, e, em seguida, escolha o **concluir** botão.  
  
     Em **Solution Explorer**, uma web part é exibida. Depois de criar a web part no designer do Visual Web Developer, você poderá testá-lo no site que você especificar.  
  
### <a name="to-add-a-visual-web-part-to-an-existing-sharepoint-project"></a>Para adicionar uma web part visual para um projeto existente do SharePoint  
  
1.  Na barra de menus, escolha **projeto**, **Adicionar Novo Item**.  
  
2.  No **Adicionar Novo Item** caixa de diálogo caixa, escolha o **Office/SharePoint** nó.  
  
3.  Na lista de modelos de projeto, escolha **Web Part Visual**, nomeie-o e, em seguida, escolha o **adicionar** botão.  
  
     Em **Solution Explorer**, a web part é exibida. Depois de criar a web part no designer do Visual Web Developer, você poderá testá-lo no site que você especificar.  
  
## <a name="see-also"></a>Consulte também  
 [Criando Web Parts do SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [Como: criar uma Web Part do SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md)   
 [Passo a passo: Criando um Web Part do SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)   
 [Instruções passo a passo: criando um Web Part para o SharePoint usando um designer](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)  
  
  