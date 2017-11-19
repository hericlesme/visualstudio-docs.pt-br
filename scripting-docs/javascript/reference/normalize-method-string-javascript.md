---
title: "Método (String) (JavaScript) normalizar | Microsoft Docs"
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
ms.assetid: d50077c1-b5fa-4e7a-9c9d-dc66cfc423ac
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: aece38339ea1ce8924f404938b2d35d07504d539
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="normalize-method-string-javascript"></a>normalizar método (String) (JavaScript)
Retorna o Formulário de Normalização Unicode de uma cadeia de caracteres especificada.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
stringObj.normalize([form]);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `stringObj`  
 Necessário. O objeto de cadeia de caracteres a ser usado no teste.  
  
 `form`  
 Opcional. O valor de formulário de normalização Unicode.  
  
## <a name="return-value"></a>Valor de retorno  
 O Formulário de Normalização Unicode de uma cadeia de caracteres especificada.  
  
## <a name="exceptions"></a>Exceções  
 Se `form` for um valor sem suporte, um `RangeError` é lançado.  
  
## <a name="remarks"></a>Comentários  
 Se `stringObj` não for uma cadeia de caracteres, ele será convertido em uma cadeia de caracteres antes do método tentar retornar o formulário de normalização Unicode da cadeia de caracteres.  
  
 `form`deve ser um valor de formulário de normalização Unicode, "NFC", "NFD", "NFKC" ou "NFKD", correspondentes aos valores especificados para [Unicode Standard Annex #15](http://www.unicode.org/reports/tr15/). O valor padrão de `form` é "NFC".  
  
## <a name="example"></a>Exemplo  
 Os exemplos de código a seguir mostram o uso do método `normalize`.  
  
```JavaScript  
// ANGSTORM SIGN and LATIN CAPITAL A WITH RING ABOVE is canonically equivalent  
"\u212b".normalize("NFC") === "\u00c5";  
  
// Decomposed, ANGSTOM SIGN is LATIN CAPITAL A followed by COMBINING RING ABOVE  
"\u212b".normalize("NFD") === "\u0041\u030a"  
  
// Normalization Form C will combine the result back into the precombined character  
"\u0041\u030a".normalize("NFC") === "\u00c5"  
  
// LATIN SMALL LIGATURE FI is compatibility equivalent with LATIN SMALL LETTER F followed by  
// LATIN SMALL LETTER I.  
"\ufb01".normalize("NFKD") === "fi";  
  
// Same mapping in NFKC  
"\ufb01".normalize("NFKC") === "fi";  
  
// NFKC will not recombine compatibility characters.  
"fi".normalize("NFKC") === "fi";  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]