---
title: "Método Search (String) (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: search
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: search method
ms.assetid: 1cae0fbc-3319-4327-ba4e-d5fa2c4a9ba0
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 730fb1604147b56fc5ab1e312bf7a6dfb5487a5a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="search-method-string-javascript"></a>Método search (String) (JavaScript)
Localiza a primeira correspondência de subcadeia de caracteres em uma pesquisa de expressão regular.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
stringObj.search(rgExp)   
```  
  
## <a name="parameters"></a>Parâmetros  
 `stringObj`  
 Necessário. O `String` objeto ou cadeia de caracteres literal no qual executar a pesquisa.  
  
 `rgExp`  
 Necessário. Uma instância de um **Expressão Regular** objeto que contém o padrão de expressão regular e os sinalizadores aplicáveis.  
  
## <a name="return-value"></a>Valor de retorno  
 Se uma correspondência for encontrada, o **pesquisa** método retorna um valor inteiro que indica o deslocamento do início da cadeia de caracteres onde a primeira correspondência ocorreu. Se nenhuma correspondência for localizada, ele retornará -1.  
  
## <a name="remarks"></a>Comentários  
 Você também pode definir o `i` sinalizador que faz com que a pesquisa diferenciar maiusculas de minúsculas.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso do **pesquisa** método.  
  
```JavaScript  
var src = "is but a Dream within a dream";  
var re = /dream/;  
var pos = src.search(re);  
document.write(pos);  
document.write("<br/>");  
  
re = /dream/i;  
pos = src.search(re);  
document.write(pos);  
  
// Output:   
// 24   
// 9  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Aplica-se a**: [objeto de cadeia de caracteres](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>Consulte também  
 [Método Exec (Expressão Regular)](../../javascript/reference/exec-method-regular-expression-javascript.md)   
 [Método match (String)](../../javascript/reference/match-method-string-javascript.md)   
 [Objeto de expressão regular](../../javascript/reference/regular-expression-object-javascript.md)   
 [Sintaxe de expressão regular (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)   
 [Substitua o método (String)](../../javascript/reference/replace-method-string-javascript.md)   
 [Método Test (Expressão Regular)](../../javascript/reference/test-method-regular-expression-javascript.md)   
 [Programação de expressão regular (JavaScript)](http://msdn.microsoft.com/en-us/3b62e27c-4f07-4726-a95b-6e841807bfaf)