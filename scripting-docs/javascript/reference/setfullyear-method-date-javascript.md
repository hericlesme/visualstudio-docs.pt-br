---
title: Método setFullYear (Date) (JavaScript) | Microsoft Docs
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
- setFullYear
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Year method
- setFullYear method
- dates, setting
ms.assetid: 635e4f5a-0210-4c01-8152-b0da4146f6ff
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1e5e20a8486d1aefeab9b244c5f1e9d1b1e60c3f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640346"
---
# <a name="setfullyear-method-date-javascript"></a>Método setFullYear (Date) (JavaScript)
Define o ano do `Date` usando o horário local do objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
dateObj.setFullYear(numYear[, numMonth[, numDate]])   
```  
  
## <a name="parameters"></a>Parâmetros  
 `dateObj`  
 Necessário. Qualquer objeto `Date`.  
  
 `numYear`  
 Necessário. Um valor numérico para o ano.  
  
 `numMonth`  
 Opcional. Um valor numérico com base em zero para o mês (de 0 para 11 de janeiro, de dezembro). Deve ser especificado se `numDate` for especificado.  
  
 `numDate`  
 Opcional. Um valor numérico igual para o dia do mês.  
  
## <a name="remarks"></a>Comentários  
 Todos os **definir** métodos levando argumentos opcionais usam o valor retornado da correspondente **obter** métodos, se você não especificar o argumento opcional. Por exemplo, se o `numMonth` argumento é opcional, mas não for especificado, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] usa o valor retornado do **getMonth** método.  
  
 Além disso, se o valor de um argumento é maior do que o intervalo de calendário ou for negativo, a data faz Avançar ou retroceder conforme apropriado.  
  
 Para definir o ano usando o Horário Coordenado Universal (UTC), use o `setUTCFullYear` método.  
  
 O intervalo de anos com suporte no objeto de data é aproximadamente 285,616 anos antes e depois de 1970.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso do `setFullYear` método:  
  
```JavaScript  
var date1 = new Date("1/1/2001");  
date1.setFullYear(2007);  
  
var date2 = new Date("1/1/2001");  
date2.setFullYear(2008, 10, 3);   
  
document.write (date1.toLocaleString());  
document.write ("<br />");  
document.write (date2.toLocaleString());  
  
// Output:  
// Monday, January 01, 2007 12:00:00 AM  
// Monday, November 03, 2008 12:00:00 AM  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Aplica-se a**: [objeto de data](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Consulte também  
 [Método getFullYear (Date)](../../javascript/reference/getfullyear-method-date-javascript.md)   
 [Método getUTCFullYear (Date)](../../javascript/reference/getutcfullyear-method-date-javascript.md)   
 [Método setUTCFullYear (Date)](../../javascript/reference/setutcfullyear-method-date-javascript.md)