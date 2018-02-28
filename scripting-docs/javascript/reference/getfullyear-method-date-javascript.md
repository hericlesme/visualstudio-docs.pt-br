---
title: "Método getFullYear (Date) (JavaScript) | Microsoft Docs"
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
- getFullYear
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- dates, returning year
- Date object
- getFullYear method
ms.assetid: f9ec1262-02e9-4791-90b5-48f33b1dc4bc
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 211d6c86435e39eb75b9b1ce3415738541ca07db
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="getfullyear-method-date-javascript"></a>Método getFullYear (Date) (JavaScript)
Obtém o ano, usando o horário local.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
dateObj.getFullYear()   
```  
  
#### <a name="parameters"></a>Parâmetros  
 Obrigatório `dateObj` referência é um `Date` objeto.  
  
## <a name="return-value"></a>Valor de retorno  
 O ano como um número de quatro dígitos. Por exemplo, o ano 1976 é retornado como 1976. Anos especificados como dois dígitos no `Date` construtor ou `setFullYear` devem para estar no século, portanto fornecido "5/14/12", `getFullYear` retorna "1912".  
  
## <a name="remarks"></a>Comentários  
 Para obter o ano usando o Horário Coordenado Universal (UTC), use o `getUTCFullYear` método.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso do **getFullYear** método.  
  
```JavaScript  
var date = new Date("1/1/01");  
document.write(date.getFullYear());  
  
// Output: 1901  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Aplica-se a**: [objeto de data](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Consulte também  
 [Método getUTCFullYear (Date)](../../javascript/reference/getutcfullyear-method-date-javascript.md)   
 [Método setFullYear (Date)](../../javascript/reference/setfullyear-method-date-javascript.md)   
 [Método setUTCFullYear (Date)](../../javascript/reference/setutcfullyear-method-date-javascript.md)