---
title: "Método toTimeString (Date) (JavaScript) | Microsoft Docs"
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
- toTimeString
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- toTimeString method
ms.assetid: a4a8c0f2-55a9-4e84-94c3-f0a547fb04b5
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4d9af1f688fee0c066158d8504e00f22af9b3a21
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="totimestring-method-date-javascript"></a>Método toTimeString (Date) (JavaScript)
Retorna a hora como um valor de cadeia de caracteres.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
objDate. toTimeString( )  
```  
  
## <a name="remarks"></a>Comentários  
 Obrigatório `objDate` referência é um `Date` objeto.  
  
 O `toTimeString` método retorna um valor de cadeia de caracteres que contém a hora no fuso horário atual.  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, a hora é definida como 2000 milissegundos após a meia-noite de 1º de janeiro de 1970 UTC e, em seguida, ele é gravado.  
  
```JavaScript  
var aDate = new Date();  
     aDate.setTime(2000);  
     document.write(aDate.toTimeString());  
  
// Output depends on the time in the current time zone.  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Método toDateString (Date)](../../javascript/reference/todatestring-method-date-javascript.md)   
 [Método toLocaleTimeString (Date)](../../javascript/reference/tolocaletimestring-method-date-javascript.md)