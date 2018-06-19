---
title: Função Object.is (JavaScript) | Microsoft Docs
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
ms.assetid: 6e2f6c6d-7cd2-47c4-a513-3ba53988d27d
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 36d4c281fdafbfacb0b1f6061ef4a90bfac99234
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24638696"
---
# <a name="objectis-function-javascript"></a>Função Object.is (JavaScript)
Retorna um valor que indica se dois objetos são o mesmo valor.  
  
## <a name="syntax"></a>Sintaxe  
  
```JavaScript  
Object.is(value1, value2)  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `value1`  
 Necessário. O primeiro valor a ser testado.  
  
 `value2`  
 Necessário. O segundo valor a ser testado.  
  
## <a name="return-value"></a>Valor de retorno  
 `true` se o valor for o mesmo valor. Caso contrário, `false`.  
  
## <a name="remarks"></a>Comentários  
 Diferente do operador = =, `Object.is` não impõe nenhum tipo ao testar valores.  
  
 A comparação aplicada pelo `Object.is` é semelhante à comparação aplicada pelo operador ===, exceto pelo fato de que `Object.is` trata `Number.isNaN` como o mesmo valor que `NaN`. Ele também trata + 0 e -0 como valores diferentes.  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]