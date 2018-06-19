---
title: Função encodeURIComponent (JavaScript) | Microsoft Docs
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
- encodeURIComponent
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- encodeURIComponent method
ms.assetid: 8202bce6-1342-40dc-a5ef-ac6d210a7d15
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 56680e9bcfe1de61d8a1eabd0ff8d2eced01d603
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636426"
---
# <a name="encodeuricomponent-function-javascript"></a>Função encodeURIComponent (JavaScript)
Codifica uma cadeia de caracteres de texto como um componente válido de identificador de um recurso uniforme (URI).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
encodeURIComponent(encodedURIString)  
```  
  
## <a name="remarks"></a>Comentários  
 Obrigatório `encodedURIString` argumento é um valor que representa um componente URI codificado.  
  
 O `encodeURIComponent` função retorna um URI codificado. Se você passar o resultado para `decodeURIComponent`, a cadeia de caracteres original será retornada. Porque o `encodeURIComponent` função codifica todos os caracteres, seja cuidadoso se a cadeia de caracteres representa um caminho como **/folder1/folder2/default.html**. Os caracteres de barra serão codificados e não será válidos se enviado como uma solicitação para um servidor web. Use o `encodeURI` funcionar se a cadeia de caracteres contém mais de um único componente URI.  
  
## <a name="example"></a>Exemplo  
 O código a seguir primeiro codifica um componente URI e, em seguida, decodifica.  
  
```JavaScript  
var uriEncode = encodeURIComponent ("www.Not a URL.com");  
var uriDecode = decodeURIComponent(uriEncode);  
  
document.write(uriEncode);  
document.write("<br/>");  
document.write(uriDecode);  
  
// Output:  
// www.Not%20a%20URL.com  
// www.Not a URL.com  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Função decodeURI](../../javascript/reference/decodeuri-function-javascript.md)   
 [Função DecodeURIComponent](../../javascript/reference/decodeuricomponent-function-javascript.md)