---
title: Método has (Set) (JavaScript) | Microsoft Docs
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
ms.assetid: fb80f2e0-fc5e-4508-af14-1c3b3b833636
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c9690e3d091e8ae0f9670fd737a29590524834c9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636716"
---
# <a name="has-method-set-javascript"></a>Método has (Set) (JavaScript)
Retorna `true` se o conjunto contém o elemento especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```JavaScript  
setObj.has(value)  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `setObj`  
 Necessário. Um objeto `Set`.  
  
 `value`  
 Necessário. O elemento para teste.  
  
## <a name="property-valuereturn-value"></a>Valor de propriedade/Valor de retorno  
 `true` se o conjunto contém o elemento especificado.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como adicionar membros a um `Set` e, em seguida, verifique se o conjunto contém um membro específico.  
  
```JavaScript  
var s = new Set();  
s.add("Thomas Jefferson");  
s.add(1776);  
  
document.write(s.has(1776));  
document.write(s.has("1776"));  
  
// Output:  
// true  
// false  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]