---
title: "Método toGMTString (Date) (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: toGMTString
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: toGMTString method
ms.assetid: 9dc1e722-5722-4b8c-a213-a2650f55f207
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cef8a61e04fbb5ada6e03fa946f434327422d9d7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="togmtstring-method-date-javascript"></a>Método toGMTString (Date) (JavaScript)
Retorna uma data convertida em uma cadeia de caracteres usando (GMT) média de Greenwich.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
dateObj.toGMTString()   
```  
  
## <a name="remarks"></a>Comentários  
 Obrigatório `dateObj` referência é qualquer `Date` objeto.  
  
 O `toGMTString` método está obsoleto e é fornecido para fins de compatibilidade apenas. É recomendável que você use o `toUTCString` método em vez disso.  
  
 O `toGMTString` método retorna um `String` objeto que contém a data formatada usando a convenção de GMT. O formato do valor de retorno é o seguinte: "05 de janeiro de 1996 00:00:00 GMT."  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Aplica-se a**: [objeto de data](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Consulte também  
 [Método toUTCString (Date)](../../javascript/reference/toutcstring-method-date-javascript.md)