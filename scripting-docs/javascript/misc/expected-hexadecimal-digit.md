---
title: Dígito hexadecimal esperado | Microsoft Docs
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
- VS.WebClient.Help.SCRIPT1023
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 67a86df7-49f9-43cb-99c6-99b1a427827a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c9e29131c4ecf4f476a30da94ec67676d6bea347
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24633086"
---
# <a name="expected-hexadecimal-digit"></a>Dígito hexadecimal esperado
Você criou uma sequência de escape Unicode incorretova. Sequências de escape Unicode começam com \u, seguido por exatamente quatro dígitos hexadecimais (não mais e não menos). Dígitos hexadecimais Unicode podem conter apenas os números 0-9, as letras maiusculas A-F e a minúscula letras a-f. O exemplo a seguir demonstra uma sequência de escape Unicode formada corretamente.  
  
```JavaScript  
z = "\u1A5F";  
```  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Certifique-se de que seu dígitos hexadecimais de Unicode começam com \u, contém somente os números 0-9, as letras maiusculas A-F, a letras minúsculas letras a-f; e são agrupadas em quatro dígitos.  
  
    > [!NOTE]
    >  Se você quiser usar o \u texto literal em uma cadeia de caracteres, use duas barras invertidas - (\\\u)-uma para escape de barra invertida primeiro.  
  
## <a name="see-also"></a>Consulte também  
 [Tipos de Dados](../../javascript/data-types-javascript.md)