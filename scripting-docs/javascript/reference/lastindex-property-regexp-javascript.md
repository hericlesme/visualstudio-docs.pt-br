---
title: Propriedade lastIndex (RegExp) (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: lastIndex
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: lastIndex property
ms.assetid: c8ae2a13-6dff-4cbe-b662-aca3d66c2a7f
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d5e24fe14d335e1494b13518543f56025625de0b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="lastindex-property-regexp-javascript"></a>Propriedade lastIndex (RegExp) (JavaScript)
Retorna a posição do caractere em que começa a próxima correspondência em uma cadeia de caracteres pesquisada.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
RegExp.lastIndex  
```  
  
## <a name="remarks"></a>Comentários  
 O objeto associado a essa propriedade é sempre global `RegExp` objeto.  
  
 O `lastIndex` é baseado em zero, ou seja, o índice do primeiro caractere é zero. Valor inicial é -1. Seu valor é modificado sempre que uma correspondência é feita.  
  
 O `lastIndex` propriedade seja modificada pelo `exec` e **teste** métodos do `RegExp` objeto e o `match`, **substituir**, e **dividir**métodos do `String` objeto.  
  
 As seguintes regras se aplicam aos valores de `lastIndex`:  
  
-   Se não houver nenhuma correspondência, `lastIndex` é definido como -1.  
  
-   Se `lastIndex` é maior que o comprimento da cadeia de caracteres, **teste** e `exec` falhar e `lastIndex` é definido como -1.  
  
-   Se `lastIndex` é igual ao comprimento da cadeia de caracteres, as correspondências de expressão regular, se o padrão corresponde a cadeia de caracteres vazia. Caso contrário, a correspondência falhar e `lastIndex` é redefinido como -1.  
  
-   Caso contrário, `lastIndex` é definido para a próxima posição após a correspondência mais recente.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso do `lastIndex` propriedade. Essa função itera uma cadeia de caracteres de pesquisa e imprime o **índice** e `lastIndex` valores para cada palavra na cadeia de caracteres.  
  
```JavaScript  
function RegExpTest()  
{  
   var ver = Number(ScriptEngineMajorVersion() + "." + ScriptEngineMinorVersion())  
   if (ver < 5.5)  
   {  
      document.write("You need a newer version of JavaScript for this to work");  
      return;  
   }  
  
   var src = "The quick brown fox jumps over the lazy dog.";  
  
   // Create regular expression pattern with a global flag.  
   var re = /\w+/g;  
  
   // Get the next word, starting at the position of lastindex.  
   var arr;  
   while ((arr = re.exec(src)) != null)  
      {  
      // New line:  
      document.write ("<br />");    
      document.write (arr.index + "-" + re.lastIndex + " ");  
      document.write (arr);  
      }  
}  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Aplica-se a**: [objeto RegExp](../../javascript/reference/regexp-object-javascript.md)  
  
## <a name="see-also"></a>Consulte também  
 [Sintaxe de expressão regular (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)