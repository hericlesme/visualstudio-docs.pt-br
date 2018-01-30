---
title: "Como: depurar o método OnStart | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- OnStart method
- debugging [Visual Studio], Windows services
- debugging managed code, OnStart method
- debugging Windows Services applications, OnStart method
- Windows Service applications, debugging
ms.assetid: b06b5d65-424b-490f-bf58-97583cd7006a
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: bcfe3062ff0f36628016e1a9c0fc70278a5b0de7
ms.sourcegitcommit: 9a2f937e42305db6e3eaa7aadc235b0ba9aafc83
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2018
---
# <a name="how-to-debug-the-onstart-method"></a>Como depurar o método OnStart
Você pode depurar um serviço do Windows, inicie o serviço e anexar o depurador ao processo do serviço. Para obter mais informações, consulte [como: depurar aplicativos de serviço do Windows](/dotnet/framework/windows-services/how-to-debug-windows-service-applications). No entanto, para depurar o <xref:System.ServiceProcess.ServiceBase.OnStart%2A?displayProperty=fullName> método de um serviço do Windows, você deve iniciar o depurador de dentro do método.  
  
1.  Adicionar uma chamada para <xref:System.Diagnostics.Debugger.Launch%2A> no início de `OnStart()`método.  
  
    ```csharp  
    protected override void OnStart(string[] args)  
    {  
        System.Diagnostics.Debugger.Launch();  
     }  
    ```  
  
2.  Iniciar o serviço (você pode usar `net start`, ou iniciar o **serviços** janela).  
  
     Você verá uma caixa de diálogo semelhante ao seguinte:  
  
     ![OnStartDebug](../debugger/media/onstartdebug.png "OnStartDebug")  
  
3.  Selecione **Sim, depurar \<nome do serviço >.**  
  
4.  Na janela de depurador Just-in-, selecione a versão do Visual Studio que você deseja usar para depuração.  
  
     ![JustInTimeDebugger](../debugger/media/justintimedebugger.png "JustInTimeDebugger")  
  
5.  Uma nova instância do Visual Studio é iniciado e a execução é interrompida no `Debugger.Launch()` método.  
  
## <a name="see-also"></a>Consulte também  
 [Segurança do depurador](../debugger/debugger-security.md)   
 [Depurando código gerenciado](../debugger/debugging-managed-code.md)