---
title: "Método concat (String) (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: concat
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- concat method (String)
- Concat method
ms.assetid: 5d28ebb2-d534-4179-9297-a4c821ee9f24
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1b6419cc6404e06fc780802a30a3b4add8320881
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="concat-method-string-javascript"></a>Método concat (Cadeia de Caracteres) (JavaScript)
Retorna uma cadeia de caracteres que contém a concatenação de cadeias de caracteres de dois ou mais.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
string1. concat([string2[, string3[, . . . [, stringN]]]])  
```  
  
## <a name="parameters"></a>Parâmetros  
 `string1`  
 Necessário. O `String` objeto ou cadeia de caracteres literal para o qual todos os outros especificado cadeias de caracteres são concatenadas.  
  
 `string2,. . ., stringN`  
 Opcional. As cadeias de caracteres a ser acrescentada ao final da `string1`.  
  
## <a name="remarks"></a>Comentários  
 O resultado da `concat` método é equivalente a: `result`  =  `string1`  +  `string2`  +  `string3`  +  `stringN`. Uma alteração do valor na cadeia de caracteres de uma fonte ou o resultado não afeta o valor em outra cadeia de caracteres. Se qualquer um dos argumentos não são cadeias de caracteres, eles primeiro são convertidos em cadeias de caracteres antes de ser concatenadas para `string1`.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso do `concat` método quando usado com uma cadeia de caracteres:  
  
```JavaScript  
var str1 = "ABCD"  
var str2 = "EFGH";  
var str3 = "1234";  
var str4 = "5678";  
document.write(str1.concat(str2, str3, str4));  
  
// Output: "ABCDEFGH12345678"  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Aplica-se a**: [objeto de cadeia de caracteres](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>Consulte também  
 [Operador de adição (+)](../../javascript/reference/addition-operator-decrement-javascript.md)