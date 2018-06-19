---
title: Método getTime (Date) (JavaScript) | Microsoft Docs
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
- getTime
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- GetTime method
- time method
ms.assetid: f0da1d4e-337c-497d-9205-093defbc6d3d
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a31e542445e89a0e2f3364d36ae44f8d2d4cf9bb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636656"
---
# <a name="gettime-method-date-javascript"></a>Método getTime (Date) (JavaScript)
Obtém o valor de tempo em milissegundos.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
dateObj.getTime()   
```  
  
#### <a name="parameters"></a>Parâmetros  
 Obrigatório `dateObj` referência é um `Date` objeto.  
  
## <a name="return-value"></a>Valor de retorno  
 Retorna o número de milissegundos entre meia-noite de 1º de janeiro de 1970 e o valor de tempo no `Date` objeto. O intervalo de datas é aproximadamente 285,616 anos a partir de um dos lados da meia-noite de 1º de janeiro de 1970. Números negativos indicam datas antes de 1970.  
  
## <a name="remarks"></a>Comentários  
 Ao fazer a vários cálculos de data e hora, convém definir variáveis iguais ao número de milissegundos em um dia, horas ou minutos. Por exemplo:  
  
```JavaScript  
var minute = 1000 * 60;  
var hour = minute * 60;  
var day = hour * 24;  
```  
  
 Consulte [Calculando datas e horas (JavaScript)](../../javascript/calculating-dates-and-times-javascript.md) para obter mais informações sobre como usar o `getTime` método.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar o método `getTime`.  
  
```JavaScript  
var minute = 1000 * 60;  
var hour = minute * 60;  
var day = hour * 24;  
  
date = new Date("1/1/2001");  
var time = date.getTime();  
  
document.write(Math.round(time / day) + " days from 1/1/1970 to 1/1/2001");  
  
// Output: 11323 days from 1/1/1970 to 1/1/2001  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Aplica-se a**: [objeto de data](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Consulte também  
 [Método setTime (Date)](../../javascript/reference/settime-method-date-javascript.md)