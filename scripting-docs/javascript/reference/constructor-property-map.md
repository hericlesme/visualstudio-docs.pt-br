---
title: Propriedade Constructor (Map) | Microsoft Docs
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
ms.assetid: a90d6a29-bd64-4e01-8d2f-988b7e3e4a24
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7050f4a7eab149862c08ea755361b5bd0d297299
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636026"
---
# <a name="constructor-property-map"></a>Propriedade constructor (Map)
Especifica a função que cria um mapa.  
  
## <a name="syntax"></a>Sintaxe  
  
```JavaScript  
map.constructor  
```  
  
## <a name="remarks"></a>Comentários  
 Obrigatório `map` é o nome do mapa.  
  
 A propriedade `constructor` é um membro do protótipo de cada objeto que tenha um protótipo. Isso inclui todos os objetos JavaScript intrínsecos, exceto os objetos `Global` e `Math`. A propriedade `constructor` contém uma referência para a função que constrói instâncias daquele objeto específico.  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]