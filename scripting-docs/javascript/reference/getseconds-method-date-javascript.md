---
title: Método getSeconds (Date) (JavaScript) | Microsoft Docs
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
- getSeconds
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- seconds method
- GetSeconds method
ms.assetid: 97b10674-af0b-4681-a846-38f972196501
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 151d720b92fb9d7068c320983a25b965078f1b2e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636776"
---
# <a name="getseconds-method-date-javascript"></a>Método getSeconds (Date) (JavaScript)
Obtém os segundos de um `Date` do objeto, usando o horário local.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
dateObj.getSeconds()   
```  
  
#### <a name="parameters"></a>Parâmetros  
 Obrigatório `dateObj` referência é um `Date` objeto.  
  
## <a name="return-value"></a>Valor de retorno  
 Retorna um número inteiro entre 0 e 59. Zero é retornada quando o tempo é menor que um segundo para o minuto atual. Se um `Date` objeto foi criado sem especificar a hora, por padrão, o valor de segundos é 0.  
  
## <a name="remarks"></a>Comentários  
 Para obter os segundos valor usando o Horário Coordenado Universal (UTC), use o `getUTCSeconds` método.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar o método `getSeconds`.  
  
```JavaScript  
var date = new Date("1/1/2001");  
document.write(date.getSeconds());  
document.write("<br/>");  
  
date.setSeconds(5);  
document.write(date.getSeconds());  
  
// Output:  
// 0  
// 5  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Aplica-se a**: [objeto de data](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Consulte também  
 [Método getUTCSeconds (Date)](../../javascript/reference/getutcseconds-method-date-javascript.md)   
 [Método setSeconds (Date)](../../javascript/reference/setseconds-method-date-javascript.md)   
 [Método setUTCSeconds (Date)](../../javascript/reference/setutcseconds-method-date-javascript.md)