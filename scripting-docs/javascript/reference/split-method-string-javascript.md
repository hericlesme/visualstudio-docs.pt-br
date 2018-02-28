---
title: "dividir o método (String) (JavaScript) | Microsoft Docs"
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
- split
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- split method
ms.assetid: 7f093336-c887-4efb-b91f-819b6d18a181
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eea90dda2e8e4d52451af247d139eeee44f83917
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="split-method-string-javascript"></a>Método split (Cadeia de Caracteres) (JavaScript)
Divide uma cadeia de caracteres em subcadeias usando o separador especificado e retorna-as como uma matriz.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
stringObj.split([separator[, limit]])  
```  
  
## <a name="parameters"></a>Parâmetros  
 `stringObj`  
 Necessário. O objeto `String` ou literal de cadeia de caracteres a ser dividido. Este objeto não for modificado com o **dividir** método.  
  
 `separator`  
 Opcional. Uma cadeia de caracteres ou uma **Expressão Regular** objeto que identifica um ou mais caracteres para usar em separar a cadeia de caracteres. Se for omitido, uma matriz de um único elemento que contém a cadeia de caracteres inteira será retornada.  
  
 `limit`  
 Opcional. Um valor usado para limitar o número de elementos retornados na matriz.  
  
## <a name="return-value"></a>Valor de retorno  
 O resultado da **dividir** método é uma matriz de cadeias de caracteres dividido em cada ponto onde `separator` ocorre em `stringObj`. O `separator` não é retornado como parte de um elemento de matriz.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso do **dividir** método.  
  
```JavaScript  
var s = "The quick brown fox jumps over the lazy dog.";  
var ss = s.split(" ");  
for (var i in ss) {  
    document.write(ss[i]);  
    document.write("<br/>");  
}  
  
// Output:   
// The  
// quick  
// brown  
// fox  
// jumps  
// over  
// the  
// lazy  
// dog.  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Aplica-se a**: [objeto de cadeia de caracteres](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>Consulte também  
 [Método concat (String)](../../javascript/reference/concat-method-string-javascript.md)   
 [Objeto RegExp](../../javascript/reference/regexp-object-javascript.md)   
 [Objeto de expressão regular](../../javascript/reference/regular-expression-object-javascript.md)   
 [Sintaxe de expressão regular (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)   
 [Aplicativo de exemplo de rolagem, movimento panorâmico e zoom](http://code.msdn.microsoft.com/ie/Scrolling-panning-and-6834aaf9)