---
title: "O URI a ser decodificado contém um caractere inválido | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.WebClient.Help.SCRIPT5024
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: a3f0fdbb-8d4b-41ae-a396-43dfc9483760
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1e93d145ea6b0991123c2a7c80f8acf54a83a264
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="the-uri-to-be-encoded-contains-an-invalid-character"></a>O URI a ser decodificado contém um caractere inválido
Você tentou codificar uma cadeia de caracteres como um URI (Uniform Resource Identifier), mas ele continha caracteres inválidos. Embora a maioria dos caracteres são válidas dentro de cadeias de caracteres a ser convertido em URIs, alguns sequências de caracteres Unicode são inválidas.  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Certifique-se de que a cadeia de caracteres a ser decodificado contém somente sequências de Unicode válidas. Um URI completo é composto de uma sequência de componentes e separadores. Os nomes de colchetes angulares representam componentes e o ":", "/", ";" e "?" são caracteres reservados usados como separadores. O formato geral é:  
  
    ```JavaScript  
    <Scheme>:<first>/<second>;<third>?<fourth>  
    ```  
  
## <a name="see-also"></a>Consulte também  
 [Função encodeURI](../../javascript/reference/encodeuri-function-javascript.md)   
 [Função encodeURIComponent](../../javascript/reference/encodeuricomponent-function-javascript.md)