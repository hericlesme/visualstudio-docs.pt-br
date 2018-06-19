---
title: Objeto booliano (JavaScript) | Microsoft Docs
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
- boolean_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Boolean object
- Boolean data type, Boolean object
ms.assetid: d67748f2-7bf5-4889-8269-e777616cc5f0
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 20695376e4935cf6ddc34f30e373df19575ece3f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24633906"
---
# <a name="boolean-object-javascript"></a>Objeto Booliano (JavaScript)
Cria um novo valor booliano.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
boolObj = new Boolean([boolValue])  
```  
  
## <a name="parameters"></a>Parâmetros  
 `boolObj`  
 Obrigatório. O nome da variável à qual o objeto `Boolean` é atribuído.  
  
 `boolValue`  
 Opcional. O valor booliano inicial para o novo objeto. Se `boolvalue` for omitido ou for `false`, 0, `null`, `NaN`, ou uma cadeia de caracteres vazia, o valor inicial do objeto Boolean é `false`. Caso contrário, o valor inicial é `true`.  
  
## <a name="remarks"></a>Comentários  
 O `Boolean` objeto é um wrapper para o tipo de dados booleano. [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]usa implicitamente a `Boolean` objeto sempre que um tipo de dados Boolean é convertido em um `Boolean` objeto.  
  
 Você raramente instanciar o `Boolean` objeto explicitamente.  
  
## <a name="properties"></a>Propriedades  
 A tabela a seguir lista as propriedades do objeto `Boolean`.  
  
|Propriedade|Descrição|  
|--------------|-----------------|  
|[Propriedade Constructor](../../javascript/reference/constructor-property-boolean.md)|Especifica a função que cria um valor booleano.|  
|[Propriedade prototype](../../javascript/reference/prototype-property-boolean.md)|Retorna uma referência ao protótipo para um valor booliano.|  
  
<a name="js56jsobjarraymeth"></a>   
## <a name="methods"></a>Métodos  
 A tabela a seguir lista os métodos do objeto `Boolean`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método toString](../../javascript/reference/tostring-method-boolean-1.md)|Retorna uma representação de cadeia de caracteres de um valor booleano.|  
|[Método valueOf](../../javascript/reference/valueof-method-boolean.md)|Obtém uma referência para o valor booliano.|  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]