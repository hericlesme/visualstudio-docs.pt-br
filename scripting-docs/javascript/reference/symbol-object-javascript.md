---
title: "Símbolo de objeto (JavaScript) | Microsoft Docs"
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
ms.assetid: 2ad059f1-4b7f-4758-882a-c74ce1283ab0
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cd755d5b753eb91b89b869645287685a97f8f571
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="symbol-object-javascript"></a>Objeto Symbol (JavaScript)
Permite que você crie um identificador exclusivo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
obj = Symbol(desc)  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `desc`  
 Opcional. A descrição do símbolo.  
  
## <a name="remarks"></a>Comentários  
 Os objetos de símbolo permitem que sejam adicionadas propriedades aos objetos existentes sem a possibilidade de interferência com as propriedades do objeto existente, sem nenhuma visibilidade não intencional e sem outras adições não coordenadas por outro código.  
  
 O símbolo é um tipo de dados primitivo. Os objetos de símbolo não podem ser criados usando o operador `new`.  
  
 Para adicionar os objetos de símbolo ao Registro global de símbolos, use as funções `Symbol.for` e `Symbol.keyFor`. Se você serializar símbolos como cadeias de caracteres, use o Registro global de símbolos para certificar-se de que uma determinada cadeia de caracteres seja mapeada para o símbolo correto para todas as pesquisas.  
  
 JavaScript inclui os seguintes valores de símbolo internos que estão disponíveis no escopo global.  
  
|Símbolo|Descrição|  
|------------|-----------------|  
|`Symbol.hasInstance`|Este método determina se um objeto de construtor reconhece um objeto como uma das instâncias do construtor. Ele é usado internamente pelo operador `instanceof`.|  
|`Symbol.isConcatSpreadable`|Essa propriedade retorna um valor booliano que indica se um objeto deve ser mesclado aos seus elementos de matriz por `Array.concat`.|  
|`Symbol.iterator`|Esse método retorna o iterador padrão para um objeto. Ele é usado internamente pela instrução `for...of`.|  
|`Symbol.toPrimitive`|Este método converte um objeto em um valor primitivo correspondente. Ele é usado internamente pela operação de abstração `ToPrimitive`.|  
|`Symbol.toStringTag`|Essa propriedade retorna um valor de cadeia de caracteres que é usado para ajudar a criar a descrição padrão de cadeia de caracteres de um objeto. Ele é usado internamente pelo método interno `Object.toString`.|  
|`Symbol.unscopables`|Essa propriedade retorna um objeto cujas propriedades são excluídas das associações do ambiente `with` do objeto associado.|  
  
## <a name="functions"></a>Funções  
 A tabela a seguir lista as funções do objeto `Symbol`.  
  
|||  
|-|-|  
|Propriedade|Descrição|  
|[Symbol.for](../../javascript/reference/symbol-for-function-javascript.md)|Retorna o símbolo para uma chave especificada ou, se a chave não estiver presente, cria um novo objeto de símbolo com a nova chave.|  
|[Keyfor](../../javascript/reference/symbol-keyfor-function-javascript.md)|Retorna a chave para um símbolo especificado.|  
|||  
  
## <a name="example"></a>Exemplo  
  
```JavaScript  
(function() {  
  
    // module-scoped symbol  
    var key = Symbol("description");  
  
    function MyClass(privateData) {  
      this[key] = privateData;  
    }  
  
    MyClass.prototype = {  
      someFunc: function() {  
        return "data: " + this[key];  
      }  
    };  
  
    var c = new MyClass("private data")  
    console.log(key);  
    console.log(c["key"]);  
    console.log(c.someFunc());  
  
})();  
  
// Output:  
// undefined  
// undefined  
// data: private data  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]