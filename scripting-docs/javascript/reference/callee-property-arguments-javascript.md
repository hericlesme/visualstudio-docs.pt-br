---
title: Propriedade callee (argumentos) (JavaScript) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- callee
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- callee property
ms.assetid: ad9d4d21-73f0-44f6-8bec-502f3456cd23
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 33f1c2926d76c0a1f088c8f4222b6f24c004b73b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24634056"
---
# <a name="callee-property-arguments-javascript"></a>Propriedade callee (argumentos) (JavaScript)
Retorna o `Function` objeto que está sendo executado, ou seja, o texto do corpo do `Function` objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
[function.]arguments.callee  
```  
  
## <a name="remarks"></a>Comentários  
 Opcional *função* argumento é o nome de execução atualmente `Function` objeto.  
  
 O `callee` propriedade é um membro do **argumentos** objeto que fica disponível apenas quando a função associada está em execução.  
  
 O valor inicial do `callee` é de propriedade de `Function` do objeto que está sendo executada. Isso permite que funções anônimas ser recursivo.  
  
## <a name="example"></a>Exemplo  
  
```JavaScript  
function factorial(n){  
  if (n <= 0)  
     return 1;  
  else  
     return n * arguments.callee(n - 1)  
}  
document.write(factorial(4));  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Aplica-se a**: [objeto arguments](../../javascript/reference/arguments-object-javascript.md)&#124; [Objeto de função](../../javascript/reference/function-object-javascript.md)  
  
## <a name="see-also"></a>Consulte também  
 [Propriedade caller (Function)](../../javascript/reference/caller-property-function-javascript.md)