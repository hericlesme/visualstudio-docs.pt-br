---
title: "Número de objeto (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: Number_JavaScript
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: Number object
ms.assetid: 76e87c37-cf6c-46cc-bafa-04be1fe3d78d
caps.latest.revision: "23"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7cbe58fdc9673a8fffe35b8b15d7edbf86ffa655
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="number-object-javascript"></a>Objeto Number (JavaScript)
Um objeto que representa um número de qualquer tipo. Todos os números de JavaScript são números de ponto flutuante de 64 bits.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
numObj = new Number(value)  
```  
  
## <a name="parameters"></a>Parâmetros  
 `numObj`  
 Obrigatório. O nome da variável à qual o objeto `Number` é atribuído.  
  
 `value`  
 Necessário. O valor numérico.  
  
## <a name="remarks"></a>Comentários  
 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] cria objetos `Number` quando uma variável é definida como um valor de número, como `var num = 255.336;`. Raramente é necessário criar objetos `Number` explicitamente.  
  
 O objeto `Number` tem suas próprias propriedades e métodos, além das propriedades e métodos herdados de `Object`. Números são convertidos em cadeias de caracteres em determinadas circunstâncias, como quando um número é adicionado ou concatenado com uma cadeia de caracteres, bem como por meio do método `toString`. Para obter mais informações, consulte [operador de adição (+)](../../javascript/reference/addition-operator-decrement-javascript.md).  
  
 O JavaScript tem várias constantes numéricas. Para obter uma lista completa, consulte [constantes de número](../../javascript/reference/number-constants-javascript.md).  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="properties"></a>Propriedades  
 A tabela a seguir lista as propriedades do objeto `Number`.  
  
|Propriedade|Descrição|  
|--------------|-----------------|  
|[Propriedade Constructor](../../javascript/reference/constructor-property-object-javascript.md)|Especifica a função que cria um objeto.|  
|[Propriedade prototype](../../javascript/reference/prototype-property-object-javascript.md)|Retorna uma referência ao protótipo para uma classe de objetos.|  
  
## <a name="functions"></a>Funções  
 A tabela a seguir lista as funções do `Number` objeto.  
  
|Função|Descrição|  
|--------------|-----------------|  
|[Função Number isfinite](../../javascript/reference/number-isfinite-function-number-javascript.md)|Retorna um valor booliano que indica se um valor é finito.|  
|[Função Number isinteger](../../javascript/reference/number-isinteger-function-number-javascript.md)|Retorna um valor booliano que indica se um valor é um número inteiro.|  
|[Função Number isNaN](../../javascript/reference/number-isnan-function-number-javascript.md)|Retorna um valor booliano que indica se um valor é o valor reservado `NaN` (e não um número).|  
|[Number. issafeinteger](../../javascript/reference/number-issafeinteger-number-javascript.md)|Retorna um valor booliano que indica se um valor pode ser representado com segurança em JavaScript.|  
  
## <a name="methods"></a>Métodos  
 A tabela a seguir lista os métodos do `Number` objeto.  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método hasOwnProperty](../../javascript/reference/hasownproperty-method-object-javascript.md)|Retorna um valor booliano que indica se um objeto tem uma propriedade com o nome especificado.|  
|[Método isPrototypeOf](../../javascript/reference/isprototypeof-method-object-javascript.md)|Retorna um valor booliano que indica se um objeto existe na hierarquia de protótipo de outro objeto.|  
|[Método propertyIsEnumerable](../../javascript/reference/propertyisenumerable-method-object-javascript.md)|Retorna um valor booliano que indica se uma propriedade especificada faz parte de um objeto e se ela é enumerável.|  
|[método toExponential](../../javascript/reference/toexponential-method-number-javascript.md)|Retorna uma cadeia de caracteres que contém um número representado em notação exponencial.|  
|[método toFixed](../../javascript/reference/tofixed-method-number-javascript.md)|Retorna uma cadeia de caracteres que representa um número em notação de ponto fixo.|  
|[Método toLocaleString](../../javascript/reference/tolocalestring-number.md)|Retorna um objeto convertido em uma cadeia de caracteres baseada na localidade atual.|  
|[método toPrecision](../../javascript/reference/toprecision-method-number-javascript.md)|Retorna uma cadeia de caracteres que contém um número que é representado em notação exponencial ou de ponto fixo e que tem um número de dígitos especificado.|  
|[Método toString](../../javascript/reference/tostring-method-object-javascript.md)|Retorna uma representação em cadeia de caracteres de um objeto.|  
|[Método valueOf](../../javascript/reference/valueof-method-object-javascript.md)|Retorna o valor primitivo do objeto especificado.|  
  
## <a name="see-also"></a>Consulte também  
 [Objetos JavaScript](../../javascript/reference/javascript-objects.md)   
 [Objeto Math](../../javascript/reference/math-object-javascript.md)   
 [Operador new](../../javascript/reference/new-operator-decrementjavascript.md)