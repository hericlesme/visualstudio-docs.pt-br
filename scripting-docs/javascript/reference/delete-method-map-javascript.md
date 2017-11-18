---
title: "Método Delete (Map) (JavaScript) | Microsoft Docs"
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
ms.assetid: a073e1a1-5862-485b-b2bd-26c66a3aff51
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5185b883cf603acdc91fe1f1c833d337c4468ba4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="delete-method-map-javascript"></a>Método delete (Map) (JavaScript)
Remove o elemento especificado de um mapa.  
  
## <a name="syntax"></a>Sintaxe  
  
```JavaScript  
mapObj.delete(key)  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `mapObj`  
 Necessário. Um objeto `Map`.  
  
 `key`  
 Necessário. A chave do elemento a ser removido.  
  
## <a name="property-valuereturn-value"></a>Valor da propriedade/valor de retorno  
 `true` se o elemento tiver sido removido.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como adicionar membros a um `Map` e, em seguida, excluir um deles.  
  
```JavaScript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
m.set("colors", 2);  
m.delete(1);  
  
m.forEach(function (item) {  
    document.write(item.toString() + "<br />");  
});  
  
// Output:  
// red  
// 2  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]