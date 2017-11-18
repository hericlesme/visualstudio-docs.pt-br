---
title: Propriedade prototype (erro) | Microsoft Docs
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
ms.assetid: 6c268a51-1a3d-4397-abf8-e54ca4e598fe
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b7d0413d3541691a38672e7c0720b58245725b76
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="prototype-property-error"></a>Propriedade prototype (Erro)
Retorna uma referência ao protótipo para um erro.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
error.prototype  
```  
  
## <a name="remarks"></a>Comentários  
 O `error` argumento é o nome de um erro.  
  
 Use o `prototype` propriedade para fornecer um conjunto básico de funcionalidade a um erro. Novas instâncias de um objeto "herdam" o comportamento do protótipo atribuído a ele.  
  
 Por exemplo, para adicionar um método ao objeto `Error` que retorna o valor do maior elemento da matriz, declare a função, adicione-a a `Error.prototype` e use-a.  
  
```JavaScript  
function getSeverity(){  
    if (this.number > 1000)  
        return "high";  
    else  
        return "low";  
}  
Error.prototype.getSev = getSeverity;  
var myError = new Error();  
myError.number = 5000;  
  
document.write(myError.getSev());   
  
// Output: high  
  
```  
  
 Todos os intrínseco [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] objetos têm um `prototype` propriedade é somente leitura. Propriedades e métodos que podem ser adicionados ao protótipo, mas o objeto não pode ser atribuído um protótipo diferente. No entanto, objetos definidos pelo usuário podem ser atribuídos um novo protótipo.  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]