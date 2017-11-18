---
title: "Propriedade prototype (número) | Microsoft Docs"
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
ms.assetid: d5fb87af-fc3a-4469-8dde-d31daf654f94
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2dba8b8886b4fdbc48a662796863b1dfca019aec
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="prototype-property-number"></a>Propriedade prototype (Número)
Retorna uma referência ao protótipo para uma classe de número.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
number.prototype  
```  
  
## <a name="remarks"></a>Comentários  
 O `number` argumento é o nome de um número.  
  
 Use a propriedade `prototype` para fornecer um conjunto básico de funcionalidades para uma classe de objetos. Novas instâncias de um objeto "herdam" o comportamento do protótipo atribuído a ele.  
  
 Por exemplo, para adicionar um método para o `Number` que retorna os dígitos do números de (inteiro) de objeto, declare a função, adicioná-lo ao `Number.prototype`e, em seguida, usá-lo.  
  
```JavaScript  
function number_digits() {  
    var digits = 0;  
    var num = this;  
    while (num) >= 1) {  
        digits++;  
        num /= 10;  
    }  
    return digits;  
}  
  
Number.prototype.digits = number_digits;  
var myNumber = new Number(3456.789);  
document.write(myNumber.digits());  
// Output:  
// 4  
```  
  
 Todos os intrínseco [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] objetos têm um `prototype` propriedade é somente leitura. Propriedades e métodos que podem ser adicionados ao protótipo, mas o objeto não pode ser atribuído um protótipo diferente. No entanto, objetos definidos pelo usuário podem ser atribuídos um novo protótipo.  
  
 As listas de método e propriedade para cada objeto intrínseco nesta referência de linguagem indicam quais são parte do protótipo do objeto e quais não são.  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]