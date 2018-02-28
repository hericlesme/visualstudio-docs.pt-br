---
title: "Método toExponential (Number) (JavaScript) | Microsoft Docs"
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
- toExponential
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- toExponential method
ms.assetid: 7c4a6d84-3c1f-4cc4-a67d-7753e5d4ed66
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fff2f2bc0c443fa9308c8d01dcea42a3cec9ff04
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="toexponential-method-number-javascript"></a>Método toExponential (Number) (JavaScript)
Representa um número em notação exponencial.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
numObj. toExponential([fractionDigits])  
```  
  
## <a name="parameters"></a>Parâmetros  
 `numObj`  
 Necessário. Um **número** objeto.  
  
 `fractionDigits`  
 Opcional. O número de dígitos após o ponto decimal. Deve estar no intervalo 0 - 20, inclusive.  
  
## <a name="return-value"></a>Valor de retorno  
 Retorna uma representação de cadeia de caracteres de um número em notação exponencial. A cadeia de caracteres contém um dígito antes do ponto decimal e pode conter `fractionDigits` dígitos depois dele.  
  
 Se `fractionDigits` não for fornecido, o `toExponential` método retorna o maior número de dígitos necessárias para especificar o número de forma exclusiva.  
  
## <a name="example"></a>Exemplo  
  
```JavaScript  
var num = new Number(123);  
var exp = num.toExponential();  
document.write(exp);  
document.write("<br/>");  
  
num = new Number(123.456);  
exp = num.toExponential(5);  
document.write(exp);  
  
// Output:   
// 1.23e+2  
// 1.23456e+2  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Aplica-se a**: [número de objeto](../../javascript/reference/number-object-javascript.md)  
  
## <a name="see-also"></a>Consulte também  
 [Método toFixed (Number)](../../javascript/reference/tofixed-method-number-javascript.md)   
 [Método toPrecision (Number)](../../javascript/reference/toprecision-method-number-javascript.md)