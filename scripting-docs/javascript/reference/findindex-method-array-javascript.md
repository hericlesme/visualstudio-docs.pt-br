---
title: "Método findIndex (Array) (JavaScript) | Microsoft Docs"
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
ms.assetid: 3a200cf0-db67-4c7b-89f8-5e9f5dc1a926
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5c8da475b776e1c04e4fe5bfc7062318cfec952c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="findindex-method-array-javascript"></a>Método findIndex (Array) (JavaScript)
Retorna um valor de índice para o primeiro elemento da matriz que atende aos critérios de teste especificados em uma função de retorno de chamada.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
arrayObj.findIndex(callbackfn [, thisArg]);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `arrayObj`  
 Necessário. O objeto de matriz.  
  
 `callbackfn`  
 Necessário. A função de retorno de chamada para testar cada elemento da matriz.  
  
 `thisArg`  
 Opcional. Especifica o objeto `this` na função de retorno de chamada. Se não for especificado, o objeto `this` é indefinido.  
  
## <a name="remarks"></a>Comentários  
 O `findIndex` chama a função de retorno de chamada uma vez para cada elemento na matriz, em ordem de crescente, até que um elemento retorne `true`. Assim que um elemento retornar true, `findIndex` retorna o valor de índice do elemento que retorna true. Se nenhum elemento na matriz retornar true, `findIndex` retornará -1.  
  
 `findIndex` não modifica o objeto de matriz.  
  
## <a name="callback-function-syntax"></a>Sintaxe da função de retorno de chamada  
 A sintaxe da função de retorno de chamada é a seguinte:  
  
 `function callbackfn(value, index, thisArg)`  
  
 Você pode declarar a função de retorno de chamada usando até três parâmetros.  
  
 Os parâmetros da função de retorno de chamada são os seguintes.  
  
|Argumento de retorno de chamada|Definição|  
|-----------------------|----------------|  
|`value`|O valor do elemento da matriz.|  
|`index`|O índice numérico do elemento da matriz.|  
|`arrayObj`|O objeto de matriz a ser percorrido.|  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, a função de retorno de chamada testa se cada elemento na matriz é igual a 2.  
  
```JavaScript  
[1,2,3].findIndex(function(x) { x == 2; });  
// Returns an index value of 1.  
  
```  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa a sintaxe de seta para testar cada elemento. Neste exemplo, nenhum elemento retorna `true`, e `findIndex` retorna -1.  
  
```  
[1,2,3].findIndex(x => x == 4);  
// Returns an index value of -1.   
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]