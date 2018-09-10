---
title: Intervalo inválido no caractere definido (JavaScript) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT5021
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 971e9d5a-f88a-47a8-af94-f3c7c4aed5ab
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e4cc8feb9a33c2995e592f8031beb2e03605891d
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44282803"
---
# <a name="invalid-range-in-character-set-javascript"></a>Intervalo inválido no conjunto de caracteres (JavaScript)
Você tentou criar uma expressão regular com um intervalo de conjunto de caractere inválido. Conjuntos de caracteres devem variar desde caracteres únicos, como a-z ou 0 a 9; Você não pode incluir classes de caractere como \w em um conjunto de caracteres. O primeiro caractere no intervalo também deve vir antes do segundo caractere no intervalo. Por exemplo:  
  
```JavaScript  
var good = /[a-z]/;     // A valid character range - a comes before z.  
var notGood = /[z-a]/;  // An invalid character range - z does not come before a.  
```  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Use caracteres único apenas para compor o seu conjunto de caracteres de expressão regular e verifique se que eles estão na ordem correta.  
  
## <a name="see-also"></a>Consulte também  
 [Objeto de expressão regular](../../javascript/reference/regular-expression-object-javascript.md)   
 [Sintaxe de expressão regular (JavaScript)](https://msdn.microsoft.com/library/1400241x)