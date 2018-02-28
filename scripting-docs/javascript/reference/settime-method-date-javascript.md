---
title: "Método setTime (Date) (JavaScript) | Microsoft Docs"
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
- setTime
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- SetTime method
- time method
ms.assetid: 86584748-7219-495b-bf56-e27f5782778c
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e66b1fbf5d668330eb727e8bfc50ee9d11a28be3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="settime-method-date-javascript"></a>Método setTime (Date) (JavaScript)
Define o valor de data e hora no `Date` objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
dateObj.setTime(milliseconds)   
```  
  
## <a name="parameters"></a>Parâmetros  
 `dateObj`  
 Necessário. Qualquer objeto `Date`.  
  
 *milissegundos*  
 Necessário. Um valor numérico que representa o número de milissegundos decorridos desde a meia-noite de 1º de janeiro de 1970 GMT.  
  
## <a name="remarks"></a>Comentários  
 Se *milissegundos* é negativo, ele indica uma data antes de 1970. O intervalo de datas disponíveis é aproximadamente 285,616 anos de um dos lados de 1970.  
  
 Definir a data e hora com o `setTime` método é independente do fuso horário.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso do método `setTime`.  
  
```JavaScript  
function SetTimeTest(newtime){  
   var d, s;                  //Declare variables.  
   d = new Date();            //Create Date object.  
   d.setTime(newtime);        //Set time.  
   s = "Current setting is ";  
   s += d.toUTCString();  
   return(s);                 //Return new setting.  
}  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Aplica-se a**: [objeto de data](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Consulte também  
 [Método getTime (Date)](../../javascript/reference/gettime-method-date-javascript.md)