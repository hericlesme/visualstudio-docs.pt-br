---
title: "Função ScriptEngineMinorVersion (JavaScript) | Microsoft Docs"
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
- ScriptEngineMinorVersion
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- ScriptEngineMinorVersion function
ms.assetid: caa506a5-e61d-4b2a-8b83-83d56a2f26cd
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b1be01c0ee10cac1c68d4750455151032a59a8e6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="scriptengineminorversion-function-javascript"></a>Função ScriptEngineMinorVersion (JavaScript)
Obtém o menor número de versão do mecanismo de script utilizado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
ScriptEngineMinorVersion()  
```  
  
## <a name="remarks"></a>Comentários  
 O valor retornado corresponde diretamente às informações de versão contidas na biblioteca de vínculo dinâmico (DLL) para a linguagem em uso.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso da função `ScriptEngineMinorVersion`.  
  
```JavaScript  
if (window.ScriptEngineMinorVersion) {  
    console.log(window.ScriptEngineMinorVersion());  
}  
  
//Output: <current minor version>  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Função ScriptEngine](../../javascript/reference/scriptengine-function-javascript.md)   
 [Função ScriptEngineBuildVersion](../../javascript/reference/scriptenginebuildversion-function-javascript.md)   
 [Função ScriptEngineMajorVersion](../../javascript/reference/scriptenginemajorversion-function-javascript.md)