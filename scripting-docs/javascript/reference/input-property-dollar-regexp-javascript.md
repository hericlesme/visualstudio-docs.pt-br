---
title: Propriedade Input ($_) (RegExp) (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: $_
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- input property
- $_ property
ms.assetid: 88c6d1d8-56f7-4334-a7eb-e899aec9cda4
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8a447950783473d975bfe799eaa2bf18008e539e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="input-property--regexp-javascript"></a>Propriedade input ($_) (RegExp) (JavaScript)
Retorna a cadeia de caracteres em relação ao qual foi realizada uma pesquisa de expressão regular. Somente leitura.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
RegExp.input  
```  
  
## <a name="remarks"></a>Comentários  
 O objeto associado a essa propriedade é sempre global `RegExp` objeto.  
  
 O valor de **entrada** propriedade é modificada a qualquer momento em que a cadeia de caracteres pesquisada é alterada.  
  
 O exemplo a seguir ilustra o uso do **entrada** propriedade:  
  
```JavaScript  
function inputDemo(){  
   var s;  
   var re = new RegExp("d(b+)(d)","ig");  
   var str = "cdbBdbsbdbdz";  
   var arr = re.exec(str);  
   s = "The string used for the match was " + RegExp.input;   
   return(s);  
}  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Aplica-se a**: [objeto RegExp](../../javascript/reference/regexp-object-javascript.md)  
  
## <a name="see-also"></a>Consulte também  
 [Sintaxe de expressão regular (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)