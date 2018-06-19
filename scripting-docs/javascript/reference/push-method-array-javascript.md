---
title: Método push (Array) (JavaScript) | Microsoft Docs
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
- push
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Push method
ms.assetid: fa6e5799-dabe-4b3d-bd1f-0afc68c77134
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ddb49f310eaff51fe9e9ba584281fdf07bc2e818
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639446"
---
# <a name="push-method-array-javascript"></a>Método push (Array) (JavaScript)
Acrescenta novos elementos a uma matriz e retorna o novo comprimento dessa matriz.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
arrayObj.push([item1 [item2 [. . . [itemN ]]]])  
```  
  
## <a name="parameters"></a>Parâmetros  
 `arrayObj`  
 Necessário. Um objeto `Array`.  
  
 `item, item2,. . ., itemN`  
 Opcional. Novos elementos do `Array`.  
  
## <a name="remarks"></a>Comentários  
 O `push` e `pop` métodos permitem que você simule o último a entrar, primeiro a sair de pilha.  
  
 O `push` método acrescenta elementos na ordem em que aparecem. Se um dos argumentos for uma matriz, ele é adicionado como um único elemento. Use o `concat` método para unir os elementos de duas ou mais matrizes.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso do método `push`.  
  
```JavaScript  
var number;  
var my_array = new Array();  
  
my_array.push (5, 6, 7);  
my_array.push (8, 9);  
  
number = my_array.pop();  
while (number != undefined)  
   {  
   document.write (number + " ");  
   number = my_array.pop();  
   }  
  
// Output:  
// 9 8 7 6 5  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Método concat (matriz)](../../javascript/reference/concat-method-array-javascript.md)   
 [Método pop (Array)](../../javascript/reference/pop-method-array-javascript.md)