---
title: 'Como: associar programaticamente uma página da Web uma pasta do Outlook | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- folders [Office development in Visual Studio], Web pages and
- Outlook [Office development in Visual Studio], Web pages attached to folders
- Web pages [Office development in Visual Studio], Outlook folders
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 5495066b05ded6fc49dfe92ed489932d8c75b24d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-associate-a-web-page-with-an-outlook-folder"></a>Como associar uma página da Web a uma pasta do Outlook programaticamente
  Este exemplo verifica se uma pasta chamada `HtmlView` no Microsoft Office Outlook. Se a pasta não existir, o código cria a pasta e atribui uma página da Web para ele. Se a pasta existir, o código exibe o conteúdo da pasta.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[Trin_OL_HTMLFolder#1](../vsto/codesnippet/CSharp/Trin_OL_HTMLFolder/thisaddin.cs#1)]  
  
## <a name="see-also"></a>Consulte também  
 [Trabalhando com pastas](../vsto/working-with-folders.md)   
 [Como: recuperar programaticamente uma pasta por nome](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)   
 [Como criar itens de pasta personalizados de forma programática](../vsto/how-to-programmatically-create-custom-folder-items.md)  
  
  