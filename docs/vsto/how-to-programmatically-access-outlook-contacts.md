---
title: 'Como: acessar programaticamente os contatos do Outlook | Microsoft Docs'
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
helpviewer_keywords: contacts [Office development in Visual Studio], searching
ms.assetid: ea2297ea-6802-40e4-af1a-1e511a71ec75
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8ee2c597c1a3b6a7c068c8206a87195779877461
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-access-outlook-contacts"></a>Como acessar contatos do Outlook programaticamente
  Este exemplo localiza todos os contatos cujos sobrenomes contêm uma cadeia de caracteres de pesquisa especificada.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[Trin_OL_AccessContacts#1](../vsto/codesnippet/CSharp/Trin_OL_AccessContacts.trin_ol_accesscontacts/thisaddin.cs#1)]
 [!code-csharp[Trin_OL_AccessContacts#1](../vsto/codesnippet/CSharp/Trin_OL_AccessContacts.trin_ol_accesscontacts/thisaddin.cs#1)]
 [!code-vb[Trin_OL_AccessContacts#1](../vsto/codesnippet/VisualBasic/Trin_OL_AccessContacts/thisaddin.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Contatos cujos sobrenomes contêm a cadeia de caracteres "**Na"** (por exemplo, Tzipi Butnaru) no **contatos** pasta.  
  
## <a name="see-also"></a>Consulte também  
 [Trabalhando com itens de contato](../vsto/working-with-contact-items.md)   
 [Como: adicionar uma entrada a contatos do Outlook programaticamente](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md)   
 [Como: procurar um contato específico programaticamente](../vsto/how-to-programmatically-search-for-a-specific-contact.md)   
 [Como: procurar um endereço de email em contatos programaticamente](../vsto/how-to-programmatically-search-for-an-e-mail-address-in-contacts.md)   
 [Como excluir contatos do Outlook de forma programática](../vsto/how-to-programmatically-delete-outlook-contacts.md)  
  
  