---
title: "Como: programaticamente pesquisar em uma pasta específica | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook folders [Office development in Visual Studio], searching
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 71b9da77857bb82a27f6bd6ae057a1df1fca8a1d
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-search-within-a-specific-folder"></a>Como pesquisar em uma pasta específica programaticamente
  Este exemplo de código usa o `Find` e `FindNext` métodos para pesquisar texto no campo assunto de mensagens de email que estão no **caixa de entrada**. Esse método usa um filtro de cadeia de caracteres para verificar a letra T como a letra inicial do `Subject` texto.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[Trin_OL_SearchFolder#1](../vsto/codesnippet/CSharp/Trin_OL_SearchFolder/thisaddin.cs#1)]  
  
## <a name="see-also"></a>Consulte também  
 [Trabalhando com pastas](../vsto/working-with-folders.md)   
 [Visão geral de modelo de objeto do Outlook](../vsto/outlook-object-model-overview.md)   
 [Como recuperar uma pasta por nome de forma programática](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)  
  
  