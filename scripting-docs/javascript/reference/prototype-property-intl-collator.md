---
title: Propriedade (intl. collator) prototype | Microsoft Docs
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
ms.assetid: c1bbb523-fb55-4395-b357-34d91cf5bba0
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 696535afde8c497bc98fc2c81a03854d66add6f4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="prototype-property-intlcollator"></a>Propriedade prototype (Intl.Collator)
Retorna uma referência ao protótipo para um agrupamento.  
  
## <a name="syntax"></a>Sintaxe  
  
```JavaScript  
collator.prototype  
```  
  
## <a name="remarks"></a>Comentários  
 O `collator` argumento é o nome de um agrupamento.  
  
 Use a propriedade `prototype` para fornecer um conjunto básico de funcionalidades para uma classe de objetos. Novas instâncias de um objeto "herdam" o comportamento do protótipo atribuído a ele.  
  
 Por exemplo, para adicionar um método ao objeto `Intl.Collator` que retorna o valor do maior elemento do conjunto, declare a função, adicione-a a `Intl.Collator.prototype` e use-a.  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]