---
title: Propriedade prototype (Set) | Microsoft Docs
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
ms.assetid: a075d5a6-e502-4636-85fc-1af001b8ac35
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8265d182562aee55f870fff4c3d5cbadf21402ac
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="prototype-property-set"></a>Propriedade prototype (Set)
Retorna uma referência ao protótipo para um conjunto.  
  
## <a name="syntax"></a>Sintaxe  
  
```JavaScript  
set.prototype  
```  
  
## <a name="remarks"></a>Comentários  
 O argumento `set` é o nome de um conjunto.  
  
 Use a propriedade `prototype` para fornecer um conjunto básico de funcionalidades para uma classe de objetos. Novas instâncias de um objeto "herdam" o comportamento do protótipo atribuído a ele.  
  
 Por exemplo, para adicionar um método ao objeto `Set` que retorna o valor do maior elemento do conjunto, declare a função, adicione-a a `Set.prototype` e use-a.  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]