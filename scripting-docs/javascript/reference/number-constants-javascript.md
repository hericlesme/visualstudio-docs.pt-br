---
title: Número de constantes (JavaScript) | Microsoft Docs
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
helpviewer_keywords:
- POSITIVE_INFINITY constant [JavaScript]
- MAX_VALUE constant [JavaScript]
- MIN_VALUE constant [JavaScript]
- number constants [JavaScript]
- Number.NEGATIVE_INFINITY constant [JavaScript]
- Number.POSITIVE_INFINITY constant [JavaScript]
- NEGATIVE_INFINITY constant [JavaScript]
- NaN constant [JavaScript]
- Number.MIN_VALUE constant [JavaScript]
- constants [JavaScript], number
- Number.NaN constant [JavaScript]
- Number.MAX_VALUE constant [JavaScript]
ms.assetid: e0701b41-99ae-4916-9ec0-f79bb15386fb
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f846ef7cbd9609f7913d6305e48cb4942476ca21
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639196"
---
# <a name="number-constants-javascript"></a>Constantes de número (JavaScript)
As seguintes constantes de número são propriedades do objeto `Number`.  
  
## <a name="number-object-constants"></a>Constantes do objeto Number  
 Você não precisa criar o objeto `Number` para acessar estas constantes.  
  
|Constante|Valor retornado|  
|--------------|--------------------|  
|`Number.EPSILON`|O menor número que pode ser representado em [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]. Igual a aproximadamente 2,2204460492503130808472633361816E-16.|  
|`Number.MAX_SAFE_INTEGER`|O maior número que pode ser representado com segurança em JavaScript. Igual a 9007199254740991.|  
|`Number.MAX_VALUE`|O maior número que pode ser representado em [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]. Igual a aproximadamente 1,79E+308.|  
|`Number.MIN_SAFE_INTEGER`|O menor número que pode ser representado com segurança em JavaScript. Igual a-9007199254740991.|  
|`Number.MIN_VALUE`|O número mais próximo a zero que pode ser representado em [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]. Igual a aproximadamente 5,00E-324.|  
|`Number.NaN`|Um valor que não é um número.<br /><br /> Em comparações de igualdade, `NaN` não é igual a nenhum valor, nem a ele próprio. Para testar se um valor é equivalente a `NaN`, use o [isNaN função](../../javascript/reference/isnan-function-javascript.md).|  
|`Number.NEGATIVE_INFINITY`|Um valor menor que o maior número negativo que pode ser representado em [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].<br /><br /> O [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] exibe os valores `NEGATIVE_INFINITY` como `-infinity`.|  
|`Number.POSITIVE_INFINITY`|Um valor maior que o maior número que pode ser representado em [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].<br /><br /> O [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] exibe os valores `POSITIVE_INFINITY` como `infinity`.|  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
 Para `Number.EPSILON`, `Number.MAX_SAFE_INTEGER` e `Number.MIN_SAFE_INTEGER`:  
  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
 **Aplica-se a**: [número de objeto](../../javascript/reference/number-object-javascript.md)  
  
## <a name="see-also"></a>Consulte também  
 [Constantes de matemática](../../javascript/reference/math-constants-javascript.md)   
 [Constantes (JavaScript)](../../javascript/reference/javascript-constants.md)   
 [Constante de infinito](../../javascript/reference/infinity-constant-javascript.md)   
 [Constante NaN](../../javascript/reference/nan-constant-javascript.md)   
 [Função isNaN](../../javascript/reference/isnan-function-javascript.md)