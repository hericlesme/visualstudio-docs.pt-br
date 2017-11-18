---
title: "Como depurar funções de API do Windows? | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.api
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], Windows API functions
- NT symbols and debugging Windows API functions
- Windows API functions, debugging
- Windows API, debugging API functions
- APIs, debugging
ms.assetid: 7c126f57-62ab-4d94-9805-632d696ba1f0
caps.latest.revision: "20"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a4d1675ecda24413fb43f92848f3c358a20a9a71
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="how-can-i-debug-windows-api-functions"></a>Como depurar funções de API do Windows?
Se você desejar depurar uma função de API do Windows que tenha os símbolos do NT carregados, deverá fazer o seguinte.  
  
### <a name="to-set-a-breakpoint-on-a-windows-api-function-with-nt-symbols-loaded"></a>Para definir um ponto de interrupção em uma função de API do Windows com os símbolos do NT carregados  
  
-   Digite o nome da função junto com o nome da DLL em que a função reside. No código de 32 bits, use a forma decorada do nome da função. Para definir um ponto de interrupção em **MessageBeep**, por exemplo, você deve inserir o seguinte.  
  
    ```  
    {,,USER32.DLL}_MessageBeep@4  
    ```  
  
     Para obter o nome decorado, consulte [exibindo nomes decorados](http://msdn.microsoft.com/en-us/f79e2717-a4db-4d12-a689-69830cce2be0).  
  
## <a name="see-also"></a>Consulte também  
 [Perguntas frequentes de código nativo de depuração](../debugger/debugging-native-code-faqs.md)   
 [Depurando código nativo](../debugger/debugging-native-code.md)