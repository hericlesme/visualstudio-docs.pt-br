---
title: Propriedade Constructor (Array) | Microsoft Docs
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
ms.assetid: b78d517b-cb56-4866-b30f-ef8121a27843
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ca779a2fa2356c1f3e1ca816f16531c0930459a4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24633926"
---
# <a name="constructor-property-array"></a>Propriedade constructor (Array)
Especifica a função que cria uma matriz.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
array.constructor  
```  
  
## <a name="remarks"></a>Comentários  
 Obrigatório `array` é o nome de uma matriz.  
  
 A propriedade `constructor` é um membro do protótipo de cada objeto que tenha um protótipo. Isso inclui todos os intrínseco [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] objetos exceto o `Global` e `Math` objetos. A propriedade `constructor` contém uma referência para a função que constrói instâncias daquele objeto específico.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso da propriedade de construtor.  
  
```JavaScript  
var x = new Array();  
  
if (x.constructor == Array)  
    document.write("Object is an Array.");  
else  
    document.write("Object is not an Array.");  
  
// Output:  
// Object is an Array.  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]