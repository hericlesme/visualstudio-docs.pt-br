---
title: "Método match (String) (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: match
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: Match method
ms.assetid: eda9ad27-4f9b-4cb1-8345-a0ae85979ca0
caps.latest.revision: "22"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 46727942d73779351f1c0cceaf2eb90a691a8ebe
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="match-method-string-javascript"></a>Método match (String) (JavaScript)
Corresponde a uma cadeia de caracteres com uma expressão regular e retorna uma matriz que contém os resultados da pesquisa.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
stringObj.match(rgExp)   
```  
  
## <a name="parameters"></a>Parâmetros  
 `stringObj`  
 Necessário. O `String` objeto ou cadeia de caracteres literal no qual executar a pesquisa.  
  
 `rgExp`  
 Necessário. Um objeto de expressão regular que contém o padrão de expressão regular e os sinalizadores aplicáveis. Isso também pode ser um nome de variável ou uma cadeia de caracteres literal que contém o padrão de expressão regular e os sinalizadores.  
  
## <a name="remarks"></a>Comentários  
 Se o `match` método não encontra uma correspondência, ele retorna `null`. Se encontrar uma correspondência, `match` retorna uma matriz e as propriedades de global `RegExp` objeto são atualizadas para refletir os resultados da correspondência.  
  
 Se o sinalizador global (`g`) não está definida, zero da matriz contém a correspondência de inteira, enquanto os elementos 1 por meio do elemento  *n*  contém qualquer subcorrespondentes. Esse comportamento é o mesmo que o comportamento do [método exec (Expressão Regular)](../../javascript/reference/exec-method-regular-expression-javascript.md) quando o sinalizador global não está definido. Se o sinalizador global estiver definido, elementos de 0 por meio de  *n*  contêm todas as correspondências que ocorrem.  
  
 Se o sinalizador global não é definida, a matriz retornada pelo `match` método tem duas propriedades, `input` e `index`. O `input` propriedade contém a cadeia de caracteres pesquisada inteira. O `index` propriedade contém a posição da subcadeia de caracteres correspondente na cadeia de caracteres pesquisada concluída.  
  
 Se o sinalizador `i` está definida, a pesquisa não diferencia maiusculas de minúsculas.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso do método `match`.  
  
```JavaScript  
var src = "azcafAJAC";  
  
var re = /[a-c]/;  
  
var result = src.match(re);  
  
// The entire match is in array element 0.  
document.write(result[0] + "<br/>");  
  
// Now try the same match with the global flag.  
var reg = /[a-c]/g;  
result = src.match(reg);  
  
// The matches are in elements 0 through n.  
for (var index = 0; index < result.length; index++)  
{  
    document.write ("submatch " + index + ": " +  result[index]);  
    document.write("<br />");  
}  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Aplica-se a**: [objeto de cadeia de caracteres](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>Consulte também  
 [Método Exec (Expressão Regular)](../../javascript/reference/exec-method-regular-expression-javascript.md)   
 [Objeto RegExp](../../javascript/reference/regexp-object-javascript.md)   
 [Objeto de expressão regular](../../javascript/reference/regular-expression-object-javascript.md)   
 [Substitua o método (String)](../../javascript/reference/replace-method-string-javascript.md)   
 [Método Search (String)](../../javascript/reference/search-method-string-javascript.md)   
 [Método Test (Expressão Regular)](../../javascript/reference/test-method-regular-expression-javascript.md)   
 [Programação de expressão regular (JavaScript)](http://msdn.microsoft.com/en-us/3b62e27c-4f07-4726-a95b-6e841807bfaf)   
 [Alternação e subexpressões (JavaScript)](http://msdn.microsoft.com/en-us/c59dd3e8-7fee-493e-9123-065af1e651ae)   
 [Referências inversas (JavaScript)](http://msdn.microsoft.com/en-us/5d8dbd5a-cd03-4548-850b-9d7bad2c839a)