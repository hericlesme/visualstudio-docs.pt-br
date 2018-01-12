---
title: 'Como: mover itens programaticamente no Outlook | Microsoft Docs'
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
helpviewer_keywords: Outlook folders [Office development in Visual Studio], moving items
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 72b35bde8775a859ef15c5e18b381615974bccd7
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-move-items-in-outlook"></a>Como mover itens no Outlook programaticamente
  Este exemplo move mensagens não lidas do **caixa de entrada** para uma pasta chamada **teste**. O exemplo só move as mensagens com a palavra **teste** no `Subject` campo.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[Trin_OL_MoveItems#1](../vsto/codesnippet/CSharp/Trin_OL_MoveItems/thisaddin.cs#1)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Uma pasta de email do Outlook chamada **teste**.  
  
-   Uma mensagem que chega com a palavra **teste** no `Subject` campo.  
  
## <a name="see-also"></a>Consulte também  
 [Trabalhando com pastas](../vsto/working-with-folders.md)   
 [Como: recuperar programaticamente uma pasta por nome](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)   
 [Como: programaticamente pesquisar em uma pasta específica](../vsto/how-to-programmatically-search-within-a-specific-folder.md)   
 [Como executar ações de forma programática quando uma mensagem de email é recebida](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)  
  
  