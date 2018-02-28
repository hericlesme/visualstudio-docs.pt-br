---
title: "Método propertyIsEnumerable (Object) (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- propertyIsEnumerable
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- propertyIsEnumerable property
ms.assetid: d90c7c2e-ea23-4710-a957-9aefbbd1f68b
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5664732db6a311586f11eb13eee4407fdf81410f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="propertyisenumerable-method-object-javascript"></a>Método propertyIsEnumerable (Object) (JavaScript)
Determina se uma propriedade especificada é enumerável.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
object. propertyIsEnumerable(proName)  
```  
  
## <a name="parameters"></a>Parâmetros  
 `object`  
 Necessário. Instância de um objeto.  
  
 `proName`  
 Necessário. Valor de um nome de propriedade de cadeia de caracteres.  
  
## <a name="remarks"></a>Comentários  
 O `propertyIsEnumerable` método `true` se `proName` existe no `object` e podem ser enumerados usando um `For` loop. O `propertyIsEnumerable` método `false` se `object` não tem uma propriedade do nome especificado ou se a propriedade especificada não é enumerável. Normalmente, as propriedades predefinidas não são enumeráveis, mas propriedades definidas pelo usuário são sempre enumeráveis.  
  
 O `propertyIsEnumerable` método não considera objetos na cadeia de protótipo.  
  
## <a name="example"></a>Exemplo  
  
```JavaScript  
var a = new Array("apple", "banana", "cactus");  
document.write(a.propertyIsEnumerable(1));  
  
// Output: true  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Propriedade prototype (Object)](../../javascript/reference/prototype-property-object-javascript.md)