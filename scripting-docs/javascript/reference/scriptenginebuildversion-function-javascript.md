---
title: "Função ScriptEngineBuildVersion (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: ScriptEngineBuildVersion
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: ScriptEngineBuildVersion function
ms.assetid: 7e255030-b0a3-420b-9c96-bb3e93c9333f
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fd458d43bebfb0d0e0b2cb6bebb483c22a60b4f0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="scriptenginebuildversion-function-javascript"></a>Função ScriptEngineBuildVersion (JavaScript)
Obtém o número de versão do build do mecanismo de script utilizado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
ScriptEngineBuildVersion()  
```  
  
## <a name="remarks"></a>Comentários  
 O valor retornado corresponde diretamente às informações de versão contidas na biblioteca de vínculo dinâmico (DLL) para a linguagem em uso.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso da função `ScriptEngineBuildVersion`:  
  
```JavaScript  
if(window.ScriptEngineBuildVersion) {  
    console.log(window.ScriptEngineBuildVersion());  
}  
  
// Output: <current build version>  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Função ScriptEngine](../../javascript/reference/scriptengine-function-javascript.md)   
 [Função ScriptEngineMajorVersion](../../javascript/reference/scriptenginemajorversion-function-javascript.md)   
 [Função ScriptEngineMinorVersion](../../javascript/reference/scriptengineminorversion-function-javascript.md)