---
title: "Função Date.UTC (JavaScript) | Microsoft Docs"
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
- UTC
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- UTC function [JavaScript]
- UTC dates, returning
- Date.UTC function [JavaScript]
ms.assetid: c0d67ce1-a47e-4dfd-bbf4-21619c406a0f
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a6a7c5622b74699e3d718ceb65e96638bdb6c3c5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="dateutc-function-javascript"></a>Função Date.UTC (JavaScript)
Retorna o número de milissegundos entre meia-noite de 1º de janeiro de 1970 Horário Coordenado Universal (UTC) (ou GMT) e a data especificada.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Date.UTC(year, month, day[, hours[, minutes[, seconds[,ms]]]])   
```  
  
## <a name="parameters"></a>Parâmetros  
 `year`  
 Necessário. A designação de ano inteiro é necessária para precisão de data entre século. Se `year` está entre 0 e 99 for usado, em seguida, `year` é considerado como 1900 + `year`.  
  
 `month`  
 Necessário. O mês como um número inteiro entre 0 e 11 (janeiro a dezembro).  
  
 `day`  
 Necessário. A data como um número inteiro entre 1 e 31.  
  
 `hours`  
 Opcional. Deve ser fornecido se `minutes` for fornecido. Um inteiro de 0 a 23 (meia-noite de 11 pm) que especifica a hora.  
  
 `minutes`  
 Opcional. Deve ser fornecido se `seconds` for fornecido. Um inteiro de 0 a 59, que especifica os minutos.  
  
 `seconds`  
 Opcional. Deve ser fornecido se `milliseconds` for fornecido. Um inteiro de 0 a 59, que especifica os segundos.  
  
 `ms`  
 Opcional. Um inteiro de 0 a 999 que especifica os milissegundos.  
  
## <a name="remarks"></a>Comentários  
 O `Date.UTC` função retorna o número de milissegundos entre meia-noite de 1º de janeiro de 1970 UTC e data fornecida. Esse valor de retorno pode ser usado no `setTime` método e na `Date` construtor do objeto. Se o valor de um argumento é maior do que o intervalo, ou é um número negativo, outros valores armazenados forem modificados de acordo. Por exemplo, se você especificar segundos de 150, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] redefine o número dois minutos e 30 segundos.  
  
 A diferença entre o `Date.UTC` função e o `Date` construtor do objeto que aceita uma data é que o `Date.UTC` função pressupõe UTC e o `Date` construtor do objeto assume a hora local.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso da função `Date.UTC`.  
  
```JavaScript  
// Determine the milliseconds per day.  
 var MinMilli = 1000 * 60;  
var HrMilli = MinMilli * 60;  
var DyMilli = HrMilli * 24;  
  
var date = new Date("June 1, 1990");  
var year = date.getFullYear();  
var month = date.getMonth();  
var day = date.getDay();  
  
var newDay = new Date("January 16, 2020");  
var yeartoday = newDay.getUTCFullYear();  
var monthtoday = newDay.getUTCMonth();  
var dayofmonthtoday = newDay.getUTCDate();  
  
// Get the milliseconds since 1/1/1970 UTC.  
var t1 = Date.UTC(year, month - 1, day)  
var t2 = Date.UTC(yeartoday, monthtoday, dayofmonthtoday);  
  
// Determine the difference in days.  
var days = (t2 - t1) / DyMilli;  
  
document.write(days);  
// Output: 10848  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Método setTime (Date)](../../javascript/reference/settime-method-date-javascript.md)