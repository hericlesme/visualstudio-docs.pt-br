---
title: "Método Add (WeakSet) (JavaScript) | Microsoft Docs"
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
ms.assetid: d35d0287-6b33-4720-b9d7-8954c428ce4e
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3ab486beaba4a26c73930b5ceaee927f73aa077a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="add-method-weakset-javascript"></a>Método add (WeakSet) (JavaScript)
Adiciona um novo elemento a um `WeakSet`.  
  
## <a name="syntax"></a>Sintaxe  
  
```JavaScript  
weaksetObj.add(obj)  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `weaksetObj`  
 Necessário. Um objeto `WeakSet`.  
  
 `obj`  
 Necessário. Novo elemento do `WeakSet`.  
  
## <a name="remarks"></a>Comentários  
 O novo elemento deve ser um objeto, em vez de um valor arbitrário e deve ser exclusivo. Se você adicionar um elemento não exclusivo a um `WeakSet`, o novo elemento não será adicionado à coleção.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como adicionar membros a um conjunto e verificar se eles foram adicionados.  
  
```JavaScript  
var ws = new WeakSet();  
  
var str = new String("Thomas Jefferson");  
var num = new Number(1776);  
  
ws.add(str);  
ws.add(num);  
  
console.log(ws.has(str));  
console.log(ws.has(num));  
  
ws.delete(str);  
console.log(ws.has(str));  
  
// Output:  
// true  
// true  
// false  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]