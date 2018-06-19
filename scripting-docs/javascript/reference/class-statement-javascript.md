---
title: Instrução Class (JavaScript) | Microsoft Docs
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
ms.assetid: bf45ebad-4678-4062-88df-55d32b603c69
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e828ae86c3f8f585179e3b097d98b3449c3f3b45
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24634226"
---
# <a name="class-statement-javascript"></a>Instrução class (JavaScript)
Declara uma nova classe.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
class classname () [extends object] {    [constructor([arg1 [,... [,argN]]]) {        statements    }]    [[static] method([arg1 [,... [,argN]]]) {        statements    }]}  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `classname`  
 Necessário. O nome da classe.  
  
 `object`  
 Opcional. Um objeto ou classe da qual a nova classe herda propriedades e métodos.  
  
 `constructor`  
 Opcional. Uma função de construtor que inicializa a instância da nova classe.  
  
 `arg1...argN`  
 Opcional. Uma lista opcional, separada por vírgula, de argumentos que a função compreende.  
  
 `statements`  
 Opcional. Um ou mais instruções [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
 `static`  
 Opcional. Especifica um método estático.  
  
 `method`  
 Opcional. Um ou mais instâncias [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] ou métodos estáticos que podem ser chamados em uma instância de classe.  
  
## <a name="remarks"></a>Comentários  
 Uma classe permite que você crie novos objetos usando heranças, construtores, métodos de instância e métodos estáticos baseados no protótipo. Você pode usar o objeto `super` dentro de um construtor de classe ou método de classe para chamar o mesmo construtor ou método na classe ou objeto pai. Ou você pode usar a instrução `extends` após o nome de classe para especificar a classe ou objeto do qual a nova classe herda os métodos.  
  
## <a name="example"></a>Exemplo  
  
```JavaScript  
class Spelunking extends EXPERIENCE.Outdoor {  
  constructor(name, location) {  
    super(name, location);  
  
    this.minSkill = Spelunking.defaultSkill();  
    //...  
  }  
  update(minSkill) {  
    //...  
    super.update(minSkill);  
  }  
  static defaultSkill() {  
    return new EXPERIENCE.Level3();  
  }  
}  
```  
  
## <a name="example"></a>Exemplo  
 Você também pode criar nomes de propriedades computadas para as classes. O exemplo de código a seguir cria um nome de propriedade computada usando a sintaxe `set`.  
  
```JavaScript  
var propName = "prop_42";  
  
class Spelunking {  
    set [propName](v) {  
        this.value = v;  
    }  
};  
  
var s = new Spelunking();  
console.log(s.value);  
s.prop_42 = 42;  
console.log(s.value);  
  
// Output:  
// undefined  
// 42  
  
```  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir cria um nome de propriedade para uma classe dinamicamente usando a sintaxe `get`.  
  
```JavaScript  
var propName = "prop_42";  
  
class Spelunking {  
    get [propName]() {  
        return 777;  
    }  
}  
  
var s = new Spelunking();  
console.log(s.prop_42);  
  
// Output:  
// 777  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv12exp](../../javascript/reference/includes/jsv12exp-md.md)]