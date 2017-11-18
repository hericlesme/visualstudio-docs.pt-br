---
title: "Método setMinutes (Date) (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: setMinutes
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- minutes
- setMinutes method
ms.assetid: 34c959cd-cd29-4cee-8e04-9061cf6d42f3
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1ce40cb3ebf769cdd8f668e246e272833780434d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="setminutes-method-date-javascript"></a>Método setMinutes (Date) (JavaScript)
Define o valor de minutos a **data** usando o horário local do objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
dateObj.setMinutes(numMinutes[, numSeconds[, numMilli]])   
```  
  
## <a name="parameters"></a>Parâmetros  
 `dateObj`  
 Necessário. Qualquer objeto `Date`.  
  
 `numMinutes`  
 Necessário. Um valor numérico igual ao valor de minutos. Deve ser fornecido se qualquer um dos seguintes argumentos é usado.  
  
 *numSeconds*  
 Opcional. Um valor numérico igual ao valor de segundos. Deve ser fornecido se o `numMilli` argumento é usado.  
  
 `numMilli`  
 Opcional. Um valor numérico igual ao valor de milissegundos.  
  
## <a name="remarks"></a>Comentários  
 Todos os **definir** métodos levando argumentos opcionais usam o valor retornado da correspondente **obter** métodos, se você não especificar um argumento opcional. Por exemplo, se o *numSeconds* argumento não especificado, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] usa o valor retornado do `getSeconds` método.  
  
 Para definir o valor de minutos usando o Horário Coordenado Universal (UTC), use o `setUTCMinutes` método.  
  
 Se o valor de um argumento é maior do que o intervalo ou é um número negativo, outros valores armazenados forem modificados de acordo. Por exemplo, se a data armazenada é "5 de janeiro de 1996 00:00:00" e **setMinutes(90)** é chamado, a data é alterada para "5 de janeiro de 1996 01:30:00." Números negativos têm um comportamento semelhante.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso do método `setMinutes`.  
  
```JavaScript  
function SetMinutesDemo(nmin, nsec){  
   var d, s;                     // Declare variables.  
   d = new Date();               // Create Date object.  
   d.setMinutes(nmin, nsec);     // Set minutes.  
   s = "Current setting is " + d.toLocaleString()   
   return(s);                    // Return new setting.  
}  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Aplica-se a**: [objeto de data](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Consulte também  
 [Método getMinutes (Date)](../../javascript/reference/getminutes-method-date-javascript.md)   
 [Método getUTCMinutes (Date)](../../javascript/reference/getutcminutes-method-date-javascript.md)   
 [Método setUTCMinutes (Date)](../../javascript/reference/setutcminutes-method-date-javascript.md)