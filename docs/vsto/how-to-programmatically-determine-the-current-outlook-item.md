---
title: 'Como: determinar o Item atual do Outlook programaticamente | Microsoft Docs'
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
helpviewer_keywords:
- mail items [Office development in Visual Studio], current
- e-mail [Office development in Visual Studio], current item
- SelectionChange event
- Outlook [Office development in Visual Studio], current item
ms.assetid: b4fb5ccd-b297-463e-9208-1fec42482531
caps.latest.revision: "28"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 112a2c1273b0087eea98736a4e47ac5de8787149
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-determine-the-current-outlook-item"></a>Como determinar o item atual do Outlook programaticamente
  Este exemplo usa o evento Explorer.SelectionChange para exibir o nome da pasta atual e algumas informações sobre o item selecionado. O código, em seguida, exibe o item selecionado.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Exemplo  
 [!code-vb[Trin_OL_CurrentItem#1](../vsto/codesnippet/VisualBasic/Trin_OL_CurrentItem/thisaddin.vb#1)]
 [!code-csharp[Trin_OL_CurrentItem#1](../vsto/codesnippet/CSharp/Trin_OL_CurrentItem/thisaddin.cs#1)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Compromisso, contatos e itens de email no Microsoft Office Outlook.  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral de modelo de objeto do Outlook](../vsto/outlook-object-model-overview.md)   
 [Como: recuperar programaticamente uma pasta por nome](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)   
 [Como pesquisar um contato específico de forma programática](../vsto/how-to-programmatically-search-for-a-specific-contact.md)  
  
  