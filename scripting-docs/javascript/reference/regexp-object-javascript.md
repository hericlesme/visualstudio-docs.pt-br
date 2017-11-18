---
title: Objeto RegExp (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: RegExp
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- RegExp object, overview
- RegExp object
ms.assetid: 7f6b1073-8cbb-49ed-94b6-56833ba663c5
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b7319e4556721bcfd397061ce525acfb3278c6b9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="regexp-object-javascript"></a>Objeto RegExp (JavaScript)
Corresponde a um objeto intrínseco global que armazena informações sobre os resultados de padrão de expressão regular.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
RegExp.property   
```  
  
## <a name="remarks"></a>Comentários  
 Obrigatório *propriedade* argumento pode ser qualquer uma da `RegExp` propriedades do objeto.  
  
 O `RegExp` objeto não pode ser criado diretamente, mas está sempre disponível para uso. Até que uma pesquisa de expressão regular bem-sucedida for concluída, os valores iniciais de várias propriedades do `RegExp` objeto são da seguinte maneira:  
  
|Propriedade|Abreviação|Valor inicial|  
|--------------|---------------|-------------------|  
|índice||-1|  
|entrada|$_|Cadeia de caracteres vazia.|  
|lastIndex||-1|  
|lastMatch|$&|Cadeia de caracteres vazia.|  
|lastParen|$+|Cadeia de caracteres vazia.|  
|leftContext|$`|Cadeia de caracteres vazia.|  
|rightContext|$'|Cadeia de caracteres vazia.|  
|$1 - $9|$1 - $9|Cadeia de caracteres vazia.|  
  
 Suas propriedades indefinidos como seu valor até que uma pesquisa de expressão regular bem-sucedida foi concluída.  
  
 Global `RegExp` objeto não deve ser confundido com o **Expressão Regular** objeto. Embora pareçam como a mesma coisa, eles são separados e distintos. As propriedades de global `RegExp` objeto contêm informações atualizadas continuamente sobre cada correspondência conforme ela ocorre, enquanto as propriedades do **Expressão Regular** objeto contêm apenas informações sobre as correspondências que ocorrem com essa instância do **Expressão Regular**.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir executa uma pesquisa de expressão regular. Ele exibe correspondências e submatches de global `RegExp` objeto e da matriz que é retornado pelo `exec` método.  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
<a name="js56jsobjregexpprop"></a>   
## <a name="properties"></a>Propriedades  
 [US $1... $9 propriedades](../../javascript/reference/dollar-1-dot-dot-dot-dollar-9-properties-regexp-javascript.md) &#124; [propriedade index](../../javascript/reference/index-property-regexp-javascript.md) &#124; [entrada propriedade](../../javascript/reference/input-property-dollar-regexp-javascript.md) &#124; [propriedade lastIndex](../../javascript/reference/lastindex-property-regexp-javascript.md) &#124; [propriedade lastMatch](../../javascript/reference/lastmatch-property-dollar-regexp-javascript.md) &#124; [propriedade lastParen](../../javascript/reference/lastparen-property-dollar-regexp-javascript.md) &#124; [propriedade leftContext](../../javascript/reference/leftcontext-property-dollar-grave-regexp-javascript.md) &#124; [propriedade rightContext](../../javascript/reference/rightcontext-property-dollar-regexp-javascript.md)  
  
## <a name="methods"></a>Métodos  
 O `RegExp` objeto não possui métodos.  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Objeto de expressão regular](../../javascript/reference/regular-expression-object-javascript.md)   
 [Sintaxe de expressão regular (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)   
 [Objeto String](../../javascript/reference/string-object-javascript.md)