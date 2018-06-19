---
title: Método concat (Array) (JavaScript) | Microsoft Docs
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
- concat
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- concat method (array)
- Concat method
ms.assetid: bc2b4a6a-209e-4d59-8c24-59db01d53b1e
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 19f3a216a36f9ad8c422036476e46b89b6ee488c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24634276"
---
# <a name="concat-method-array-javascript"></a>Método concat (Array) (JavaScript)
Combina duas ou mais matrizes.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
array1.concat([item1[, item2[, . . . [, itemN]]]])   
```  
  
## <a name="parameters"></a>Parâmetros  
 `array1`  
 Necessário. O `Array` do objeto ao qual as outras matrizes são concatenadas.  
  
 `item1,. . ., itemN`  
 Opcional. Itens adicionais a serem adicionados ao final da `array1`.  
  
## <a name="remarks"></a>Comentários  
 O `concat` método retorna um `Array` objeto que contém a concatenação de `array1` e quaisquer outros itens fornecidos.  
  
 Os itens a serem adicionados (*itemN item1*) para a matriz são adicionados, em ordem a partir do primeiro item na lista. Se um dos itens é uma matriz, seu conteúdo é adicionado ao final da `array1`. Se o item for algo diferente de uma matriz, ele é adicionado ao final da matriz como um único elemento de matriz.  
  
 Elementos de matrizes de origem são copiados para a matriz resultante da seguinte maneira:  
  
-   Se um objeto é copiado de qualquer uma das matrizes são concatenadas para a nova matriz, a referência de objeto continua apontar para o mesmo objeto. Uma alteração na nova matriz ou a matriz original resulta em uma alteração para o outro.  
  
-   Se um valor de cadeia de caracteres ou número é adicionado à nova matriz, somente o valor é copiado. Alterar o valor em uma matriz não afeta o valor no outro.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar o `concat` método quando usado com uma matriz:  
  
```JavaScript  
var a, b, c, d;  
a = new Array(1,2,3);  
b = "dog";  
c = new Array(42, "cat");  
d = a.concat(b, c);  
document.write(d);  
  
//Output:   
1, 2, 3, "dog", 42, "cat"  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Método concat (String)](../../javascript/reference/concat-method-string-javascript.md)   
 [Método join (Array)](../../javascript/reference/join-method-array-javascript.md)