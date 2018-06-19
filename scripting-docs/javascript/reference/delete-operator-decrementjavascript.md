---
title: Operador Delete (JavaScript) | Microsoft Docs
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
- delete_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- array elements, deleting
- properties, deleting
- delete operator
ms.assetid: 55c6487e-96ea-455b-a7ed-dc35c41ac2f3
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ee3def1977c0b29ee14ebf836f2d9ebb51d5a5ef
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636406"
---
# <a name="delete-operator-javascript"></a>Operador delete (JavaScript)
Exclui uma propriedade de um objeto ou remove um elemento de uma matriz.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
delete expression  
```  
  
## <a name="remarks"></a>Comentários  
 O `expression` argumento é uma opção válida [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] expressão que geralmente resulta em um elemento de matriz ou nome de propriedade.  
  
 Se o resultado de `expression` é um objeto, a propriedade especificada em `expression` existir, e o objeto não permitirá que ele deve ser excluída, `false` será retornado.  
  
 Em todos os outros casos, `true` será retornado.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como remover um elemento de uma matriz.  
  
```JavaScript  
// Create an array.  
var ar = new Array (10, 11, 12, 13, 14);  
  
// Remove an element from the array.  
delete ar[1];  
  
// Print the results.  
document.write ("element 1: " + ar[1]);  
document.write ("<br />");  
document.write ("array: " + ar);  
// Output:  
//  element 1: undefined  
//  array: 10,,12,13,14  
```  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como excluir propriedades de um objeto.  
  
```JavaScript  
// Create an object and add expando properties.  
var myObj = new Object();  
myObj.name = "Fred";  
myObj.count = 42;  
  
// Delete the properties from the object.  
delete myObj.name;  
delete myObj["count"];  
  
// Print the results.  
document.write ("name: " + myObj.name);  
document.write ("<br />");  
document.write ("count: " + myObj.count);  
// Output:  
//  name: undefined  
//  count: undefined  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Precedência do operador](../../javascript/operator-subtractprecedence-javascript.md)   
 [Resumo de operador (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)