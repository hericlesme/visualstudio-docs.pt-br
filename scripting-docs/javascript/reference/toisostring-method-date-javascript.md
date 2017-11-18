---
title: "Método toISOString (Date) (JavaScript) | Microsoft Docs"
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
helpviewer_keywords: toISOString method [JavaScript]
ms.assetid: 58577d8f-3ae8-4887-8687-26233ea79ff6
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 31559e1bc44849573ec7dc903411ce98b0a4440d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="toisostring-method-date-javascript"></a>Método toISOString (Date) (JavaScript)
Retorna uma data como um valor de cadeia de caracteres no formato ISO.  
  
## <a name="syntax"></a>Sintaxe  
  
```JavaScript  
  
objDate.toISOString()  
```  
  
## <a name="return-value"></a>Valor de retorno  
 Uma representação de cadeia de caracteres de data na organização internacional de formato de normalização (ISO).  
  
## <a name="exceptions"></a>Exceções  
 Se `objDate` não contém uma data válida, um `RangeError` exceção será lançada.  
  
## <a name="remarks"></a>Comentários  
 O formato ISO é uma simplificação do formato ISO 8601. Para obter mais informações, consulte [Date and Time Strings](../../javascript/date-and-time-strings-javascript.md).  
  
 O fuso horário é sempre UTC, indicado pelo sufixo Z na saída.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso do método `toISOString`.  
  
```JavaScript  
var dt = new Date("30 July 2010 15:05 UTC");  
document.write(dt.toISOString());  
document.write("<br />");  
document.write(dt.toUTCString());  
  
// Output:  
//  2010-07-30T15:05:00.000Z  
//  Fri, 30 Jul 2010 15:05:00 UTC  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Objeto Date](../../javascript/reference/date-object-javascript.md)   
 [Cadeias de caracteres de data e hora](../../javascript/date-and-time-strings-javascript.md)