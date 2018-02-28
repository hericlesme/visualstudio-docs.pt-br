---
title: Operador instanceof (JavaScript) | Microsoft Docs
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
- instanceof_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- instanceOf operator
ms.assetid: 92467bdc-56b5-42dc-adbd-a219776454d2
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b2124fe815c89c3c157be3ea729fa7edb9d96b39
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/13/2018
---
# <a name="instanceof-operator-javascript"></a>Operador instanceof (JavaScript)
Retorna um valor booliano que indica se um objeto é ou não uma instância de uma classe específica.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
result = object instanceof class  
```  
  
## <a name="parameters"></a>Parâmetros  
 `result`  
 Necessário. Qualquer variável.  
  
 `object`  
 Necessário. Qualquer expressão de objeto.  
  
 `class`  
 Necessário. Qualquer classe de objeto definida.  
  
## <a name="remarks"></a>Comentários  
 O `instanceof` operador retorna `true` se `object` é uma instância de `class`. Ele retorna `true` se `class` está presente na cadeia de protótipo do objeto. Ele retorna `false` se `object` não é uma instância de `class`, ou se `object` é `null`.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar o `instanceof` operador.  
  
```JavaScript  
function objTest(obj){  
    var i, t, s = "";  
    t = new Array();  
    t["Date"] = Date;  
    t["Object"] = Object;  
    t["Array"] = Array;  
        for (i in t){  
            if (obj instanceof t[i]) {   
                s += "obj is an instance of " + i + "<br/>";  
            }  
            else {  
                s += "obj is not an instance of " + i + "<br/>";  
        }  
    }  
    return(s);  
}  
  
var obj = new Date();  
document.write(objTest(obj));  
  
// Output:   
// obj is an instance of Date  
// obj is an instance of Object  
// obj is not an instance of Array  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Precedência do operador](../../javascript/operator-subtractprecedence-javascript.md)   
 [Resumo de operador (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)