---
title: Propriedade prototype (WeakSet) | Microsoft Docs
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
ms.assetid: 950e15a2-2f56-4cb9-8e48-020efd97f938
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8c66c7854a83dcf3128025350a7fcdd17f4dfaf5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639156"
---
# <a name="prototype-property-weakset"></a>Propriedade prototype (WeakSet)
Retorna uma referência ao protótipo para um `WeakSet`.  
  
## <a name="syntax"></a>Sintaxe  
  
```JavaScript  
weakset.prototype  
```  
  
## <a name="remarks"></a>Comentários  
 O argumento `weakset` é o nome de um conjunto.  
  
 Use a propriedade `prototype` para fornecer um conjunto básico de funcionalidades para uma classe de objetos. Novas instâncias de um objeto "herdam" o comportamento do protótipo atribuído a ele.  
  
 Por exemplo, para adicionar um método ao objeto `WeakSet` que retorna o valor do maior elemento do conjunto, declare a função, adicione-a a `WeakSet.prototype` e use-a.  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]