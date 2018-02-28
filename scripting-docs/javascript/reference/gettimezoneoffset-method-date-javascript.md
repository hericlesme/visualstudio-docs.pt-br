---
title: "Método getTimezoneOffset (Date) (JavaScript) | Microsoft Docs"
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
- getTimeZoneOffset
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- getTimezoneOffset method
- time zones [Visual Studio]
ms.assetid: 58ee22b0-4688-45bd-a337-cc23119b09ce
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e49a3c8b7060e6097300f8aaf99b2ef869833018
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="gettimezoneoffset-method-date-javascript"></a>Método getTimezoneOffset (Date) (JavaScript)
Obtém a diferença de minutos entre a hora no computador local e o Horário Coordenado Universal (UTC).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
dateObj.getTimezoneOffset()   
```  
  
#### <a name="parameters"></a>Parâmetros  
 Obrigatório `dateObj` referência é um `Date` objeto.  
  
## <a name="return-value"></a>Valor de retorno  
 Retorna o número de minutos entre a hora no computador atual (o computador cliente ou, se esse método é chamado de um script do servidor, a máquina do servidor) e o UTC. É positivo se o atual horário do computador local estiver atrás de UTC (por exemplo, horário de verão do Pacífico) e negativo se o atual horário do computador local está à frente do UTC (por exemplo, Japão). Se um servidor em Nova York é contatado por um cliente em Los Angeles em 1 de dezembro, `getTimezoneOffset` retorna 480 se executado no cliente ou 300 se executado no servidor.  
  
## <a name="remarks"></a>Comentários  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar o método `getTimezoneOffset`.  
  
```JavaScript  
var date =  new Date();  
var minutes = date.getTimezoneOffset();  
  
if (minutes < 0)  
    document.write(minutes / 60 + " hours after UTC");  
else  
    document.write(minutes / 60 + " hours before UTC");  
  
// Output (for example, where local time is PST):   
7 hours before UTC  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Aplica-se a**: [objeto de data](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Consulte também  
 [Método getTime (Date)](../../javascript/reference/gettime-method-date-javascript.md)