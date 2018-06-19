---
title: Função decodeURIComponent (JavaScript) | Microsoft Docs
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
- decodeURIComponent
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- decodeURIComponent method
ms.assetid: 486ccee2-afd7-4863-97ce-4adb50cf39c0
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ef7bdcd374a328bad632381d19e9823853d37f01
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636186"
---
# <a name="decodeuricomponent-function-javascript"></a>Função decodeURIComponent (JavaScript)
Obtém a versão sem codificação de um componente codificado de identificador de um recurso uniforme (URI).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
decodeURIComponent(encodedURIString)  
```  
  
## <a name="remarks"></a>Comentários  
 Obrigatório `encodedURIString` argumento é um valor que representa um componente URI codificado.  
  
 Um URIComponent faz parte de um URI completo.  
  
 Se o `encodedURIString` não é válido, um URIError ocorre.  
  
## <a name="example"></a>Exemplo  
 O código a seguir primeiro codifica e decodifica, em seguida, um URI.  
  
```JavaScript  
var uriEncode = encodeURI ("http://www.Not a URL.com");  
var uriDecode = decodeURIComponent(uriEncode);  
  
document.write (uriEncode);  
document.write("<br/>");  
document.write (uriDecode);  
  
// Output:  
// http://www.Not%20a%20URL.com  
// http://www.Not a URL.com  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Função decodeURI](../../javascript/reference/decodeuri-function-javascript.md)   
 [Função encodeURI](../../javascript/reference/encodeuri-function-javascript.md)