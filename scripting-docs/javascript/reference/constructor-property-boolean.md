---
title: Propriedade Constructor (booliano) | Microsoft Docs
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
ms.assetid: b67ca875-23c6-4687-a5ce-1cdd25d1c923
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 091da5342c4713c8eba646a8bd78c315a6a0fa48
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="constructor-property-boolean"></a>Propriedade constructor (Booliano)
Especifica a função que cria um valor booleano.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
boolean.constructor([[value])  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `boolean`  
 O nome de booliano.  
  
 `value`  
 Opcional. Especifica o valor booliano. Isso pode ser os números de 1 ou 0, ou as cadeias de caracteres "verdadeiro" ou "false".  
  
## <a name="remarks"></a>Comentários  
 O `constructor` propriedade contém uma referência para a função que constrói instâncias do objeto booliano.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso da propriedade de construtor.  
  
```JavaScript  
var x = new Boolean("true");  
  
if (x.constructor == Boolean)  
    document.write("Object is a Boolelan.");  
  
// Output:  
// Object is a Boolean.  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]