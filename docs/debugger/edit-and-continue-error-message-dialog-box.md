---
title: "Editar e continuar a caixa de diálogo de mensagem de erro | Microsoft Docs"
ms.custom: 
ms.date: 06/22/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.debug.ENC.SupportedButNotAvaiable
- vs.debug.ENC.CannotEditWhileException
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords: Edit and Continue Error Message dialog box
ms.assetid: f98c91c0-447a-4533-85b6-87170a0dc4c3
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 21d72c5bb4bacaed0324d688d96c663e3153b6a1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="edit-and-continue-error-message-dialog-box"></a>Caixa de diálogo Mensagem de Erro de Editar e Continuar
Essa caixa de diálogo aparece quando você estiver depurando em uma linguagem que suporta editar e continuar, mas **editar e continuar** não está disponível para o tipo de alterações de código que você fez. A mensagem de erro dentro da caixa fornece uma explicação mais detalhada. As possíveis razões para ver essa caixa de diálogo incluem:  

-   Você tentou editar o código do SQL Server.

-   Você tentou editar o código otimizado. (Talvez seja necessário alternar de uma compilação de versão para uma compilação de depuração.)

-   Você tentou editar código enquanto ele estava em execução (em vez de enquanto está em pausa no depurador). Tente [definindo um ponto de interrupção](../debugger/using-breakpoints.md) e edição do código enquanto está em pausa.

-   Você tentou editar o código gerenciado quando a depuração não gerenciada foi habilitada. Editar e continuar não funciona com [depuração de modo misto](../debugger/how-to-debug-in-mixed-mode.md).

-   Você fez um código de alteração que não é suportado pelo Edit and Continue em sua linguagem de programação. Para obter mais informações, consulte Tópicos para alterações de código sem suporte em [c#](../debugger/supported-code-changes-csharp.md), [Visual Basic](../debugger/unsupported-edits-in-visual-basic-edit-and-continue.md), e [C++](../debugger/supported-code-changes-cpp.md).
  
-   Você tentou editar o código em um programa que você anexou em vez de a partir de **depurar** menu.  
  
-   Você tentou editar o código durante a depuração de um Dr. Watson.  
  
-   Você tentou editar código depois que ocorreu uma exceção sem tratamento e a opção "**desenrolar a pilha de chamadas em exceções não tratadas**" não foi selecionada.  
  
-   Você tentou editar o código ao depurar um aplicativo inserido de tempo de execução.
  
-   Você tentou editar o código gerenciado usando a versão do .NET Framework 4.5.1 antes do e o destino é um aplicativo de 64 bits. Se você desejar usar Editar e Continuar, deve definir o destino como x86. (*projectname* **propriedades**, **compilar** guia **compilador avançadas** configuração.).  
  
-   Você tentou editar o código em um assembly que foi modificado durante a depuração e foi recarregado.  
  
-   Você tentou editar o código em um assembly que não foi carregado.  
  
-   Você iniciou a depuração de uma versão antiga do aplicativo (já que a nova versão tem erros de compilação).
  
## <a name="uielement-list"></a>Lista UIElement  
 **OKEY**  
 Saia da caixa de diálogo e cancele a tentativa de edição imediatamente anterior.  
  
## <a name="see-also"></a>Consulte também  
 [C++ Edit e Continue blog post](https://blogs.msdn.microsoft.com/vcblog/2016/07/01/c-edit-and-continue-in-visual-studio-2015-update-3/)  
 [Alterações de código com suporte (C++)](../debugger/supported-code-changes-cpp.md)