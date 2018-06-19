---
title: Propriedade (intl. NumberFormat) prototype | Microsoft Docs
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
ms.assetid: 7f6a7e26-108b-4b32-97c2-7f96b9252c50
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b037ce7476574252966e17fcf64246beeaaea1e8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639016"
---
# <a name="prototype-property-intlnumberformat"></a>Propriedade prototype (Intl.NumberFormat)
Retorna uma referência ao protótipo para um formatador.  
  
## <a name="syntax"></a>Sintaxe  
  
```JavaScript  
numberFormat.prototype  
```  
  
## <a name="remarks"></a>Comentários  
 O `numberFormat` argumento é o nome de um formatador.  
  
 Use a propriedade `prototype` para fornecer um conjunto básico de funcionalidades para uma classe de objetos. Novas instâncias de um objeto "herdam" o comportamento do protótipo atribuído a ele.  
  
 Por exemplo, para adicionar um método ao objeto `Intl.NumberFormat` que retorna o valor do maior elemento do conjunto, declare a função, adicione-a a `Intl.NumberFormat.prototype` e use-a.  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]