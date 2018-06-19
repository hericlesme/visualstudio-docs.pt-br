---
title: Método Delete (Set) (JavaScript) | Microsoft Docs
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
ms.assetid: 052c409e-10c9-49f2-955d-5ad7e31c14f3
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 72762b93c6996fd72bd035c5d653f0e85f4ffd33
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636086"
---
# <a name="delete-method-set-javascript"></a>Método delete (Set) (JavaScript)
Remove o elemento especificado de um conjunto.  
  
## <a name="syntax"></a>Sintaxe  
  
```JavaScript  
setObj.delete(value)  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `setObj`  
 Necessário. Um objeto `Set`.  
  
 `value`  
 Necessário. O elemento a ser removido.  
  
## <a name="property-valuereturn-value"></a>Valor de propriedade/Valor de retorno  
 `true` se o elemento tiver sido removido.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como adicionar membros a um `Set` e, em seguida, excluir um deles.  
  
```JavaScript  
var s = new Set();  
s.add("Thomas Jefferson");  
s.add(1776);  
s.add("founding father");  
s.delete("founding father");  
  
s.forEach(function (item) {  
    document.write(item.toString() + ", ");  
});  
  
// Output:  
// Thomas Jefferson, 1776,  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]