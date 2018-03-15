---
title: "Função Object setprototypeof (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: a2609f6e-aeee-4c13-b7cf-c31ddf58ff35
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0a2ae28420893cd49691c1a6ac50fe5896700947
ms.sourcegitcommit: e01ccb5ca4504a327d54f33589911f5d8be9c35c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2018
---
# <a name="objectsetprototypeof-function-javascript"></a>Função Object.setPrototypeOf (JavaScript)
Define o protótipo de um objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Object.setPrototypeOf(obj, proto);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `obj`  
 Necessário. O objeto para o qual você está definindo o protótipo.  
  
 `proto`  
 Necessário. O novo objeto de protótipo.  
  
## <a name="remarks"></a>Comentários  
  
> [!WARNING]
>  Definir o protótipo pode reduzir o desempenho de todo o código JavaScript que tenha acesso a um objeto cujo protótipo foi modificado.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir mostra como definir o protótipo para um objeto.  
  
```JavaScript  
function Rectangle() {  
}  
  
var rec = new Rectangle();  
  
if (console && console.log) {  
    console.log(Object.getPrototypeOf(rec) === Rectangle.prototype);  // Returns true  
    Object.setPrototypeOf(rec, Object.prototype);  
    console.log(Object.getPrototypeOf(rec) === Rectangle.prototype);  // Returns false  
}  
```  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir mostra como adicionar propriedades a um objeto adicionando-os ao protótipo.  
  
```JavaScript  
var proto = { y: 2 };  
  
var obj = { x: 10 };  
Object.setPrototypeOf(obj, proto);  
  
proto.y = 20;  
proto.z = 40;  
  
if (console && console.log) {  
    console.log(obj.x === 10);  // Returns true  
    console.log(obj.y === 20);  // Returns true  
    console.log(obj.z === 40);  // Returns true  
}  
```  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir adiciona propriedades ao objeto `String`, definindo um novo protótipo nele.  
  
```JavaScript  
var stringProp = { desc: "description" };  
  
Object.setPrototypeOf(String, stringProp);  
var s1 = "333";  
var s2 = new String("333");  
  
if (console && console.log) {  
  
    console.log(String.desc === "description"); // Returns true  
    console.log(s1.desc === "description");     // Returns false  
    console.log(s2.desc === "description");     // Returns false  
  
    Object.setPrototypeOf(s1, String); // Can't be set.  
    Object.setPrototypeOf(s2, String);  
  
    console.log(s1.desc === "description"); // Returns false  
    console.log(s2.desc === "description"); // Returns true  
}  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]
