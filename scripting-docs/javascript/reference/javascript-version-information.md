---
title: "Informações de versão do JavaScript | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- JavaScript, version information
ms.assetid: 440f4924-f7a9-48e0-873e-bd599a93b437
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3a2335c3697be9ef3e2d674ac37047ddd3de242d
ms.sourcegitcommit: 873c0e1a31def013bcca1b0caa0eb0249de89bec
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2018
---
# <a name="javascript-version-information"></a>JavaScript Informações da versão
Versões diferentes de JavaScript oferecem suporte a diferentes conjuntos de elementos JavaScript. Os aplicativos [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] oferecem suporte a um conjunto de recursos ligeiramente diferente daqueles do Internet Explorer.  
  
> [!IMPORTANT]
>  Um aplicativo [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] é um novo tipo de aplicativo que é executado em dispositivos [!INCLUDE[win8](../../javascript/includes/win8-md.md)]. Para obter mais informações sobre [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] aplicativos, consulte [o que é um aplicativo da Windows Store?](http://msdn.microsoft.com/en-us/231c1fba-9f87-468e-94aa-45dd57edcc70)  
  
 O modo Standards (usado em todas as versões do Internet Explorer, até o Internet Explorer 11, quando há uma diretiva `<!doctype>`) dá suporte a um conjunto de elementos  diferente do modo Quirks (usado quando não há diretiva `<!doctype>`). Para obter mais informações sobre controle de versão, consulte [definindo compatibilidade de documentos](http://go.microsoft.com/fwlink/?LinkId=208537).  
  
 A tabela a seguir mostra os modos de documento do Internet Explorer (e aplicativos da Store que representam o [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] e o [!INCLUDE[winphone_appname](../../javascript/reference/includes/winphone-appname-md.md)]) que dão suporte a elementos de linguagem específicos. Modos de documento que oferecem suporte a um determinado elemento são indicados pela letra **Y**, e os modos de documento que não dão suporte a um determinado elemento são indicados pela letra **N**.  
  
> [!IMPORTANT]
>  [!INCLUDE[jsv12text](../../javascript/includes/jsv12text-md.md)] (Navegador edge no Windows 10) não inclui suporte para modos de documento herdado. O suporte para aplicativos [!INCLUDE[winphone_appname](../../javascript/reference/includes/winphone-appname-md.md)] começa com o Windows Phone 8.1. Recursos experimentais (sobre: flags) são indicados por "Exp".  
  
 A tabela contém informações de resumo. Para obter informações mais específicas, consulte a documentação do elemento de linguagem.  
  
|Elemento de linguagem|Quirks, Internet Explorer 6 Standards, Internet Explorer 7 Standards|Internet Explorer 8 Standards|Internet Explorer 9 Standards|Internet Explorer 10 Standards|Internet Explorer 11 Standards|Edge|Aplicativos da Store|  
|----------------------|--------------------------------------------------------------------------|-----------------------------------|-----------------------------------|------------------------------------|------------------------------------|----------|----------------|  
|[__proto\_ \_ propriedade (Object)](../../javascript/reference/proto-property-object-javascript.md)|N|N|N|N|S|S|v8 (Win): N<br />v8.1 (Win): S<br />v8.1 (Phone): S|  
|[Propriedades $1...$9 (RegExp)](../../javascript/reference/dollar-1-dot-dot-dot-dollar-9-properties-regexp-javascript.md)|S|S|S|S|S|S|S|  
|[Propriedade 0n](../../javascript/reference/0-dot-dot-dot-n-properties-arguments-javascript.md)|S|S|S|S|S|S|S|  
|[Função ABS](../../javascript/reference/math-abs-function-javascript.md)|S|S|S|S|S|S|S|  
|[Função ACOS](../../javascript/reference/math-acos-function-javascript.md)|S|S|S|S|S|S|S|  
|[Função ACOSH](../../javascript/reference/math-acosh-function-javascript.md)|N|N|N|N|N|S|v8.1: N<br />V10: S|  
|[Objeto ActiveXObject](../../javascript/reference/activexobject-object-javascript.md)|S|S|S|S|S|S|N|  
|[Operador de atribuição de adição (+=)](../../javascript/reference/addition-assignment-operator-decrement-equal-javascript.md)|S|S|S|S|S|S|S|  
|[Operador de adição (+)](../../javascript/reference/addition-operator-decrement-javascript.md)|S|S|S|S|S|S|S|  
|[Método Apply](../../javascript/reference/apply-method-function-javascript.md)|S|S|S|S|S|S|S|  
|[Objeto arguments](../../javascript/reference/arguments-object-javascript.md)|S|S|S|S|S|S|S|  
|[Propriedade arguments](../../javascript/reference/arguments-property-function-javascript.md)|S|S|S|S|S|S|S|  
|[Objeto Array](../../javascript/reference/array-object-javascript.md)|S|S|S|S|S|S|S|  
|[Função Array.from (Array)](../../javascript/reference/array-from-function-array-javascript.md)|N|N|N|N|N|N|v8.1: N<br />V10: S|  
|[Função Array.isArray](../../javascript/reference/array-isarray-function-javascript.md)|N|N|S|S|S|S|S|  
|[Função Array.of (Array)](../../javascript/reference/array-of-function-array-javascript.md)|N|N|N|N|N|N|v8.1: N<br />V10: S|  
|[Objeto ArrayBuffer](../../javascript/reference/arraybuffer-object.md)|N|N|N|S|S|S|S|  
|[Funções](../../javascript/functions-javascript.md)|N|N|N|N|N|N|v8.1: N<br />V10: S|  
|[Função ASIN](../../javascript/reference/math-asin-function-javascript.md)|S|S|S|S|S|S|S|  
|[Função Object.assign (Object)](../../javascript/reference/object-assign-function-object-javascript.md)|N|N|N|N|N|N|v8.1: N<br />V10: S|  
|[Operador de atribuição (=)](../../javascript/reference/assignment-operator-decrement-equal-javascript.md)|S|S|S|S|S|S|S|  
|[Função ATAN](../../javascript/reference/math-atan-function-javascript.md)|S|S|S|S|S|S|S|  
|[Função ATAN2](../../javascript/reference/math-atan2-function-javascript.md)|S|S|S|S|S|S|S|  
|[Método atEnd](../../javascript/reference/atend-method-enumerator-javascript.md)|S|S|S|S|S|S|N|  
|[Método Bind](../../javascript/reference/bind-method-function-javascript.md)|N|N|S|S|S|S|S|  
|[Operador de atribuição AND bit a bit (&=)](../../javascript/reference/bitwise-and-assignment-operator-decrement-equal-javascript.md)|S|S|S|S|S|S|S|  
|[Operador AND bit a bit (&)](../../javascript/reference/bitwise-and-operator-decrement-javascript.md)|S|S|S|S|S|S|S|  
|[Bit a bit operador Left Shift (<\<)](../../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)|S|S|S|S|S|S|S|  
|[Operador NOT bit a bit (~)](../../javascript/reference/bitwise-not-operator-decrement-tilde-javascript.md)|S|S|S|S|S|S|S|  
|[Bit a bit ou operador de atribuição (&#124; =)](../../javascript/reference/bitwise-or-assignment-operator-decrement-equal-javascript.md)|S|S|S|S|S|S|S|  
|[OR bit a bit operador (&#124;)](../../javascript/reference/bitwise-or-operator-decrement-javascript.md)|S|S|S|S|S|S|S|  
|[Operador bit a bit de deslocamento para a direita (>>)](../../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)|S|S|S|S|S|S|S|  
|[Operador de atribuição YOR bit a bit (^ =)](../../javascript/reference/bitwise-xor-assignment-operator-decrement-hat-equal-javascript.md)|S|S|S|S|S|S|S|  
|[Operador YOR bit a bit (^)](../../javascript/reference/bitwise-xor-operator-decrement-hat-javascript.md)|S|S|S|S|S|S|S|  
|[Método BLINK](../../javascript/reference/html-tag-methods-javascript.md)|S|S|S|S|S|S|S|  
|[Método Bold](../../javascript/reference/html-tag-methods-javascript.md)|S|S|S|S|S|S|S|  
|[Objeto Boolean](../../javascript/reference/boolean-object-javascript.md)|S|S|S|S|S|S|S|  
|[Instrução Break](../../javascript/reference/break-statement-javascript.md)|S|S|S|S|S|S|S|  
|[chamada de método](../../javascript/reference/call-method-function-javascript.md)|S|S|S|S|S|S|S|  
|[Propriedade callee](../../javascript/reference/callee-property-arguments-javascript.md)|S|S|S|S|S|S|S|  
|[Propriedade Caller](../../javascript/reference/caller-property-function-javascript.md)|S|S|S|S|S|S|S|  
|[Instrução catch](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)|S|S|S|S|S|S|S|  
|[Função ceil](../../javascript/reference/math-ceil-function-javascript.md)|S|S|S|S|S|S|S|  
|[Método charAt](../../javascript/reference/charat-method-string-javascript.md)|S|S|S|S|S|S|S|  
|[Método charCodeAt](../../javascript/reference/charcodeat-method-string-javascript.md)|S|S|S|S|S|S|S|  
|[Instrução Class](../../javascript/reference/class-statement-javascript.md)|N|N|N|N|N|Exp.|v8.1: N<br />V10: Exp.|  
|[Método codePointAt (String)](../../javascript/reference/codepointat-method-string-javascript.md)|N|N|N|N|N|S|v8.1: N<br />V10: S|  
|[Operador vírgula (,)](../../javascript/reference/comma-operator-decrement-javascript.md)|S|S|S|S|S|S|S|  
|[(Instrução de comentário de linha única)](../../javascript/reference/comment-statements-javascript.md)|S|S|S|S|S|S|S|  
|[/*.. \*/ (Instrução de comentário de várias linhas)](../../javascript/reference/comment-statements-javascript.md)|S|S|S|S|S|S|S|  
|[Operadores de Comparação](../../javascript/reference/comparison-operators-javascript.md)|S|S|S|S|S|S|S|  
|[Método Compile](../../javascript/reference/compile-method-regular-expression-javascript.md)|S|S|S|S|S|S|S|  
|[Método concat (Array)](../../javascript/reference/concat-method-array-javascript.md)|S|S|S|S|S|S|S|  
|[Método concat (String)](../../javascript/reference/concat-method-string-javascript.md)|S|S|S|S|S|S|S|  
|[Compilação Condicional](../../javascript/advanced/conditional-compilation-javascript.md)|S|S|S|S|N|N|N|  
|[Variáveis de compilação condicional](../../javascript/advanced/conditional-compilation-variables-javascript.md)|S|S|S|S|N|N|N|  
|[Operador condicional (ternário) (?:)](../../javascript/reference/conditional-ternary-operator-decrement-javascript.md)|S|S|S|S|S|S|S|  
|[Propriedade Constructor](../../javascript/reference/constructor-property-object-javascript.md)|S|S|S|S|S|S|S|  
|[Instrução const](../../javascript/reference/const-statement-javascript.md)|N|N|N|N|S|S|v8 (Win): N<br />v8.1 (Win): S<br />v8.1 (Phone): S|  
|[Instrução continue](../../javascript/reference/continue-statement-javascript.md)|S|S|S|S|S|S|S|  
|[CoS função](../../javascript/reference/math-cos-function-javascript.md)|S|S|S|S|S|S|S|  
|[Criar função](../../javascript/reference/object-create-function-javascript.md)|N|N|S|S|S|S|S|  
|[Objeto DataView](../../javascript/reference/dataview-object.md)|N|N|N|S|S|S|S|  
|[Objeto Date](../../javascript/reference/date-object-javascript.md)|S|S|S|S|S|S|S|  
|[Objeto Debug](../../javascript/reference/debug-object-javascript.md)|S|S|S|S|S|S|S|  
|[Propriedade Debug.setNonUserCodeExceptions](../../javascript/reference/debug-setnonusercodeexceptions-property.md)|N|N|N|S|S|S|S|  
|[Propriedade Debug.setNonUserCodeExceptions](../../javascript/reference/debug-setnonusercodeexceptions-property.md)|N|N|N|S|S|S|S|  
|[Instrução debugger](../../javascript/reference/debugger-statement-javascript.md)|S|S|S|S|S|S|S|  
|[Função decodeURI](../../javascript/reference/decodeuri-function-javascript.md)|S|S|S|S|S|S|S|  
|[Função decodeURIComponent](../../javascript/reference/decodeuricomponent-function-javascript.md)|S|S|S|S|S|S|S|  
|[Operador de decremento (-)](../../javascript/reference/increment-and-decrement-operators-javascript.md)|S|S|S|S|S|S|S|  
|[Funções](../../javascript/functions-javascript.md)|N|N|N|N|N|Exp.|v8.1: N<br />V10: Exp.|  
|[Função defineProperties](../../javascript/reference/object-defineproperties-function-javascript.md)|N|S*|S|S|S|S|S|  
|[Função defineProperty](../../javascript/reference/object-defineproperty-function-javascript.md)|N|S*|S|S|S|S|S|  
|[Operador delete](../../javascript/reference/delete-operator-decrementjavascript.md)|S|S|S|S|S|S|S|  
|[Propriedade Description](../../javascript/reference/description-property-error-javascript.md)|S|S|S|S|S|S|S|  
|[Método Dimensions](../../javascript/reference/dimensions-method-vbarray-javascript.md)|S|S|S|S|S|S|S|  
|[Operador de atribuição de divisão (/=)](../../javascript/reference/division-assignment-operator-decrement-equal-javascript.md)|S|S|S|S|S|S|S|  
|[Operador de divisão (/)](../../javascript/reference/division-operator-decrement-javascript.md)|S|S|S|S|S|S|S|  
|[Instrução do...while](../../javascript/reference/do-dot-dot-dot-while-statement-javascript.md)|S|S|S|S|S|S|S|  
|[Constante E](../../javascript/reference/math-constants-javascript.md)|S|S|S|S|S|S|S|  
|[Função encodeURI](../../javascript/reference/encodeuri-function-javascript.md)|S|S|S|S|S|S|S|  
|[Função componente encodeURI](../../javascript/reference/encodeuricomponent-function-javascript.md)|S|S|S|S|S|S|S|  
|[Método entries (Array)](../../javascript/reference/entries-method-array-javascript.md)|N|N|N|N|N|N|v8.1: N<br />V10: S|  
|[Objeto Enumerator](../../javascript/reference/enumerator-object-javascript.md)|S|S|S|S|S|S|N|  
|[Constantes Number](../../javascript/reference/number-constants-javascript.md)|N|N|N|N|N|N|v8.1: N<br />V10: S|  
|[Operador de igualdade (= =)](../../javascript/reference/comparison-operators-javascript.md)|S|S|S|S|S|S|S|  
|[Objeto Error](../../javascript/reference/error-object-javascript.md)|S|S|S|S|S|S|S|  
|[Propriedade stack (Error)](../../javascript/reference/stack-property-error-javascript.md)|N|N|N|S|S|S|S|  
|[Propriedade stackTraceLimit (Error)](../../javascript/reference/stacktracelimit-property-error-javascript.md)|N|N|N|S|S|S|S|  
|[Função escape](../../javascript/reference/escape-function-javascript.md)|S|S|S|S|S|S|S|  
|[Função eval](../../javascript/reference/eval-function-javascript.md)|S|S|S|S|S|S|S|  
|[Método Exec](../../javascript/reference/exec-method-regular-expression-javascript.md)|S|S|S|S|S|S|S|  
|[Método every](../../javascript/reference/every-method-array-javascript.md)|N|N|S|S|S|S|S|  
|[Função Exp](../../javascript/reference/math-exp-function-javascript.md)|S|S|S|S|S|S|S|  
|[Método fill (Array)](../../javascript/reference/fill-method-array-javascript.md)|N|N|N|N|N|N|v8.1: N<br />V10: S|  
|[Método Filter](../../javascript/reference/filter-method-array-javascript.md)|N|N|S|S|S|S|S|  
|[Instrução Finally](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)|S|S|S|S|S|S|S|  
|[Método findIndex (Array)](../../javascript/reference/findindex-method-array-javascript.md)|N|N|N|N|N|N|v8.1: N<br />V10: S|  
|[Método Fixed](../../javascript/reference/html-tag-methods-javascript.md)|S|S|S|S|S|S|S|  
|[Objeto Float32Array](../../javascript/reference/float32array-object.md)|N|N|N|S|S|S|S|  
|[Objeto Float64Array](../../javascript/reference/float64array-object.md)|N|N|N|S|S|S|S|  
|[Função Floor](../../javascript/reference/math-floor-function-javascript.md)|S|S|S|S|S|S|S|  
|[Método FontColor](../../javascript/reference/html-tag-methods-javascript.md)|S|S|S|S|S|S|S|  
|[Método FontSize](../../javascript/reference/html-tag-methods-javascript.md)|S|S|S|S|S|S|S|  
|[Instrução for](../../javascript/reference/for-statement-javascript.md)|S|S|S|S|S|S|S|  
|[Método forEach](../../javascript/reference/foreach-method-array-javascript.md)|N|N|S|S|S|S|S|  
|[Instrução for...in](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)|S|S|S|S|S|S|S|  
|[Instrução for...of](../../javascript/reference/for-dot-dot-dot-of-statement-javascript.md)|N|N|N|N|N|S|v8.1: N<br />V10: S|  
|[Função Freeze](../../javascript/reference/object-freeze-function-javascript.md)|N|N|S|S|S|S|S|  
|[Função fromCharCode](../../javascript/reference/string-fromcharcode-function-javascript.md)|S|S|S|S|S|S|S|  
|[Função fromCodePoint](../../javascript/reference/string-fromcodepoint-function-javascript.md)|N|N|N|N|N|S|v8.1: N<br />V10: S|  
|[Objeto Function](../../javascript/reference/function-object-javascript.md)|S|S|S|S|S|S|S|  
|[Instrução Function](../../javascript/reference/function-statement-javascript.md)|S|S|S|S|S|S|S|  
|[Geradores](../../javascript/advanced/iterators-and-generators-javascript.md)|N|N|N|N|N|Exp.|v8.1: N<br />V10: Exp.|  
|[Método getDate](../../javascript/reference/getdate-method-date-javascript.md)|S|S|S|S|S|S|S|  
|[Método getDay](../../javascript/reference/getday-method-date-javascript.md)|S|S|S|S|S|S|S|  
|[Método getFullYear](../../javascript/reference/getfullyear-method-date-javascript.md)|S|S|S|S|S|S|S|  
|[Método getHours](../../javascript/reference/gethours-method-date-javascript.md)|S|S|S|S|S|S|S|  
|[Método getItem](../../javascript/reference/getitem-method-vbarray-javascript.md)|S|S|S|S|S|S|S|  
|[Método getMilliseconds](../../javascript/reference/getmilliseconds-method-date-javascript.md)|S|S|S|S|S|S|S|  
|[Método getMinutes](../../javascript/reference/getminutes-method-date-javascript.md)|S|S|S|S|S|S|S|  
|[Método getMonth](../../javascript/reference/getmonth-method-date-javascript.md)|S|S|S|S|S|S|S|  
|[Função GetObject](../../javascript/reference/getobject-function-javascript.md)|S|S|N|N|N|N|N|  
|[Função getOwnPropertyDescriptor](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)|N|S*|S|S|S|S|S|  
|[Função getOwnPropertyNames](../../javascript/reference/object-getownpropertynames-function-javascript.md)|N|N|S|S|S|S|S|  
|[Função getPrototypeOf](../../javascript/reference/object-getprototypeof-function-javascript.md)|N|N|S|S|S|S|S|  
|[Método getSeconds](../../javascript/reference/getseconds-method-date-javascript.md)|S|S|S|S|S|S|S|  
|[Método getTime](../../javascript/reference/gettime-method-date-javascript.md)|S|S|S|S|S|S|S|  
|[Método getTimezoneOffset](../../javascript/reference/gettimezoneoffset-method-date-javascript.md)|S|S|S|S|S|S|S|  
|[Método getUTCDate](../../javascript/reference/getutcdate-method-date-javascript.md)|S|S|S|S|S|S|S|  
|[Método getUTCDay](../../javascript/reference/getutcday-method-date-javascript.md)|S|S|S|S|S|S|S|  
|[Método getUTCFullYear](../../javascript/reference/getutcfullyear-method-date-javascript.md)|S|S|S|S|S|S|S|  
|[Método getUTCHours](../../javascript/reference/getutchours-method-date-javascript.md)|S|S|S|S|S|S|S|  
|[Método getUTCMilliseconds](../../javascript/reference/getutcmilliseconds-method-date-javascript.md)|S|S|S|S|S|S|S|  
|[Método getUTCMinutes](../../javascript/reference/getutcminutes-method-date-javascript.md)|S|S|S|S|S|S|S|  
|[Método getUTCMonth](../../javascript/reference/getutcmonth-method-date-javascript.md)|S|S|S|S|S|S|S|  
|[Método getUTCSeconds](../../javascript/reference/getutcseconds-method-date-javascript.md)|S|S|S|S|S|S|S|  
|[Método getVarDate](../../javascript/reference/getvardate-method-date-javascript.md)|S|S|S|S|S|S|N|  
|[Método getYear](../../javascript/reference/getyear-method-date-javascript.md)|S|S|S|S|S|S|S|  
|[Objeto Global](../../javascript/reference/global-object-javascript.md)|S|S|S|S|S|S|S|  
|[Propriedade global](../../javascript/reference/global-property-regular-expression-javascript.md)|S|S|S|S|S|S|S|  
|[Operador maior que (>)](../../javascript/reference/comparison-operators-javascript.md)|S|S|S|S|S|S|S|  
|[Maior que ou igual ao operador (> =)](../../javascript/reference/comparison-operators-javascript.md)|S|S|S|S|S|S|S|  
|[Método hasOwnProperty](../../javascript/reference/hasownproperty-method-object-javascript.md)|S|S|S|S|S|S|S|  
|[Métodos de marcação de HTML](../../javascript/reference/html-tag-methods-javascript.md)|S|S|S|S|S|S|S|  
|[Função hypot](../../javascript/reference/math-hypot-function-javascript.md)|N|N|N|N|N|S|v8.1: N<br />V10: S|  
|[Operador de identidade (=)](../../javascript/reference/comparison-operators-javascript.md)|S|S|S|S|S|S|S|  
|[Instrução if...else](../../javascript/reference/if-dot-dot-dot-else-statement-javascript.md)|S|S|S|S|S|S|S|  
|[Propriedade ignoreCase](../../javascript/reference/ignorecase-property-regular-expression-javascript.md)|S|S|S|S|S|S|S|  
|[Função imul](../../javascript/reference/math-imul-function-javascript.md)|N|N|N|N|N|S|v8.1: N<br />V10: S|  
|[Operador in](../../javascript/reference/in-operator-decrementjavascript.md)|S|S|S|S|S|S|S|  
|[Método includes (String)](../../javascript/reference/includes-method-string-javascript.md)|N|N|N|N|N|S|v8.1: N<br />V10: S|  
|[Operador de incremento (+ +)](../../javascript/reference/increment-and-decrement-operators-javascript.md)|S|S|S|S|S|S|S|  
|[Propriedade Index](../../javascript/reference/index-property-regexp-javascript.md)|S|S|S|S|S|S|S|  
|[Método indexOf (Array)](../../javascript/reference/indexof-method-array-javascript.md)|N|N|S|S|S|S|S|  
|[Método indexOf (String)](../../javascript/reference/indexof-method-string-javascript.md)|S|S|S|S|S|S|S|  
|[Operador de desigualdade (! =)](../../javascript/reference/comparison-operators-javascript.md)|S|S|S|S|S|S|S|  
|[Constante de infinito](../../javascript/reference/infinity-constant-javascript.md)|S|S|S|S|S|S|S|  
|[Propriedade Input ($_)](../../javascript/reference/input-property-dollar-regexp-javascript.md)|S|S|S|S|S|S|S|  
|[Operador instanceof](../../javascript/reference/instanceof-operator-decrementjavascript.md)|S|S|S|S|S|S|S|  
|[Objeto Int8Array](../../javascript/reference/int8array-object.md)|N|N|N|S|S|S|S|  
|[Objeto Int16Array](../../javascript/reference/int16array-object.md)|N|N|N|S|S|S|S|  
|[Objeto Int32Array](../../javascript/reference/int32array-object.md)|N|N|N|S|S|S|S|  
|[Objeto Intl.Collator](../../javascript/reference/intl-collator-object-javascript.md)|N|N|N|N|S|S|v8 (Win): N<br />v8.1 (Win): S<br />v8.1 (Phone): S|  
|[Objeto Intl.DateTimeFormat](../../javascript/reference/intl-datetimeformat-object-javascript.md)|N|N|N|N|S|S|v8: N<br />v8.1: S|  
|[Objeto Intl.NumberFormat](../../javascript/reference/intl-numberformat-object-javascript.md)|N|N|N|N|S|S|v8: N<br />v8.1: S|  
|[Função isFinite](../../javascript/reference/isfinite-function-javascript.md)|S|S|S|S|S|S|S|  
|[Função isArray](../../javascript/reference/array-isarray-function-javascript.md)|N|N|S|S|S|S|S|  
|[Função IsExtensible](../../javascript/reference/object-isextensible-function-javascript.md)|N|N|S|S|S|S|S|  
|[Função isFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)|N|N|S|S|S|S|S|  
|[Função isInteger](../../javascript/reference/number-isinteger-function-number-javascript.md)|N|N|N|N|N|S|v8.1: N<br />V10: S|  
|[Função isNaN](../../javascript/reference/isnan-function-javascript.md)|S|S|S|S|S|S|S|  
|[Função isNaN (número)](../../javascript/reference/number-isnan-function-number-javascript.md)|N|N|N|N|N|S|v8.1: N<br />V10: S|  
|[Formato de data ISO](../../javascript/date-and-time-strings-javascript.md)|N|N|S|S|S|S|S|  
|[Método IsPrototypeOf](../../javascript/reference/isprototypeof-method-object-javascript.md)|S|S|S|S|S|S|S|  
|[Função isSealed](../../javascript/reference/object-issealed-function-javascript.md)|N|N|S|S|S|S|S|  
|[Método italics](../../javascript/reference/html-tag-methods-javascript.md)|S|S|S|S|S|S|S|  
|[Iteradores](../../javascript/advanced/iterators-and-generators-javascript.md)|N|N|N|N|N|S|v8.1: N<br />V10: S|  
|[Método item](../../javascript/reference/item-method-enumerator-javascript.md)|S|S|S|S|S|S|S|  
|[Método join](../../javascript/reference/join-method-array-javascript.md)|S|S|S|S|S|S|S|  
|[Objeto JSON](../../javascript/reference/json-object-javascript.md)|N|S|S|S|S|S|S|  
|[teclas de função](../../javascript/reference/object-keys-function-javascript.md)|N|N|S|S|S|S|S|  
|[Método keys (Array)](../../javascript/reference/keys-method-array-javascript.md)|N|N|N|N|N|S|v8.1: N<br />V10: S|  
|[Instrução Labeled](../../javascript/reference/labeled-statement-javascript.md)|S|S|S|S|S|S|S|  
|[Propriedade lastIndex](../../javascript/reference/lastindex-property-regexp-javascript.md)|S|S|S|S|S|S|S|  
|[Método lastIndexOf (Array)](../../javascript/reference/lastindexof-method-array-javascript.md)|N|N|S|S|S|S|S|  
|[Método lastIndexOf (String)](../../javascript/reference/lastindexof-method-string-javascript.md)|S|S|S|S|S|S|S|  
|[lastMatch Property ($&)](../../javascript/reference/lastmatch-property-dollar-regexp-javascript.md)|S|S|S|S|S|S|S|  
|[lastParen Property ($+)](../../javascript/reference/lastparen-property-dollar-regexp-javascript.md)|S|S|S|S|S|S|S|  
|[Método LBound](../../javascript/reference/lbound-method-vbarray-javascript.md)|S|S|S|S|S|S|S|  
|[Propriedade leftContext ($')](../../javascript/reference/leftcontext-property-dollar-grave-regexp-javascript.md)|S|S|S|S|S|S|S|  
|[Operador de atribuição de deslocamento para a esquerda(<<=)](../../javascript/reference/left-shift-assignment-operator-decrement-equal-javascript.md)|S|S|S|S|S|S|S|  
|[Propriedade Length (argumentos)](../../javascript/reference/length-property-arguments-javascript.md)|S|S|S|S|S|S|S|  
|[Propriedade length (Array)](../../javascript/reference/length-property-array-javascript.md)|S|S|S|S|S|S|S|  
|[Propriedade length (Function)](../../javascript/reference/length-property-function-javascript.md)|S|S|S|S|S|S|S|  
|[Propriedade length (String)](../../javascript/reference/length-property-string-javascript.md)|S|S|S|S|S|S|S|  
|[Operador menor que (<)](../../javascript/reference/comparison-operators-javascript.md)|S|S|S|S|S|S|S|  
|[Operador menor que ou igual a (< =)](../../javascript/reference/comparison-operators-javascript.md)|S|S|S|S|S|S|S|  
|[Instrução let](../../javascript/reference/let-statement-javascript.md)|N|N|N|N|S|S|v8: N<br />v8.1: S|  
|[Método link](../../javascript/reference/html-tag-methods-javascript.md)|S|S|S|S|S|S|S|  
|[Constante LN2](../../javascript/reference/math-constants-javascript.md)|S|S|S|S|S|S|S|  
|[Constante LN10](../../javascript/reference/math-constants-javascript.md)|S|S|S|S|S|S|S|  
|[Método localeCompare](../../javascript/reference/localecompare-method-string-javascript.md)|S|S|S|S|S|S|S|  
|[Função log](../../javascript/reference/math-log-function-javascript.md)|S|S|S|S|S|S|S|  
|[Constante LOG2E](../../javascript/reference/math-constants-javascript.md)|S|S|S|S|S|S|S|  
|[LOG10E Constant](../../javascript/reference/math-constants-javascript.md)|S|S|S|S|S|S|S|  
|[Operador AND lógico (&&)](../../javascript/reference/logical-and-operator-decrement-javascript.md)|S|S|S|S|S|S|S|  
|[Operador NOT lógico (!)](../../javascript/reference/logical-not-operator-decrement-exclpt-javascript.md)|S|S|S|S|S|S|S|  
|[OR lógico operador (&#124; &#124;)](../../javascript/reference/logical-or-operator-decrement-javascript.md)|S|S|S|S|S|S|S|  
|[Método Map](../../javascript/reference/map-method-array-javascript.md)|N|N|S|S|S|S|S|  
|[Objeto Map](../../javascript/reference/map-object-javascript.md)|N|N|N|N|S|S|v8: N<br />v8.1: S|  
|[Método match](../../javascript/reference/match-method-string-javascript.md)|S|S|S|S|S|S|S|  
|[Objeto Math](../../javascript/reference/math-object-javascript.md)|S|S|S|S|S|S|S|  
|[Função max](../../javascript/reference/math-max-function-javascript.md)|S|S|S|S|S|S|S|  
|[Constante MAX_VALUE](../../javascript/reference/number-constants-javascript.md)|S|S|S|S|S|S|S|  
|[Propriedade Message](../../javascript/reference/message-property-error-javascript.md)|S|S|S|S|S|S|S|  
|[Função min](../../javascript/reference/math-min-function-javascript.md)|S|S|S|S|S|S|S|  
|[Constante MIN_VALUE](../../javascript/reference/number-constants-javascript.md)|S|S|S|S|S|S|S|  
|[Operador de atribuição de resto (% =)](../../javascript/reference/modulus-assignment-operator-decrement-javascript.md)|S|S|S|S|S|S|S|  
|[Operador restante (%)](../../javascript/reference/modulus-operator-decrementjavascript.md)|S|S|S|S|S|S|S|  
|[Método moveFirst](../../javascript/reference/movefirst-method-enumerator-javascript.md)|S|S|S|S|S|S|S|  
|[Método moveNext](../../javascript/reference/movenext-method-enumerator-javascript.md)|S|S|S|S|S|S|S|  
|[Propriedade Multiline](../../javascript/reference/multiline-property-regular-expression-javascript.md)|S|S|S|S|S|S|S|  
|[Operador de atribuição de multiplicação (*=)](../../javascript/reference/multiplication-assignment-operator-decrement-equal-javascript.md)|S|S|S|S|S|S|S|  
|[Operador de multiplicação (*)](../../javascript/reference/multiplication-operator-decrement-javascript.md)|S|S|S|S|S|S|S|  
|[Propriedade Name](../../javascript/reference/name-property-error-javascript.md)|S|S|S|S|S|S|S|  
|[Constante NaN (Global)](../../javascript/reference/nan-constant-javascript.md)|S|S|S|S|S|S|S|  
|[Constante NaN (número)](../../javascript/reference/number-constants-javascript.md)|S|S|S|S|S|S|S|  
|[Constante NEGATIVE_INFINITY](../../javascript/reference/number-constants-javascript.md)|S|S|S|S|S|S|S|  
|[Operador new](../../javascript/reference/new-operator-decrementjavascript.md)|S|S|S|S|S|S|S|  
|[Operador nonidentity (! = =)](../../javascript/reference/comparison-operators-javascript.md)|S|S|S|S|S|S|S|  
|[Função Now](../../javascript/reference/date-now-function-javascript.md)|N|N|S|S|S|S|S|  
|[Objeto Number](../../javascript/reference/number-object-javascript.md)|S|S|S|S|S|S|S|  
|[Propriedade de número](../../javascript/reference/number-property-error-javascript.md)|S|S|S|S|S|S|S|  
|[Objeto Object](../../javascript/reference/object-object-javascript.md)|S|S|S|S|S|S|S|  
|[Precedência do Operador](../../javascript/operator-subtractprecedence-javascript.md)|S|S|S|S|S|S|S|  
|[Função Date.parse](../../javascript/reference/date-parse-function-javascript.md)|S|S|S|S|S|S|S|  
|[Função JSON.parse](../../javascript/reference/json-parse-function-javascript.md)|N|S|S|S|S|S|S|  
|[Função parseFloat](../../javascript/reference/parsefloat-function-javascript.md)|S|S|S|S|S|S|S|  
|[Função parseInt](../../javascript/reference/parseint-function-javascript.md)|S|S|S|S|S|S|S|  
|[Constante PI](../../javascript/reference/math-constants-javascript.md)|S|S|S|S|S|S|S|  
|[Método pop](../../javascript/reference/pop-method-array-javascript.md)|S|S|S|S|S|S|S|  
|[Constante POSITIVE_INFINITY](../../javascript/reference/number-constants-javascript.md)|S|S|S|S|S|S|S|  
|[Função pow](../../javascript/reference/math-pow-function-javascript.md)|S|S|S|S|S|S|S|  
|[Função preventExtensions](../../javascript/reference/object-preventextensions-function-javascript.md)|N|N|S|S|S|S|S|  
|[Objeto Promise](../../javascript/reference/promise-object-javascript.md)|N|N|N|N|N|S|v8.1: N<br />V10: S|  
|[Propriedade prototype](../../javascript/reference/prototype-property-object-javascript.md)|S|S|S|S|S|S|S|  
|[Método propertyIsEnumerable](../../javascript/reference/propertyisenumerable-method-object-javascript.md)|S|S|S|S|S|S|S|  
|[Objeto Proxy](../../javascript/reference/proxy-object-javascript.md)|N|N|N|N|N|S|v8.1: N<br />V10: S|  
|[Método push](../../javascript/reference/push-method-array-javascript.md)|S|S|S|S|S|S|S|  
|[Função Random](../../javascript/reference/math-random-function-javascript.md)|S|S|S|S|S|S|S|  
|[Função RAW](../../javascript/reference/string-raw-function-javascript.md)|N|N|N|N|N|S|v8.1: N<br />V10: S|  
|[Método reduce](../../javascript/reference/reduce-method-array-javascript.md)|N|N|S|S|S|S|S|  
|[Método reduceRight](../../javascript/reference/reduceright-method-array-javascript.md)|N|N|S|S|S|S|S|  
|[Objeto RegExp](../../javascript/reference/regexp-object-javascript.md)|S|S|S|S|S|S|S|  
|[Objeto Regular Expression](../../javascript/reference/regular-expression-object-javascript.md)|S|S|S|S|S|S|S|  
|[Sintaxe de expressão regular](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)|S|S|S|S|S|S|S|  
|[Sinalizador /y de expressão regular](../../javascript/reference/regular-expression-object-javascript.md)|N|N|N|N|N|Exp.|v8.1: N<br />V10: Exp.|  
|[Método repeat (String)](../../javascript/reference/repeat-method-string-javascript.md)|N|N|N|N|N|S|v8.1: N<br />V10: S|  
|[Método Replace](../../javascript/reference/replace-method-string-javascript.md)|S|S|S|S|S|S|S|  
|[Funções](../../javascript/functions-javascript.md)|N|N|N|N|N|N|v8.1: N<br />V10: S|  
|[Instrução return](../../javascript/reference/return-statement-javascript.md)|S|S|S|S|S|S|S|  
|[Método reverse](../../javascript/reference/reverse-method-javascript.md)|S|S|S|S|S|S|S|  
|[Propriedade rightContext ($')](../../javascript/reference/rightcontext-property-dollar-regexp-javascript.md)|S|S|S|S|S|S|S|  
|[Operador de atribuição de deslocamento para a direita (>>=)](../../javascript/reference/right-shift-assignment-operator-decrement-equal-javascript.md)|S|S|S|S|S|S|S|  
|[Função Round](../../javascript/reference/math-round-function-javascript.md)|S|S|S|S|S|S|S|  
|[Função ScriptEngine](../../javascript/reference/scriptengine-function-javascript.md)|S|S|S|S|S|S|S|  
|[Função ScriptEngineBuildVersion](../../javascript/reference/scriptenginebuildversion-function-javascript.md)|S|S|S|S|S|S|S|  
|[Função ScriptEngineMajorVersion](../../javascript/reference/scriptenginemajorversion-function-javascript.md)|S|S|S|S|S|S|S|  
|[Função ScriptEngineMinorVersion](../../javascript/reference/scriptengineminorversion-function-javascript.md)|S|S|S|S|S|S|S|  
|[Função seal](../../javascript/reference/object-seal-function-javascript.md)|N|N|S|S|S|S|S|  
|[Método Search](../../javascript/reference/search-method-string-javascript.md)|S|S|S|S|S|S|S|  
|[Objeto Set](../../javascript/reference/set-object-javascript.md)|N|N|N|N|S|S|v8: N<br />v8.1: S|  
|[Método setDate](../../javascript/reference/setdate-method-date-javascript.md)|S|S|S|S|S|S|S|  
|[Método setFullYear](../../javascript/reference/setfullyear-method-date-javascript.md)||S|S|S|S|S|S|  
|[Método setHours](../../javascript/reference/sethours-method-date-javascript.md)|S|S|S|S|S|S|S|  
|[Método setMilliseconds](../../javascript/reference/setmilliseconds-method-date-javascript.md)|S|S|S|S|S|S|S|  
|[Método setMinutes](../../javascript/reference/setminutes-method-date-javascript.md)|S|S|S|S|S|S|S|  
|[Método setMonth](../../javascript/reference/setmonth-method-date-javascript.md)|S|S|S|S|S|S|S|  
|[Método setSeconds](../../javascript/reference/setseconds-method-date-javascript.md)|S|S|S|S|S|S|S|  
|[Método setTime](../../javascript/reference/settime-method-date-javascript.md)|S|S|S|S|S|S|S|  
|[Método setUTCDate](../../javascript/reference/setutcdate-method-date-javascript.md)|S|S|S|S|S|S|S|  
|[Método setUTCFullYear](../../javascript/reference/setutcfullyear-method-date-javascript.md)|S|S|S|S|S|S|S|  
|[Método setUTCHours](../../javascript/reference/setutchours-method-date-javascript.md)|S|S|S|S|S|S|S|  
|[Método setUTCMilliseconds](../../javascript/reference/setutcmilliseconds-method-date-javascript.md)|S|S|S|S|S|S|S|  
|[Método setUTCMinutes](../../javascript/reference/setutcminutes-method-date-javascript.md)|S|S|S|S|S|S|S|  
|[Método setUTCMonth](../../javascript/reference/setutcmonth-method-date-javascript.md)|S|S|S|S|S|S|S|  
|[Método setUTCSeconds](../../javascript/reference/setutcseconds-method-date-javascript.md)|S|S|S|S|S|S|S|  
|[Método setYear](../../javascript/reference/setyear-method-date-javascript.md)|S|S|S|S|S|S|S|  
|[Método SHIFT](../../javascript/reference/shift-method-array-javascript.md)|S|S|S|S|S|S|S|  
|[Função Sin](../../javascript/reference/math-sin-function-javascript.md)|S|S|S|S|S|S|S|  
|[Método slice (Array)](../../javascript/reference/slice-method-array-javascript.md)|S|S|S|S|S|S|S|  
|[Método slice (String)](../../javascript/reference/slice-method-string-javascript.md)|S|S|S|S|S|S|S|  
|[Método Small](../../javascript/reference/html-tag-methods-javascript.md)|S|S|S|S|S|S|S|  
|[Método some](../../javascript/reference/some-method-array-javascript.md)|N|N|S|S|S|S|S|  
|[Método Sort](../../javascript/reference/sort-method-array-javascript.md)|S|S|S|S|S|S|S|  
|[Propriedade Source](../../javascript/reference/source-property-regular-expression-javascript.md)|S|S|S|S|S|S|S|  
|[Método splice](../../javascript/reference/splice-method-array-javascript.md)|S|S|S|S|S|S|S|  
|[Método split](../../javascript/reference/split-method-string-javascript.md)|S|S|S|S|S|S|S|  
|[Funções](../../javascript/functions-javascript.md)|N|N|N|N|N|S|v8.1: N<br />V10: S|  
|[Função Sqrt](../../javascript/reference/math-sqrt-function-javascript.md)|S|S|S|S|S|S|S|  
|[SQRT1_2 Constant](../../javascript/reference/math-constants-javascript.md)|S|S|S|S|S|S|S|  
|[Constante SQRT2](../../javascript/reference/math-constants-javascript.md)|S|S|S|S|S|S|S|  
|[Diretiva use strict](../../javascript/reference/use-strict-directive.md)|N|N|N|S|S|S|S|  
|[Método Strike](../../javascript/reference/html-tag-methods-javascript.md)|S|S|S|S|S|S|S|  
|[Objeto String](../../javascript/reference/string-object-javascript.md)|S|S|S|S|S|S|S|  
|[Função JSON.stringify](../../javascript/reference/json-stringify-function-javascript.md)|N|S|S|S|S|S|S|  
|[Método sub](../../javascript/reference/html-tag-methods-javascript.md)|S|S|S|S|S|S|S|  
|[Método substr](../../javascript/reference/substr-method-string-javascript.md)|S|S|S|S|S|S|S|  
|[Método substring](../../javascript/reference/substring-method-string-javascript.md)|S|S|S|S|S|S|S|  
|[Operador de atribuição de subtração (-=)](../../javascript/reference/subtraction-assignment-operator-decrement-equal-javascript.md)|S|S|S|S|S|S|S|  
|[Operador de subtração (-)](../../javascript/reference/subtraction-operator-decrement-javascript.md)|S|S|S|S|S|S|S|  
|[Método sup](../../javascript/reference/html-tag-methods-javascript.md)|S|S|S|S|S|S|S|  
|[Instrução switch](../../javascript/reference/switch-statement-javascript.md)|S|S|S|S|S|S|S|  
|[Objeto Symbol](../../javascript/reference/symbol-object-javascript.md)|N|N|N|N|N|S|v8.1: N<br />V10: S|  
|[Função TAN](../../javascript/reference/math-tan-function-javascript.md)|S|S|S|S|S|S|S|  
|[Cadeias de caracteres de modelo](../../javascript/advanced/template-strings-javascript.md)|N|N|N|N|N|S|v8.1: N<br />V10: S|  
|[Método de teste](../../javascript/reference/test-method-regular-expression-javascript.md)|S|S|S|S|S|S|S|  
|[Instrução this](../../javascript/reference/this-statement-javascript.md)|S|S|S|S|S|S|S|  
|[Instrução throw](../../javascript/reference/throw-statement-javascript.md)|S|S|S|S|S|S|S|  
|[Método toArray](../../javascript/reference/toarray-method-vbarray-javascript.md)|S|S|S|S|S|S|S|  
|[Método toDateString](../../javascript/reference/todatestring-method-date-javascript.md)|S|S|S|S|S|S|S|  
|[Método toExponential](../../javascript/reference/toexponential-method-number-javascript.md)|S|S|S|S|S|S|S|  
|[Método toFixed](../../javascript/reference/tofixed-method-number-javascript.md)|S|S|S|S|S|S|S|  
|[Método toGMTString](../../javascript/reference/togmtstring-method-date-javascript.md)|S|S|S|S|S|S|S|  
|[Método toISOString](../../javascript/reference/toisostring-method-date-javascript.md)|N|N|S|S|S|S|S|  
|[Método toJSON](../../javascript/reference/tojson-method-date-javascript.md)|N|S|S|S|S|S|S|  
|[Método toLocaleDateString](../../javascript/reference/tolocaledatestring-method-date-javascript.md)|S|S|S|S|S|S|S|  
|[Método toLocaleLowercase](../../javascript/reference/tolocalelowercase-method-string-javascript.md)|S|S|S|S|S|S|S|  
|[Método toLocaleString](../../javascript/reference/tolocalestring-method-object-javascript.md)|S|S|S|S|S|S|S|  
|[Método toLocaleTimeString](../../javascript/reference/tolocaletimestring-method-date-javascript.md)|S|S|S|S|S|S|S|  
|[Método toLocaleUppercase](../../javascript/reference/tolocaleuppercase-method-string-javascript.md)|S|S|S|S|S|S|S|  
|[Método toLowerCase](../../javascript/reference/tolowercase-method-javascript.md)|S|S|S|S|S|S|S|  
|[Método toPrecision](../../javascript/reference/toprecision-method-number-javascript.md)|S|S|S|S|S|S|S|  
|[Método toString](../../javascript/reference/tostring-method-object-javascript.md)|S|S|S|S|S|S|S|  
|[Método toTimeString](../../javascript/reference/totimestring-method-date-javascript.md)|S|S|S|S|S|S|S|  
|[Método toUpperCase](../../javascript/reference/touppercase-method-string-javascript.md)|S|S|S|S|S|S|S|  
|[Método toUTCString](../../javascript/reference/toutcstring-method-date-javascript.md)|S|S|S|S|S|S|S|  
|[Método trim](../../javascript/reference/trim-method-string-javascript.md)|N|N|S|S|S|S|S|  
|[Instrução Try](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)|S|S|S|S|S|S|S|  
|[Operador TypeOf](../../javascript/reference/typeof-operator-decrementjavascript.md)|S|S|S|S|S|S|S|  
|[Método UBound](../../javascript/reference/ubound-method-vbarray-javascript.md)|S|S|S|S|S|S|S|  
|[Objeto Uint8Array](../../javascript/reference/uint8array-object.md)|N|N|N|S|S|S|S|  
|[Objeto Uint16Array](../../javascript/reference/uint16array-object.md)|N|N|N|S|S|S|S|  
|[Objeto Uint32Array](../../javascript/reference/uint32array-object.md)|N|N|N|S|S|S|S|  
|[Objeto Uint8ClampedArray](../../javascript/reference/uint8clampedarray-object-javascript.md)|N|N|N|N|S|S|v8: Não<br />v8.1 (Win): Sim<br />v8.1 (Phone): Não<br />V10: S|  
|[Operador unário de negação (-)](../../javascript/reference/subtraction-operator-decrement-javascript.md)|S|S|S|S|S|S|S|  
|[Constante undefined](../../javascript/reference/undefined-constant-javascript.md)|S|S|S|S|S|S|S|  
|[Função unescape](../../javascript/reference/unescape-function-javascript.md)|S|S|S|S|S|S|S|  
|[Caracteres de escape de ponto de código Unicode](../../javascript/advanced/special-characters-javascript.md)|N|N|N|N|N|S|v8.1: N<br />V10: S|  
|[Método unshift](../../javascript/reference/unshift-method-array-javascript.md)|S|S|S|S|S|S|S|  
|[Operador de atribuição de deslocamento para a direita sem sinal (>>>=)](../../javascript/reference/unsigned-right-shift-assignment-operator-decrement-equal-javascript.md)|S|S|S|S|S|S|S|  
|[Operador de deslocamento para a direita sem sinal (>>>)](../../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)|S|S|S|S|S|S|S|  
|[Diretiva use strict](../../javascript/reference/use-strict-directive.md)|N|N|N|S|S|S|S|  
|[Função UTC](../../javascript/reference/date-utc-function-javascript.md)|S|S|S|S|S|S|S|  
|[Método valueOf](../../javascript/reference/valueof-method-object-javascript.md)|S|S|S|S|S|S|S|  
|[Método values (Array)](../../javascript/reference/values-method-array-javascript.md)|N|N|N|N|N|S|v8.1: N<br />V10: S|  
|[Instrução var](../../javascript/reference/var-statement-javascript.md)|S|S|S|S|S|S|S|  
|[Objeto VBArray](../../javascript/reference/vbarray-object-javascript.md)|S|S|S|S|S|S|N|  
|[Operador void](../../javascript/reference/void-operator-decrementjavascript.md)|S|S|S|S|S|S|S|  
|[Objeto WeakMap](../../javascript/reference/weakmap-object-javascript.md)|N|N|N|N|S|S|v8: N<br />v8.1: S|  
|[Objeto WeakSet](../../javascript/reference/weakset-object-javascript.md)|N|N|N|N|N|S|v8.1: N<br />V10: S|  
|[Instrução while](../../javascript/reference/while-statement-javascript.md)|S|S|S|S|S|S|S|  
|[Objeto WinRTError](../../javascript/reference/winrterror-object-javascript.md)|N|N|N|S|S|S|S|  
|[Instrução with](../../javascript/reference/with-statement-javascript.md)|S|S|S|S|S|S|S|  
|[Função Write](../../javascript/reference/debug-write-function-javascript.md)|S|S|S|S|S|S|S|  
|[Função writein](../../javascript/reference/debug-writeln-function-javascript.md)|S|S|S|S|S|S|S|  
  
 \* Oferece suporte a objetos DOM, mas não definido pelo usuário a objetos. Os atributos `enumerable` e `configurable` podem ser especificados, mas não são usados.  
  
## <a name="see-also"></a>Consulte também  
 [Definindo a compatibilidade do documento](http://go.microsoft.com/fwlink/?LinkId=208537)