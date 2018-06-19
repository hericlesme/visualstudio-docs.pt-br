---
title: Função Object Assign (Object) (JavaScript) | Microsoft Docs
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
ms.assetid: 2dd6b312-dcd3-414e-8d53-088c6341c46d
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c156369299e58eac556d43a87476de2ce09173e1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24638816"
---
# <a name="objectassign-function-object-javascript"></a>Função Object.assign (Object) (JavaScript)
Copia os valores de um ou mais objetos de origem para um objeto de destino.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Object.assign(target, ...sources );  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `target`  
 Necessário. Um objeto para o qual propriedades enumeráveis são copiadas.  
  
 `...sources`  
 Necessário. Um ou mais objetos para os quais propriedades enumeráveis são copiadas.  
  
## <a name="exceptions"></a>Exceções  
 Essa função lança um `TypeError` se houver um erro de atribuição, que encerra a operação de cópia. Um `TypeError` será lançado se uma propriedade de destino não for gravável.  
  
## <a name="remarks"></a>Comentários  
 Essa função retorna o objeto de destino. Somente *enumerável próprio* propriedades são copiadas do objeto de origem para o objeto de destino. Você pode usar essa função para mesclar ou clonar objetos.  
  
 As fontes `null` ou `undefined` são tratadas como objetos vazios e não contribuem para o objeto de destino.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir mostra como mesclar um objeto usando `Object.assign`.  
  
```JavaScript  
var first = { name: "Bob" };  
var last = { lastName: "Smith" };  
  
var person = Object.assign(first, last);  
console.log(person);  
  
// Output:  
// { name: "Bob", lastName: "Smith" }   
```  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como clonar um objeto usando `Object.assign`.  
  
```JavaScript  
var obj = { person: "Bob Smith"};  
var clone = Object.assign({}, obj);  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]