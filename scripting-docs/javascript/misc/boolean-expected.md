---
title: Booliano esperado | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT5010
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 35d71b7f-53fd-44c4-a7c7-b1550c65cfd4
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 600ab26f60c2196ebc682adcffcd6b24c23cd358
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="boolean-expected"></a>Booliano esperado
Você tentou invocar o **Boolean.prototype.toString** ou **Boolean.prototype.valueOf** método em um objeto de um tipo diferente de `Boolean`. O objeto desse tipo de chamada deve ser do tipo `Boolean`. Por exemplo:  
  
```JavaScript  
var o = new Object;  
o.f = Boolean.prototype.toString;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Invoque apenas o valor booliano**. prototype.toString** ou **Boolean.prototype.valueOf** métodos em objetos do tipo **booliano.**  
  
## <a name="see-also"></a>Consulte também  
 [Objeto booliano](../../javascript/reference/boolean-object-javascript.md)   
 [Tipos de Dados](../../javascript/data-types-javascript.md)   
 [Controlando o fluxo de programa](../../javascript/controlling-program-flow-javascript.md)   
 [Copiar, passar e comparar dados](../../javascript/advanced/copying-passing-and-comparing-data-javascript.md)