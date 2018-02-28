---
title: "Função Date Parse (JavaScript) | Microsoft Docs"
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
- parse
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- parse function [JavaScript]
- Date.parse function [JavaScript]
ms.assetid: ed737e50-6398-4462-8779-2af3c03f8325
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0a73fda66ef24df17a5213a182c04667fc4dfabf
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="dateparse-function-javascript"></a>Função Date.parse (JavaScript)
Analisa uma cadeia de caracteres que contém uma data e retorna o número de milissegundos entre essa data e a meia-noite de 1º de janeiro de 1970.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Date.parse(dateVal)   
```  
  
## <a name="remarks"></a>Comentários  
 Obrigatório `dateVal` argumento é uma cadeia de caracteres que contém uma data ou um valor VT_DATE recuperados de um objeto ActiveX ou em outro objeto. Para obter informações sobre a data de cadeias de caracteres de `Date.parse` pode analisar a função. consulte [Date and Time Strings](../../javascript/date-and-time-strings-javascript.md).  
  
 O `Date.parse` função retorna um valor inteiro que representa o número de milissegundos entre meia-noite de 1º de janeiro de 1970 e a data fornecida em `dateVal`.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso da função `Date.parse`.  
  
```JavaScript  
var dateString = "November 1, 1997 10:15 AM";  
var mSec = Date.parse(dateString);  
document.write(mSec);  
// Output: 878404500000  
```  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir retorna a diferença entre a data fornecida e 1/1/1970.  
  
```JavaScript  
var minMilli = 1000 * 60;  
var hrMilli = minMilli * 60;  
var dyMilli = hrMilli * 24;  
  
var testDate = new Date("June 1, 1990");  
var ms = Date.parse(testDate);  
var days = Math.round(ms / dyMilli);  
  
var dateStr = "";  
dateStr += "There are " + days + " days ";  
dateStr += "between 01/01/1970 and " + testDate;  
document.write(dateStr);  
  
// Output: There are 7456 days between 01/01/1970 and Fri Jun 1 00:00:00 PDT 1990  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Método getDate (Date)](../../javascript/reference/getdate-method-date-javascript.md)