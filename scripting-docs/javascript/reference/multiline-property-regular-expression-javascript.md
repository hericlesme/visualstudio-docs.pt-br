---
title: "Propriedade Multiline (Expressão Regular) (JavaScript) | Microsoft Docs"
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
- multiline
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- multiline property
ms.assetid: ca7b276a-1fe2-4189-ac27-f089ab3e9974
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 289cb8d8e103d8c4ac1b1ef06714105d21cba743
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="multiline-property-regular-expression-javascript"></a>Propriedade multiline (expressão regular) (JavaScript)
Retorna um valor booliano que indica o estado do sinalizador várias linhas (**m**) usado com uma expressão regular. O padrão é **false**. Somente leitura.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
rgExp.multiline  
```  
  
## <a name="remarks"></a>Comentários  
 Obrigatório `rgExp` argumento é uma ocorrência da `RegExp` objeto  
  
 O **várias linhas** propriedade retorna **true** se o sinalizador de várias linhas é definido para uma expressão regular e retorna **false** se não for. O **várias linhas** é de propriedade **true** se o objeto de expressão regular foi criado com o **m** sinalizador.  
  
 Se **várias linhas** é **false**, "^" corresponde a posição no início de uma cadeia de caracteres e "$" corresponde à posição do final de uma cadeia de caracteres. Se **várias linhas** é **true**, "^" corresponde à posição no início de uma cadeia de caracteres, como a posição após um "\n" ou "\r" e "$" corresponde à posição do final de uma cadeia de caracteres e a posição anterior "\n "ou"\r".  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o comportamento do **várias linhas** propriedade. Se você passar "m" para a função mostrada abaixo, a palavra "while" será substituída com a palavra "e". Isso é porque está definida com o sinalizador de várias linhas e a palavra "ao" ocorre no início da linha após o caractere de nova linha. O sinalizador de várias linhas permite que a pesquisa a ser executada em cadeias de caracteres de várias linhas.  
  
```JavaScript  
function RegExpMultilineDemo(flag){  
   // The flag parameter is a string that contains  
   // g, i, or m.  The flags can be combined.  
  
   // Check flags for validity.  
   if (flag.match(/[^gim]/))  
      {  
      return ("Flag specified is not valid");  
      }  
  
   // Create the string on which to perform the replacement.  
   var ss = "The man hit the ball with the bat ";  
   ss += "\nwhile the fielder caught the ball with the glove.";  
  
   // Replace "while" with "and".  
   var re = new RegExp("^while", flag);  
   var r = ss.replace(re, "and");          
  
   // Output the multiline flag and the resulting string.  
   var s = "";  
   s += "Result for multiline = " + re.multiline.toString();  
   s += ": " + r;  
  
   return(s);  
  
}  
  
sa = RegExpMultilineDemo("m");  
sb = RegExpMultilineDemo("");  
document.write (sa + "<br />" + sb);  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Aplica-se a**: [objeto Regular Expression](../../javascript/reference/regular-expression-object-javascript.md)  
  
## <a name="see-also"></a>Consulte também  
 [Propriedade global (Expressão Regular)](../../javascript/reference/global-property-regular-expression-javascript.md)   
 [Propriedade ignoreCase (Expressão Regular)](../../javascript/reference/ignorecase-property-regular-expression-javascript.md)   
 [Sintaxe de expressão regular (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)