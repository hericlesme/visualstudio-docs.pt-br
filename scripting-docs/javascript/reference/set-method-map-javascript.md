---
title: "Método Set (Map) (JavaScript) | Microsoft Docs"
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
ms.assetid: 31ee71a0-b09d-442a-9e02-825accf94ffa
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2a84a5b2714fde55fba03d581faa851d7245e001
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="set-method-map-javascript"></a>Método set (Map) (JavaScript)
Adiciona um novo elemento a um mapa.  
  
## <a name="syntax"></a>Sintaxe  
  
```JavaScript  
mapObj.set(key, value)  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `mapObj`  
 Necessário. Um objeto `Map`.  
  
 `key`  
 Necessário. A chave para o novo elemento.  
  
 `value`  
 Necessário. O valor do elemento a ser adicionado.  
  
## <a name="property-valuereturn-value"></a>Valor da propriedade/valor de retorno  
 Retorna o `Map` objeto que contém o par chave/valor novo.  
  
## <a name="remarks"></a>Comentários  
 Se você adicionar um valor à coleção usando uma chave existente, o novo valor substituirá o valor antigo.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como adicionar membros a um `Map` e, em seguida, recuperá-las.  
  
```JavaScript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
m.set("colors", 2);  
  
m.forEach(function (item) {  
    document.write(item.toString() + "<br />");  
});  
  
// Output:  
// black  
// red  
// 2  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]