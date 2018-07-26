---
title: Enviar mensagens de diagnóstico para a janela de saída | Microsoft Docs
ms.custom: ''
ms.date: 04/25/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- diagnostic messages [C#]
- System.Diagnostics.Debug class, Output window
- messages, diagnostic
- Debug.Print replacements
- diagnosis
- Output window, diagnostic messages
- System.Diagnostics.Trace class, Output window
- Trace class, diagnostic messages
- diagnostics
- debugger, Output window
- debugging [Visual Studio], diagnostic messages in Output window
- Debug class
ms.assetid: 386e9524-be17-4573-83fb-4f7c5cae0be0
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 27cec31b775ba5f8d201c81cbd65f5b161353986
ms.sourcegitcommit: 71b307ce86c4079cc7ad686d8d5f96a6a123aadd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/25/2018
ms.locfileid: "39252291"
---
# <a name="send-diagnostic-messages-to-the-output-window"></a>Enviar mensagens de diagnóstico para a janela de saída
Você pode escrever mensagens em tempo de execução para o **saída** janela usando o <xref:System.Diagnostics.Debug> classe ou o <xref:System.Diagnostics.Trace> classe, que fazem parte do <xref:System.Diagnostics> biblioteca de classes. Use o <xref:System.Diagnostics.Debug> classe se apenas de saída em de *depurar* versão do seu programa. Use o <xref:System.Diagnostics.Trace> classe se você quiser que a saída em ambos os *depurar* e *versão* versões.  
  
## <a name="output-methods"></a>Métodos de saída  
 As classes <xref:System.Diagnostics.Trace> e <xref:System.Diagnostics.Debug> fornecem os seguintes métodos de saída:  
  
-   Vários métodos `Write`, os quais geram informações sem interromper a execução. Esses métodos substituem o método `Debug.Print` usado em versões anteriores do Visual Basic.  
  
-   Métodos <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> e <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName>, que interrompem informações de execução e de saída se uma condição especificada falhar. Por padrão, o método `Assert` exibe informações em uma caixa de diálogo. Para obter mais informações, consulte [asserções em código gerenciado](../debugger/assertions-in-managed-code.md).  
  
-   Os métodos <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=fullName> e <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=fullName>, que sempre interrompem informações de execução e de saída. Por padrão, os métodos `Fail` exibem informações em uma caixa de diálogo.  
  
 Além do programa fora do seu aplicativo, o **saída** janela pode exibir as informações sobre:  
  
-   Módulos que o depurador carregou ou descarregou.  
  
-   Exceções lançadas.  
  
-   Processos encerrados.  
  
-   Threads encerrados.  
  
## <a name="see-also"></a>Consulte também  
 [Segurança do depurador](../debugger/debugger-security.md)   
 [Janela de Saída](../ide/reference/output-window.md)   
 [Rastreando e instrumentando aplicativos](/dotnet/framework/debug-trace-profile/tracing-and-instrumenting-applications)  
 [Tipos de projeto do C#, F# e Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Depurando código gerenciado](../debugger/debugging-managed-code.md)
