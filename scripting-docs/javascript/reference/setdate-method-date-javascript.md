---
title: Método setDate (Date) (JavaScript) | Microsoft Docs
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
- setDate
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- setDate method
- dates, setting
ms.assetid: a84b9b01-a6d0-489f-8a13-e7af9e9630b2
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8d74340287b3a7348419d302f79775eb610c6983
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640306"
---
# <a name="setdate-method-date-javascript"></a>Método setDate (Date) (JavaScript)
Define o valor numérico do dia do mês do `Date` usando o horário local do objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
dateObj.setDate(numDate)   
```  
  
## <a name="parameters"></a>Parâmetros  
 `dateObj`  
 Necessário. Qualquer objeto `Date`.  
  
 `numDate`  
 Necessário. Um valor numérico igual para o dia do mês.  
  
## <a name="remarks"></a>Comentários  
 Para definir o valor de dia do mês usando o Horário Coordenado Universal (UTC), use o `setUTCDate` método.  
  
 Se o valor de `numDate` é maior que o número de dias do mês, a reverte data sobre um posterior mês e/ou ano. Por exemplo, se a data armazenada é 5 de janeiro de 1996 e `setDate(32)` é chamado, a alteração da data de 1º de fevereiro de 1996. Se `numDate` for um número negativo, reverte a data a um anteriores mês e/ou ano. Por exemplo, se a data armazenada é 5 de janeiro de 1996 e `setDate(-32)` é chamado, a alteração da data de 29 de novembro de 1995.  
  
 O [método setFullYear (Date)](../../javascript/reference/setfullyear-method-date-javascript.md) pode ser usado para definir o ano, mês e dia do mês.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar o método `setDate`.  
  
```JavaScript  
var date = new Date("12/15/1990");  
date.setDate(30);  
document.write(date);  
  
// Output (for the PST time zone): Sun Dec 30 00:00:00 PST 1990  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Aplica-se a**: [objeto de data](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Consulte também  
 [Método getDate (Date)](../../javascript/reference/getdate-method-date-javascript.md)   
 [Método setFullYear (Date)](../../javascript/reference/setfullyear-method-date-javascript.md)   
 [Método setMonth (Date)](../../javascript/reference/setmonth-method-date-javascript.md)   
 [Método setUTCDate (Date)](../../javascript/reference/setutcdate-method-date-javascript.md)