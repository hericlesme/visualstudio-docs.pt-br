---
title: "Método Includes (String) (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 2639e4e5-23ba-424a-80ea-be067a4cd65e
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 848143b64d3e32452aea41f08b6f5c57879d3e17
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="includes-method-string-javascript"></a>Método includes (String) (JavaScript)
Retorna um valor booliano que indica se a cadeia de caracteres transmitida está contida no objeto de cadeia de caracteres.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
stringObj.includes(substring [, position]);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `stringObj`  
 Necessário. O objeto de cadeia de caracteres a ser usado no teste.  
  
 `substring`  
 Necessário. A cadeia de caracteres a ser testada.  
  
 `position`  
 Opcional. A posição do primeiro caractere a ser testado com relação ao objeto de cadeia de caracteres, começando com 0.  
  
## <a name="return-value"></a>Valor de retorno  
 Se a cadeia de caracteres transmitida estiver contida no objeto de cadeia de caracteres, o método `includes` retorna `true`. Caso contrário, retorna `false`.  
  
## <a name="remarks"></a>Comentários  
  
## <a name="example"></a>Exemplo  
  
```JavaScript  
// Returns true   
"abcde".includes("cd")  
"abcde".includes("cd", 2)  
  
// Returns false  
"abcde".includes("CD")  
"abcde".includes("cd", 3)  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]