---
title: 'Como: programaticamente salvar anexos de itens de email do Outlook | Microsoft Docs'
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
- Outlook [Office development in Visual Studio], attachments
- e-mail [Office development in Visual Studio], attachments
- saving e-mail attachments
- mail items [Office development in Visual Studio], attachments
- attachments [Office development in Visual Studio]
ms.assetid: 2f05e2bb-ae4f-407c-a6da-a3b1a4c31ab3
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 50673163fdbdd1c0927f6efa56eae39e8cc2e3c8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-save-attachments-from-outlook-e-mail-items"></a>Como salvar anexos de itens de email do Outlook programaticamente
  Este exemplo salva anexos de email para uma pasta especificada quando o email é recebido na caixa de entrada.  
  
> [!IMPORTANT]  
>  Este exemplo funciona apenas se você adicionar uma pasta chamada **TestFileSave** na raiz do diretório C.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[Trin_OL_SaveAttachments#1](../vsto/codesnippet/CSharp/Trin_OL_SaveAttachments/thisaddin.cs#1)]  
  
## <a name="see-also"></a>Consulte também  
 [Trabalhando com itens de email](../vsto/working-with-mail-items.md)   
 [Como: recuperar programaticamente uma pasta por nome](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)   
 [Como: executar ações programaticamente quando é recebida uma mensagem de email](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)   
 [Como pesquisar em uma pasta específica de forma programática](../vsto/how-to-programmatically-search-within-a-specific-folder.md)  
  
  