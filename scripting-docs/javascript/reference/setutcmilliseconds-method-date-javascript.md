---
title: "Método setUTCMilliseconds (Date) (JavaScript) | Microsoft Docs"
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
- setUTCMilliseconds
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- milliseconds
- dates, UTC
- UTC times, setting
- setUTCMilliseconds method
ms.assetid: ed8e4486-d4b2-4b73-836b-dd1d3bb991a0
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 279d00b256b3b0763e2f15f549fdc6ee81c20254
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="setutcmilliseconds-method-date-javascript"></a>Método setUTCMilliseconds (Date) (JavaScript)
Define o valor de milissegundos a `Date` usando o Horário Coordenado Universal (UTC) do objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
dateObj.setUTCMilliseconds(numMilli)   
```  
  
## <a name="parameters"></a>Parâmetros  
 `dateObj`  
 Necessário. Qualquer objeto `Date`.  
  
 `numMilli`  
 Necessário. Um valor numérico igual ao valor de milissegundos.  
  
## <a name="remarks"></a>Comentários  
 Para definir os milissegundos usando o horário local, use o `setMilliseconds` método.  
  
 Se o valor de `numMilli` é maior do que 999, ou é um número negativo, o número armazenado segundos (e minutos, horas, e assim por diante, se necessário) é incrementado uma quantidade apropriada.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso do método `setUTCMilliseconds`.  
  
```JavaScript  
function SetUTCMSecDemo(nmsec){     
// Create Date object.  
   var d = new Date();             
// Set UTC milliseconds.  
   d.setUTCMilliseconds(nmsec);    
  
   var s = "Current setting is ";  
   s += d.toUTCString();  
   s += " and " + d.getUTCMilliseconds();  
   s += " milliseconds"  
   return(s);  
}  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Aplica-se a**: [objeto de data](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Consulte também  
 [Método getMilliseconds (Date)](../../javascript/reference/getmilliseconds-method-date-javascript.md)   
 [Método getUTCMilliseconds (Date)](../../javascript/reference/getutcmilliseconds-method-date-javascript.md)   
 [Método setMilliseconds (Date)](../../javascript/reference/setmilliseconds-method-date-javascript.md)