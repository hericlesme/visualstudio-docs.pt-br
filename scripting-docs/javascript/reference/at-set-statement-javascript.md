---
title: "@setInstrução (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '@set_JavaScriptKeyword'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- '@set statement'
- conditional compilation, variables
ms.assetid: 36f15926-3e69-422d-82a2-d186dc088203
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 10f74a1d57a61d78897b660812a6fd8078244b6b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="set-statement-javascript"></a>@setInstrução (JavaScript)
Cria variáveis usadas com instruções de compilação condicional.  
  
> [!WARNING]
>  Não há suporte à compilação condicional no modo Standards do Internet Explorer 11 nem em aplicativos [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]. A compilação condicional é compatível com o modo Standards do Internet Explorer 10 e em todas as versões anteriores do navegador.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
@set @varname = term   
```  
  
## <a name="parameters"></a>Parâmetros  
 *varname*  
 Necessário. Nome de variável [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] válido. Deve ser sempre precedido por um caractere "@".  
  
 `term`  
 Necessário. Zero ou mais operadores unários seguidos por uma constante, variável de compilação condicional ou expressão entre parênteses.  
  
## <a name="remarks"></a>Comentários  
 Variáveis numéricas e boolianas são aceitas na compilação condicional. Cadeias de caracteres não. As variáveis criadas com o uso de `@set` são geralmente usadas em instruções de compilação condicional, mas podem ser usadas em qualquer parte do código [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
 Exemplos de declarações de variáveis são semelhantes a:  
  
```JavaScript  
  
      @set @myvar1 = 12  
  
@set @myvar2 = (@myvar1 * 20)  
  
@set @myvar3 = @_jscript_version  
```  
  
 Os operadores a seguir são válidos em expressões entre parênteses:  
  
-   `! ~`  
  
-   `* / %`  
  
-   `+ -`  
  
-   `<< >> >>>`  
  
-   `< <= > >=`  
  
-   `== != === !==`  
  
-   `& ^ |`  
  
-   `&& | |`  
  
 Se uma variável for usada antes de ter sido definida, seu valor será `NaN`. `NaN` pode ser verificado com o uso da instrução `@if`:  
  
```JavaScript  
@if (@newVar != @newVar)  
   ...  
```  
  
 Isso funciona porque `NaN` é o único valor que não é igual a ele mesmo.  
  
## <a name="requirements"></a>Requisitos  
 Válido em todas as versões do Internet Explorer, mas não em aplicativos [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)].  
  
## <a name="see-also"></a>Consulte também  
 [Compilação condicional](../../javascript/advanced/conditional-compilation-javascript.md)   
 [Variáveis de compilação condicional](../../javascript/advanced/conditional-compilation-variables-javascript.md)   
 [@cc_onInstrução](../../javascript/reference/at-cc-on-statement-javascript.md)   
 [Instrução @if](../../javascript/reference/at-if-statement-javascript.md)