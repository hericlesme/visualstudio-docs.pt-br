---
title: Propriedade prototype (WeakMap) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: d28b8a9b-38c9-443d-9586-7cc74784bd99
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5cc1bff0d62f2aeb8d6fb78a0857f287fb34078c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639246"
---
# <a name="prototype-property-weakmap"></a>Propriedade prototype (WeakMap)
Retorna uma referência ao protótipo para um `WeakMap` objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```JavaScript  
weakmap.prototype  
```  
  
## <a name="remarks"></a>Comentários  
 O `weakmap` argumento é o nome de uma `WeakMap` objeto.  
  
 Use a propriedade `prototype` para fornecer um conjunto básico de funcionalidades para uma classe de objetos. Novas instâncias de um objeto "herdam" o comportamento do protótipo atribuído a ele.  
  
 Por exemplo, para adicionar um método para o `WeakMap` que retorna o valor do maior elemento do objeto de `WeakMap`, declarar a função, adicione-o a `WeakMap.prototype`e, em seguida, usá-lo.  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]