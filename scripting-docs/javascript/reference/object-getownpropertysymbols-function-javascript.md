---
title: "Função Object. getownpropertysymbols (JavaScript) | Microsoft Docs"
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
ms.assetid: 68dd69b9-5a33-44c2-ba5f-21a4ae6c0879
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2bcddba77305e30e4c5ae13f6b1fc5c9385b7108
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="objectgetownpropertysymbols-function-javascript"></a>Função Object.getOwnPropertySymbols (JavaScript)
Retorna as propriedades do próprio símbolo de um objeto. As propriedades do próprio símbolo de um objeto são aquelas definidas diretamente no objeto, e não herdadas do protótipo do objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Object.getOwnPropertySymbols(object);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `object`  
 Necessário. O objeto que contém os próprios símbolos.  
  
## <a name="return-value"></a>Valor de retorno  
 Uma matriz que contém os próprios símbolos do objeto.  
  
## <a name="remarks"></a>Comentários  
 Você precisa usar `Object.getOwnPropertySymbols` para obter as propriedades de símbolo de um objeto. `Object.getOwnPropertyNames` não retornará as propriedades de símbolo.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir mostra como obter as propriedades de símbolo de um objeto.  
  
```JavaScript  
var obj = {};  
var key = Symbol('description');  
  
obj[key] = 'data';  
  
var symbols = Object.getOwnPropertySymbols(obj);  
  
console.log(s[0].toString());  
  
// Output:  
// undefined  
// Symbol(description)  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]