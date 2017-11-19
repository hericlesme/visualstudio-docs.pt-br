---
title: Propriedade prototype (Data) | Microsoft Docs
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
ms.assetid: 44f9c637-7da7-4833-906d-358506f32ced
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8c0b337964d2a2fe17a4e9a7906d81069470e61b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="prototype-property-date"></a>Propriedade prototype (Data)
Retorna uma referência ao protótipo para uma data.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
date.prototype  
```  
  
## <a name="remarks"></a>Comentários  
 O argumento `date` é o nome de um objeto.  
  
 Use o `prototype` propriedade para fornecer um conjunto básico de funcionalidades para uma data. Novas instâncias de um objeto "herdam" o comportamento do protótipo atribuído a ele.  
  
 Por exemplo, para adicionar um método ao objeto `Date` que retorna o valor do maior elemento da matriz, declare a função, adicione-a a `Date.prototype` e use-a.  
  
```JavaScript  
function max( ){  
    var max = new Date();  
    max.setFullYear(2200, 01, 01);  
    return max;  
}  
Date.prototype.maxDate = max;  
var myDate = new Date();  
  
if (myDate < myDate.maxDate())  
    document.write("today isn't the max");  
else if (myDate == myDate.maxDate())  
    document.write("today is the max");   
  
// Output:  
// today isn't the max  
  
```  
  
 Todos os intrínseco [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] objetos têm um `prototype` propriedade é somente leitura. Propriedades e métodos que podem ser adicionados ao protótipo, mas o objeto não pode ser atribuído um protótipo diferente. No entanto, objetos definidos pelo usuário podem ser atribuídos um novo protótipo.  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]