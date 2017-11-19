---
title: "Método getMilliseconds (Date) (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: getMilliseconds
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- milliseconds
- getMilliseconds method
ms.assetid: 1b512146-1e8a-44a4-89da-6cc5338d15cb
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 33e5fc54dffbe06e47f0978e6cef94b1f650c90f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="getmilliseconds-method-date-javascript"></a>Método getMilliseconds (Date) (JavaScript)
Obtém os milissegundos de uma data, usando o horário local.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
dateObj.getMilliseconds()   
```  
  
#### <a name="parameters"></a>Parâmetros  
 Obrigatório `dateObj` referência é um `Date` objeto.  
  
## <a name="return-value"></a>Valor de retorno  
 Retorna os milissegundos de uma data. O valor pode variar de 0 a 999. Se uma data foi construída sem especificar os milissegundos, o valor retornado será 0.  
  
## <a name="remarks"></a>Comentários  
 Para obter o número de milissegundos em Horário Coordenado Universal (UTC), use o `getUTCMilliseconds` método.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar o **getMilliseconds** método.  
  
```JavaScript  
var date = new Date("1/1/2001");  
document.write(date.getMilliseconds());  
document.write("<br/>");  
  
date.setMilliseconds(5);  
document.write(date.getMilliseconds());  
// Output:   
// 0  
// 5  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Aplica-se a**: [objeto de data](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Consulte também  
 [Método getUTCMilliseconds (Date)](../../javascript/reference/getutcmilliseconds-method-date-javascript.md)   
 [Método setMilliseconds (Date)](../../javascript/reference/setmilliseconds-method-date-javascript.md)   
 [Método setUTCMilliseconds (Date)](../../javascript/reference/setutcmilliseconds-method-date-javascript.md)