---
title: "Método getUTCMinutes (Date) (JavaScript) | Microsoft Docs"
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
- getUTCMinutes
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- minutes
- UTC times, returning
- getUTCMinutes method
ms.assetid: b6d92543-b285-4e46-8f47-bba36e53fabd
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fe691d3b52d18340eeeff81a91c049a262277c54
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="getutcminutes-method-date-javascript"></a>Método getUTCMinutes (Date) (JavaScript)
Obtém os minutos de um `Date` usando o Horário Coordenado Universal (UTC) do objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
dateObj.getUTCMinutes()   
```  
  
#### <a name="parameters"></a>Parâmetros  
 Obrigatório `dateObj` referência é um `Date` objeto.  
  
## <a name="return-value"></a>Valor de retorno  
 Retorna um número inteiro entre 0 e 59. Zero será retornado que o tempo é menor que um minuto após a hora. Se um `Date` objeto foi criado sem especificar a hora, por padrão o UTC valor de minuto é 0. No entanto, em outros fusos horários pode ser diferente.  
  
## <a name="remarks"></a>Comentários  
 Para obter o número de minutos armazenados usando o horário local, use o `getMinutes` método.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso do método `getUTCMinutes`.  
  
```JavaScript  
var date = new Date("1/1/2001");  
document.write(date.getUTCMinutes());  
document.write("<br/>");  
  
date.setMinutes(5);  
document.write(date.getUTCMinutes());  
  
// Output:   
// 0  
// 5  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Aplica-se a**: [objeto de data](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Consulte também  
 [Método getMinutes (Date)](../../javascript/reference/getminutes-method-date-javascript.md)   
 [Método setMinutes (Date)](../../javascript/reference/setminutes-method-date-javascript.md)   
 [Método setUTCMinutes (Date)](../../javascript/reference/setutcminutes-method-date-javascript.md)