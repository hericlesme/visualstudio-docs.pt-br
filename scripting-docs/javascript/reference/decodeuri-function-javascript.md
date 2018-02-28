---
title: "Função decodeURI (JavaScript) | Microsoft Docs"
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
- decodeURI
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- decodeURI method
ms.assetid: af6c81dc-10f4-4243-a7ce-d18ae3ea0fb8
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 97291142083ae88c7dc84d9cd08af5c3c39ff9e8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="decodeuri-function-javascript"></a>Função decodeURI (JavaScript)
Obtém a versão sem codificação de um codificado identificador URI (Uniform Resource).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
decodeURI(URIstring)  
```  
  
## <a name="remarks"></a>Comentários  
 Obrigatório `URIstring` argumento é um valor que representa um URI codificado.  
  
 Use o `decodeURI` função em vez de preterido `unescape` função.  
  
 O `decodeURI` função retorna um valor de cadeia de caracteres.  
  
 Se o `URIString` não é válido, um URIError ocorre.  
  
 **Aplica-se a**: [objeto Global](../../javascript/reference/global-object-javascript.md)  
  
## <a name="example"></a>Exemplo  
 O código a seguir primeiro codifica um componente URI e, em seguida, decodifica.  
  
```JavaScript  
var uriEncode = encodeURIComponent ("www.Not a URL.com");  
var uriDecode = decodeURIComponent(uriEncode);  
  
document.write (uriEncode);  
document.write ("<br/>");  
document.write (uriDecode);  
  
// Output:  
// www.Not%20a%20URL.com  
// www.Not a URL.com  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Função decodeURIComponent](../../javascript/reference/decodeuricomponent-function-javascript.md)   
 [Função encodeURI](../../javascript/reference/encodeuri-function-javascript.md)   
 [Objeto Global](../../javascript/reference/global-object-javascript.md)