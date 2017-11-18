---
title: "Função Promise race (promessa) | Microsoft Docs"
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
ms.assetid: 9236eced-d313-4d03-8c3e-d89d762b3084
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fedd512f4565009c8429b43b0d9d93de943d13fb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="promiserace-function-promise"></a>Função Promise.race (Promessa)
Cria uma nova promessa que será resolvida ou rejeitada com o mesmo valor de resultado que a primeira promessa a ser resolvida ou rejeitada entre os argumentos passados.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Promise.race(iterable)  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `iterable`  
 Necessário. Um ou mais promessas.  
  
## <a name="remarks"></a>Comentários  
 Se uma das promessas em `iterable` já está em um estado resolvido ou rejeitado, `Promise.race` retorna uma promessa resolvida ou rejeitada da mesma forma, com o valor do resultado igual ao valor usado para resolver (ou rejeitar) a promessa. Se várias promessas em `iterable` já estiverem resolvidas ou rejeitadas, `Promise.race` retorna uma promessa resolvida da mesma forma que a primeira promessa iterada. Se nenhum promessa que pode ser iterada for resolvida ou rejeitada, a promessa retornada de `Promise.race` também não é resolvida ou rejeitada.  
  
## <a name="example"></a>Exemplo  
  
```JavaScript  
var p1 = new Promise(function(resolve, reject) {  
    setTimeout(resolve, 0, 'success');  
});  
var p2 = new Promise(function(resolve, reject) { });  
var p2 = new Promise(function(resolve, reject) { });  
  
var race = Promise.race( [p1, p2, p3] );  
race.then(function(result) {  
    console.log(result);  
});  
  
// Output:  
// success  
  
var race = Promise.race( [Promise.reject('failure'),  
    Promise.resolve('success')] );  
race.catch(function(result) {  
    console.log(result);  
});  
  
// Output:  
// failure  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Objeto Promise](../../javascript/reference/promise-object-javascript.md)