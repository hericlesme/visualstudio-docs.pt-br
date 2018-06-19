---
title: Método isPrototypeOf (Object) (JavaScript) | Microsoft Docs
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
- isPrototypeOf
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- isPrototypeOf method
ms.assetid: 9c821319-c208-480f-915e-565ef6e017b6
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 47ce97faecfade089bbf0b7a725a02ee73b54718
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637376"
---
# <a name="isprototypeof-method-object-javascript"></a>Método isPrototypeOf (Object) (JavaScript)
Determina se um objeto existe na cadeia de protótipos de outro objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
prototype.isPrototypeOf(object)  
```  
  
## <a name="parameters"></a>Parâmetros  
 `prototype`  
 Necessário. Um protótipo de objeto.  
  
 `object`  
 Necessário. Outro objeto cuja cadeia de protótipos deve ser verificada.  
  
## <a name="remarks"></a>Comentários  
 O método `isPrototypeOf` retornará `true` se `object` possuir `prototype` em sua cadeia de protótipos. A cadeia de protótipos é usada para compartilhar a funcionalidade entre instâncias do mesmo tipo de objeto. O método `isPrototypeOf` retornará `false` quando `object` não for um objeto ou quando `prototype` não aparecer na cadeia de protótipos de `object`.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso do método `isPrototypeOf`.  
  
```JavaScript  
function Rectangle() {  
}  
  
var rec = new Rectangle();  
  
document.write(Rectangle.prototype.isPrototypeOf(rec));  
  
// Output: true  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Propriedade prototype (Object)](../../javascript/reference/prototype-property-object-javascript.md)