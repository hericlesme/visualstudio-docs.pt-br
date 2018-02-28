---
title: Propriedade Stack (Error) (JavaScript) | Microsoft Docs
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
- Error.stack
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- JavaScript error stack
- error stack [JavaScript]
ms.assetid: 1dc21fdd-853c-4664-bf1c-24eb1f6f2daf
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 14e4a2537b1543b7e8d9727afdeb8ea5dee61bbc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="stack-property-error-javascript"></a>Propriedade stack (Error) (JavaScript)
Obtém ou define a pilha de erro como uma cadeia de caracteres que contém os quadros de rastreamento de pilha.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
object  
.stack   
```  
  
## <a name="remarks"></a>Comentários  
 A propriedade `stack` está definida como `undefined` quando o erro é construído e obtém as informações de rastreamento quando o erro é gerado. Se um erro ocorrer várias vezes, a propriedade `stack` será atualizada sempre que o erro for gerado.  
  
 Registros de ativação são exibidos no seguinte formato: **em FunctionName (\<nome/URL totalmente qualificada >:\<número da linha >:\<número da coluna >)**  
  
 Se você criar o seu próprio objeto de erro e definir o rastreamento de pilha para um valor, o valor não será substituído quando o erro for gerado.  
  
 A propriedade `stack` não mostra as funções embutidas em seus quadros. Ela mostra apenas a pilha física.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como obter a pilha quando estamos obtendo um erro.  
  
```JavaScript  
try  
    {  
        var x = y.name;  
    }  
catch(e)  
    {  
        document.write ("Error stack: ")  
        document.write (e.stack);  
    }  
```  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como definir e, em seguida, obter a pilha.  
  
```JavaScript  
try  
    {  
        var err = Error("my error");  
        err.stack = "my stack trace";  
        throw err;  
    }  
catch(e)  
    {  
        document.write ("Error stack: ")  
        document.write (e.stack);  
    }  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]  
  
 **Aplica-se a**: [objeto Error](../../javascript/reference/error-object-javascript.md)  
  
## <a name="see-also"></a>Consulte também  
 [Propriedade Description (erro)](../../javascript/reference/description-property-error-javascript.md)   
 [Propriedade Message (erro)](../../javascript/reference/message-property-error-javascript.md)   
 [Propriedade Name (erro)](../../javascript/reference/name-property-error-javascript.md)   
 [Propriedade stackTraceLimit (Error)](../../javascript/reference/stacktracelimit-property-error-javascript.md)