---
title: "O tamanho da matriz deve ser atribuído a um número finito e positivo | Microsoft Docs"
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
- VS.WebClient.Help.SCRIPT5030
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: c51c66a4-a543-4e95-b18d-2cfbcb3d1fdd
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 63a9d714173334192028b9096de41968befa85ef
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="array-length-must-be-assigned-a-finite-positive-number"></a>O tamanho da matriz deve receber um número finito e positivo
Ao definir o **comprimento** propriedade de um objeto existente **matriz** objeto, você especificou um comprimento de matriz não era um número positivo ou zero. Esse erro ocorre quando você atribui um valor para o **comprimento** propriedade de um `Array` objeto negativo ou não é um número (`NaN`). Observe que [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] automaticamente converte números fracionários em inteiros.  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Atribua um número inteiro positivo para a propriedade de comprimento. Não há nenhum limite superior para o tamanho de uma matriz, diferente do valor de inteiro máximo (aproximadamente 4 bilhões). O exemplo a seguir demonstra a maneira correta para definir o **comprimento** propriedade de um **matriz** objeto.  
  
    ```JavaScript  
    var my_array = new Array();  
    my_array.length = 99;  
    ```  
  
## <a name="see-also"></a>Consulte também  
 [Usando matrizes](../../javascript/advanced/using-arrays-javascript.md)