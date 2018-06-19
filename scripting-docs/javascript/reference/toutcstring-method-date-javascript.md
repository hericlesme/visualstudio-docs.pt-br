---
title: Método toUTCString (Date) (JavaScript) | Microsoft Docs
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
- toUTCString
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- UTC dates, converting to strings
- toUTCString method
ms.assetid: eb0983ed-7884-42fa-a2cc-de92b3111207
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0bd5efc43152c1af2dd467b73dce235e8fe52f29
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640736"
---
# <a name="toutcstring-method-date-javascript"></a>Método toUTCString (Date) (JavaScript)
Retorna uma data convertida em uma cadeia de caracteres usando o Horário Coordenado Universal (UTC).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
dateObj.toUTCString()   
```  
  
## <a name="remarks"></a>Comentários  
 Obrigatório `dateObj` referência é qualquer `Date` objeto.  
  
 O `toUTCString` método retorna um `String` objeto que contém a data formatada usando a convenção de UTC em um conveniente ler facilmente o formulário.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso do método `toUTCString`.  
  
```JavaScript  
function toUTCStrDemo(){  
   var d, s;                   //Declare variables.  
   d = new Date();             //Create Date object.  
   s = "Current setting is ";  
   s += d.toUTCString();       //Convert to UTC string.  
   return(s);                  //Return UTC string.  
}  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Aplica-se a**: [objeto de data](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Consulte também  
 [Método toGMTString (Date)](../../javascript/reference/togmtstring-method-date-javascript.md)