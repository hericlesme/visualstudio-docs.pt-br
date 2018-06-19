---
title: Propriedade Constructor (WeakSet) | Microsoft Docs
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
ms.assetid: 234e7104-9b78-4bfa-8f77-2bc44a570928
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5519c37f459e8236c6ed482b181799076832c50b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636126"
---
# <a name="constructor-property-weakset"></a>Propriedade constructor (WeakSet)
Especifica a função que cria um `WeakSet`.  
  
## <a name="syntax"></a>Sintaxe  
  
```JavaScript  
weakset.constructor  
```  
  
## <a name="remarks"></a>Comentários  
 O `weakset` necessário é o nome do conjunto.  
  
 A propriedade `constructor` é um membro do protótipo de cada objeto que tenha um protótipo. Isso inclui todos os objetos JavaScript intrínsecos, exceto os objetos `Global` e `Math`. A propriedade `constructor` contém uma referência para a função que constrói instâncias daquele objeto específico.  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]