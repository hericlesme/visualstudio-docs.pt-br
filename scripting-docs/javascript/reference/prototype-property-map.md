---
title: Propriedade prototype (Map) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: c7b429cb-97b7-400e-a214-1b18bddd6b02
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 45601bdff2dfc8047f2499ab07dcdedd66662fc5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="prototype-property-map"></a>Propriedade prototype (Map)
Retorna uma referência ao protótipo para um mapa.  
  
## <a name="syntax"></a>Sintaxe  
  
```JavaScript  
map.prototype  
```  
  
## <a name="remarks"></a>Comentários  
 O `map` argumento é o nome de um mapa.  
  
 Use a propriedade `prototype` para fornecer um conjunto básico de funcionalidades para uma classe de objetos. Novas instâncias de um objeto "herdam" o comportamento do protótipo atribuído a ele.  
  
 Por exemplo, para adicionar um método ao objeto `Map` que retorna o valor do maior elemento do conjunto, declare a função, adicione-a a `Map.prototype` e use-a.  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]