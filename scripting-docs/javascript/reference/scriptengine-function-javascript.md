---
title: "Função ScriptEngine (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ScriptEngine
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- ScriptEngine function
ms.assetid: 65674b2b-d2c2-4493-99b3-f0d20fda8249
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d441fcce065677f7b673a9979acff9cf9aa2ce90
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="scriptengine-function-javascript"></a>Função ScriptEngine (JavaScript)
Obtém o nome da linguagem de script em uso.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
ScriptEngine()  
```  
  
## <a name="remarks"></a>Comentários  
 A função `ScriptEngine` retorna "JScript", que indica que [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] é o mecanismo de script atual.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso da função `ScriptEngine`:  
  
```JavaScript  
if (window.ScriptEngine) {  
    console.log(window.ScriptEngine());  
}  
  
// Output: JScript  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Função ScriptEngineBuildVersion](../../javascript/reference/scriptenginebuildversion-function-javascript.md)   
 [Função ScriptEngineMajorVersion](../../javascript/reference/scriptenginemajorversion-function-javascript.md)   
 [Função ScriptEngineMinorVersion](../../javascript/reference/scriptengineminorversion-function-javascript.md)