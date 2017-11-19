---
title: Objeto Set (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: Set
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 4a4dd749-2a76-44fb-9cb0-a3ef317f75fb
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5134ec09c9a8642499212af9dd5fd44de0068adc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="set-object-javascript"></a>Objeto Set (JavaScript)
Uma coleção de valores únicos de qualquer tipo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
setObj = new Set()     
```  
  
## <a name="remarks"></a>Comentários  
 Se você tentar adicionar um valor não exclusivo a um `Set`, o novo valor não será adicionado à coleção.  
  
## <a name="properties"></a>Propriedades  
 A tabela a seguir lista as propriedades do objeto `Set`.  
  
|Propriedade|Descrição|  
|--------------|-----------------|  
|[construtor](../../javascript/reference/constructor-property-set.md)|Especifica a função que cria um conjunto.|  
|[protótipo](../../javascript/reference/prototype-property-set.md)|Retorna uma referência ao protótipo para um conjunto.|  
|[size](../../javascript/reference/size-property-set-javascript.md)|Retorna o número de elementos em um conjunto.|  
  
## <a name="methods"></a>Métodos  
 A tabela a seguir lista os métodos do objeto `Set`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[add](../../javascript/reference/add-method-set-javascript.md)|Adiciona um elemento a um conjunto.|  
|[clear](../../javascript/reference/clear-method-set-javascript.md)|Remove todos os elementos de um conjunto.|  
|[delete](../../javascript/reference/delete-method-set-javascript.md)|Remove um elemento especificado de um conjunto.|  
|[forEach](../../javascript/reference/foreach-method-set-javascript.md)|Executa a ação especificada para cada elemento em um conjunto.|  
|[tem](../../javascript/reference/has-method-set-javascript.md)|Retorna `true` se o conjunto contém um elemento especificado.|  
|[toString](../../javascript/reference/tostring-method-set-javascript.md)|Retorna uma representação de cadeia de caracteres de um conjunto.|  
|[valueOf](../../javascript/reference/valueof-method-set-javascript.md)|Retorna o valor primitivo do objeto especificado.|  
  
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