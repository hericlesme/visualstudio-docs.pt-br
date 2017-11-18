---
title: Objeto de data esperado | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.WebClient.Help.SCRIPT5006
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: d6ab82e6-ca64-46b4-a06c-5c6b0aa057cb
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 05e27b822f933ade811084552f6f0379257ae82e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="date-object-expected"></a>Objeto de data esperado
Você tentou invocar o **Date.prototype.toString** ou **Date.prototype.valueOf** método em um objeto de um tipo diferente de `Date`. O objeto desse tipo de chamada deve ser do tipo `Date`. Por exemplo:  
  
```JavaScript  
var o = new Object;  
o.f = Date.prototype.toString;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Invoque apenas o **Date.prototype.toString** ou **Date.prototype.valueOf** métodos em objetos do tipo `Date`.  
  
## <a name="see-also"></a>Consulte também  
 [Objeto Date](../../javascript/reference/date-object-javascript.md)   
 [Método getDate (Date)](../../javascript/reference/getdate-method-date-javascript.md)   
 [Objetos intrínsecos](../../javascript/intrinsic-objects-javascript.md)