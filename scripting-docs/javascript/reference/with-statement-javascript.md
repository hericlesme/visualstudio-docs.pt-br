---
title: "Instrução With (JavaScript) | Microsoft Docs"
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
- with_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- With statement
ms.assetid: 892c7621-ae9e-4c10-8adb-05532274b1ca
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 35d49b13261c66cde0ecd53517a99361f6aecb79
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="with-statement-javascript"></a>Instrução with (JavaScript)
Estabelece o objeto padrão para uma instrução.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
with (object) {  
    statements  
}   
```  
  
## <a name="parameters"></a>Parâmetros  
 `object`  
 O objeto padrão.  
  
 `statements`  
 Uma ou mais instruções para o qual `object` é o objeto padrão.  
  
## <a name="remarks"></a>Comentários  
 O `with` instrução normalmente é usada para reduzir a quantidade de código que você precisa escrever em determinadas situações.  
  
> [!WARNING]
>  O uso de `with` não é permitido no modo estrito. O uso de `with` podem tornar mais difícil de ler e para depurar o código e geralmente deve ser evitado.  
  
## <a name="example"></a>Exemplo  
 Neste exemplo, o `Math` objeto é usado várias vezes:  
  
```JavaScript  
x = Math.cos(3 * Math.PI) + Math.sin(Math.LN10)   
y = Math.tan(14 * Math.E)  
```  
  
## <a name="example"></a>Exemplo  
 Se você reconfigurar o exemplo para usar o `with` instrução, o código se torna mais sucinto:  
  
```JavaScript  
with (Math){  
   x = cos(3 * PI) + sin (LN10)    
   y = tan(14 * E)  
}  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Instrução this](../../javascript/reference/this-statement-javascript.md)