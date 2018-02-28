---
title: "Método setUTCMonth (Date) (JavaScript) | Microsoft Docs"
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
- setUTCMonth
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- dates, UTC
- setUTCMonth method
- Month method
- UTC dates, setting
ms.assetid: cdac5f64-c4fd-44cc-ba3a-9a8dd3dd3fad
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 02cb69026b66e3f307a8709ab3f5b23d9518643a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="setutcmonth-method-date-javascript"></a>Método setUTCMonth (Date) (JavaScript)
Define o valor de mês de `Date` usando o Horário Coordenado Universal (UTC) do objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
dateObj.setUTCMonth(numMonth[, dateVal])   
```  
  
## <a name="parameters"></a>Parâmetros  
 `dateObj`  
 Necessário. Qualquer objeto `Date`.  
  
 `numMonth`  
 Necessário. Um valor numérico igual para o mês. O valor de janeiro é 0 e outros valores de mês siga consecutivamente.  
  
 `dateVal`  
 Opcional. Um valor numérico que representa o dia do mês. Se não for fornecido, o valor de uma chamada para o `getUTCDate` método é usado.  
  
## <a name="remarks"></a>Comentários  
 Para definir o valor do mês usando o horário local, use o `setMonth` método.  
  
 Se o valor de `numMonth` é maior do que 11 (janeiro é mês 0), ou é um número negativo, o ano armazenado é aumentada ou diminuída adequadamente. Por exemplo, se a data armazenada é "5 de janeiro de 1996 00:00:00.00", e **setUTCMonth(14)** é chamado, a data é alterada para "5 de março de 1997 00:00:00.00".  
  
 O **setUTCFullYear** método pode ser usado para definir o ano, mês e dia do mês.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso do método `setUTCMonth`.  
  
```JavaScript  
function SetUTCMonthDemo(newmonth){  
   var d, s;                       // Declare variables.  
   d = new Date();                 // Create Date object.  
   d.setUTCMonth(newmonth);        // Set UTC month.  
   s = "Current setting is ";  
   s += d.toUTCString();   
   return(s);                      // Return new setting.  
}  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Aplica-se a**: [objeto de data](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Consulte também  
 [Método getMonth (Date)](../../javascript/reference/getmonth-method-date-javascript.md)   
 [Método getUTCMonth (Date)](../../javascript/reference/getutcmonth-method-date-javascript.md)   
 [Método setMonth (Date)](../../javascript/reference/setmonth-method-date-javascript.md)