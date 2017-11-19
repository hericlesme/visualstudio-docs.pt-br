---
title: "Método Exec (Expressão Regular) (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: exec
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- matching strings
- Exec method
ms.assetid: 83092452-60cc-4218-b4ae-af9e3cb96c34
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 426cc1a8162b03090289cf737a03d64a75df77e9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="exec-method-regular-expression-javascript"></a>Método exec (expressão regular) (JavaScript)
Executa uma pesquisa em uma cadeia de caracteres usando um padrão de expressão regular e retorna uma matriz que contém os resultados da pesquisa.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
rgExp.exec(str)   
```  
  
## <a name="parameters"></a>Parâmetros  
 `rgExp`  
 Necessário. Uma instância de um **Expressão Regular** objeto que contém o padrão de expressão regular e os sinalizadores aplicáveis.  
  
 `str`  
 Necessário. O `String` objeto ou cadeia de caracteres literal no qual executar a pesquisa.  
  
## <a name="remarks"></a>Comentários  
 Se o `exec` método não encontra uma correspondência, ele retorna `null`. Se encontrar uma correspondência, `exec` retorna uma matriz e as propriedades de global `RegExp` objeto são atualizadas para refletir os resultados da correspondência. Zero do elemento da matriz contém a correspondência de inteira, enquanto os elementos 1 -  *n*  contém qualquer subcorrespondentes ocorridas durante a correspondência. Esse comportamento é idêntico ao comportamento do `match` método sem o sinalizador global (**g**) definido.  
  
 Se o sinalizador global é definido para uma expressão regular, `exec` pesquisa no início da cadeia de caracteres na posição indicada pelo valor de `lastIndex`. Se o sinalizador global não for definido, `exec` ignora o valor de `lastIndex` e pesquisas desde o início da cadeia de caracteres.  
  
 A matriz retornada pelo `exec` método tem três propriedades, **entrada**, **índice** e **lastIndex.** O **entrada** propriedade contém a cadeia de caracteres pesquisada inteira. O **índice** propriedade contém a posição da subcadeia de caracteres correspondente na cadeia de caracteres pesquisada concluída. O `lastIndex` propriedade contém a posição após o último caractere na correspondência.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso do `exec` método:  
  
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
      document.write (arr.index + "-" + arr.lastIndex + " ");  
      document.write (arr[0]);  
      }  
}  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Aplica-se a**: [objeto Regular Expression](../../javascript/reference/regular-expression-object-javascript.md)  
  
## <a name="see-also"></a>Consulte também  
 [Método match (String)](../../javascript/reference/match-method-string-javascript.md)   
 [Objeto RegExp](../../javascript/reference/regexp-object-javascript.md)   
 [Sintaxe de expressão regular (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)   
 [Método Search (String)](../../javascript/reference/search-method-string-javascript.md)   
 [Método Test (Expressão Regular)](../../javascript/reference/test-method-regular-expression-javascript.md)   
 [Programação de expressão regular (JavaScript)](http://msdn.microsoft.com/en-us/3b62e27c-4f07-4726-a95b-6e841807bfaf)