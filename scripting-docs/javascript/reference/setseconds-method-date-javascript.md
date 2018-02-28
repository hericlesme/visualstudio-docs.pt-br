---
title: "Método setSeconds (Date) (JavaScript) | Microsoft Docs"
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
- setSeconds
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- setSeconds method
- seconds method
ms.assetid: 986ffa54-1db6-4af2-ab8b-8353f64f0b57
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6b8d545307f6aac3506310c868a2860a6159a106
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="setseconds-method-date-javascript"></a>Método setSeconds (Date) (JavaScript)
Define o valor de segundos no `Date` usando o horário local do objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
dateObj  
.setSeconds(  
numSeconds[, numMilli])   
```  
  
## <a name="parameters"></a>Parâmetros  
 `dateObj`  
 Necessário. Qualquer objeto `Date`.  
  
 *numSeconds*  
 Necessário. Um valor numérico igual ao valor de segundos.  
  
 `numMilli`  
 Opcional. Um valor numérico igual ao valor de milissegundos.  
  
## <a name="remarks"></a>Comentários  
 Todos os **definir** métodos levando argumentos opcionais usam o valor retornado da correspondente **obter** métodos, se você não especificar um argumento opcional. Por exemplo, se o `numMilli` argumento não for especificado, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] usa o valor retornado do **getMilliseconds** método.  
  
 Para definir os segundos valor usando o Horário Coordenado Universal (UTC), use o `setUTCSeconds` método.  
  
 Se o valor de um argumento é maior do que o intervalo ou é um número negativo, outros valores armazenados forem modificados de acordo. Por exemplo, se a data armazenada é "5 de janeiro de 1996 00:00:00" e **setSeconds(150)** é chamado, a data é alterada para "5 de janeiro de 1996 00:02:30."  
  
 O `setHours` método pode ser usado para definir as horas, minutos, segundos e milissegundos.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso do método `setSeconds`.  
  
```JavaScript  
function SetSecondsDemo(nsec){  
   var d = new Date();         //Create Date object.  
   d.setSeconds(nsec);         //Set seconds.  
   var s = "Current setting is ";  
   s += d.toLocaleString();  
   return(s);                  //Return new setting.  
}  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Aplica-se a**: [objeto de data](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Consulte também  
 [Método getSeconds (Date)](../../javascript/reference/getseconds-method-date-javascript.md)   
 [Método getUTCSeconds (Date)](../../javascript/reference/getutcseconds-method-date-javascript.md)   
 [Método setUTCSeconds (Date)](../../javascript/reference/setutcseconds-method-date-javascript.md)