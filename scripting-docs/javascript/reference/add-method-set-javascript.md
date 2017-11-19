---
title: "Método Add (Set) (JavaScript) | Microsoft Docs"
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
ms.assetid: b4eea447-fd5b-4380-978e-1b95f6dbc438
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 287dbfb6480289ed57edc26d41e9900e4a76c27b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="add-method-set-javascript"></a>Método add (Set) (JavaScript)
Adiciona um novo elemento a um conjunto.  
  
## <a name="syntax"></a>Sintaxe  
  
```JavaScript  
setObj.add(value)  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `setObj`  
 Necessário. Um objeto `Set`.  
  
 `value`  
 Necessário. Novo elemento do `Set`.  
  
## <a name="remarks"></a>Comentários  
 O novo elemento pode ser de qualquer tipo e deve ser exclusivo. Se você adicionar um elemento não exclusivo a um `Set`, o novo elemento não será adicionado à coleção.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como adicionar membros a um conjunto e, em seguida, recuperá-las.  
  
```JavaScript  
var s = new Set();  
s.add("Thomas Jefferson");  
s.add(1776);  
s.add("founding father");  
  
s.forEach(function (item) {  
    document.write(item.toString() + ", ");  
});  
  
// Output:  
// Thomas Jefferson, 1776, founding father,  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]