---
title: Propriedade prototype (String) | Microsoft Docs
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
ms.assetid: 437ce478-9c45-45f7-8952-bd71856cfcd8
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: df8c6abbd64fce9172d805c2e22dee51f4fbbee4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639176"
---
# <a name="prototype-property-string"></a>Propriedade prototype (String)
Retorna uma referência ao protótipo para uma classe de cadeia de caracteres.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
string.prototype  
```  
  
## <a name="remarks"></a>Comentários  
 O `string` argumento é o nome de uma cadeia de caracteres.  
  
 Use a propriedade `prototype` para fornecer um conjunto básico de funcionalidades para uma classe de objetos. Novas instâncias de um objeto "herdam" o comportamento do protótipo atribuído a ele.  
  
 Por exemplo, para adicionar um método para o `String` que retorna o valor do último elemento da cadeia de caracteres do objeto, declare a função, adicione-o para `String.prototype`e, em seguida, usá-lo.  
  
```JavaScript  
function string_last( ){  
    return this.charAt(this.length - 1);  
}  
String.prototype.last = string_last;  
var myString = new String("every good boy does fine");  
document.write(myString.last());  
  
// Output:  
// e  
```  
  
 Todos os intrínseco [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] objetos têm um `prototype` propriedade é somente leitura. Propriedades e métodos que podem ser adicionados ao protótipo, mas o objeto não pode ser atribuído um protótipo diferente. No entanto, objetos definidos pelo usuário podem ser atribuídos um novo protótipo.  
  
 As listas de método e propriedade para cada objeto intrínseco nesta referência de linguagem indicam quais são parte do protótipo do objeto e quais não são.  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]