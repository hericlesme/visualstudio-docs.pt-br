---
title: stackTraceLimit propriedade (Error) (JavaScript) | Microsoft Docs
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
- Error.stackTraceLimit
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- error stack track limit [JavaScript]
- JavaScript error stack
- error stack [JavaScript]
- JavaScript stack trace limit
ms.assetid: 127ef8e8-892e-4263-9ebc-03364af01212
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9af736ee8b385f93b761f1dfa021c23ee5376292
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="stacktracelimit-property-error-javascript"></a>stackTraceLimit Propriedade (Error) (JavaScript)
Obtém ou define o limite de rastreamento de pilha, que é equivalente ao número de quadros de erro para exibir. O limite padrão é 10.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
Error  
.stackTraceLimit   
```  
  
## <a name="remarks"></a>Comentários  
 Você pode definir o `stackTraceLimit` propriedade para qualquer valor positivo entre 0 e `Infinity`. Se o `stackTraceLimit` estiver definida como 0 no momento em que um erro será lançado, não há rastreamento de pilha é mostrado. Se a propriedade é definida como um valor negativo ou um valor não numérico, o valor é convertido em 0. Se o stackTraceLimit for definido como `Infinity`, toda a pilha é mostrada. Caso contrário, `ToUint32` é usado para converter o valor.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como definir e, em seguida, obter o limite de rastreamento de pilha.  
  
```JavaScript  
try  
    {  
    var err = new Error("my error");  
    Error.stackTraceLimit = 7;  
    throw err;  
    }  
catch(e)  
    {  
    document.write ("Error stack trace limit: ")  
    document.write (Error.stackTraceLimit);  
    }  
```  
  
## <a name="requirements"></a>Requisitos  
 Suporte no Internet Explorer 10 e no [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] aplicativos.  
  
 **Aplica-se a**: [objeto Error](../../javascript/reference/error-object-javascript.md)  
  
## <a name="see-also"></a>Consulte também  
 [Propriedade Description (erro)](../../javascript/reference/description-property-error-javascript.md)   
 [Propriedade Message (erro)](../../javascript/reference/message-property-error-javascript.md)   
 [Propriedade Name (erro)](../../javascript/reference/name-property-error-javascript.md)   
 [Propriedade stack (Error)](../../javascript/reference/stack-property-error-javascript.md)