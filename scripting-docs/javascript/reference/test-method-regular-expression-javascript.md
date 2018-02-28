---
title: "Método Test (Expressão Regular) (JavaScript) | Microsoft Docs"
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
- test
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- test method
ms.assetid: 4f4b6e39-cb1a-4be9-a66f-7b846075580d
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 53e2d2c23821cba5149367c7b5a735fa471bf581
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="test-method-regular-expression-javascript"></a>Método test (expressão regular) (JavaScript)
Retorna um valor booliano que indica se existe ou não um padrão em uma cadeia de caracteres pesquisada.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
rgExp.test(str)   
```  
  
## <a name="parameters"></a>Parâmetros  
 `rgExp`  
 Necessário. Uma instância de um **Expressão Regular** objeto que contém o padrão de expressão regular e os sinalizadores aplicáveis.  
  
 `str`  
 Necessário. A cadeia de caracteres na qual executar a pesquisa.  
  
## <a name="remarks"></a>Comentários  
 O **teste** método verifica se um padrão existe dentro de uma cadeia de caracteres e retorna **true** nesse caso, e **false** caso contrário.  
  
 As propriedades de global `RegExp` objeto não foram modificados pelo **teste** método.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso do **teste** método. Para usar este exemplo, passe a função de um padrão de expressão regular e uma cadeia de caracteres. A função será de teste para a ocorrência do padrão de expressão regular na cadeia de caracteres e retornam uma cadeia de caracteres que indica os resultados da pesquisa:  
  
```JavaScript  
function TestDemo(re, teststring)  
{  
   // Test string for existence of regular expression.  
   var found = re.test(teststring)  
  
   // Format the output.  
   var s = "";  
   s += "'" + teststring + "'"  
  
   if (found)  
      s += " contains ";  
   else  
      s += " does not contain ";  
  
   s += "'" + re.source + "'"  
   return(s);  
}  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Aplica-se a**: [objeto Regular Expression](../../javascript/reference/regular-expression-object-javascript.md)  
  
## <a name="see-also"></a>Consulte também  
 [Objeto RegExp](../../javascript/reference/regexp-object-javascript.md)   
 [Objeto de expressão regular](../../javascript/reference/regular-expression-object-javascript.md)   
 [Sintaxe de expressão regular (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)