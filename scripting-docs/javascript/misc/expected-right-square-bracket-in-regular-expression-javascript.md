---
title: Esperado &#39;] &#39; na expressão regular (JavaScript) | Microsoft Docs
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
- VS.WebClient.Help.SCRIPT5019
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 1ca2079a-44dd-479f-a1e3-e04a14d0739e
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4c59dcbeea91a1bc01e870d0a49fd22cace6562d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24633316"
---
# <a name="expected-3939-in-regular-expression-javascript"></a>Esperado &#39;] &#39; na expressão regular (JavaScript)
Você tentou criar uma classe de caracteres para uma correspondência da expressão regular, mas não inclui o colchete direito. Combinações de caracteres literal individuais podem ser montadas em classes de caracteres, colocando-os entre colchetes. Uma classe de caracteres corresponde a qualquer caractere que ele contém. Por exemplo, / [abc] / corresponde a qualquer uma das letras "a", "b", ou "c".  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Adicione o colchete direito à expressão regular.  
  
    > [!NOTE]
    >  Se você deseja corresponder a um único colchete, escape-o com uma barra invertida - \\[- o para que ele não será interpretado como um caractere especial por [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## <a name="see-also"></a>Consulte também  
 [Objeto de expressão regular](../../javascript/reference/regular-expression-object-javascript.md)   
 [Sintaxe de expressão regular (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)