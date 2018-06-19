---
title: Objeto WeakSet (JavaScript) | Microsoft Docs
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
ms.assetid: f97e6e7c-d678-4e32-978e-d949a7cafa3a
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e42849c03f698d6ed5f8b0e28725c85555a74d2b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641596"
---
# <a name="weakset-object-javascript"></a>Objeto WeakSet (JavaScript)
Uma coleção de objetos exclusivos que pode ser de qualquer tipo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
setObj = new WeakSet()  
```  
  
## <a name="remarks"></a>Comentários  
 Se você tentar adicionar um objeto não exclusivo a um `WeakSet`, o novo objeto não será adicionado à coleção.  
  
 Ao contrário de um `Set`, somente os objetos podem ser adicionados à coleção. Os valores arbitrários não podem ser adicionados à coleção.  
  
 Em um `WeakSet` do objeto, referências a objetos no conjunto são mantidas 'fracamente'. Isso significa que `WeakSet` não impedirá que aconteça uma coleta de lixo nos objetos. Quando não houver nenhuma referência (diferente de `WeakSet`) para os objetos, o coletor de lixo poderá coletar os objetos.  
  
 `WeakSet` (ou `WeakMap`) pode ser útil em alguns cenários que envolvem o cache de metadados do objeto ou objetos. Por exemplo, os metadados para objetos não extensíveis podem ser armazenados em um `WeakSet`, ou você pode criar um cache de imagens de usuário usando `WeakSet`.  
  
## <a name="properties"></a>Propriedades  
 A tabela a seguir lista as propriedades do objeto `WeakSet`.  
  
|Propriedade|Descrição|  
|--------------|-----------------|  
|construtor|Especifica a função que cria um conjunto.|  
|protótipo|Retorna uma referência ao protótipo para um conjunto.|  
  
## <a name="methods"></a>Métodos  
 A tabela a seguir lista os métodos do objeto `WeakSet`.  
  
|Método|Descrição|  
|------------|-----------------|  
|adicionar|Adiciona um elemento a um conjunto.|  
|excluir|Remove um elemento especificado de um conjunto.|  
|tem|Retorna `true` se o conjunto contém um elemento especificado.|  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como adicionar membros a um conjunto e, em seguida, verificar se eles foram adicionados.  
  
```JavaScript  
var ws = new WeakSet();  
  
var str = new String("Thomas Jefferson");  
var num = new Number(1776);  
  
ws.add(str);  
ws.add(num);  
  
console.log(ws.has(str));  
console.log(ws.has(num));  
  
ws.delete(str);  
console.log(ws.has(str));  
  
// Output:  
// true  
// true  
// false  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]