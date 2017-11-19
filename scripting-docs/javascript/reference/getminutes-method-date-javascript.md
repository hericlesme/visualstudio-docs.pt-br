---
title: "Método getMinutes (Date) (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: getMinutes
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- GetMinutes method
- minutes method
ms.assetid: d4139b5d-04e1-474c-9a83-e9d40597243a
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ff08fd84345c9ceb816444a1b44643a8353b60b1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="getminutes-method-date-javascript"></a>Método getMinutes (Date) (JavaScript)
Obtém os minutos de um `Date` do objeto, usando o horário local.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
dateObj.getMinutes()   
```  
  
#### <a name="parameters"></a>Parâmetros  
 Obrigatório `dateObj` referência é um `Date` objeto.  
  
## <a name="return-value"></a>Valor de retorno  
 Retorna um número inteiro entre 0 e 59. Zero será retornado que o tempo é menor que um minuto após a hora. Se um `Date` objeto foi criado sem especificar a hora, por padrão, o valor de minuto é 0.  
  
## <a name="remarks"></a>Comentários  
 Para obter o valor de minutos usando o Horário Coordenado Universal (UTC), use o `getUTCMinutes` método.  
  
## <a name="example"></a>Exemplo  
 A exemplo a seguir mostra como o `getMinutes` método.  
  
```JavaScript  
var date = new Date("1/1/2001");  
document.write(date.getMinutes());  
document.write("<br/>");  
  
date.setMinutes(5);  
document.write(date.getMinutes());  
  
// Output:  
// 0  
// 5  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Aplica-se a**: [objeto de data](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Consulte também  
 [Método getUTCMinutes (Date)](../../javascript/reference/getutcminutes-method-date-javascript.md)   
 [Método setMinutes (Date)](../../javascript/reference/setminutes-method-date-javascript.md)   
 [Método setUTCMinutes (Date)](../../javascript/reference/setutcminutes-method-date-javascript.md)