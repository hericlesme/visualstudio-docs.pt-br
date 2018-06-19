---
title: Método setMilliseconds (Date) (JavaScript) | Microsoft Docs
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
- setMilliseconds
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- milliseconds
- setMilliseconds method
ms.assetid: 6c398961-130e-4f60-802f-6c30e1ef4de4
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f0cd339e1352511312ef9a9abf9a7ff02955c986
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639796"
---
# <a name="setmilliseconds-method-date-javascript"></a>Método setMilliseconds (Date) (JavaScript)
Define o valor de milissegundos a `Date` usando o horário local do objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
dateObj.  
setMilliseconds(  
numMilli  
)   
```  
  
## <a name="parameters"></a>Parâmetros  
 `dateObj`  
 Necessário. Qualquer objeto `Date`.  
  
 `numMilli`  
 Necessário. Um valor numérico igual ao valor de milissegundos.  
  
## <a name="remarks"></a>Comentários  
 Para definir o valor de milissegundos usando o Horário Coordenado Universal (UTC), use o `setUTCMilliseconds` método.  
  
 Se o valor de `numMilli` é maior do que 999 ou é um número negativo, o número armazenado segundos (e minutos, horas, e assim por diante se necessário) é incrementado uma quantidade apropriada.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso do método `setMilliseconds`.  
  
```JavaScript  
function SetMSecDemo(nmsec){  
   var d, s;                    // Declare variables.  
   d = new Date();              // Create Date object.  
   d.setMilliseconds(nmsec);    // Set milliseconds.  
   s = "Current setting is ";  
   s += d.toLocaleString();  
   s += " and " + d.getMilliseconds();  
   s += " milliseconds";  
   return(s);                   // Return new date setting.  
}  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Aplica-se a**: [objeto de data](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Consulte também  
 [Método getMilliseconds (Date)](../../javascript/reference/getmilliseconds-method-date-javascript.md)   
 [Método getUTCMilliseconds (Date)](../../javascript/reference/getutcmilliseconds-method-date-javascript.md)   
 [Método setUTCMilliseconds (Date)](../../javascript/reference/setutcmilliseconds-method-date-javascript.md)