---
title: "Função unescape (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: unescape
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: Unescape method
ms.assetid: 4adf0270-88b5-4d54-8110-d879d6ae97c2
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 96601fc21f47c86aec8c3702a6861c3676aacacf
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="unescape-function-javascript"></a>Função unescape (JavaScript)
Decodifica `String` objetos codificados com o `escape` função. Preterido.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
unescape(charString)   
```  
  
## <a name="remarks"></a>Comentários  
 Obrigatório `charString` argumento é uma `String` objeto ou literal a ser decodificado.  
  
 O `unescape` função retorna um valor de cadeia de caracteres que contém o conteúdo de `charstring`. Todos os caracteres codificados com o %*xx* formato hexadecimal são substituídas por seus equivalentes do conjunto de caracteres ASCII.  
  
 Caracteres codificados em **%u** *xxxx* formato (caracteres Unicode) são substituídas pelo caractere Unicode com codificação hexadecimal *xxxx*.  
  
> [!NOTE]
>  O `unescape` função não deve ser usada para decodificar identificadores de recurso uniforme (URI). Use `decodeURI` e `decodeURIComponent` funções.  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Aplica-se a**: [objeto Global](../../javascript/reference/global-object-javascript.md)  
  
## <a name="see-also"></a>Consulte também  
 [Função decodeURI](../../javascript/reference/decodeuri-function-javascript.md)   
 [Função decodeURIComponent](../../javascript/reference/decodeuricomponent-function-javascript.md)   
 [Função escape](../../javascript/reference/escape-function-javascript.md)   
 [Objeto String](../../javascript/reference/string-object-javascript.md)