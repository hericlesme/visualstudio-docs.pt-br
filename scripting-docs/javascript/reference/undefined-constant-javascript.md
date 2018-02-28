---
title: indefinido constante (JavaScript) | Microsoft Docs
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
- undefined
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- undefined property
ms.assetid: 2a689d7d-00b0-48fb-9c95-5c2867bde006
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8ba7fa8b160e4f5d954c8d6545da5fae41c2f74b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="undefined-constant-javascript"></a>Constante indefinida (JavaScript)
Um valor que nunca tenha sido definido, como uma variável que não foi inicializada.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
undefined  
```  
  
## <a name="remarks"></a>Comentários  
 O `undefined` constante é um membro do `Global` de objeto e fica disponível quando o mecanismo de script é inicializado. Quando uma variável foi declarada mas não inicializada, seu valor é **indefinido**.  
  
 Se uma variável não foi declarada, você não pode comparar a `undefined`, mas você pode comparar o tipo da variável à cadeia de caracteres "indefinida".  
  
 O `undefined` constante é a útil quando explicitamente teste ou definindo uma variável como indefinido.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar o `undefined` constante.  
  
```JavaScript  
// A variable that has not been initialized.  
var declared;  
  
if (declared == undefined)  
    document.write("declared has not been given a value <br/>");  
else  
    document.write("declared has been given a value <br/>");  
  
document.write("typeof declared is " + typeof(declared) + "<br/>");  
  
// An undeclared variable cannot be compared to undefined,  
// so the next line would generate an error.  
// if (notDeclared == undefined);  
  
document.write("typeof notDeclared is " + typeof(notDeclared));  
  
// Output:  
// declared has not been given a value  
// typeof declared is undefined  
// typeof notDeclared is undefined  
```  
  
## <a name="requirements"></a>Requisitos  
 O `undefined` propriedade foi introduzida no [!INCLUDE[jsv55text](../../javascript/reference/includes/jsv55text-md.md)]e foi feita somente leitura em [!INCLUDE[jsv9textspecific](../../javascript/reference/includes/jsv9textspecific-md.md)].  
  
 **Aplica-se a**: [objeto Global](../../javascript/reference/global-object-javascript.md)  
  
## <a name="see-also"></a>Consulte também  
 [Operador TypeOf](../../javascript/reference/typeof-operator-decrementjavascript.md)