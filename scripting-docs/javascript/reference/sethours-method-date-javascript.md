---
title: "Método setHours (Date) (JavaScript) | Microsoft Docs"
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
- setHours
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- hours
- setHours method
- dates, setting
ms.assetid: 460f742d-f8d2-4874-9d07-2fb969fef066
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f9757f8416953eaf756dba96b91100527606cf9c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="sethours-method-date-javascript"></a>Método setHours (Date) (JavaScript)
Define o valor de hora no `Date` usando o horário local do objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
dateObj.setHours(numHours[, numMin[, numSec[, numMilli]]])   
```  
  
## <a name="parameters"></a>Parâmetros  
 `dateObj`  
 Necessário. Qualquer objeto `Date`.  
  
 `numHours`  
 Necessário. Um valor numérico igual ao valor de horas.  
  
 `numMin`  
 Opcional. Um valor numérico igual ao valor de minutos. Deve ser fornecido se qualquer um dos seguintes argumentos é usado.  
  
 `numSec`  
 Opcional. Um valor numérico igual ao valor de segundos. Deve ser fornecido se o argumento a seguir é usado.  
  
 `numMilli`  
 Opcional. Um valor numérico igual ao valor de milissegundos.  
  
## <a name="remarks"></a>Comentários  
 Todos os **definir** métodos levando argumentos opcionais usam o valor retornado da correspondente **obter** métodos, se você não especificar um argumento opcional. Por exemplo, se o `numMinutes` argumento não for especificado, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] usa o valor retornado do `getMinutes` método.  
  
 Para definir o valor de horas usando o Horário Coordenado Universal (UTC), use o `setUTCHours` método.  
  
 Se o valor de um argumento é maior do que o intervalo ou é um número negativo, outros valores armazenados forem modificados de acordo. Por exemplo, se a data armazenada é "5 de janeiro de 1996 00:00:00", e **setHours(30)** é chamado, a data é alterada para "6 de janeiro de 1996 06:00:00." Números negativos têm um comportamento semelhante.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso do método `setHours`.  
  
```JavaScript  
function SetHoursDemo(nhr, nmin, nsec){  
   var d, s;                     //Declare variables.  
   d = new Date();               //Create Date object.  
   d.setHours(nhr, nmin, nsec);  //Set hours, minutes, & seconds.  
   s = "Current setting is " + d.toLocaleString()   
   return(s);                    //Return new date setting.  
}  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Aplica-se a**: [objeto de data](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Consulte também  
 [Método getHours (Date)](../../javascript/reference/gethours-method-date-javascript.md)   
 [Método getUTCHours (Date)](../../javascript/reference/getutchours-method-date-javascript.md)   
 [Método setUTCHours (Date)](../../javascript/reference/setutchours-method-date-javascript.md)