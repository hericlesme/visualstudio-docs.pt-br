---
title: Propriedade ignoreCase (Expressão Regular) (JavaScript) | Microsoft Docs
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
- ignoreCase
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- IgnoreCase property
ms.assetid: 816f0df5-5a82-44a5-a4ab-dbc91fa76e61
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ae9fee8e6303fb944f59c11c173f9e8b7f7cc75a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637856"
---
# <a name="ignorecase-property-regular-expression-javascript"></a>Propriedade ignoreCase (expressão regular) (JavaScript)
Retorna um valor booliano que indica o estado do sinalizador ignoreCase (**,**) usado com uma expressão regular. O padrão é **false**. Somente leitura.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
rgExp.ignoreCase  
```  
  
## <a name="remarks"></a>Comentários  
 Obrigatório `rgExp` referência é uma ocorrência da `RegExp` objeto.  
  
 O **ignoreCase** propriedade retorna **true** se o sinalizador ignoreCase está definido para uma expressão regular e retorna **false** se não for.  
  
 O sinalizador ignoreCase, quando usado, indica que uma pesquisa deve ignorar maiusculas e minúsculas durante a correspondência de padrão na cadeia de caracteres pesquisada.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso do **ignoreCase** propriedade. Se você passar "gi" para a função mostrada abaixo, todas as instâncias da palavra "the" não são substituídas por "a", incluindo inicial "A". Isso é porque com a definição do sinalizador ignoreCase pesquisa ignora qualquer diferenciação de maiusculas e minúsculas. Portanto "T" é igual a "t" para fins de correspondência.  
  
 Esta função retorna os valores booleanos que indicam o estado dos sinalizadores permitidos de expressão regular, que são **g**, **,**, e **m**. A função também retorna a cadeia de caracteres com todas as substituições feitas.  
  
```JavaScript  
function RegExpPropDemo(flag){  
    // The flag parameter is a string that contains  
    // g, i, or m. The flags can be combined.  
  
    // Check flags for validity.  
    if (flag.match(/[^gim]/))  
        {  
        return ("Flag specified is not valid");  
        }  
  
    // Create the string on which to perform the replacement.  
    var orig = "The batter hit the ball with the bat ";  
    orig += "and the fielder caught the ball with the glove.";  
  
    // Replace "the" with "a".  
    var re = new RegExp("the", flag);  
    var r = orig.replace(re, "a");          
  
    // Output the resulting string and the values of the flags.  
    var s = "";  
    s += "global: " + re.global.toString();  
    s += "<br />";  
    s += "ignoreCase: " + re.ignoreCase.toString();  
    s += "<br />";  
    s += "multiline: " + re.multiline.toString();  
    s += "<br />";  
    s += "Resulting String: " + r;  
    s += "<br />";  
    s += "<br />";  
    return (s);  
}  
  
document.write(RegExpPropDemo("gi"));  
document.write(RegExpPropDemo("g"));  
```  
  
## <a name="example"></a>Exemplo  
 A seguir está a saída resultante.  
  
```JavaScript  
global: true  
ignoreCase: true  
multiline: false  
Resulting String: a batter hit a ball with a bat and a fielder caught a ball with a glove.  
  
global: true  
ignoreCase: false  
multiline: false  
Resulting String: The batter hit a ball with a bat and a fielder caught a ball with a glove.  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Aplica-se a**: [objeto Regular Expression](../../javascript/reference/regular-expression-object-javascript.md)  
  
## <a name="see-also"></a>Consulte também  
 [Propriedade global (Expressão Regular)](../../javascript/reference/global-property-regular-expression-javascript.md)   
 [Propriedade Multiline (Expressão Regular)](../../javascript/reference/multiline-property-regular-expression-javascript.md)   
 [Sintaxe de expressão regular (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)