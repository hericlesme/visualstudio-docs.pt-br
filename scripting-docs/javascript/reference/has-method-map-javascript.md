---
title: Método has (Map) (JavaScript) | Microsoft Docs
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
ms.assetid: 876df854-2941-4db2-92c6-1b497840b169
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 48228b495c845bef91caa0b85e67980100a6f790
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636706"
---
# <a name="has-method-map-javascript"></a>Método has (Map) (JavaScript)
Retorna `true` se o mapa contém o elemento especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```JavaScript  
mapObj.has(key)  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `mapObj`  
 Necessário. Um objeto `Map`.  
  
 `key`  
 Necessário. A chave do elemento para teste.  
  
## <a name="property-valuereturn-value"></a>Valor da propriedade/valor de retorno  
 `true`Se o mapa contém o elemento especificado.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como adicionar um membro a um `Map` e, em seguida, verifique se o mapa contém.  
  
```JavaScript  
var m = new Map();  
m.set(2, "red");  
  
document.write(m.has(2));  
  
// Output:  
// true  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]