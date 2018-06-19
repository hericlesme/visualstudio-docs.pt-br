---
title: VBArray esperado | Microsoft Docs
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
- VS.WebClient.Help.SCRIPT5013
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: f2998d7d-13a4-4bbe-b872-3ff3316551e4
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9b07c5e08e4178c9c31045317627424f5192f5e1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24633186"
---
# <a name="vbarray-expected"></a>VBArray esperado
Você forneceu um objeto que não era um safeArray de Visual Basic, quando um era esperado.  
  
```  
new VBArray(safeArray);  
```  
  
 VBArrays são somente leitura e não pode ser criados diretamente. O argumento de safeArray é um valor de VBArray e deve ter obtido um valor VBArray antes de ser passado para o `VBArray` construtor. Isso pode ser feito somente por recuperar o valor de um controle ActiveX existente ou em outro objeto.  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Certifique-se de que você passar somente **VBArray** objetos para o **VBArray** construtor.  
  
## <a name="see-also"></a>Consulte também  
 [Objeto VBArray](../../javascript/reference/vbarray-object-javascript.md)   
 [Usando matrizes](../../javascript/advanced/using-arrays-javascript.md)