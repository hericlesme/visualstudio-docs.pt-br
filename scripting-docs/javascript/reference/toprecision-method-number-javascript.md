---
title: "Método toPrecision (Number) (JavaScript) | Microsoft Docs"
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
- toPrecision
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- toPrecision method
ms.assetid: ac13c82f-1038-447a-823f-f755bba535ca
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eeab7642dcd88677d1b5a7102e3cf342d7ee1d29
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="toprecision-method-number-javascript"></a>Método toPrecision (Number) (JavaScript)
Representa um número em notação exponencial ou de ponto fixo com um número especificado de dígitos.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
numObj.toPrecision([precision])  
```  
  
## <a name="parameters"></a>Parâmetros  
 `numObj`  
 Necessário. Um objeto `Number`.  
  
 `precision`  
 Opcional. O número de dígitos significativos. Deve estar no intervalo 1-21, inclusive.  
  
## <a name="return-value"></a>Valor de retorno  
 Para os números na notação exponencial, `precision` - 1 são retornados dígitos após o ponto decimal. Para os números na notação fixa, `precision` dígitos significantes são retornados.  
  
 Se `precision` não for fornecido ou está **indefinido**, o **toString** método é chamado em vez disso.  
  
## <a name="example"></a>Exemplo  
 O código a seguir mostra como usar `toPrecision`.  
  
```JavaScript  
var num = new Number(123);  
var prec = num.toPrecision();  
document.write(prec);  
document.write("<br/>");  
  
num = new Number(123.456);  
prec = num.toPrecision(5);  
document.write(prec);  
  
// Output:  
// 123  
// 123.46  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Aplica-se a**: [número de objeto](../../javascript/reference/number-object-javascript.md)  
  
## <a name="see-also"></a>Consulte também  
 [Método toFixed (Number)](../../javascript/reference/tofixed-method-number-javascript.md)   
 [Método toExponential (Number)](../../javascript/reference/toexponential-method-number-javascript.md)