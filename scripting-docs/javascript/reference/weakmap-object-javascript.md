---
title: Objeto WeakMap (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: WeakMap
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 4682d2dc-caf9-4fa8-8313-a0a0b804fd1d
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8de97f8acb94921090696e9019a1df5d945db7c6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="weakmap-object-javascript"></a>Objeto WeakMap (JavaScript)
Uma coleção de pares de chave e valor, em que cada chave é uma referência de objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
weakmapObj = new WeakMap()  
```  
  
## <a name="remarks"></a>Comentários  
 Um `WeakMap` objeto não pode ser enumerado.  
  
 Se você adicionar um valor à coleção usando uma chave existente, o novo valor substituirá o valor antigo.  
  
 Em um `WeakMap` do objeto, referências a objetos de chave são mantidas 'fracamente'. Isso significa que `WeakMap` não impedirá que aconteça nos objetos de chave de uma coleta de lixo. Quando não houver nenhuma referência (diferente de `WeakMap`) para os objetos de chave, o coletor de lixo poderá coletar os objetos de chave.  
  
## <a name="properties"></a>Propriedades  
 A tabela a seguir lista as propriedades do objeto `WeakMap`.  
  
|Propriedade|Descrição|  
|--------------|-----------------|  
|[construtor](../../javascript/reference/constructor-property-weakmap.md)|Especifica a função que cria um `WeakMap`.|  
|[protótipo](../../javascript/reference/prototype-property-weakmap.md)|Retorna uma referência ao protótipo para um `WeakMap`.|  
  
## <a name="methods"></a>Métodos  
 A tabela a seguir lista os métodos do objeto `WeakMap`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[clear](../../javascript/reference/clear-method-weakmap-javascript.md)|Remove todos os elementos de um `WeakMap`.|  
|[delete](../../javascript/reference/delete-method-weakmap-javascript.md)|Remove um elemento especificado de um `WeakMap`.|  
|[get](../../javascript/reference/get-method-weakmap-javascript.md)|Retorna um elemento especificado de um `WeakMap`.|  
|[tem](../../javascript/reference/has-method-weakmap-javascript.md)|Retorna `true` se o `WeakMap` contém um elemento especificado.|  
|[set](../../javascript/reference/set-method-weakmap-javascript.md)|Adiciona um novo elemento a um `WeakMap`.|  
|[toString](../../javascript/reference/tostring-method-weakmap-javascript.md)|Retorna uma representação de cadeia de caracteres de um `WeakMap`.|  
|[valueOf](../../javascript/reference/valueof-method-weakmap-javascript.md)|Retorna o valor primitivo do objeto especificado.|  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como adicionar membros a um `WeakMap` do objeto e, em seguida, recuperá-las.  
  
```JavaScript  
var dog = {  
    breed: "yorkie"  
}  
  
var cat = {  
    breed: "burmese"  
}  
  
var wm = new WeakMap();  
wm.set(dog, "fido");  
wm.set(cat, "pepper");  
  
document.write(wm.get(dog) + ": ");  
document.write(dog.breed);  
document.write("<br />");  
document.write(wm.get(cat) + ": ");  
document.write(cat.breed);  
  
// Output:  
// fido: yorkie  
// pepper: burmese  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]