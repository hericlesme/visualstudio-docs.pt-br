---
title: Método setUTCDate (Date) (JavaScript) | Microsoft Docs
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
- setUTCDate
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- dates, UTC
- dates, setting
- UTC dates, setting
- setUTCDate method
ms.assetid: e6c3b876-70fe-4103-b197-6c84c078ce10
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5631a36c8b1c4f1ee50dcadb39f0f21ae5aa28e3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640596"
---
# <a name="setutcdate-method-date-javascript"></a>Método setUTCDate (Date) (JavaScript)
Define o dia numérico do mês no `Date` usando o Horário Coordenado Universal (UTC) do objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
dateObj.setUTCDate(numDate)   
```  
  
## <a name="parameters"></a>Parâmetros  
 `dateObj`  
 Necessário. Qualquer objeto `Date`.  
  
 *numDate*  
 Necessário. Um valor numérico igual para o dia do mês.  
  
## <a name="remarks"></a>Comentários  
 Para definir o dia do mês usando o horário local, use o `setDate` método.  
  
 Se o valor de *numDate* é maior que o número de dias do mês armazenados no **data** de objeto ou é um número negativo, a data é definida como uma data igual a *numDate* menos o número de dias do mês armazenado. Por exemplo, se a data armazenada é 5 de janeiro de 1996, e **setUTCDate(32)** é chamado, a alteração da data de 1º de fevereiro de 1996. Números negativos têm um comportamento semelhante.  
  
 O **setUTCFullYear** método pode ser usado para definir o ano, mês e dia do mês.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso do método `setUTCDate`.  
  
```JavaScript  
function SetUTCDateDemo(newdayofmonth){  
   var d = new Date();           // Create Date object.  
   d.setUTCDate(newdayofmonth);  // Set UTC day of month.  
   var s = "Current setting is ";  
   s += d.toUTCString();   
   return(s);                    // Return new setting.  
}  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Aplica-se a**: [objeto de data](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Consulte também  
 [Método getDate (Date)](../../javascript/reference/getdate-method-date-javascript.md)   
 [Método getUTCDate (Date)](../../javascript/reference/getutcdate-method-date-javascript.md)   
 [Método setDate (Date)](../../javascript/reference/setdate-method-date-javascript.md)