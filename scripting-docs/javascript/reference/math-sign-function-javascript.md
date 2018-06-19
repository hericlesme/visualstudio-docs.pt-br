---
title: Função Math Sign (JavaScript) | Microsoft Docs
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
ms.assetid: 8b462020-ceff-4947-8dd1-c78e6aff8d98
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2cae32118f2265e02c67592facff8e49e8edd633
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24638026"
---
# <a name="mathsign-function-javascript"></a>Função Math.sign (JavaScript)
Retorna o sinal de um número, indicando se o número é positivo, negativo ou 0.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Math.sign(number)  
```  
  
## <a name="remarks"></a>Comentários  
 O argumento `number` obrigatório é uma expressão numérica para a qual o sinal é necessário.  
  
 O valor retornado é um dos seguintes:  
  
-   `NaN`, se `number` for `NaN`.  
  
-   -0, se `number` é - 0.  
  
-   +0, se `number` for +0.  
  
-   -1, se `number` é negativo e não - 0.  
  
-   -1, se `number` for positivo e não +0.  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]