---
title: Compartilhar o retorno de log do Unity com o VSTU | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5d71f906-6e50-4399-b59b-d38c6dfef7ee
caps.latest.revision: "2"
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload: unity
ms.openlocfilehash: 6c078affefbb24a9fbbb65c854911f4b91f12183
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="share-the-unity-log-callback-with-vstu"></a>Compartilhar o retorno de chamada de log do Unity com o VSTU
As Ferramentas do Visual Studio para Unity registram um retorno de chamada de log do Unity para transmitir seu console para o Visual Studio. Se os scripts do seu editor também registram um retorno de chamada de log do Unity, o retorno de chamada VSTU pode interferir em seu retorno de chamada. Para evitar essa possibilidade, use o evento `VisualStudioIntegration.LogCallback` para cooperar com VSTU.  

## <a name="demonstrates"></a>Demonstra  
 Como compartilhar o retorno de chamada de log do Unity criado pelas Ferramentas do Visual Studio para Unity.  

## <a name="example"></a>Exemplo  

```csharp  
using System;  

using UnityEngine;  
using UnityEditor;  

using SyntaxTree.VisualStudio.Unity.Bridge;  

[InitializeOnLoad]  
public class LogCallbackHook  
{  
    static LogCallbackHook()  
    {  
        VisualStudioIntegration.LogCallback += (string condition, string trace, LogType type) =>  
        {  
            // place code that implements your log callback here  
        };  
    }  
}  
```  

## <a name="see-also"></a>Consulte também  
 [Exemplo: geração de arquivo de projeto](../cross-platform/customize-project-files-created-by-vstu.md)
