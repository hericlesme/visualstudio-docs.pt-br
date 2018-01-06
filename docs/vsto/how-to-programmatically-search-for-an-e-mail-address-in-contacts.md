---
title: "Como: procurar um endereço de email em contatos programaticamente | Microsoft Docs"
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
- e-mail [Office development in Visual Studio], searching
- contacts [Office development in Visual Studio], searching
- searching contacts
ms.assetid: e973a407-8b94-45c7-acdf-fe330115fb33
caps.latest.revision: "25"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 57c0cac0dd2b22b38284caec0a2bfb40d6e5b101
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-search-for-an-e-mail-address-in-contacts"></a>Como procurar um endereço de email em Contatos programaticamente
  Este exemplo procura uma pasta de contato para contatos que têm o nome de domínio **example.com** em seus endereços de email.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[Trin_OL_SearchEmail#1](../vsto/codesnippet/CSharp/Trin_OL_SearchEmail/thisaddin.cs#1)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Contatos que têm o nome de domínio **example.com** em seus endereços de email (por exemplo, `somebody@example.com`), e que têm nomes e sobrenomes.  
  
## <a name="see-also"></a>Consulte também  
 [Trabalhando com itens de contato](../vsto/working-with-contact-items.md)   
 [Como: enviar email](../vsto/how-to-programmatically-send-e-mail-programmatically.md)   
 [Como: acessar programaticamente os contatos do Outlook](../vsto/how-to-programmatically-access-outlook-contacts.md)   
 [Como adicionar uma entrada a contatos do Outlook de forma programática](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md)  
  
  