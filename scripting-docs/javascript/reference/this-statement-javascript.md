---
title: Essa instrução (JavaScript) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- this_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- this statement
- constructors, referring to current object
ms.assetid: 8510a00b-2f14-4700-a276-4d9a523c5112
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f4afed1bd978d1985c151efa77873c93e699f0b1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640316"
---
# <a name="this-statement-javascript"></a>Instrução this (JavaScript)
Faz referência ao objeto atual.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
this.property  
```  
  
## <a name="remarks"></a>Comentários  
 O argumento `property` necessário é uma das propriedades do objeto atual.  
  
 A palavra-chave `this` pode ser usada em construtores de objetos para fazer referência ao objeto atual.  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, **isso** refere-se ao objeto recém-criado do carro e atribui valores a três propriedades:  
  
```JavaScript  
function Car(color, make, model){  
   this.color = color;  
   this.make = make;  
   this.model = model;  
}  
```  
  
 O **isso** palavra-chave geralmente se refere a **janela** se usado fora do escopo de qualquer objeto do objeto. No entanto, os manipuladores de eventos internos `this` referem-se ao elemento DOM que gerou o evento.  
  
 No código a seguir (para o Internet Explorer 9 ou posterior), o manipulador de eventos imprime a versão de cadeia de caracteres de um botão que possui um ID de "clicker".  
  
```JavaScript  
document.getElementById("clicker").addEventListener("click", eventHandler, false);  
  
        function eventHandler(ev) {  
            document.write(this.toString());  
        }  
  
// Output (when you click the button): [object HTMLButtonElement]  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Operador new](../../javascript/reference/new-operator-decrementjavascript.md)   
 [Usar o método bind](../../javascript/advanced/using-the-bind-method-javascript.md)