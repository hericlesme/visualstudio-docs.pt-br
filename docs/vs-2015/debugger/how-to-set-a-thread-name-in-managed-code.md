---
title: 'Como: definir um nome de Thread em código gerenciado | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Thread.Name property
- threading [Visual Studio], names
- thread names
- debugging [Visual Studio], threads
ms.assetid: c0c4d74a-0314-4b71-81c9-b0b019347ab8
caps.latest.revision: 31
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0175bee3280f3ecfdb49fc280007810d4e1c2860
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47473263"
---
# <a name="how-to-set-a-thread-name-in-managed-code"></a>Como definir um nome de thread no código gerenciado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [como: definir um nome de Thread em código gerenciado](https://docs.microsoft.com/visualstudio/debugger/how-to-set-a-thread-name-in-managed-code).  
  
A nomeação de thread é possível em qualquer edição do Visual Studio. Nomeação de thread é útil para manter o controle de threads na **Threads** janela. Porque o **Threads** janela não está disponível nas edições do Visual Studio Express, a nomeação de thread tem pouca utilidade nas edições Express.  
  
 Para definir um nome do thread no código gerenciado, use a propriedade <xref:System.Threading.Thread.Name%2A>.  
  
## <a name="example"></a>Exemplo  
  
```  
Public Class Needle  
    ' This method will be called when the thread is started.  
    Sub Baz()  
        Console.WriteLine("Needle Baz is running on another thread")  
    End Sub  
End Class  
  
Sub Main()  
    Console.WriteLine("Thread Simple Sample")  
    Dim oNeedle As New Needle()  
   ' Create a Thread object.   
    Dim oThread As New System.Threading.Thread(AddressOf oNeedle.Baz)  
    ' Set the Thread name to "MainThread".  
    oThread.Name = "MainThread"  
    ' Starting the thread invokes the ThreadStart delegate  
    oThread.Start()  
End Sub  
```  
  
## <a name="see-also"></a>Consulte também  
 [Depurar aplicativos multithread](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Como definir um nome de thread em código nativo](../debugger/how-to-set-a-thread-name-in-native-code.md)



