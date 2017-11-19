---
title: "Propriedade arguments (função) (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: arguments
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- arguments, arguments property
- Arguments property
ms.assetid: efc7a1ee-0880-4f05-b0f2-808f31a4af1d
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5b0b18fb8164639119e5db5e7a5d76b4280f9c9d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="arguments-property-function-javascript"></a>Propriedade arguments (função) (JavaScript)
Obtém os argumentos para execução no momento `Function` objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
function.arguments  
```  
  
## <a name="remarks"></a>Comentários  
 O `function` argumento é o nome da função atualmente em execução e pode ser omitido.  
  
 Esta propriedade permite que uma função manipular um número variável de argumentos. O **comprimento** propriedade o `arguments` objeto contém o número de argumentos passados para a função. Os argumentos individuais dentro de `arguments` objeto pode ser acessado da mesma forma que os elementos de matriz são acessados.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso da propriedade `arguments`:  
  
```JavaScript  
function ArgTest(arg1, arg2){  
   var s = "";  
   s += "The individual arguments are: "  
   for (n = 0; n < arguments.length; n++){  
      s += ArgTest.arguments[n];  
      s += " ";  
   }  
   return(s);  
}  
document.write(ArgTest(1, 2, "hello"));  
  
//Output: function ArgTest(arg1, arg2){  
   var s = "";  
   s += "The individual arguments are: "  
   for (n = 0; n < arguments.length; n++){  
      s += ArgTest.arguments[n];  
      s += " ";  
   }  
   return(s);  
}  
document.write(ArgTest(1, 2, "hello"));  
  
// Output: The individual arguments are: 1 2 hello  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Objeto arguments](../../javascript/reference/arguments-object-javascript.md)   
 [Instrução Function](../../javascript/reference/function-statement-javascript.md)