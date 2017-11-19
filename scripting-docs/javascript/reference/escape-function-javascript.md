---
title: "Função escape (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: escape
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- encoding string objects
- Escape method
- hexadecimal
- String object, encoding
ms.assetid: caa92bea-ba69-4109-a68a-6e2debda463a
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b53a447ae6dde917c12a4711d9038136dc4500cf
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="escape-function-javascript"></a>Função escape (JavaScript)
Codifica cadeias de caracteres para que podem ser lido em todos os computadores. Preterido.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
escape(charString)   
```  
  
## <a name="remarks"></a>Comentários  
 Obrigatório `charString` é qualquer `String` objeto ou literal a ser decodificado.  
  
 O **escape** função retorna um valor de cadeia de caracteres (em formato Unicode) que contém o conteúdo do `charstring`. Todos os espaços, pontuações acentuadas caracteres, e quaisquer outros caracteres não ASCII são substituídos por `%` *xx* codificação, onde *xx* equivale a número hexadecimal que representa o caractere. Por exemplo, um espaço é retornado como "% 20".  
  
 Caracteres com um valor maior que 255 são armazenados usando o **%u** *xxxx* formato.  
  
> [!NOTE]
>  O **escape** função não deve ser usada para codificar os identificadores de recurso uniforme (URI). Use `encodeURI` e `encodeURIComponent` funções.  
  
 **Aplica-se a**: [objeto Global](../../javascript/reference/global-object-javascript.md)  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Função encodeURI](../../javascript/reference/encodeuri-function-javascript.md)   
 [Função encodeURIComponent](../../javascript/reference/encodeuricomponent-function-javascript.md)   
 [Objeto de cadeia de caracteres](../../javascript/reference/string-object-javascript.md)   
 [Função unescape](../../javascript/reference/unescape-function-javascript.md)