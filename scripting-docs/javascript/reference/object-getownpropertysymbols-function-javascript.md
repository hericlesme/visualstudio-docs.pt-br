---
title: Função Object. getownpropertysymbols (JavaScript) | Microsoft Docs
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
ms.assetid: 68dd69b9-5a33-44c2-ba5f-21a4ae6c0879
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2cc47ae365841332f11cb02da1469a4c9fff80c3
ms.sourcegitcommit: abae48f476832f79cc2c5bac43bb1226d3fe4e48
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/16/2018
ms.locfileid: "27814954"
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
  
console.log(symbols[0].toString());  
  
// Output:  
// undefined  
// Symbol(description)  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]