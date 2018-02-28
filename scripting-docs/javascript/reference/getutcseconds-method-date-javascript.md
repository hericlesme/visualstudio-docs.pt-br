---
title: "Método getUTCSeconds (Date) (JavaScript) | Microsoft Docs"
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
- getUTCSeconds
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- UTC times, returning
- seconds method
- getUTCSeconds method
ms.assetid: 2d8ea7dc-79f8-4a9b-b2ab-732db2bcd5fd
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4f398145f8e31ed633bf3215de7d5a5ef669b7ef
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="getutcseconds-method-date-javascript"></a>Método getUTCSeconds (Date) (JavaScript)
Obtém os segundos de um `Date` usando o Horário Coordenado Universal (UTC) do objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
dateObj.getUTCSeconds()   
```  
  
#### <a name="parameters"></a>Parâmetros  
 Obrigatório `dateObj` referência é um `Date` objeto.  
  
## <a name="return-value"></a>Valor de retorno  
 Retorna um número inteiro entre 0 e 59. Zero é retornada quando o tempo é menor que um segundo para o minuto atual. Se um `Date` objeto foi criado sem especificar a hora, por padrão o UTC valor segundos é 0.  
  
## <a name="remarks"></a>Comentários  
 Para obter o número de segundos na hora local, use o `getSeconds` método.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar o método `getUTCSeconds`.  
  
```JavaScript  
var date = new Date("1/1/2001");  
document.write(date. getUTCSeconds());  
  
// Output: 0  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Aplica-se a**: [objeto de data](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Consulte também  
 [Método getSeconds (Date)](../../javascript/reference/getseconds-method-date-javascript.md)   
 [Método setSeconds (Date)](../../javascript/reference/setseconds-method-date-javascript.md)   
 [Método setUTCSeconds (Date)](../../javascript/reference/setutcseconds-method-date-javascript.md)