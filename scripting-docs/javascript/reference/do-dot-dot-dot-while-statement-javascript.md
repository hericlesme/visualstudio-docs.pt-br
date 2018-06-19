---
title: Instrução do... While (JavaScript) | Microsoft Docs
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
- do_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- do...while statement
- terminating loops
- loop structures, do and do-while
ms.assetid: 8b7782ba-fbad-48cd-9639-193566da6ae5
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 895d98a3de3a6691ce60bf0456bb838403619f88
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636626"
---
# <a name="dowhile-statement-javascript"></a>Instrução do...while (JavaScript)
Executa um bloco de instruções uma vez e depois repete a execução do loop até que uma expressão de condição for avaliada como `false`.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
do {  
    statement  
}  
while (expression) ;   
```  
  
## <a name="parameters"></a>Parâmetros  
 `statement`  
 Necessário. A instrução a ser executada se `expression` é `true`. Pode ser uma instrução composta.  
  
 `expression`  
 Necessário. Uma expressão que pode ser forçada ao booliano `true` ou `false`. Se `expression` é `true`, o loop é executado novamente. Se `expression` é `false`, o loop é encerrado.  
  
## <a name="remarks"></a>Comentários  
 Ao contrário de `while` instrução, um `do...while` loop é executado uma vez antes da expressão condicional é avaliada.  
  
 Em qualquer linha em uma `do...while` bloco, você pode usar o `break` instrução para fazer com que o fluxo de programa sair do loop, ou você pode usar o `continue` instrução ir diretamente para o `while` expressão.  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, as instruções de `do...while` loop continuar a executar desde que a variável `i` é inferior a 10.  
  
```JavaScript  
var i = 0;  
do {  
    document.write(i + " ");  
    i++;  
} while (i < 10);  
  
// Output: 0 1 2 3 4 5 6 7 8 9   
```  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, as instruções dentro do loop são executadas uma vez, embora a condição não for atendida.  
  
```JavaScript  
var i = 10;  
do {  
    document.write(i + " ");  
    i++;  
} while (i < 10);  
  
// Output: 10  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Instrução break](../../javascript/reference/break-statement-javascript.md)   
 [Instrução continue](../../javascript/reference/continue-statement-javascript.md)   
 [Instrução for](../../javascript/reference/for-statement-javascript.md)   
 [loop for... na instrução](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)   
 [Instrução While](../../javascript/reference/while-statement-javascript.md)   
 [Instrução Labeled](../../javascript/reference/labeled-statement-javascript.md)