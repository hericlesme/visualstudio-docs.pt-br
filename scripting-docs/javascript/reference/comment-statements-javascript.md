---
title: Comentário de instruções (JavaScript) | Microsoft Docs
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
- Comment_JavaScript
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- comments, ignoring
- comment statements
ms.assetid: b604824f-ac17-49d3-bcdb-2a893ab5fff8
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c270379725550e116928bbecd69e6be51c34992f
ms.sourcegitcommit: 3b692c9bf332b7b9150901e16daf99a64b599fee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/10/2018
---
# <a name="comment-statements-javascript"></a>Instruções de comentário (JavaScript)
Faz com que os comentários sejam ignorados pelo analisador [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Single-line Comment:  
// comment   
```  
  
```  
Multiline Comment:  
/*  
comment  
*/  
```  
  
```  
Comments with conditional compilation:  
//@CondStatement   
  
/*@  
condStatement  
@*/  
```  
  
## <a name="remarks"></a>Comentários  
 O argumento `comment` é o texto de qualquer comentário que você deseja incluir em seu script. O argumento `condStatement` deve ser usado se a compilação condicional for ativada. Se forem usados comentários de linha única, não pode haver nenhum espaço entre os caracteres "//" e "@".  
  
 Use comentários para evitar que partes de um script sejam lidas pelo analisador [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]. Você pode usar comentários para incluir comentários explicativos em um programa.  
  
 Se forem usados comentários de linha única, o analisador ignora qualquer texto entre o marcador de comentário e o fim da linha. Se forem usados comentários de várias linhas, o analisador ignora qualquer texto entre o marcador de início e fim.  
  
 Comentários são usados para dar suporte à compilação condicional enquanto mantém a compatibilidade com navegadores que não oferecem suporte a esse recurso. Esses navegadores tratam essas formas de comentários como comentários de linha única ou de várias linhas, respectivamente.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra os usos mais comuns de comentários.  
  
```JavaScript  
/* This is a multiline comment that  
    can span as many lines as necessary.  */  
function myfunction(arg1, arg2){  
    var r;  
    // This is a single line comment.  
    r = arg1 + arg2  
    return(r);  
}  
```  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar a compilação condicional. Este exemplo usa delimitadores de comentário especiais que são usados somente quando a compilação condicional é ativada pela instrução `@cc_on`. Os mecanismos de script que não dão suporte à compilação condicional enxergam apenas a mensagem informando que não há suporte à compilação condicional.  
  
```JavaScript  
/*@cc_on @*/  
/*@if (@_jscript_version >= 4)  
    alert("JavaScript version 4 or better");  
    @else @*/  
    alert("Conditional compilation not supported by this scripting engine.");  
/*@end @*/  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]