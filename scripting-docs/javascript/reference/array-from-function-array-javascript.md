---
title: "Função Array from (Array) (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 1bf59a99-f860-4c4d-b4c6-d5f1f946a490
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a240cb439942bfeb6b4c9a1febb4d24cef1c5c18
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="arrayfrom-function-array-javascript"></a>Função array.from (Array) (JavaScript)
Retorna uma matriz de um objeto que pode ser iterado ou semelhante a uma matriz.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Array.from (arrayLike [ , mapfn [ , thisArg ] ] );  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `arrayLike`  
 Necessário. Um objeto de matriz ou um objeto que pode ser iterado.  
  
 `mapfn`  
 Opcional. Uma função de mapeamento para chamar cada elemento `arrayLike`.  
  
 `thisArg`  
 Opcional. Especifica o objeto `this` na função de mapeamento.  
  
## <a name="remarks"></a>Comentários  
 O parâmetro `arrayLike` deve ser um objeto com elementos indexados e uma propriedade `length` ou um objeto que pode ser iterado, como um objeto `Set`.  
  
 A função de mapeamento opcional é chamada em cada elemento da matriz.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir retorna uma matriz de uma coleção de nós de elementos DOM.  
  
```JavaScript  
var elemArr = Array.from(document.querySelectorAll('*'));  
var elem = elemArr[0]; // elem contains a reference to the first DOM element  
  
```  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir retorna uma matriz de caracteres.  
  
```JavaScript  
var charArr = Array.from("abc");  
// charArr[0] == "a";  
```  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir retorna uma matriz de objetos contidos na coleção.  
  
```JavaScript  
var setObj = new Set("a", "b", "c");  
var objArr = Array.from(setObj);  
// objArr[1] == "b";   
```  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra o uso da sintaxe de seta e uma função de mapeamento para alterar o valor de elementos.  
  
```JavaScript  
var arr = Array.from([1, 2, 3], x => x * 10);  
// arr[0] == 10;  
// arr[1] == 20;  
// arr[2] == 30;  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]