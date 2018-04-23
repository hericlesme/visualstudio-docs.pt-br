---
title: 'Como: criar uma Web Part do SharePoint | Microsoft Docs'
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
- Web Parts [SharePoint development in Visual Studio], adding
- Web Parts [SharePoint development in Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 708a1b1a0b64dbed5c02e6fcaf7da9e8892f5664
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-a-sharepoint-web-part"></a>Como criar um Web Part do SharePoint
  Você pode criar e personalizar uma web part, adicionando um **Web Part** item a qualquer projeto do SharePoint e, em seguida, editando o arquivo de código para a web part ou usando um designer. Para obter mais informações, consulte [como: criar uma Web Part do SharePoint usando um Designer](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md).  
  
### <a name="to-create-a-sharepoint-web-part"></a>Para criar uma Web Part do SharePoint  
  
1.  Crie ou abra um projeto do SharePoint.  
  
     Para obter mais informações, consulte [projeto do SharePoint e modelos de Item de projeto](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
2.  Escolha o nó do projeto do SharePoint no **Solution Explorer** e, em seguida, escolha **projeto**, **Adicionar Novo Item**.  
  
3.  No **Adicionar Novo Item** caixa de diálogo caixa, expanda o **SharePoint** nó e, em seguida, escolha o **2010** nó.  
  
4.  Na lista de modelos do SharePoint, escolha **Web Part**.  
  
5.  No **nome** caixa, especifique um nome para a web part e, em seguida, escolha o **adicionar** botão.  
  
     A web part aparece em **Gerenciador de soluções**. Para obter mais informações sobre os arquivos que inclua uma web part, consulte [criando Web Parts para SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md).  
  
6.  Em **Solution Explorer**, abra o arquivo de código para a web part que você acabou de criar.  
  
     Por exemplo, se o nome da sua web part é WebPart1, abra WebPart1.vb (no Visual Basic) ou Webpart1 (em c#).  
  
7.  No arquivo de código, adicione controles para o <xref:System.Web.UI.Control.CreateChildControls%2A> método.  
  
     Para obter um exemplo, consulte [passo a passo: Criando um Web Part do SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md).  
  
## <a name="see-also"></a>Consulte também  
 [Criando Web Parts do SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [Como: criar uma Web Part do SharePoint usando um Designer](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)   
 [Passo a passo: Criando um Web Part do SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)   
 [Instruções passo a passo: criando um Web Part para o SharePoint usando um designer](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)  
  
  