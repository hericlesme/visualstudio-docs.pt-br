---
title: Função ScriptEngineMajorVersion (JavaScript) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- ScriptEngineMajorVersion
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- ScriptEngineMajorVersion function
ms.assetid: 3e251bce-1e14-4cb5-b79f-53845d1920fd
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 815e6fb92744fc2145cae2cbaa6a5574c3ea3ecc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639676"
---
# <a name="scriptenginemajorversion-function-javascript"></a>Função ScriptEngineMajorVersion (JavaScript)
Obtém o número da versão principal do mecanismo de script utilizado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
ScriptEngineMajorVersion()  
```  
  
## <a name="remarks"></a>Comentários  
 O valor retornado corresponde diretamente às informações de versão contidas na biblioteca de vínculo dinâmico (DLL) para a linguagem em uso.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso da função `ScriptEngineMajorVersion`:  
  
```JavaScript  
if (window.ScriptEngineMajorVersion) {  
    console.log(window.ScriptEngine());   
}  
  
Output: <current major version>  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Função ScriptEngine](../../javascript/reference/scriptengine-function-javascript.md)   
 [Função ScriptEngineBuildVersion](../../javascript/reference/scriptenginebuildversion-function-javascript.md)   
 [Função ScriptEngineMinorVersion](../../javascript/reference/scriptengineminorversion-function-javascript.md)