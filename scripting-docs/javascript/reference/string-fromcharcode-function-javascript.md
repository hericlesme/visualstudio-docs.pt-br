---
title: Função String fromCharCode (JavaScript) | Microsoft Docs
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
- fromCharCode
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- fromCharCodeAt method
- characters, from Unicode
ms.assetid: f64120c1-23a7-48ca-8d1c-db3e8856cab4
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dbcd9062d7da0b73647c1d9eb6cc207af23c3532
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639836"
---
# <a name="stringfromcharcode-function-javascript"></a>Função String.fromCharCode (JavaScript)
Retorna uma cadeia de caracteres de um número de valores de caracteres Unicode.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
String.fromCharCode([code1[, code2[, ...[, codeN]]]])   
```  
  
## <a name="parameters"></a>Parâmetros  
 `String`  
 Necessário. O objeto `String`.  
  
 `code1`, . . . , `codeN`  
 Opcional. Uma série de valores de caractere Unicode para converter uma cadeia de caracteres. Se nenhum argumento for fornecido, o resultado é a cadeia de caracteres vazia.  
  
## <a name="remarks"></a>Comentários  
 Chamar essa função no `String` objeto em vez de em uma instância de cadeia de caracteres.  
  
 O exemplo a seguir mostra como usar esse método:  
  
```JavaScript  
var test = String.fromCharCode(112, 108, 97, 105, 110);  
document.write(test);  
  
// Output: plain  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Método charCodeAt (String)](../../javascript/reference/charcodeat-method-string-javascript.md)