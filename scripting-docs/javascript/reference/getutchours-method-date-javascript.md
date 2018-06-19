---
title: Método getUTCHours (Date) (JavaScript) | Microsoft Docs
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
- getUTCHours
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- hours
- UTC times, returning
- getUTCHours method
ms.assetid: 7c9825dd-4b3a-4614-8e09-f40df123b630
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c47fe66e6eecb9e3aaa53f0d0988631062676d17
ms.sourcegitcommit: ba29e4d37db92ec784d4acf9c6e120cf0ea677e9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2018
ms.locfileid: "28943843"
---
# <a name="getutchours-method-date-javascript"></a>Método getUTCHours (Date) (JavaScript)
Obtém o valor de horas em um `Date` usando o Horário Coordenado Universal (UTC) do objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
dateObj.getUTCHours()   
```  
  
#### <a name="parameters"></a>Parâmetros  
 Obrigatório `dateObj` referência é um `Date` objeto.  
  
## <a name="return-value"></a>Valor de retorno  
 Retorna um número inteiro entre 0 e 23, que indica o número de horas desde a meia-noite. Zero será retornado se a hora está antes de 1:00:00 am. Se um `Date` objeto foi criado sem especificar a hora, por padrão, a hora é 0 na hora UTC. Esse tempo pode ser diferente de zero em outros fusos horários.  
  
## <a name="remarks"></a>Comentários  
 Para obter o número de horas decorrido desde a meia-noite usando o horário local, use o `getHours` método.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso do método `getUTCHours`.  
  
```JavaScript  
var date = new Date("1/1/2001");  
document.write(date.getUTCHours());  
document.write("<br/>");  
  
var date2 = new Date("1/1/2001 11:22:33");  
document.write(date2.getUTCHours());  
  
// Output (in the PST time zone):  
// 15 
// 2  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Aplica-se a**: [objeto de data](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Consulte também  
 [Método getHours (Date)](../../javascript/reference/gethours-method-date-javascript.md)   
 [Método setHours (Date)](../../javascript/reference/sethours-method-date-javascript.md)   
 [Método setUTCHours (Date)](../../javascript/reference/setutchours-method-date-javascript.md)
