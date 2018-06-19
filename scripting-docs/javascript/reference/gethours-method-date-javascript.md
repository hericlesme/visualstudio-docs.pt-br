---
title: Método getHours (Date) (JavaScript) | Microsoft Docs
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
- getHours
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Date object
- GetHours method
- Hours method
ms.assetid: c3936496-a213-4d15-b308-d53926ed310c
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 87170f96ee6ae6b4a825436717a94749cc336ee0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636616"
---
# <a name="gethours-method-date-javascript"></a>Método getHours (Date) (JavaScript)
Obtém as horas em uma data, usando o horário local.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
dateObj.getHours()   
```  
  
#### <a name="parameters"></a>Parâmetros  
 Obrigatório `dateObj` referência é um `Date` objeto.  
  
## <a name="return-value"></a>Valor de retorno  
 Um inteiro entre 0 e 23, que indica o número de horas desde a meia-noite. Zero será retornado se a hora está antes de 1:00:00 am. Se um `Date` objeto foi criado sem especificar a hora, por padrão, a hora é 0.  
  
## <a name="remarks"></a>Comentários  
 Para obter o valor de horas usando o Horário Coordenado Universal (UTC), use o `getUTCHours` método.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar o método `getHours`.  
  
```JavaScript  
var date = new Date("1/1/2001");  
document.write(date.getHours());  
document.write("<br/>");  
  
date.setTime(50000000);  
document.write(date.getHours());  
  
// Output:  
// 0   
// 5  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Aplica-se a**: [objeto de data](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Consulte também  
 [Método getUTCHours (Date)](../../javascript/reference/getutchours-method-date-javascript.md)   
 [Método setHours (Date)](../../javascript/reference/sethours-method-date-javascript.md)   
 [Método setUTCHours (Date)](../../javascript/reference/setutchours-method-date-javascript.md)