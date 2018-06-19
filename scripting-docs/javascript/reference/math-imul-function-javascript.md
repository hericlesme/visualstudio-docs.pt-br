---
title: Função Math imul (JavaScript) | Microsoft Docs
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
ms.assetid: dce5e11c-36b9-4c39-84d3-6cd494dd1cbf
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 57820d0926d574c75924f4eef6265ef7fa0766da
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24638866"
---
# <a name="mathimul-function-javascript"></a>Função Math.imul (JavaScript)
Retorna o produto de dois números que são tratados como inteiros com sinal de 32 bits.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Math.imul(x, y);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `x`  
 Necessário. O primeiro número.  
  
 `y`  
 Necessário. O segundo número.  
  
## <a name="remarks"></a>Comentários  
 Essa função é usada para compiladores como Emscripten e Mandreel, que não implementam a multiplicação de inteiro da mesma maneira como JavaScript.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir mostra como multiplicar números usando `Math.imul`.  
  
```JavaScript  
var result1 = Math.imul(2, 5);  
// result1 == 10  
  
var result2 = Math.imul(Math.pow(2, 32) - 1, Math.pow(2, 32) - 2);  
// result2 == 2   
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]