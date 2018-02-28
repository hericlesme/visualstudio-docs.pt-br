---
title: Quantificador inesperado (JavaScript) | Microsoft Docs
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
- VS.WebClient.Help.SCRIPT5018
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: ba6d34f9-2d6f-486c-a929-6cd9818be322
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fb6d6d3129057c399dd7369c6f69eb7396f07ab4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="unexpected-quantifier-javascript"></a>Quantificador inesperado (JavaScript)
Ao compor o padrão de pesquisa de expressão regular, você criou um elemento padrão com um fator de repetição inválida. Por exemplo, o padrão  
  
```  
/^+/  
```  
  
 é inválido porque o elemento ^ (início de entrada) não pode ter um fator de repetição. A tabela a seguir lista os elementos que não podem ter fatores de repetição.  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|^|Início da entrada|  
|$|fim de entrada|  
|\b|Limite de palavra|  
|\B|Limite de palavra não|  
|*|Zero ou mais repetições|  
|+|Um ou mais repetições|  
|?|Repetições de zero ou um|  
|{n}|repetições n|  
|{n}|n ou mais repetições|  
|{n, m}|De n a m repetições, inclusivas|  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Certifique-se de que o elemento padrão de pesquisa contém apenas os fatores de repetição legal.  
  
## <a name="see-also"></a>Consulte também  
 [Objeto de expressão regular](../../javascript/reference/regular-expression-object-javascript.md)   
 [Sintaxe de expressão regular (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)