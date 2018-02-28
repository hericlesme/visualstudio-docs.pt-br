---
title: "Método getMonth (Date) (JavaScript) | Microsoft Docs"
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
- getMonth
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Date object
- dates, month value
- Month method
- GetMonth method
ms.assetid: c20dd8ba-1d78-42f1-8717-ed3dfd2362dd
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eeffd7ffc7bee5fa63607e342a9a9dced7088d35
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="getmonth-method-date-javascript"></a>Método getMonth (Date) (JavaScript)
Obtém o mês, usando o horário local.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
dateObj.getMonth()   
```  
  
#### <a name="parameters"></a>Parâmetros  
 Obrigatório `dateObj` referência é um `Date` objeto.  
  
## <a name="return-value"></a>Valor de retorno  
 O `getMonth` método retorna um número inteiro entre 0 (janeiro) e 11 (dezembro). Para uma `Date` construído com "5 de janeiro de 1996", `getMonth` retornará 0.  
  
## <a name="remarks"></a>Comentários  
 Para obter o valor do mês usando o Horário Coordenado Universal (UTC), use o `getUTCMonth` método.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar o método `getMonth`.  
  
```JavaScript  
var date = new Date("1/1/2001");  
document.write(date.getMonth());  
  
// Output: 0  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Aplica-se a**: [objeto de data](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Consulte também  
 [Método getUTCMonth (Date)](../../javascript/reference/getutcmonth-method-date-javascript.md)   
 [Método setMonth (Date)](../../javascript/reference/setmonth-method-date-javascript.md)   
 [Método setUTCMonth (Date)](../../javascript/reference/setutcmonth-method-date-javascript.md)