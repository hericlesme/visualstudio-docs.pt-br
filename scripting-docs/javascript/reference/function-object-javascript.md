---
title: "Função Object (JavaScript) | Microsoft Docs"
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
- function
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Function object
ms.assetid: d3834767-203c-475e-848c-95c423ba15b6
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4392fd57967e6312c96af50bdff2415d0f2dcd4d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="function-object-javascript"></a>Objeto Function (JavaScript)
Cria uma nova função.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
function functionName([argname1  [, ...[, argnameN]]])  
{  
   body  
}  
```  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
functionName = new Function( [argname1,  [... argnameN,]] body );  
```  
  
## <a name="parameters"></a>Parâmetros  
 `functionName`  
 Necessário. O nome da função recém-criado  
  
 `argname1...argnameN`  
 Opcional. Uma lista de argumentos que aceitos pela função.  
  
 `body`  
 Opcional. Uma cadeia de caracteres que contém o bloco de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] código a ser executado quando a função é chamada.  
  
## <a name="remarks"></a>Comentários  
 A função é um tipo de dados básicos em [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]. A sintaxe 1 cria um valor de função [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] converte em uma `Function` objeto quando necessário. [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]converte `Function` objetos criados por 2 de sintaxe em valores de função no momento em que a função é chamada.  
  
 A sintaxe 1 é o modo padrão para criar novas funções no [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]. A sintaxe 2 é uma forma alternativa usada para criar objetos de função explicitamente.  
  
 Por exemplo, para declarar uma função que adiciona os dois argumentos passados para ele, você pode fazer isso em uma das duas maneiras:  
  
## <a name="example-1"></a>Exemplo 1  
  
```JavaScript  
function add(x, y)  
{  
   return(x + y);  
}  
```  
  
## <a name="example-2"></a>Exemplo 2  
  
```  
var add = function(x, y) {  
     return(x+y);  
}  
```  
  
 Em ambos os casos, você chama a função com uma linha de código semelhante ao seguinte:  
  
```JavaScript  
add(2, 3);  
```  
  
> [!NOTE]
>  Quando você chama uma função, certifique-se de que você sempre incluir os parênteses e os argumentos necessários. Chamando uma função sem parênteses faz com que a função a ser retornado, em vez do valor de retorno da função.  
  
## <a name="properties"></a>Propriedades  
 [0... n propriedades](../../javascript/reference/0-dot-dot-dot-n-properties-arguments-javascript.md) &#124;[ Propriedade arguments](../../javascript/reference/arguments-property-function-javascript.md) &#124; [propriedade callee](../../javascript/reference/callee-property-arguments-javascript.md) &#124; [propriedade caller](../../javascript/reference/caller-property-function-javascript.md) &#124; [propriedade constructor](../../javascript/reference/constructor-property-object-javascript.md) &#124; [propriedade length (função)](../../javascript/reference/length-property-function-javascript.md) &#124; [propriedade prototype](../../javascript/reference/prototype-property-object-javascript.md)  
  
## <a name="methods"></a>Métodos  
 [Método Apply](../../javascript/reference/apply-method-function-javascript.md) &#124; [método bind](../../javascript/reference/bind-method-function-javascript.md) &#124; [chamar o método](../../javascript/reference/call-method-function-javascript.md) &#124; [método toString](../../javascript/reference/tostring-method-object-javascript.md) &#124; [método valueOf](../../javascript/reference/valueof-method-object-javascript.md)  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Function](../../javascript/reference/function-statement-javascript.md)   
 [Operador new](../../javascript/reference/new-operator-decrementjavascript.md)   
 [Instrução var](../../javascript/reference/var-statement-javascript.md)