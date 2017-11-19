---
title: Propriedade Length (matriz) (JavaScript) | Microsoft Docs
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
- Array object
- Length property
- length property (array)
ms.assetid: e1c6377c-2e84-440a-9660-f1f512e4a938
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6e69fd5387b1d7430491b1693dec07581f165cc9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="length-property-array-javascript"></a>Propriedade length Array) (JavaScript)
Obtém ou define o comprimento da matriz. Trata-se de um número uma unidade maior que o elemento mais alto definido em uma matriz.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
numVar = arrayObj.length   
```  
  
## <a name="parameters"></a>Parâmetros  
 `numVar`  
 Necessário. Qualquer número.  
  
 `arrayObj`  
 Necessário. Qualquer objeto `Array`.  
  
## <a name="remarks"></a>Comentários  
 Em JavaScript, as matrizes são esparsas e os elementos de uma matriz não precisam ser contíguos. A propriedade `length` não é necessariamente o número de elementos na matriz. Por exemplo, na seguinte definição de matriz, `my_array.length` contém 7, não 2:  
  
```JavaScript  
var my_array = new Array( );  
my_array[0] = "Test";  
my_array[6] = "Another Test";  
```  
  
 Se você definir a propriedade `length` menor do que seu valor anterior, a matriz será truncada e quaisquer elementos com índices de matriz iguais ou maiores que o novo valor da propriedade `length` serão perdidos.  
  
 Se você definir a propriedade de comprimento maior que seu valor anterior, a matriz será expandida e quaisquer novos elementos criados terão o valor `undefined`.  
  
 O exemplo a seguir ilustra o uso da propriedade `length`:  
  
```JavaScript  
var a;  
a = new Array(0,1,2,3,4);  
document.write(a.length);  
  
// Output  
// 5  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
> [!NOTE]
>  Começando com o modo Standards do Internet Explorer 9, as vírgulas à direita incluídas na inicialização de uma Matriz são tratadas de maneira diferente.