---
title: "Método substr (String) (JavaScript) | Microsoft Docs"
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
- substr
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- substr method
ms.assetid: f12541c1-2623-482e-941d-2e22bc3c4a4a
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6b002bfefbeb81c534c882fa4a4720c93ccca185
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="substr-method-string-javascript"></a>Método substr (String) (JavaScript)
Obtém uma subcadeia de caracteres começando no local especificado e com o comprimento especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
stringvar.substr(start [, length ])   
```  
  
## <a name="parameters"></a>Parâmetros  
 `stringvar`  
 Necessário. Uma cadeia de caracteres literal ou `String` da qual a subcadeia de caracteres é extraída do objeto.  
  
 `start`  
 Necessário. A posição inicial da subcadeia de caracteres desejada. O índice do primeiro caractere na cadeia de caracteres é zero.  
  
 `length`  
 Opcional. O número de caracteres a ser incluído na subcadeia de caracteres retornada.  
  
## <a name="remarks"></a>Comentários  
 Se `length` for zero ou negativo, uma cadeia de caracteres vazia é retornada. Se não for especificado, a subcadeia de caracteres continua até o final de `stringvar`.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso do método `substr`.  
  
```JavaScript  
var s = "The quick brown fox jumps over the lazy dog.";  
var ss = s.substr(10, 5);    
document.write("[" + ss + "] <br>");  
  
ss = s.substr(10);  
document.write("[" + ss + "] <br>");  
  
ss = s.substr(10, -5);  
document.write("[" + ss + "] <br>");  
  
// Output:  
// [brown]   
// [brown fox jumps over the lazy dog.]   
// []  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Aplica-se a**: [objeto de cadeia de caracteres](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>Consulte também  
 [Método substring (String)](../../javascript/reference/substring-method-string-javascript.md)