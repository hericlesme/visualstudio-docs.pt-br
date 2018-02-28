---
title: Pode &#39; t ter &#39; quebra &#39; fora do loop | Microsoft Docs
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
- VS.WebClient.Help.SCRIPT1019
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 11d02172-2a78-4705-a730-d21111db5f42
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bb23f1bc3de087515cad9ba4910cf2ebaf640353
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="can39t-have-39break39-outside-of-loop"></a>Pode &#39; t ter &#39; quebra &#39; fora do loop
Você tentou usar o **quebra** palavra-chave fora de um loop. O **quebra** palavra-chave é usada para encerrar um loop ou `switch` instrução. Ele deve ser inserido no corpo de um loop ou `switch` instrução. No entanto, um **rótulo** pode seguir a palavra-chave break.  
  
```  
break labelname;  
```  
  
 Você só precisa de forma de rotulado o **quebra** loops aninhados de palavra-chave quando você está usando ou `switch` instruções e precisa interromper um loop que não é o mais interno.  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Verifique se o **quebra** palavra-chave aparece dentro de uma instrução de circunscrição loop ou comutador.  
  
## <a name="see-also"></a>Consulte também  
 [Instrução break](../../javascript/reference/break-statement-javascript.md)   
 [Controlando o fluxo de programa](../../javascript/controlling-program-flow-javascript.md)   
 [Solucionar problemas com scripts](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)