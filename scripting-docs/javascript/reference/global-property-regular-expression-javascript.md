---
title: "Propriedade global (Expressão Regular) (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: Global
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: global property
ms.assetid: 76a0f115-0d89-4aca-86d5-932895c6d649
caps.latest.revision: "19"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7e2b0256fea60b7ab998c504e79565fc7028cd98
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="global-property-regular-expression-javascript"></a>Propriedade global (expressão regular) (JavaScript)
Retorna um valor booliano que indica o estado do sinalizador global (**g**) usado com uma expressão regular. O padrão é **false**. Somente leitura.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
rgExp.global  
```  
  
## <a name="remarks"></a>Comentários  
 Obrigatório `rgExp` referência é uma instância de um **Expressão Regular** objeto.  
  
 O `global` propriedade retorna **true** se o sinalizador global está definido para uma expressão regular e retorna **false** se não for.  
  
 O sinalizador global, quando usado, indica que uma pesquisa deve localizar todas as ocorrências do padrão na cadeia de caracteres pesquisada, não apenas o primeiro deles. Isso também é conhecido como correspondência global.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso do `global` propriedade. Se você passar **g** para a função mostrada abaixo, todas as instâncias da palavra "the" não são substituídas por "a". Observe que a "The" no início da cadeia de caracteres não é substituída porque o **,** (Ignorar maiusculas e minúsculas) sinalizador não for passado para a função.  
  
 Esta função exibe a condição das propriedades associadas com os sinalizadores de expressão regular permitido, que são **g**, **,**, e **m**. A função também exibe a cadeia de caracteres com todas as substituições feitas.  
  
```JavaScript  
function RegExpPropDemo(flag){  
   // The flag parameter is a string that contains  
   // g, i, or m.  The flags can be combined.  
  
   // Check flags for validity.  
   if (flag.match(/[^gim]/))  
      {  
      return ("Flag specified is not valid");  
      }  
  
   // Create the string on which to perform the replacement.  
   var ss = "The batter hit the ball with the bat ";  
   ss += "and the fielder caught the ball with the glove.";  
  
   //Replace "the" with "a".  
   var re = new RegExp("the", flag);  
   var r = ss.replace(re, "a");          
  
   // Output the resulting string and the flags.  
   var s = "";  
   s += "global: " + re.global.toString();  
   s += "<br />";  
   s += "ignoreCase: " + re.ignoreCase.toString();  
   s += "<br />";  
   s += "multiline: " + re.multiline.toString();  
   s += "<br />";  
   s += "Resulting String: " + r;  
  
   return (s);  
}  
  
document.write(RegExpPropDemo("g"));  
```  
  
## <a name="example"></a>Exemplo  
 A seguir está a saída resultante.  
  
```JavaScript  
global: true  
ignoreCase: false  
multiline: false  
Resulting String: The batter hit a ball with a bat and a fielder caught a ball with a glove.  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Aplica-se a**: [objeto Regular Expression](../../javascript/reference/regular-expression-object-javascript.md)  
  
## <a name="see-also"></a>Consulte também  
 [Propriedade ignoreCase (Expressão Regular)](../../javascript/reference/ignorecase-property-regular-expression-javascript.md)   
 [Propriedade Multiline (Expressão Regular)](../../javascript/reference/multiline-property-regular-expression-javascript.md)   
 [Sintaxe de expressão regular (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)