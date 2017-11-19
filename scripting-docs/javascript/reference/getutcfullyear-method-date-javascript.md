---
title: "Método getUTCFullYear (Date) (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: getUTCFullYear
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- getUTCFullYear method
- Date object
- UTCFullYear method
- dates, UTC
- UTC dates, returning
- Full Year method
- UTC dates, getting
ms.assetid: f11e5363-ef8a-48dd-9d56-4ee7290c7c48
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c8268631a96eed1f61ef4ba908b78680c8522096
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="getutcfullyear-method-date-javascript"></a>Método getUTCFullYear (Date) (JavaScript)
Obtém o ano usando o Horário Coordenado Universal (UTC).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
dateObj.getUTCFullYear()   
```  
  
#### <a name="parameters"></a>Parâmetros  
 Obrigatório `dateObj` referência é um `Date` objeto.  
  
## <a name="return-value"></a>Valor de retorno  
 Retorna o ano como um número de quatro dígitos. Anos especificados como dois dígitos no `Date` construtor ou `setFullYear` devem para estar no século, portanto fornecido "5/14/12", `getUTCFullYear` retorna "1912".  
  
## <a name="remarks"></a>Comentários  
 Para obter o ano usando a hora local, use o `getFullYear` método.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar o método `getUTCFullYear`.  
  
```JavaScript  
var date = new Date("1/9/36");  
document.write(date.getUTCFullYear());  
  
// Output: 1936  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Aplica-se a**: [objeto de data](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Consulte também  
 [Método getFullYear (Date)](../../javascript/reference/getfullyear-method-date-javascript.md)   
 [Método setFullYear (Date)](../../javascript/reference/setfullyear-method-date-javascript.md)   
 [Método setUTCFullYear (Date)](../../javascript/reference/setutcfullyear-method-date-javascript.md)