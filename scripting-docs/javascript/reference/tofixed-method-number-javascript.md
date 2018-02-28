---
title: "Método toFixed (Number) (JavaScript) | Microsoft Docs"
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
- toFixed
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- toFixed method
ms.assetid: b5f03400-865e-4ab2-818c-f734c0f6d6f0
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dd51dd67632f4e6417fee72fd19575025423bbf1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="tofixed-method-number-javascript"></a>Método toFixed (Number) (JavaScript)
Representa um número em notação de ponto fixo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
numObj.toFixed([fractionDigits])  
```  
  
## <a name="parameters"></a>Parâmetros  
 `numObj`  
 Necessário uma `Number` objeto.  
  
 `fractionDigits`  
 Opcional. O número de dígitos após o ponto decimal. Deve estar no intervalo 0 - 20, inclusive.  
  
## <a name="return-value"></a>Valor de retorno  
 Retorna uma representação de cadeia de caracteres de um número em notação de ponto fixo, que contém `fractionDigits` dígitos após o ponto decimal.  
  
 Se `fractionDigits` não for fornecido ou **indefinido**, o valor padrão é zero.  
  
## <a name="example"></a>Exemplo  
 O código a seguir mostra como usar `toFixed`.  
  
```JavaScript  
var num = new Number(123);  
var fix = num.toFixed();  
document.write(fix);  
document.write("<br/>");  
  
num = new Number(123.456);  
fix = num.toFixed(5);  
document.write(fix);  
  
// Output:  
// 123  
123.45600  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Aplica-se a**: [número de objeto](../../javascript/reference/number-object-javascript.md)  
  
## <a name="see-also"></a>Consulte também  
 [Método toExponential (Number)](../../javascript/reference/toexponential-method-number-javascript.md)   
 [Método toPrecision (Number)](../../javascript/reference/toprecision-method-number-javascript.md)