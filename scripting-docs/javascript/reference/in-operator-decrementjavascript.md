---
title: Operador in (JavaScript) | Microsoft Docs
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
- in_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- in operator
ms.assetid: dcd8f901-96b8-4c91-848b-b1ec0ab1c11c
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eefcd4c53d2e3366a26f0d8dfb099f59038507ae
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637446"
---
# <a name="in-operator-javascript"></a>Operador in (JavaScript)
Testa a existência de uma propriedade em um objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
result = property in object  
```  
  
## <a name="parameters"></a>Parâmetros  
 `result`  
 Necessário. Qualquer variável.  
  
 `property`  
 Necessário. Uma expressão que é avaliada como uma expressão de cadeia de caracteres.  
  
 `object`  
 Necessário. Qualquer objeto.  
  
## <a name="remarks"></a>Comentários  
 O `in` operador determina se um objeto tem uma propriedade chamada `property`. Ele também determina se a propriedade é parte da cadeia de protótipo do objeto. Para obter mais informações sobre os protótipos de objeto, consulte [protótipos e herança de protótipo](../../javascript/advanced/prototypes-and-prototype-inheritance.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar o `in` operador:  
  
```JavaScript  
// Create an object that has some properties.  
var myObject = new Object();  
myObject.name = "James";  
myObject.age = "22";  
myObject.phone = "555 0234";  
  
if ("phone" in myObject)  
   document.write ("property is present");  
else  
   document.write ("property is not present");  
  
// Output: property is present  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Precedência do operador](../../javascript/operator-subtractprecedence-javascript.md)   
 [Resumo de operador (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)