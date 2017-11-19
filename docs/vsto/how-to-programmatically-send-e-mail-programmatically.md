---
title: 'Como: enviar email | Microsoft Docs'
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
- mail items [Office development in Visual Studio], sending e-mail
- Outlook [Office development in Visual Studio], creating e-mail
- Outlook [Office development in Visual Studio], sending e-mail
- e-mail [Office development in Visual Studio], sending
ms.assetid: 4fa0e1b5-2caf-4a11-8626-df643b23f5f0
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 98b0eefafa86fdaf8f7a664ac75a2f7c71a43549
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-send-e-mail"></a>Como: enviar email  
  Este exemplo envia uma mensagem de email para contatos que têm o nome de domínio **example.com** em seus endereços de email.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[Trin_OL_ProgramEmail#1](../vsto/codesnippet/CSharp/Trin_OL_ProgramEMail/thisaddin.cs#1)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Contatos que têm o nome de domínio **example.com** em seus endereços de email.  
  
## <a name="robust-programming"></a>Programação robusta  
 Não remova o código de filtro que procura o nome de domínio **example.com**. Sua solução enviará mensagens de email para todos os seus contatos, se você remover o filtro.  
  
## <a name="see-also"></a>Consulte também  
 [Trabalhando com itens de email](../vsto/working-with-mail-items.md)   
 [Como: criar programaticamente um Item de email](../vsto/how-to-programmatically-create-an-e-mail-item.md)   
 [Como: acessar programaticamente os contatos do Outlook](../vsto/how-to-programmatically-access-outlook-contacts.md)   
 [Como executar ações de forma programática quando uma mensagem de email é recebida](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)  
  
  