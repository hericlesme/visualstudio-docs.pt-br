---
title: Propriedade Constructor (erro) (JavaScript) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- constructor
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- constructor property
ms.assetid: 6f5d0e9d-e85f-4fde-b558-744510483d69
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 569dab69906aa167ef486923bd7ceb7455ac243e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636256"
---
# <a name="constructor-property-object-javascript"></a>Propriedade constructor (Erro) (JavaScript)
Especifica a função que cria um objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
object.constructor  
```  
  
## <a name="remarks"></a>Comentários  
 Obrigatório `object` é o nome de um objeto ou função.  
  
 A propriedade `constructor` é um membro do protótipo de cada objeto que tenha um protótipo. Isso inclui todos os intrínseco [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] objetos exceto o `Global` e `Math` objetos. A propriedade `constructor` contém uma referência para a função que constrói instâncias daquele objeto específico.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso da propriedade de construtor.  
  
```JavaScript  
// A constructor function.  
function MyObj() {  
    this.number = 1;  
}  
  
var x = new String("Hi");  
  
if (x.constructor == String)  
    document.write("Object is a String.");  
document.write ("<br />");  
  
var y = new MyObj;  
if (y.constructor == MyObj)  
    document.write("Object constructor is MyObj.");  
  
// Output:  
// Object is a String.  
// Object constructor is MyObj.  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Propriedade prototype (Object)](../../javascript/reference/prototype-property-object-javascript.md)