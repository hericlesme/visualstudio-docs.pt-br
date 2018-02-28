---
title: "Função Math.Abs (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- abs
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- absolute values, calculating
- absolute values
- numeric expressions
- abs method
ms.assetid: 9af4b5b8-de77-47bb-bb59-abdde371e4c3
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5719905a7de375f1b409378f0579e3d8b25209fc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="mathabs-function-javascript"></a>Função Math.abs (JavaScript)
Retorna o valor absoluto de um número (o valor sem considerar se ela é positivo ou negativo). Por exemplo, o valor absoluto de -5 é o mesmo que o valor absoluto de 5.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Math.abs(number)  
```  
  
#### <a name="parameters"></a>Parâmetros  
 Obrigatório `number` argumento é uma expressão numérica para a qual o valor absoluto é necessário.  
  
## <a name="return-value"></a>Valor de retorno  
 O valor absoluto do `number` argumento.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso da função `abs`.  
  
```JavaScript  
var s;  
var v1 = Math.abs(6);  
var v2 = Math.abs(-6);  
if (v1 == v2) {  
    document.write("Absolute values are the same.");  
}  
else {  
document.write("Absolute values are different.");  
}  
  
// Output: Absolute values are the same.  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Aplica-se a**: [objeto Math](../../javascript/reference/math-object-javascript.md)  
  
## <a name="see-also"></a>Consulte também  
 [Objeto Math](../../javascript/reference/math-object-javascript.md)