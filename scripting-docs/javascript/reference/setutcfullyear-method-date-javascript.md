---
title: "Método setUTCFullYear (Date) (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: setUTCFullYear
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- dates, UTC
- setUTCFullYear method
- UTC dates, setting
ms.assetid: e6c51b49-0149-4f9a-aa74-c73c0306f98e
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2dda8b75dd8bc8dac87ea383546f392b064c1d63
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="setutcfullyear-method-date-javascript"></a>Método setUTCFullYear (Date) (JavaScript)
Define o valor de ano de `Date` usando o Horário Coordenado Universal (UTC) do objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
dateObj.setUTCFullYear(numYear[, numMonth[, numDate]])   
```  
  
## <a name="parameters"></a>Parâmetros  
 `dateObj`  
 Necessário. Qualquer objeto `Date`.  
  
 `numYear`  
 Necessário. Um valor numérico igual ao ano.  
  
 `numMonth`  
 Opcional. Um valor numérico igual para o mês. O valor de janeiro é 0 e outros valores de mês siga consecutivamente. Deve ser fornecido se *numDate* é fornecido.  
  
 *numDate*  
 Opcional. Um valor numérico igual para o dia do mês.  
  
## <a name="remarks"></a>Comentários  
 Todos os **definir** métodos levando argumentos opcionais usam o valor retornado da correspondente **obter** métodos, se você não especificar um argumento opcional. Por exemplo, se o `numMonth` argumento não for especificado, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] usa o valor retornado do `getUTCMonth` método.  
  
 Além disso, se o valor de um argumento é maior que o intervalo ou um negativo número, os valores armazenados forem modificados de acordo.  
  
 Para definir o ano usando a hora local, use o `setFullYear` método.  
  
 O intervalo de anos com suporte no `Date` objeto é de aproximadamente 285,616 anos de um dos lados de 1970.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso do método `setUTCFullYear`.  
  
```JavaScript  
var dtFirst = new Date();  
dtFirst.setUTCFullYear(2007);  
  
var dtSecond = new Date();  
// 10 is the value for November.   
dtSecond.setUTCFullYear(2008, 10, 3);   
  
document.write (dtFirst.toUTCString());  
document.write ("<br />");  
document.write (dtSecond.toUTCString());  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Aplica-se a**: [objeto de data](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Consulte também  
 [Método getFullYear (Date)](../../javascript/reference/getfullyear-method-date-javascript.md)   
 [Método getUTCFullYear (Date)](../../javascript/reference/getutcfullyear-method-date-javascript.md)   
 [Método setFullYear (Date)](../../javascript/reference/setfullyear-method-date-javascript.md)