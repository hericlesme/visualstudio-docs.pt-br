---
title: "Função Math.log (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: log
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- log method
- Math object
ms.assetid: 5d617fb5-4b27-404e-842f-eea5549a7c1a
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 62bfb6bf9bb95b541a51224af4484ded22ccb4e8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="mathlog-function-javascript"></a>Função Math.log (JavaScript)
Retorna o logaritmo natural (base `e`) de um número.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Math.log(number)   
```  
  
#### <a name="parameters"></a>Parâmetros  
 número  
 Um número.  
  
## <a name="return-value"></a>Valor de retorno  
 Se `number` for positivo, essa função retorna o logaritmo natural do número. Se `number` for negativo, a função retornará `NaN`. Se `number` é 0, a função retornará `-Infinity`.  
  
## <a name="example"></a>Exemplo  
 O código a seguir mostra como usar essa função.  
  
```JavaScript  
var numArr = [ 45.3, 69.0, 557.04, 0.222 ];  
  
for (i in numArr) {  
    document.write(Math.log(numArr[i]));  
    document.write("<br/>");  
}  
  
// Output:   
// 3.8133070324889884  
// 4.23410650459726  
// 6.322637050634291  
// -1.5050778971098575  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Aplica-se a**: [objeto Math](../../javascript/reference/math-object-javascript.md)  
  
## <a name="see-also"></a>Consulte também  
 [Função Math.sqrt](../../javascript/reference/math-sqrt-function-javascript.md)