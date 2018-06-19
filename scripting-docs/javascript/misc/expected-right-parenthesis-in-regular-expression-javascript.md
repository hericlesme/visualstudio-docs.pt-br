---
title: Esperado &#39;) &#39; na expressão regular (JavaScript) | Microsoft Docs
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
- VS.WebClient.Help.SCRIPT5020
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 2087ba1d-9783-4d40-b609-e8542f579f7f
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ca4560c638cc0e9209141ba9b0878208eb84eb0c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24633876"
---
# <a name="expected-3939-in-regular-expression-javascript"></a>Esperado &#39;) &#39; na expressão regular (JavaScript)
Você tentou criar uma captura de expressão regular, declaração ou grupo, mas não inclui o parêntese de fechamento. Parênteses têm várias finalidades em expressões regulares. Primeiramente, eles são usados para capturar subexpressões, para especificar declarações ou agrupar padrões para que os itens podem ser tratados como uma única unidade, *, +,?, e assim por diante.  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Adicione os parênteses de fechamento na extrema direita.  
  
    > [!NOTE]
    >  Se você deseja corresponder um parêntese único, escape-o com uma barra invertida - \\(- para que ele não será interpretado como um caractere especial por [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## <a name="see-also"></a>Consulte também  
 [Objeto de expressão regular](../../javascript/reference/regular-expression-object-javascript.md)   
 [Sintaxe de expressão regular (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)