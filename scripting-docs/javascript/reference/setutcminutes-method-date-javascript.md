---
title: Método setUTCMinutes (Date) (JavaScript) | Microsoft Docs
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
- setUTCMinutes
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- minutes
- dates, UTC
- UTC times, setting
- setUTCMinutes method
ms.assetid: 2415e788-6d28-46dd-a103-0931a1fd1446
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 37df1bcefa358f2c9076a3da877bd642d19178b0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640876"
---
# <a name="setutcminutes-method-date-javascript"></a>Método setUTCMinutes (Date) (JavaScript)
Define o valor de minutos a `Date` usando o Horário Coordenado Universal (UTC) do objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
dateObj.setUTCMinutes(numMinutes[, numSeconds[, numMilli]])   
```  
  
## <a name="parameters"></a>Parâmetros  
 `dateObj`  
 Necessário. Qualquer objeto `Date`.  
  
 `numMinutes`  
 Necessário. Um valor numérico igual ao valor de minutos. Deve ser fornecido se qualquer um dos seguintes argumentos é usado.  
  
 *numSeconds*  
 Opcional. Um valor numérico igual ao valor de segundos. Deve ser fornecido se `numMilli` é usado.  
  
 `numMilli`  
 Opcional. Um valor numérico igual ao valor de milissegundos.  
  
## <a name="remarks"></a>Comentários  
 Todos os **definir** métodos levando argumentos opcionais usam o valor retornado da correspondente **obter** métodos, se você não especificar um argumento opcional. Por exemplo, se o *numSeconds* argumento não for especificado, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] usa o valor retornado do `getUTCSeconds` método.  
  
 Para modificar o valor de minutos usando o horário local, use o `setMinutes` método.  
  
 Se o valor de um argumento é maior do que o intervalo, ou é um número negativo, outros valores armazenados forem modificados de acordo. Por exemplo, se a data armazenada é "5 de janeiro de 1996 00:00:00.00", e **setUTCMinutes(70)** é chamado, a data é alterada para "01:10:00.00 5 de janeiro de 1996."  
  
 O **setUTCHours** método pode ser usado para definir as horas, minutos, segundos e milissegundos.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso do `setUTCMinutes` método:  
  
```JavaScript  
function SetUTCMinutesDemo(nmin, nsec){  
   var d, s;                    // Declare variables.  
   d = new Date();              // Create Date object.  
   d.setUTCMinutes(nmin,nsec);  // Set UTC minutes.  
   s = "Current setting is " + d.toUTCString()   
   return(s);                   // Return new setting.  
}  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Aplica-se a**: [objeto de data](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Consulte também  
 [Método getMinutes (Date)](../../javascript/reference/getminutes-method-date-javascript.md)   
 [Método getUTCMinutes (Date)](../../javascript/reference/getutcminutes-method-date-javascript.md)   
 [Método setMinutes (Date)](../../javascript/reference/setminutes-method-date-javascript.md)