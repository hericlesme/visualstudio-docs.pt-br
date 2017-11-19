---
title: 0... n propriedades (argumentos) (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: 0...n
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: 0...n properties
ms.assetid: 52857c4b-3d56-4500-93ff-4db4729c2578
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f46c7dafef1cdc27d27f619936349637af172740
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="0n-properties-arguments-javascript"></a>0...n Properties (argumentos) (JavaScript)
Retorna o valor real de argumentos individuais de um **argumentos** objeto retornado pelo **argumentos** propriedade de uma função em execução.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
[function.]arguments[[0|1|2|...|n]]  
```  
  
## <a name="parameters"></a>Parâmetros  
 *function*  
 Opcional. O nome de execução atualmente `Function` objeto.  
  
 0, 1, 2, *, n*  
 Necessário. Inteiro não negativo no intervalo de 0 a  *n*  onde 0 representa o primeiro argumento e  *n*  representa o argumento final. O valor do argumento final  *n*  é **arguments 1**.  
  
## <a name="remarks"></a>Comentários  
 Os valores retornados por 0. . . propriedades n são os valores reais passados para a função em execução. Ao mesmo tempo, na verdade, não é uma matriz de argumentos, os argumentos individuais que compõem o **argumentos** objeto são acessados da mesma forma que os elementos da matriz são acessados.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso da **0...**  ***n***Propriedades do **argumentos** objeto. Para entender completamente o exemplo, passe um ou mais argumentos para a função:  
  
```JavaScript  
function ArgTest(){  
   var s = "";  
   s += "The individual arguments are: "  
   for (n = 0; n < arguments.length; n++){  
      s += ArgTest.arguments[n];  
      s += " ";  
   }  
   return(s);  
}  
document.write(ArgTest(1, 2, "hello", new Date()));  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Aplica-se a**: [objeto arguments](../../javascript/reference/arguments-object-javascript.md)&#124; [Objeto de função](../../javascript/reference/function-object-javascript.md)  
  
## <a name="see-also"></a>Consulte também  
 [Propriedade Length (argumentos)](../../javascript/reference/length-property-arguments-javascript.md)   
 [Propriedade length (Function)](../../javascript/reference/length-property-function-javascript.md)