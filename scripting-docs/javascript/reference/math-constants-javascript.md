---
title: Constantes de matemática (JavaScript) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- LN2 constant [JavaScript]
- E constant [JavaScript]
- LOG10E constant [JavaScript]
- SQRT1_2 constant [JavaScript]
- LOG2E constant [JavaScript]
- Math.SQRT2 constant [JavaScript]
- PI constant [JavaScript]
- Math.LOG2E constant [JavaScript]
- constants [JavaScript], math
- Math.E constant [JavaScript]
- logarithm consants [JavaScript]
- Math.LOG10E constant [JavaScript]
- Math.SQRT1_2 constant [JavaScript]
- SQRT2 constant [JavaScript]
- square root constants [JavaScript]
- Math.PI constant [JavaScript]
- math constants [JavaScript]
- LN10 constant [JavaScript]
- Math.LN2 constant [JavaScript]
- Math.LN10 constant [JavaScript]
ms.assetid: 8a674046-cb99-4103-92be-83697fba6344
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9942abb69af416cd4cd7f092dc9f1478e0bc3a69
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24638946"
---
# <a name="math-constants-javascript"></a>Constantes de matemática (JavaScript)
Constantes de matemática retornam valores constantes que são propriedades do `Math` objeto.  
  
## <a name="math-object-constants"></a>Constantes do Objeto de Matemática  
 A tabela a seguir lista os valores constantes que são propriedades do [objeto Math](../../javascript/reference/math-object-javascript.md).  
  
|Constante|Descrição|Valor aproximado|  
|--------------|-----------------|-----------------------|  
|`Math.E`|A constante matemática e. Este é o número de Euler, a base dos logaritmos naturais.|2.718|  
|`Math.LN2`|O logaritmo natural de 2.|0.693|  
|`Math.LN10`|O logaritmo natural de 10.|2.302|  
|`Math.LOG2E`|O logaritmo de base 2 de e.|1.443|  
|`Math.LOG10E`|O logaritmo de base 10 de e.|0.434|  
|`Math.PI`|Pi. Esta é a razão entre a circunferência de um círculo e seu diâmetro.|3.14159|  
|`Math.SQRT1_2`|A raiz quadrada de 0,5, ou, de modo equivalente, um dividido pela raiz quadrada de 2.|0.707|  
|`Math.SQRT2`|A raiz quadrada de 2.|1.414|  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra como usar o `Math.PI` constante.  
  
```JavaScript  
var radius = 3;  
var area = Math.PI * radius * radius;  
document.write(area);  
  
// Output: 28.274333882308138  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Aplica-se a**: [objeto Math](../../javascript/reference/math-object-javascript.md)  
  
## <a name="see-also"></a>Consulte também  
 [Constantes de número](../../javascript/reference/number-constants-javascript.md)   
 [Constantes JavaScript](../../javascript/reference/javascript-constants.md)