---
title: Método indexOf (String) (JavaScript) | Microsoft Docs
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
- indexOf
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- indexOf method, string
- string, indexOf method
ms.assetid: a17372fa-669b-471b-9240-46927a265152
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ecd96acb21f9d7711f9ee00dbf1c1bb70705c0d8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637646"
---
# <a name="indexof-method-string-javascript"></a>Método indexOf (String) (JavaScript)
Retorna a posição da primeira ocorrência de uma subcadeia.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
strObj. indexOf(subString[, startIndex])  
```  
  
## <a name="parameters"></a>Parâmetros  
 `strObj`  
 Necessário. Um `String` literal de cadeia de caracteres ou objeto.  
  
 `subString`  
 Necessário. A subcadeia a ser pesquisada na cadeia de caracteres  
  
 `startIndex`  
 Opcional. O índice no qual começar a pesquisar o objeto `String`. Se ele for omitido, a pesquisa começará no início da cadeia de caracteres.  
  
## <a name="remarks"></a>Comentários  
 O **indexOf** método retorna o início da subcadeia de caracteres no `String` objeto. Se a subcadeia não for encontrada, -1 será retornado.  
  
 Se `startindex` for negativo, `startindex` será tratado como zero. Se ele for maior que o índice mais alto, será tratado como o índice mais alto.  
  
 A pesquisa é realizada da esquerda para a direita. Caso contrário, esse método é idêntico ao **lastIndexOf**.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso do **indexOf** método.  
  
```JavaScript  
var str = "original equipment manufacturer";  
  
var s = "equip is at position " + str.indexOf("equip");  
s += "<br />";  
s += "abc is at position " + str.indexOf("abc");  
  
document.write(s);  
  
// Output:  
// equip is at position 9  
// abc is at position -1  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Aplica-se a**: [objeto de cadeia de caracteres](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>Consulte também  
 [Método lastIndexOf (String)](../../javascript/reference/lastindexof-method-string-javascript.md)   
 [Aplicativo de exemplo de rolagem, movimento panorâmico e zoom](http://code.msdn.microsoft.com/ie/Scrolling-panning-and-6834aaf9)