---
title: "Método setMonth (Date) (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: setMonth
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Month method
- setMonth method
ms.assetid: 4f5be295-d536-46c0-b3a4-ad06457efe82
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0f2672abebd327af8b0da58d46ebc183b8159711
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="setmonth-method-date-javascript"></a>Método setMonth (Date) (JavaScript)
Define o valor de mês de `Date` usando o horário local do objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
dateObj. setMonth(numMonth[, dateVal])   
```  
  
## <a name="parameters"></a>Parâmetros  
 `dateObj`  
 Necessário. Qualquer objeto `Date`.  
  
 `numMonth`  
 Necessário. Um valor numérico igual para o mês. O valor de janeiro é 0 e outros valores de mês siga consecutivamente.  
  
 `dateVal`  
 Opcional. Um valor numérico que representa o dia do mês. Se esse valor não for fornecido, o valor de uma chamada para o `getDate` método é usado.  
  
## <a name="remarks"></a>Comentários  
 Para definir o valor do mês usando o Horário Coordenado Universal (UTC), use o `setUTCMonth` método.  
  
 Se o valor de `numMonth` é maior do que 11 (janeiro é mês 0) ou um número negativo, o ano armazenado é modificado de acordo. Por exemplo, se a data armazenada é "5 de janeiro de 1996" e **setMonth(14)** é chamado, a data é alterada para "5 de março de 1997."  
  
 O **setFullYear** método pode ser usado para definir o ano, mês e dia do mês.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso do método `setMonth`.  
  
```JavaScript  
date = new Date('1/1/1990');  
date.setMonth(14);  
document.write(date);  
  
// Output: Fri Mar 1 00:00:00 PST 1991  
// Note that the time zone corresponds to the time zone on the local computer.  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Aplica-se a**: [objeto de data](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Consulte também  
 [Método getMonth (Date)](../../javascript/reference/getmonth-method-date-javascript.md)   
 [Método getUTCMonth (Date)](../../javascript/reference/getutcmonth-method-date-javascript.md)   
 [Método setUTCMonth (Date)](../../javascript/reference/setutcmonth-method-date-javascript.md)