---
title: Instrução switch (JavaScript) | Microsoft Docs
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
- switch_JavaScriptKeyword
- default_JavaScriptKeyword
- case_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- switch statement
ms.assetid: 61f80e8b-3739-4146-a893-c2832d92b28c
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a301fc8bcc72b48c6ba8e999c0ebb70fe9d92b41
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641306"
---
# <a name="switch-statement-javascript"></a>Instrução switch (JavaScript)
Habilita a execução de uma ou mais instruções quando o valor de uma expressão especificada corresponde a um rótulo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
switch (expression) {  
    case label :  
        statementlist  
    case label :  
    default :  
        statementlist  
}   
```  
  
## <a name="parameters"></a>Parâmetros  
 `expression`  
 A expressão a ser avaliada.  
  
 `label`  
 Um identificador a ser comparado com `expression`. Se `label` é um `expression`, execução começa com o `statementlist` imediatamente após os dois-pontos e continua até encontrar um `break` instrução, que é opcional, ou até o fim do `switch` instrução.  
  
 `statementlist`  
 Uma ou mais instruções a serem executadas.  
  
## <a name="remarks"></a>Comentários  
 Use o `default` cláusula para fornecer uma instrução a ser executada se nenhum rótulo valores correspondências `expression`. Ele pode aparecer em qualquer lugar dentro do `switch` bloco de código.  
  
 Zero ou mais `label` blocos podem ser especificados. Se nenhum `label` corresponde ao valor do `expression`e um `default` caso não for fornecido, não há instruções são executadas.  
  
 Execução flui através de um `switch` instrução da seguinte maneira:  
  
-   Avaliar `expression` e examine `label` na ordem até que uma correspondência for encontrada.  
  
-   Se um `label` valor for igual a `expression`, execute a seus que acompanha `statementlist`.  
  
     Continuar a execução até que um `break` instrução for encontrada, ou o `switch` termina de instrução. Isso significa que várias `label` blocos são executados se um `break` instrução não é usada.  
  
-   Se nenhum `label` é igual a `expression`, vá para o `default` caso. Se não houver nenhum `default` caso, vá para a última etapa.  
  
-   Continuar em execução na instrução a seguir o fim do `switch` bloco de código.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir testa um objeto para seu tipo.  
  
```JavaScript  
function MyObjectType(obj) {  
    switch (obj.constructor) {  
        case Date:  
            document.write("Object is a Date.");  
            break;  
        case Number:  
            document.write("Object is a Number.");  
            break;  
        case String:  
            document.write("Object is a String.");  
            break;  
        default:  
            document.write("Object is unknown.");  
    }  
}  
  
// Output when obj is a Date:  
// Object is a Date.  
  
// Output when obj is a Number:  
// Object is a Number.  
  
// Output when obj is a String:  
// Object is a String.  
  
// Output when obj is something other than a Date, Number, or String:  
// Object is unknown.  
  
```  
  
## <a name="example"></a>Exemplo  
 O código a seguir mostra o que acontece se você não usar um `break` instrução.  
  
```JavaScript  
function MyObjectType(obj) {  
    switch (obj.constructor) {  
        case Date:  
            document.write("Object is a Date.");  
        case Number:  
            document.write("Object is a Number.");  
        case String:  
            document.write("Object is a String.");  
        default:  
            document.write("Object is unknown.");  
    }  
}  
  
// Output when obj is a Date:  
// Object is a Date.Object is a Number.Object is a String.Object is unknown.  
  
// Output when obj is a Number:  
// Object is a Number.Object is a String.Object is unknown.  
  
// Output when obj is a String:  
// Object is a String.Object is unknown.  
  
// Output when obj is something other than a Date, Number, or String:  
// Object is unknown.  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Instrução break](../../javascript/reference/break-statement-javascript.md)   
 [Instrução if...else](../../javascript/reference/if-dot-dot-dot-else-statement-javascript.md)