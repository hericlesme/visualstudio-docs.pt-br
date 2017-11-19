---
title: "Propriedade Length (função) (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: length Property
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Length property
- length property (function)
ms.assetid: fdc8e1c9-0dac-4e1b-ba3a-11073c37ef63
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4fbd0334c18da2c6ef8de8366555d79f791e6855
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="length-property-function-javascript"></a>Propriedade length (função) (JavaScript)
Obtém o número de argumentos definidos para uma função.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
functionName.length  
```  
  
## <a name="remarks"></a>Comentários  
 Obrigatório *functionName* é o nome da função.  
  
 O **comprimento** propriedade de uma função é inicializada pelo mecanismo de script para o número de argumentos na definição da função quando uma instância da função é criada.  
  
 O que acontece quando uma função é chamada com um número de argumentos diferentes do valor de seu **comprimento** propriedade depende da função.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso do **comprimento** propriedade:  
  
```JavaScript  
function ArgTest(a, b){  
    var s = "";  
  
    s += "Expected Arguments: " + ArgTest.length;  
    s += "<br />";  
    s += "Passed Arguments: " + arguments.length;  
  
    return s;  
}  
  
document.write(ArgTest(1, 2));  
  
// Output:   
// Expected Arguments: 2  
// Passed Arguments: 2  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Propriedade arguments (função)](../../javascript/reference/arguments-property-function-javascript.md)   
 [Propriedade Length (matriz)](../../javascript/reference/length-property-array-javascript.md)   
 [Propriedade length (String)](../../javascript/reference/length-property-string-javascript.md)