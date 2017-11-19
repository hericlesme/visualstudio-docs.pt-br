---
title: Editar e continuar (Visual Basic) | Microsoft Docs
ms.custom: 
ms.date: 10/11/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue, 64-bit
- Edit and Continue [Visual Basic]
- debugging [Visual Basic], Edit and Continue
- Visual Basic, Edit and Continue
- 64-bit Edit and Continue
ms.assetid: 7e90f34f-e699-45ab-a4c9-a4b527c498c8
caps.latest.revision: "40"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c3dc1b7e6eee583494070cc9ebb151181dc805da
ms.sourcegitcommit: 26419ab0cccdc30d279c32d6a841758cfa903806
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/11/2017
---
# <a name="edit-and-continue-visual-basic"></a>Editar e Continuar (Visual Basic)
Editar e Continuar são um recurso para depuração do [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] que permite alterar seu código durante a execução em modo de interrupção. Depois que as edições do código tiverem sido aplicadas, você poderá retomar a execução de código com as novas edições no lugar e visualizar o efeito.  
  
 Você pode usar o recurso Editar e Continuar sempre que entrar no modo de Interrupção. No modo de interrupção, o ponteiro de instrução, uma seta amarela na janela de origem, aponta para a linha que contém uma instrução executável em um corpo de método ou propriedade que será executado Avançar.

 Editar e Continuar dá suporte à maioria das alterações que você talvez queira fazer durante uma sessão de depuração, mas há algumas exceções. Para obter mais informações, consulte [suporte para alterações de código (c# e Visual Basic)](../debugger/supported-code-changes-csharp.md).   
  
 Quando você faz uma edição não autorizada, a alteração será marcada com um sublinhado ondulado roxo e uma tarefa será exibida na Lista de Tarefas. Você deve desfazer uma edição não autorizada se quiser continuar usando Editar e Continuar. Certas edições não autorizadas podem ser permitidas se forem feitas fora de Editar e Continuar. Se você quiser reter os resultados de uma edição não autorizada, deverá parar de depurar e reiniciar o aplicativo.  
  
 Editar e continuar há suporte para aplicativos UWP para Windows 10 e x86 e x64 aplicativos para o .NET Framework 4.6 desktop ou versões posteriores (.NET Framework é apenas uma versão de área de trabalho).

 > [!NOTE]
 > Plataformas e aplicativos sem suporte incluem ASP.NET 5, emulador Silverlight 5, Windows Phone e Windows Phone e Windows 8.1.
  
 Editar e continuar não é suportado quando você inicia a depuração usando **anexar ao processo**. Editar e continuar não há suporte para o código otimizado ou misto código gerenciado e nativo. Para obter mais informações, consulte [suporte para alterações de código (c# e Visual Basic](../debugger/supported-code-changes-csharp.md).
  
 Os tópicos desta seção fornecem detalhes adicionais sobre como usar esse recurso e que tipos de alterações não são permitidas.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Como aplicar edições no modo de interrupção com Editar e Continuar](../debugger/how-to-apply-edits-in-break-mode-with-edit-and-continue.md)  
 Explica como aplicar edições do código no modo de Interrupção.  
  
 [Alterações de código suportadas (c# e Visual Basic](../debugger/supported-code-changes-csharp.md)   
 Descreve quais tipos de edições não podem ser executadas em Editar e Continuar do [!INCLUDE[vb_current_short](../debugger/includes/vb_current_short_md.md)].  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Editar e continuar](../debugger/edit-and-continue.md)  
 Fornece uma lista de tópicos em Editar e Continuar.