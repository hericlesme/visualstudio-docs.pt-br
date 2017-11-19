---
title: "Método getUTCDate (Date) (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: getUTCDate
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Date object
- dates, UTC
- UTC dates, returning
- getUTCDate method
ms.assetid: 9e4c763f-c94c-44c9-9684-cb632d75b62e
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e4c38244e989027139329ae6aab762fd9fbabb3a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="getutcdate-method-date-javascript"></a>Método getUTCDate (Date) (JavaScript)
Obtém o dia-de-mês, usando o Horário Coordenado Universal (UTC).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
dateObj.getUTCDate()   
```  
  
#### <a name="parameters"></a>Parâmetros  
 Obrigatório `dateObj` referência é um `Date` objeto.  
  
## <a name="return-value"></a>Valor de retorno  
 Retorna um inteiro entre 1 e 31 que representa o dia-de-mês.  
  
## <a name="remarks"></a>Comentários  
 Para obter o dia do mês usando o horário local, use o `getDate` método.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar o método `getUTCDate`.  
  
```JavaScript  
var date = new Date("1/23/2001");  
document.write(date.getUTCDate());  
  
// Output: 23  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Aplica-se a**: [objeto de data](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Consulte também  
 [Método getDate (Date)](../../javascript/reference/getdate-method-date-javascript.md)   
 [Método setDate (Date)](../../javascript/reference/setdate-method-date-javascript.md)   
 [Método setUTCDate (Date)](../../javascript/reference/setutcdate-method-date-javascript.md)