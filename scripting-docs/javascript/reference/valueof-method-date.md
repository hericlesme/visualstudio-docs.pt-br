---
title: Método valueOf (Date) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 39a1f96e-14b0-4db2-b53d-cdfd67cbb208
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 87c5e6ea3c3e28d866f7cabf92dc97b81703b5b1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640456"
---
# <a name="valueof-method-date"></a>Método valueOf (Date)
Retorna o valor de hora armazenado em milissegundos desde a meia-noite de 1º de janeiro de 1970 UTC.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
date.valueOf()  
```  
  
#### <a name="parameters"></a>Parâmetros  
 O `date` objeto é qualquer instância de uma data.  
  
## <a name="return-value"></a>Valor de retorno  
 O valor de hora armazenado em milissegundos desde a meia-noite de 1º de janeiro de 1970 UTC. Este é o mesmo valor como `getTime`.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso do `valueOf` método com uma data.  
  
```JavaScript  
var myDate = new Date();  
myDate.setFullYear(2100, 5, 5);  
if (myDate.getTime() == myDate.valueOf())  
    document.write("values are the same");  
else  
    document.write("values are different");  
  
// Output: values are the same  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]