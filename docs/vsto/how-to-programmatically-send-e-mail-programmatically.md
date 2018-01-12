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
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: f8681fecf8dc2d4c3a26aeaeb372faeb57e54094
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
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
  
  