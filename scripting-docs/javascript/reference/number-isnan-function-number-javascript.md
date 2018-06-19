---
title: Função Number isNaN (Number) (JavaScript) | Microsoft Docs
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
ms.assetid: 2d9813d6-ec9c-433b-b060-8e3c3ff62ca4
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7c11abe2dd2fc70431800d31f4c44279a88cd75d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639056"
---
# <a name="numberisnan-function-number-javascript"></a>Função Number.isNaN (Number) (JavaScript)
Retorna um valor booliano que indica se um valor é o valor reservado `NaN` (e não um número).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Number.isNaN(numValue)   
```  
  
#### <a name="parameters"></a>Parâmetros  
 `numValue`  
 Necessário. O valor a ser testado em relação a `NaN`.  
  
## <a name="return-value"></a>Valor de retorno  
 `true` se o valor convertido para o tipo `Number` for o `NaN`. Caso contrário, `false`.  
  
## <a name="remarks"></a>Comentários  
 Você normalmente usa esse método para testar valores retornados dos métodos `parseInt` e `parseFloat`.  
  
 `Number.isNaN` corrige problemas com a função global `isNaN`. `Number.isNaN` só converte o argumento para o tipo de Número depois compará-lo com `NaN`. Como resultado, retorna `true` se e somente se o argumento passado tiver exatamente o mesmo valor que `NaN`. A função global `isNaN` converte o argumento para o tipo de Número antes da comparação, o que pode resultar em valores não numéricos que não retornam `true`, enquanto podem não retornar `true` para `Number.isNaN`.  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
 **Aplica-se a**: [número de objeto](../../javascript/reference/number-object-javascript.md)  
  
## <a name="example"></a>Exemplo  
  
```JavaScript  
// Returns true.  
Number.isNaN(NaN);  
Number.isNaN(Number.NaN);  
Number.isNaN(0 / 0);  
  
// Returns false.  
Number.isNaN(100);  
// Returns false.  
// Strings are converted to numbers and return false.  
Number.isNaN("100");  
Number.isNaN("ABC");  
Number.isNaN("10C");  
Number.isNaN("abc123");  
  
```