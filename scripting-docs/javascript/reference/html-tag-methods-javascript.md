---
title: "Métodos HTML Tag (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- link method [JavaScript]
- blink method [JavaScript]
- fontsize method [JavaScript]
- italics method [JavaScript]
- sup method [JavaScript]
- anchor method [JavaScript]
- fixed method [JavaScript]
- fontcolor method [JavaScript]
- bold method [JavaScript]
- small method [JavaScript]
- HTML Tag methods [JavaScript]
- sub method [JavaScript]
- big method [JavaScript]
ms.assetid: 50376223-be95-4aa4-9147-9e738a5d3cfa
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7639bc609d8e9b7e4b212fe67ae40f81487d708e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="html-tag-methods-javascript"></a>Métodos de marcação HTML (JavaScript)
Você pode usar métodos de marcação HTML para colocar elementos HTML ao redor do texto em uma `String` objeto.  
  
## <a name="syntax"></a>Sintaxe  
 A tabela a seguir lista a sintaxe e uma descrição de cada método de marca HTML.  
  
 Na coluna de sintaxe, `string1` é um `String` objeto ou literal.  
  
 Indica a coluna padrão [World Wide Web Consortium (W3C)](http://go.microsoft.com/fwlink/?LinkId=199553) recomendações para HTML 4. "Recomendado" indica que o elemento HTML não é recomendado em favor de folhas de estilo.  
  
|Sintaxe|Descrição do método|Descrição do parâmetro|Padrão|  
|------------|------------------------|---------------------------|--------------|  
|`string1`.Anchor (`name`)|Insere uma âncora HTML que tem um atributo NAME ao redor do texto.|O `name` parâmetro é o texto a ser colocado no atributo nome da âncora de HTML.||  
|`string1`.big()|Coloca o HTML \<BIG > marcas ao redor do texto.||Não recomendado|  
|`string1`.BLINK()|Coloca o HTML \<BLINK > marcas ao redor do texto. O \<BLINK > marca não é suportada no Internet Explorer.||Não no padrão|  
|`string1`.Bold()|Coloca o HTML \<B > marcas ao redor do texto.||Não recomendado|  
|`string1`.Fixed()|Coloca o HTML \<TT > marcas ao redor do texto.||Não recomendado|  
|`string1`.FontColor (`color`)|Coloca o HTML \<fonte > marcas com um atributo COLOR ao redor do texto.|O `color` parâmetro é um valor de cadeia de caracteres que contém o valor hexadecimal ou nome predefinido para uma cor. Nomes válidos de cor predefinidos dependem de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] hospedar o navegador e sua versão.|Preterido|  
|`string1`.FontSize (`size`)|Coloca o HTML \<fonte > marcas com um atributo SIZE ao redor do texto.|O `size` parâmetro é um valor inteiro que especifica o tamanho do texto. Valores inteiros válidos dependem de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] navegador e a versão do host.|Preterido|  
|`string1`.italics()|Coloca o HTML \<I > marcas ao redor do texto.||Não recomendado|  
|`string1`. link (`href`)|Insere uma âncora HTML que tem um atributo HREF ao redor do texto.|O `href` parâmetro é o texto a ser colocado no atributo HREF da âncora de HTML.||  
|`string1`.Small()|Coloca o HTML \<pequeno > marcas ao redor do texto.||Não recomendado|  
|`string1`.Strike()|Coloca o HTML \<STRIKE > marcas ao redor do texto.||Preterido|  
|`string1`.sub()|Coloca o HTML \<SUB > marcas ao redor do texto.|||  
|`string1`.SUP()|Coloca o HTML \<SUP > marcas ao redor do texto.|||  
  
## <a name="remarks"></a>Comentários  
 Nenhuma verificação é executada para determinar se as marcas HTML já foram aplicadas à cadeia de caracteres.  
  
## <a name="example"></a>Exemplo  
 Os exemplos a seguir mostram como usar os métodos de marcas HTML.  
  
```JavaScript  
// anchor method.  
var strVariable = "This is an anchor.";  
document.write(strVariable.anchor("Anchor1"));  
// Output: <A NAME="Anchor1">This is an anchor.</A>  
  
// big method.  
var strVariable = "This is a string.";  
document.write(strVariable.big());  
// Output: <BIG>This is a string.</BIG>  
  
//  blink method.  
var strVariable = "This is a string.";  
document.write(strVariable.blink());  
// Output: <BLINK>This is a string.</BLINK>  
  
//  bold method.  
var strVariable = "This is a string.";  
document.write(strVariable.bold());  
// Output: <B>This is a string.</B>  
  
//  fixed method.  
var strVariable = "This is a string.";  
document.write(strVariable.fixed());  
// Output: <TT>This is a string.</TT>  
  
//  fontcolor method.  
var strVariable = "This is a string.";  
document.write(strVariable.fontcolor("red"));  
// Output: <FONT COLOR="red">This is a string.</FONT>  
  
//  fontsize method.  
var strVariable = "This is a string.";  
document.write(strVariable.fontsize(-1));  
// Output: <FONT SIZE="-1">This is a string.</FONT>  
  
//  italics method  
var strVariable = "This is a string.";  
document.write(strVariable.italics());  
// Output: <I>This is a string.</I>  
  
//  link method.  
var strVariable = "This is a hyperlink.";  
document.write(strVariable.link("http://www.microsoft.com"));  
// Output: <A HREF="http://www.microsoft.com">This is a hyperlink.</A>  
  
//  small method.  
var strVariable = "This is a string.";  
document.write(strVariable.small());  
// Output: <SMALL>This is a string.</SMALL>  
  
//  strike method.  
var strVariable = "This is a string.";  
document.write(strVariable.strike());  
// Output: <STRIKE>This is a string.</STRIKE>  
  
//  sub method.  
var strVariable = "This is a string.";  
document.write(strVariable.sub());  
// Output: <SUB>This is a string.</SUB>  
  
//  sup method.  
var strVariable = "This is a string.";  
document.write(strVariable.sup());  
// Output: <SUP>This is a string.</SUP>  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Aplica-se a**: [objeto de cadeia de caracteres](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>Consulte também  
 [Objeto String](../../javascript/reference/string-object-javascript.md)