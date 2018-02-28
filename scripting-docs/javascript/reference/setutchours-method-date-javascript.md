---
title: "Método setUTCHours (Date) (JavaScript) | Microsoft Docs"
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
- setUTCHours
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- dates, UTC
- UTC times, setting
- setUTCHours method
ms.assetid: 257e36fd-fb06-4a4d-8634-d66a020a1511
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9fe83735028f86d38ef270beac6c44dfa4caae7f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="setutchours-method-date-javascript"></a>Método setUTCHours (Date) (JavaScript)
Define o valor de horas a `Date` usando o Horário Coordenado Universal (UTC) do objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
dateObj.setUTCHours(numHours[, numMin[, numSec[, numMilli]]])   
```  
  
## <a name="parameters"></a>Parâmetros  
 `dateObj`  
 Necessário. Qualquer objeto `Date`.  
  
 `numHours`  
 Necessário. Um valor numérico igual ao valor de horas.  
  
 `numMin`  
 Opcional. Um valor numérico igual ao valor de minutos. Deve ser fornecido se `numSec` ou `numMilli` são usados.  
  
 `numSec`  
 Opcional. Um valor numérico igual ao valor de segundos. Deve ser fornecido se `numMilli` argumento é usado.  
  
 `numMilli`  
 Opcional. Um valor numérico igual ao valor de milissegundos.  
  
## <a name="remarks"></a>Comentários  
 Todos os **definir** métodos levando argumentos opcionais usam o valor retornado da correspondente **obter** métodos, se você não especificar um argumento opcional. Por exemplo, se o `numMin` argumento não for especificado, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] usa o valor retornado do `getUTCMinutes` método.  
  
 Para definir o valor de horas usando o horário local, use o `setHours` método.  
  
 Se o valor de um argumento é maior do que o intervalo, ou é um número negativo, outros valores armazenados forem modificados de acordo. Por exemplo, se a data armazenada é "5 de janeiro de 1996 00:00:00.00", e **setUTCHours(30)** é chamado, a data é alterada para "6 de janeiro de 1996 06:00:00.00".  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso do método `setUTCHours`.  
  
```JavaScript  
function SetUTCHoursDemo(nhr, nmin, nsec){     
   var d, s;                        // Declare variables.  
   d = new Date();                  // Create Date object.  
   d.setUTCHours(nhr, nmin, nsec);  // Set UTC hours, minutes, seconds.  
   s = "Current setting is " + d.toUTCString()   
   return(s);                       // Return new setting.  
}  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Aplica-se a**: [objeto de data](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Consulte também  
 [Método getHours (Date)](../../javascript/reference/gethours-method-date-javascript.md)   
 [Método getUTCHours (Date)](../../javascript/reference/getutchours-method-date-javascript.md)   
 [Método setHours (Date)](../../javascript/reference/sethours-method-date-javascript.md)