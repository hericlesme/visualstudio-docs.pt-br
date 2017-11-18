---
title: "Função Promise.All (Promise) | Microsoft Docs"
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
ms.assetid: 02a7b90c-96f6-4484-9466-d261efa1b494
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 997a419a990b407ae018f7da39fd75673ea28b6d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="promiseall-function-promise"></a>Função Promise.all (Promise)
Une duas ou mais promessas e retorna somente quando todas as promessas especificadas são concluídas ou rejeitadas.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Promise.all(func1, func2 [,funcN])  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `func1`  
 Necessário. Uma função que retorna uma promessa.  
  
 `func2`  
 Necessário. Uma função que retorna uma promessa.  
  
 `funcN`  
 Opcional. Uma ou mais funções que retornam uma promessa.  
  
## <a name="remarks"></a>Comentários  
 O resultado retornado é uma matriz de valores retornados pelas promessas concluídas. Se uma das promessas associadas for rejeitada, `Promise.all` retorna imediatamente o motivo da rejeição da promessa (todos os outros valores retornados são descartados).  
  
## <a name="example"></a>Exemplo  
 Neste código, a primeira chamada para o tempo limite retorna após 5.000 ms. O processador de conclusão chama `Promise.all`, que retorna somente quando as duas chamadas para o tempo limite forem concluídas ou rejeitadas.  
  
```JavaScript  
function timeout(duration) {  
    return new Promise(function(resolve, reject) {  
        setTimeout(resolve, duration);  
    });  
}  
  
var p = timeout(5000).then(() => {  
    return Promise.all([timeout(100), timeout(200)]);  
})  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Objeto Promise](../../javascript/reference/promise-object-javascript.md)