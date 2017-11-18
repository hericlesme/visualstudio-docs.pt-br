---
title: Propriedade prototype (booliano) | Microsoft Docs
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
ms.assetid: e4f07cb5-3462-488c-a418-76064ab10eae
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 52d2d241c4d550fe4491ea827fab9d586281242d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="prototype-property-boolean"></a>Propriedade prototype (booliano)
Retorna uma referência ao protótipo para um valor booliano.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
boolean.prototype  
```  
  
## <a name="remarks"></a>Comentários  
 O argumento `boolean` é o nome de um objeto.  
  
 A propriedade `prototype` fornece um conjunto básico de funcionalidades a uma classe de objetos. Novas instâncias de um objeto "herdam" o comportamento do protótipo atribuído a ele. Você pode adicionar propriedades e métodos ao protótipo, mas não é possível atribuir objetos internos a outros protótipos.  
  
 Por exemplo, para adicionar um método ao objeto `Boolean` que retorna o valor do maior elemento da matriz, declare a função, adicione-a a `Boolean.prototype` e use-a.  
  
```JavaScript  
function isFalse( ){  
    if (this.toString() == "false")  
         return true;  
    else  
        return false;  
}  
Boolean.prototype.isFalse = isFalse;  
var bool = new Boolean(1);  
document.write(bool.isFalse());  
  
// Output:  
// false  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]