---
title: Objeto Map (JavaScript) | Microsoft Docs
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
- Map
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: a91dbcbe-f58d-41a0-be15-8c9d30020327
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d89890f9fecaf61e47e136734ed7fefb7b73cabd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="map-object-javascript"></a>Objeto Map (JavaScript)
Uma coleção de pares de chave e valor.  
  
## <a name="syntax"></a>Sintaxe  
  
```JavaScript  
mapObj = new Map()  
```  
  
## <a name="remarks"></a>Comentários  
 As chaves e valores na coleção podem ser de qualquer tipo. Se você adicionar um valor à coleção usando uma chave existente, o novo valor substituirá o valor antigo.  
  
## <a name="properties"></a>Propriedades  
 A tabela a seguir lista as propriedades do objeto `Map`.  
  
|Propriedade|Descrição|  
|--------------|-----------------|  
|[construtor](../../javascript/reference/constructor-property-map.md)|Especifica a função que cria um mapa.|  
|[protótipo](../../javascript/reference/prototype-property-map.md)|Retorna uma referência ao protótipo para um mapa.|  
|[size](../../javascript/reference/size-property-map-javascript.md)|Retorna o número de elementos em um mapa.|  
  
## <a name="methods"></a>Métodos  
 A tabela a seguir lista os métodos do objeto `Map`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[clear](../../javascript/reference/clear-method-map-javascript.md)|Remove todos os elementos de um mapa.|  
|[delete](../../javascript/reference/delete-method-map-javascript.md)|Remove um elemento especificado de um mapa.|  
|[forEach](../../javascript/reference/foreach-method-map-javascript.md)|Executa a ação especificada para cada elemento em um mapa.|  
|[get](../../javascript/reference/get-method-map-javascript.md)|Retorna um elemento especificado de um mapa.|  
|[tem](../../javascript/reference/has-method-map-javascript.md)|Retorna `true` se o mapa contém um elemento especificado.|  
|[set](../../javascript/reference/set-method-map-javascript.md)|Adiciona um novo elemento a um mapa.|  
|[toString](../../javascript/reference/tostring-method-map-javascript.md)|Retorna uma representação de cadeia de caracteres de um mapa.|  
|[valueOf](../../javascript/reference/valueof-method-map-javascript.md)|Retorna o valor primitivo do objeto especificado.|  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como adicionar membros a um `Map` e, em seguida, recuperá-las.  
  
```JavaScript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
m.set("colors", 2);  
m.set({x:1}, 3);  
  
m.forEach(function (item, key, mapObj) {  
    document.write(item.toString() + "<br />");  
});  
  
document.write("<br />");  
document.write(m.get(2));  
  
// Output:  
// black  
// red  
// 2  
// 3  
//  
// red  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]