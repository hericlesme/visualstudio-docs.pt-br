---
title: "Instrução (JavaScript) rotulada | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: labeled_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- continue statement
- labeled statement
- identifiers, statements
ms.assetid: 019f898e-9e27-4be4-a22f-c5927c7fcae2
caps.latest.revision: "19"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bd72b15d3fc9083ca127a48981c0cd0a7ee56b6c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="labeled-statement-javascript"></a>Instrução rotulada (JavaScript)
Fornece um identificador para uma instrução.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
      label :  
   statements   
```  
  
## <a name="parameters"></a>Parâmetros  
 *rótulo*  
 Necessário. Um identificador exclusivo usado para se referir à instrução rotulada.  
  
 `statements`  
 Opcional. Uma ou mais instruções associadas *rótulo*.  
  
## <a name="remarks"></a>Comentários  
 Rótulos que são usados pelo **quebra** e **continuar** instruções para especificar a instrução para o qual o **quebra** e **continuar** se aplicam.  
  
## <a name="example"></a>Exemplo  
 No código a seguir, o **continuar** instrução refere-se para o **para** loop que é precedido pelo `Inner:` instrução. Quando `j` é 24, o **continuar** instrução faz com que que **para** loop para ir para a próxima iteração. Os números de 21 a 23 e 25 a 30 impressos em cada linha.  
  
```JavaScript  
Outer:  
for (i = 1; i <= 10; i++) {  
   document.write ("<br />");  
   document.write ("i: " + i);  
   document.write (" j: ");  
  
Inner:  
   for (j = 21; j <= 30; j++) {  
      if (j == 24)  
          {  
          continue Inner;  
      }  
      document.write (j + " ");  
  }  
}  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Instrução break](../../javascript/reference/break-statement-javascript.md)   
 [Instrução continue](../../javascript/reference/continue-statement-javascript.md)