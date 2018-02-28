---
title: Objeto arguments (JavaScript) | Microsoft Docs
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
- arguments
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- arguments, arguments object
- arguments object
ms.assetid: 5eb79ca9-bbb8-4a42-aaf5-16a93ecb425f
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2a5c526d19ad5469d9d099f51cc5a2e2d089814f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="arguments-object-javascript"></a>Objeto arguments (JavaScript)
Um objeto que representa os argumentos à função em execução no momento e as funções que o chamaram.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
[function.]arguments[n]  
```  
  
## <a name="parameters"></a>Parâmetros  
 *function*  
 Opcional. O nome de execução atualmente `Function` objeto.  
  
 *n*  
 Necessário. O índice com base em zero para valores de argumento passado para o `Function` objeto.  
  
## <a name="remarks"></a>Comentários  
 Você não pode criar explicitamente uma **argumentos** objeto. O **argumentos** objeto ficará disponível apenas quando uma função começa a ser executada. O **argumentos** objeto da função não é uma matriz, mas os argumentos individuais são acessados da mesma forma que os elementos de matriz são acessados. O índice  *n*  é, na verdade, uma referência a uma da **0**  ***n***  propriedades do **argumentos** objeto.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso do **argumentos** objeto.  
  
```JavaScript  
function ArgTest(a, b)  
{  
   var s = "";  
  
   s += "Expected Arguments: " + ArgTest.length;  
   s += "<br />";  
   s += "Passed Arguments: " + arguments.length;  
   s += "<br />";  
  
   s += "The individual arguments are: "  
   for (n = 0; n < arguments.length; n++)  
   {  
      s += ArgTest.arguments[n];  
      s += " ";  
   }  
  
   document.write(s);  
}  
  
ArgTest(1, 2, "hello", new Date())  
  
// Output:  
// Expected Arguments: 2  
// Passed Arguments: 4  
// The individual arguments are: 1 2 hello Tues Jan 8 08:27:09 PST 20xx  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [0... n propriedades (argumentos)](../../javascript/reference/0-dot-dot-dot-n-properties-arguments-javascript.md)   
 [Propriedade callee (argumentos)](../../javascript/reference/callee-property-arguments-javascript.md)   
 [Propriedade length (arguments)](../../javascript/reference/length-property-arguments-javascript.md)