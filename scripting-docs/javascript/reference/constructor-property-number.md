---
title: Propriedade Constructor (número) | Microsoft Docs
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
ms.assetid: a348fe53-1b4a-42f5-964b-53d57342c906
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 72679f55aef9b0ac8dc01794c7460dbd8cf0bdf8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636066"
---
# <a name="constructor-property-number"></a>Propriedade constructor (Número)
Especifica a função que cria um número.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
number.constructor  
```  
  
## <a name="remarks"></a>Comentários  
 Obrigatório `number` é o nome de uma cadeia de caracteres.  
  
 A propriedade `constructor` é um membro do protótipo de cada objeto que tenha um protótipo. Isso inclui todos os intrínseco [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] objetos exceto o `Global` e `Math` objetos. A propriedade `constructor` contém uma referência para a função que constrói instâncias daquele objeto específico.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso da propriedade de construtor.  
  
```JavaScript  
var num = new Number();  
  
if (num.constructor == Number)  
    document.write("Object is a Number.");  
else  
    document.write("Object is not a Number.");  
  
// Output:  
// Object is a Number.  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]