---
title: "Método hasOwnProperty (Object) (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: hasOwnProperty
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: hasOwnProperty method
ms.assetid: 3eb69d69-486f-4792-9518-4452aef369ca
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 397b68fc87bf730886c928e099037ff0183a7f63
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="hasownproperty-method-object-javascript"></a>Método hasOwnProperty (Object) (JavaScript)
Determina se um objeto tem uma propriedade com o nome especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
object.hasOwnProperty(proName)  
```  
  
## <a name="parameters"></a>Parâmetros  
 `object`  
 Necessário. Instância de um objeto.  
  
 `proName`  
 Necessário. Valor de um nome de propriedade de cadeia de caracteres.  
  
## <a name="remarks"></a>Comentários  
 O `hasOwnProperty` método `true` se `object` tem uma propriedade do nome especificado, `false` se não existir. Esse método não verifica as propriedades de cadeia de protótipo do objeto; a propriedade deve ser um membro do objeto em si.  
  
 Não há suporte para essa propriedade em objetos de host para o Internet Explorer 8 e abaixo.  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, todas as `String` objetos compartilham um comum dividir o método. O código a seguir exibirá **false** e **true**.  
  
```JavaScript  
var s = new String("Sample");  
document.write(s.hasOwnProperty("split"));  
document.write("<br/>");  
document.write(String.prototype.hasOwnProperty("split"));  
  
// Output:  
// false  
// true  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Operador in](../../javascript/reference/in-operator-decrementjavascript.md)