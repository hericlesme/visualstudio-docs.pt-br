---
title: '@cc_onInstrução (JavaScript) | Microsoft Docs'
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
- '@cc_on_JavaScriptKeyword'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- conditional compilation, activating
- '@cc_on statement'
- '@set statement'
- '@if statement'
ms.assetid: fdeda7ee-b9f4-4e52-8aa2-21c90c02a332
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d7e993d5bc8302931a5722495da70612e79f7dfd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24634016"
---
# <a name="ccon-statement-javascript"></a>@cc_onInstrução (JavaScript)
Ativa o suporte à compilação condicional dentro de comentários em um script.  
  
> [!WARNING]
>  Não há suporte à compilação condicional no modo Standards do Internet Explorer 11 nem em aplicativos [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]. A compilação condicional é compatível com o modo Standards do Internet Explorer 10 e em todas as versões anteriores do navegador.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
@cc_on   
```  
  
## <a name="remarks"></a>Comentários  
 A instrução `@cc_on` ativa a compilação condicional dentro de comentários em um script.  
  
 Não é comum usar variáveis de compilação condicional em scripts escritos para páginas ASP ou ASP.NET ou para programas de linha de comando, pois os recursos dos compiladores podem ser determinados com o uso de outros métodos.  
  
 Ao escrever um script para uma página da Web, sempre coloque o código de compilação condicional em comentários. Isso permite que os hosts que não oferecem suporte à compilação condicional possam ignorá-la.  
  
 É altamente recomendável usar a instrução `@cc_on` dentro de um comentário. Assim, os navegadores que não oferecem suporte para compilação condicional aceitarão o script como uma sintaxe válida:  
  
 Uma instrução `@if` ou `@set` fora de um comentário também ativa a compilação condicional.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso da instrução `@cc_on`.  
  
```JavaScript  
/*@cc_on @*/  
/*@  
    document.write("JavaScript version: " + @_jscript_version + ".");  
    document.write("<br />");  
    @if (@_win32)  
        document.write("Running on the 32-bit version of Windows.");  
    @elif (@_win16)  
        document.write("Running on the 16-bit version of Windows.");  
    @else  
        document.write("Running on a different operating system.");  
    @end  
@*/  
```  
  
## <a name="requirements"></a>Requisitos  
 Válido em todas as versões do Internet Explorer, mas não em aplicativos [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)].  
  
## <a name="see-also"></a>Consulte também  
 [Compilação condicional](../../javascript/advanced/conditional-compilation-javascript.md)   
 [Variáveis de compilação condicional](../../javascript/advanced/conditional-compilation-variables-javascript.md)   
 [@ifInstrução](../../javascript/reference/at-if-statement-javascript.md)   
 [Instrução @set](../../javascript/reference/at-set-statement-javascript.md)