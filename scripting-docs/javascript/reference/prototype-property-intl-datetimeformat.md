---
title: Propriedade (intl. DateTimeFormat) prototype | Microsoft Docs
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
ms.assetid: e1e693ff-1775-407e-b655-18a60d238ded
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 64dff17e4aaf62940f4c9c5f8b422fcbceb7212a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="prototype-property-intldatetimeformat"></a>Propriedade prototype (Intl.DateTimeFormat)
Retorna uma referência ao protótipo para um formatador.  
  
## <a name="syntax"></a>Sintaxe  
  
```JavaScript  
dateTimeFormat.prototype  
```  
  
## <a name="remarks"></a>Comentários  
 O `dateTimeFormat` argumento é o nome de um formatador.  
  
 Use a propriedade `prototype` para fornecer um conjunto básico de funcionalidades para uma classe de objetos. Novas instâncias de um objeto "herdam" o comportamento do protótipo atribuído a ele.  
  
 Por exemplo, para adicionar um método ao objeto `Intl.DateTimeFormat` que retorna o valor do maior elemento do conjunto, declare a função, adicione-a a `Intl.DateTimeFormat.prototype` e use-a.  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]