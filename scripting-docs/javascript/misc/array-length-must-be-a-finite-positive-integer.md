---
title: O tamanho da matriz deve ser um inteiro positivo finito | Microsoft Docs
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
- VS.WebClient.Help.SCRIPT5029
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 1a467040-4702-4178-848f-418a5974e907
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c6589bd2e9bb4acbec5f169087a49e64417dfae7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="array-length-must-be-a-finite-positive-integer"></a>O tamanho da matriz deve ser um número inteiro finito e positivo
Você está chamando o **matriz** construtor com um argumento que não é um número inteiro (números inteiros consistem em zero e o conjunto de números inteiros positivos).  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Usar números inteiros positivos somente ao criar um novo `Array` objeto. Se você quiser criar uma matriz com um único elemento que não é um inteiro, você deve fazê-lo em um processo de duas etapas. Primeiro crie uma matriz com um elemento e coloque o valor do primeiro elemento (array[0]). Este é um exemplo que gera este erro.  
  
    ```JavaScript  
    var piArray = new Array(3.14159);  
    ```  
  
     O exemplo a seguir demonstra a maneira correta para especificar uma matriz com um único elemento numérico.  
  
    ```JavaScript  
    var piArray = new Array(1);  
    piArray [0] = 3.14159;  
    ```  
  
     Não há nenhum limite superior para o tamanho de uma matriz, diferente do valor de inteiro máximo (aproximadamente 4 bilhões).  
  
## <a name="see-also"></a>Consulte também  
 [Usando matrizes](../../javascript/advanced/using-arrays-javascript.md)