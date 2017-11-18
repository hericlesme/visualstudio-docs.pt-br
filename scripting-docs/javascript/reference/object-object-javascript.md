---
title: Objeto Object (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: object
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: Object object
ms.assetid: d24ef8fc-217b-4828-94e1-19f72780bae0
caps.latest.revision: "25"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 17e82b9c66c286c7f847e7b67b1b5928aadd613e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="object-object-javascript"></a>Objeto Object (JavaScript)
Fornece funcionalidade comum a todos os objetos [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
obj  
 = new Object([value])   
```  
  
## <a name="parameters"></a>Parâmetros  
 `obj`  
 Obrigatório. O nome da variável à qual o objeto `Object` é atribuído.  
  
 *value*  
 Opcional. Qualquer um dos tipos de dados primitivos [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] (número, booliano ou cadeia de caracteres). Se o valor for um objeto, o objeto é retornado sem modificações. Se *valor* é `null`, **indefinido**, ou não fornecido, será criado um objeto sem conteúdo.  
  
## <a name="remarks"></a>Comentários  
 O `Object` objeto está contido em todos os outros objetos [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]; todos os seus métodos e propriedades estão disponíveis em todos os outros objetos. Os métodos podem ser redefinidos em objetos definidos pelo usuário e são chamados por [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] em momentos apropriados. O **toString** método é um exemplo de redefinido com frequência `Object` método.  
  
 Nesta referência de linguagem, a descrição de cada método `Object` inclui informações de implementação padrão e específica de objetos para os objetos intrínsecos [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## <a name="requirements"></a>Requisitos  
 O `Object Object` foi introduzido no [!INCLUDE[jsv3text](../../javascript/reference/includes/jsv3text-md.md)]. Alguns membros nas listas a seguir foram introduzidos em versões posteriores.  
  
## <a name="properties"></a>Propriedades  
 A tabela a seguir lista propriedades de `Object Object`.  
  
|Propriedade|Descrição|  
|--------------|-----------------|  
|[__proto\_ \_ propriedade](../../javascript/reference/proto-property-object-javascript.md)|Especifica o protótipo de um objeto.|  
|[Propriedade Constructor](../../javascript/reference/constructor-property-object-javascript.md)|Especifica a função que cria um objeto.|  
|[Propriedade prototype](../../javascript/reference/prototype-property-object-javascript.md)|Retorna uma referência ao protótipo para uma classe de objetos.|  
  
## <a name="functions"></a>Funções  
 A tabela a seguir lista funções de `Object Object`.  
  
|Função|Descrição|  
|--------------|-----------------|  
|[Função Object Assign](../../javascript/reference/object-assign-function-object-javascript.md)|Copia os valores de um ou mais objetos de origem para um objeto de destino.|  
|[Função Object.create](../../javascript/reference/object-create-function-javascript.md)|Cria um objeto que tem um protótipo especificado e, opcionalmente, contém propriedades especificadas.|  
|[Função Object.defineProperties](../../javascript/reference/object-defineproperties-function-javascript.md)|Adiciona uma ou mais propriedades a um objeto e/ou modifica os atributos de propriedades existentes.|  
|[Função Object.defineProperty](../../javascript/reference/object-defineproperty-function-javascript.md)|Adiciona uma propriedade a um objeto ou modifica atributos de uma propriedade existente.|  
|[Função Object.freeze](../../javascript/reference/object-freeze-function-javascript.md)|Impede a modificação de valores e atributos de propriedades existentes e impede a adição de novas propriedades.|  
|[Função Object.getOwnPropertyDescriptor](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)|Retorna a definição de uma propriedade de dados ou uma propriedade do acessador.|  
|[Função Object.getOwnPropertyNames](../../javascript/reference/object-getownpropertynames-function-javascript.md)|Retorna os nomes das propriedades e métodos de um objeto.|  
|[Função Object.getOwnPropertySymbols](../../javascript/reference/object-getownpropertysymbols-function-javascript.md)|Retorna as propriedades de símbolo de um objeto.|  
|[Função Object.getPrototypeOf](../../javascript/reference/object-getprototypeof-function-javascript.md)|Retorna o protótipo de um objeto.|  
|[Função Object.is](../../javascript/reference/object-is-function-javascript.md)|Retorna um valor que indica se dois objetos são o mesmo valor.|  
|[Função Object.isExtensible](../../javascript/reference/object-isextensible-function-javascript.md)|Retorna um valor que indica se novas propriedades podem ser adicionadas a um objeto.|  
|[Função Object.isFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)|Retorna `true` se atributos e valores da propriedade existente não puderem ser modificados em um objeto e novas propriedades não puderem ser adicionadas ao objeto.|  
|[Função Object.isSealed](../../javascript/reference/object-issealed-function-javascript.md)|Retorna `true` se atributos da propriedade existente não puderem ser modificados em um objeto e novas propriedades não puderem ser adicionadas ao objeto.|  
|[Função Object.keys](../../javascript/reference/object-keys-function-javascript.md)|Retorna os nomes das propriedades e métodos enumeráveis um objeto.|  
|[Função Object.preventExtensions](../../javascript/reference/object-preventextensions-function-javascript.md)|Impede a adição de novas propriedades a um objeto.|  
|[Função Object.seal](../../javascript/reference/object-seal-function-javascript.md)|Impede a modificação de atributos de propriedades existentes e impede a adição de novas propriedades.|  
|[Função Object.setPrototypeOf](../../javascript/reference/object-setprototypeof-function-javascript.md)|Define o protótipo de um objeto.|  
  
## <a name="methods"></a>Métodos  
 A tabela a seguir lista métodos de `Object Object`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[método hasOwnProperty](../../javascript/reference/hasownproperty-method-object-javascript.md)|Retorna um valor booliano que indica se um objeto tem uma propriedade com o nome especificado.|  
|[método isPrototypeOf](../../javascript/reference/isprototypeof-method-object-javascript.md)|Retorna um valor booliano que indica se um objeto existe na hierarquia de protótipo de outro objeto.|  
|[método propertyIsEnumerable](../../javascript/reference/propertyisenumerable-method-object-javascript.md)|Retorna um valor booliano que indica se uma propriedade especificada faz parte de um objeto e se ela é enumerável.|  
|[método toLocaleString](../../javascript/reference/tolocalestring-method-object-javascript.md)|Retorna um objeto convertido em uma cadeia de caracteres baseada na localidade atual.|  
|[método toString](../../javascript/reference/tostring-method-object-javascript.md)|Retorna uma representação em cadeia de caracteres de um objeto.|  
|[método valueOf](../../javascript/reference/valueof-method-object-javascript.md)|Retorna o valor primitivo do objeto especificado.|  
  
## <a name="see-also"></a>Consulte também  
 [Objetos JavaScript](../../javascript/reference/javascript-objects.md)