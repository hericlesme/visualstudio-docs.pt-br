---
title: Propriedade Length (argumentos) (JavaScript) | Microsoft Docs
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
- length Property
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- length property (arguments)
- Length property
ms.assetid: 3cf36823-15bc-489b-a951-24c4923d9dba
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cede75a91244442f5f28ec9f71b7128814bed5d2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="length-property-arguments-javascript"></a>Propriedade length (argumentos) (JavaScript)
Retorna o número real de argumentos passados para uma função pelo chamador.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
[function.]arguments.length  
```  
  
## <a name="remarks"></a>Comentários  
 Opcional *função* argumento é o nome de execução atualmente `Function` objeto.  
  
 O **comprimento** propriedade o **argumentos** objeto é inicializado pelo mecanismo de script para o número real de argumentos passados para um `Function` ao início da execução na função do objeto.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso do **comprimento** propriedade o **argumentos** objeto. Para entender completamente o exemplo, passe mais argumentos para a função de 2 argumentos esperado:  
  
```JavaScript  
function ArgTest(a, b){  
   var s = "";  
  
   s += "Expected Arguments: " + ArgTest.length;  
   s += "<br />";  
   s += "Passed Arguments: " + arguments.length;  
  
   document.write (s);  
}  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Aplica-se a**: [objeto arguments](../../javascript/reference/arguments-object-javascript.md)&#124; [Objeto de função](../../javascript/reference/function-object-javascript.md)  
  
## <a name="see-also"></a>Consulte também  
 [Propriedade arguments (função)](../../javascript/reference/arguments-property-function-javascript.md)   
 [Propriedade Length (matriz)](../../javascript/reference/length-property-array-javascript.md)   
 [Propriedade length (String)](../../javascript/reference/length-property-string-javascript.md)