---
title: "@ifInstrução (JavaScript) | Microsoft Docs"
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
- '@if_JavaScriptKeyword'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- elif statement
- conditional statements, if
- if statement, @if
- else statement
- '@if statement'
ms.assetid: ff11b29d-c06a-4276-b11d-db73e2da98ac
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 87cfc157ab16b183ccf687fa221393be4ab74757
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="if-statement-javascript"></a>@ifInstrução (JavaScript)
Execute um grupo de instruções condicionalmente, dependendo do valor de uma expressão.  
  
> [!WARNING]
>  Não há suporte à compilação condicional no modo Standards do Internet Explorer 11 nem em aplicativos [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]. A compilação condicional é compatível com o modo Standards do Internet Explorer 10 e em todas as versões anteriores do navegador.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
      @if (  
   condition1  
)  
   text1  
[@elif (  
   condition2  
)  
   text2]  
[@else  
   text3]  
@end   
```  
  
## <a name="parameters"></a>Parâmetros  
 *condição1, condition2*  
 Opcional. Uma expressão que pode ser forçada em uma expressão booliana.  
  
 `text1`  
 Opcional. Texto a ser analisado se `condition1` é **true**.  
  
 `text2`  
 Opcional. Texto a ser analisado se `condition1` é **false** e `condition2` é **true**.  
  
 `text3`  
 Opcional. Texto a ser analisado se `condition1` e `condition2` são **false**.  
  
## <a name="remarks"></a>Comentários  
 Ao escrever uma instrução `@if`, não é necessário colocar cada cláusula em uma linha separada. Você pode usar várias  **@elif**  cláusulas. No entanto, todos os  **@elif**  cláusulas devem vir antes de um  **@else**  cláusula.  
  
 A instrução `@if` é normalmente usada para determinar qual texto entre várias opções deve ser usado para a saída de texto.  
  
 Não é comum usar variáveis de compilação condicional em scripts escritos para páginas ASP ou ASP.NET ou para programas de linha de comando. Isso ocorre porque os recursos dos compiladores podem ser determinados com o uso de outros métodos.  
  
 Ao escrever um script para uma página da Web, sempre adicione o código de compilação condicional dentro de um comentário. Isso permite que os hosts que não oferecem suporte à compilação condicional possam ignorá-la.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso do  **@if...@elif... @else... @end**  instrução.  
  
```JavaScript  
/*@cc_on @*/  
/*@  
    document.write("JavaScript version: " + @_jscript_version + ".");  
    document.write("<br />");  
    @if (@_win32)  
        document.write("Running on a 32-bit version of Windows.");  
    @elif (@_win16)  
        document.write("Running on a 16-bit version of Windows.");  
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
 [@cc_onInstrução](../../javascript/reference/at-cc-on-statement-javascript.md)   
 [Instrução @set](../../javascript/reference/at-set-statement-javascript.md)