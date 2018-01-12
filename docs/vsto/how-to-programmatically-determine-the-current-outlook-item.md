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
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: de17e299e98a46a82547bc38dfecd17a9f5aea58
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
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
  
  