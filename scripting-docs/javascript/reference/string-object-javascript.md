---
title: Cadeia de caracteres (JavaScript) do objeto | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: String_JavaScript
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- String object
- String object, overview
ms.assetid: 8063ecd5-5778-4e87-b985-b21420171914
caps.latest.revision: "32"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d58f567bb301b29324fee8ed75fc95fd1a4791ea
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="string-object-javascript"></a>Objeto String (JavaScript)
Permite a manipulação e a formatação de cadeias de caracteres de texto, bem como a determinação e a localização de subcadeias de caracteres dentro de cadeias de caracteres.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
newString = new String(["stringLiteral"])  
```  
  
## <a name="parameters"></a>Parâmetros  
 `newString`  
 Obrigatório. O nome da variável à qual o objeto `String` é atribuído.  
  
 `stringLiteral`  
 Opcional. Qualquer grupo de caracteres Unicode.  
  
## <a name="remarks"></a>Comentários  
 O [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] fornece sequências de escape que você pode incluir em cadeias de caracteres para criar caracteres que não podem ser digitados diretamente. Por exemplo, `\t` especifica um caractere de tabulação. Para obter mais informações, consulte [Caracteres especiais](../../javascript/advanced/special-characters-javascript.md).  
  
## <a name="string-literals"></a>Literais da Cadeia de Caracteres  
 Um *literal de cadeia de caracteres* é zero ou mais caracteres entre aspas simples ou duplas. Um literal de cadeia de caracteres tem um tipo de dados primário (primitivo) `string`. Um *o objeto de cadeia de caracteres* é criado usando o [novo operador](../../javascript/reference/new-operator-decrementjavascript.md), e tem um tipo de dados `Object`.  
  
 O exemplo a seguir mostra que o tipo de dados de um literal de cadeia de caracteres não é o mesmo de um objeto `String`.  
  
```JavaScript  
var strLit = "This is a string literal.";  
var strObj = new String("This is a string object.");  
  
document.write(typeof strLit);  
document.write("<br/>");  
document.write(typeof strObj);  
// Output:  
// string  
// object  
```  
  
## <a name="methods-for-string-literals"></a>Métodos para Literais da Cadeia de Caracteres  
 Quando você chama um método em um literal de cadeia de caracteres, ele é convertido temporariamente em um objeto wrapper de cadeia de caracteres. O literal de cadeia de caracteres é tratado como se o operador `new` tivesse sido usado para criá-lo.  
  
 O exemplo a seguir aplica o método `toUpperCase` a um literal de cadeia de caracteres.  
  
```JavaScript  
var strLit = "This is a string literal.";  
  
var result1 = strLit.toUpperCase();  
  
var result2 = (new String(strLit)).toUpperCase();  
  
document.write(result1);  
document.write("<br/>");  
document.write(result2);  
// Output:   
// THIS IS A STRING LITERAL.  
// THIS IS A STRING LITERAL.  
```  
  
## <a name="accessing-an-individual-character"></a>Acessando um Caractere Individual  
 Você pode acessar um caractere individual de uma cadeia de caracteres como uma propriedade indexada de matrizes somente leitura. Esse recurso foi introduzido no [!INCLUDE[jsv9text](../../javascript/includes/jsv9text-md.md)]. O exemplo a seguir acessa caracteres de cadeia de caracteres individuais.  
  
```JavaScript  
var str = "abcd";  
var result = str[2];  
document.write (result);  
// Output: c  
  
var result = "the"[0];  
document.write(result);  
// Output: t  
```  
  
## <a name="requirements"></a>Requisitos  
 O `String Object` foi introduzido no [!INCLUDE[jsv1text](../../javascript/reference/includes/jsv1text-md.md)]. Alguns membros nas listas a seguir foram introduzidos em versões posteriores.  
  
<a name="js56jsobjstringprop"></a>   
## <a name="properties"></a>Propriedades  
 A tabela a seguir lista as propriedades do objeto `String`.  
  
|Propriedade|Descrição|  
|--------------|-----------------|  
|[Propriedade Constructor](../../javascript/reference/constructor-property-string.md)|Especifica a função que cria um objeto.|  
|[Propriedade length (String)](../../javascript/reference/length-property-string-javascript.md)|Retorna o comprimento de um objeto `String`.|  
|[Propriedade prototype](../../javascript/reference/prototype-property-string.md)|Retorna uma referência ao protótipo para uma classe de objetos.|  
  
## <a name="functions"></a>Funções  
 A tabela a seguir lista as funções do objeto `String`.  
  
|Função|Descrição|  
|--------------|-----------------|  
|[Função String.fromCharCode](../../javascript/reference/string-fromcharcode-function-javascript.md)|Retorna uma cadeia de caracteres de um número de valores de caracteres Unicode.|  
|[Função String.fromCodePoint](../../javascript/reference/string-fromcodepoint-function-javascript.md)|Retorna a cadeia de caracteres associada a um ponto de código Unicode UTF-16.|  
|[Função String.raw](../../javascript/reference/string-raw-function-javascript.md)|Retorna o formulário de cadeia de caracteres bruta de uma cadeia de caracteres de modelo.|  
  
<a name="js56jsobjstringmeth"></a>   
## <a name="methods"></a>Métodos  
 A tabela a seguir lista os métodos do objeto `String`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método Anchor](../../javascript/reference/html-tag-methods-javascript.md)|Insere uma âncora HTML que tem um atributo NAME ao redor do texto.|  
|[Método big](../../javascript/reference/html-tag-methods-javascript.md)|Coloca o HTML \<BIG > marcas ao redor do texto.|  
|[Método BLINK](../../javascript/reference/html-tag-methods-javascript.md)|Coloca o HTML \<BLINK > marcas ao redor do texto.|  
|[Método Bold](../../javascript/reference/html-tag-methods-javascript.md)|Coloca o HTML \<B > marcas ao redor do texto.|  
|[Método charAt](../../javascript/reference/charat-method-string-javascript.md)|Retorna o caractere no índice especificado.|  
|[Método charCodeAt](../../javascript/reference/charcodeat-method-string-javascript.md)|Retorna a codificação Unicode do caractere especificado.|  
|[Método codePointAt](../../javascript/reference/codepointat-method-string-javascript.md)|Retorna o ponto de código de um caractere Unicode UTF-16.|  
|[Método concat (String)](../../javascript/reference/concat-method-string-javascript.md)|Retorna uma cadeia de caracteres que contém a concatenação de duas cadeias de caracteres fornecidas.|  
|[Método endsWith](../../javascript/reference/endswith-method-string-javascript.md)|Retorna um valor booliano que indica se a cadeia de caracteres ou cadeia secundária termina com a cadeia transmitida.|  
|[Método Includes](../../javascript/reference/includes-method-string-javascript.md)|Retorna um valor booliano que indica se a cadeia de caracteres transmitida está contida no objeto de cadeia de caracteres.|  
|[Método Fixed](../../javascript/reference/html-tag-methods-javascript.md)|Coloca o HTML \<TT > marcas ao redor do texto.|  
|[Método FontColor](../../javascript/reference/html-tag-methods-javascript.md)|Coloca o HTML \<fonte > marcas com um atributo COLOR ao redor do texto.|  
|[Método FontSize](../../javascript/reference/html-tag-methods-javascript.md)|Coloca o HTML \<fonte > marcas com um atributo SIZE ao redor do texto.|  
|[Método hasOwnProperty](../../javascript/reference/hasownproperty-method-object-javascript.md)|Retorna um valor booliano que indica se um objeto tem uma propriedade com o nome especificado.|  
|[Método indexOf (String)](../../javascript/reference/indexof-method-string-javascript.md)|Retorna a posição do caractere em que a primeira ocorrência de uma subcadeia de caracteres ocorre dentro de uma cadeia de caracteres.|  
|[Método isPrototypeOf](../../javascript/reference/isprototypeof-method-object-javascript.md)|Retorna um valor booliano que indica se um objeto existe na cadeia de protótipo de outro objeto.|  
|[Método italics](../../javascript/reference/html-tag-methods-javascript.md)|Coloca o HTML \<I > marcas ao redor do texto.|  
|[Método lastIndexOf (String)](../../javascript/reference/lastindexof-method-string-javascript.md)|Retorna à última ocorrência de uma subcadeia de caracteres dentro de uma cadeia de caracteres.|  
|[Método link](../../javascript/reference/html-tag-methods-javascript.md)|Insere uma âncora HTML que tem um atributo HREF ao redor do texto.|  
|[Método localeCompare](../../javascript/reference/localecompare-method-string-javascript.md)|Retorna um valor que indica se duas cadeias de caracteres são equivalentes na localidade atual.|  
|[Método match](../../javascript/reference/match-method-string-javascript.md)|Pesquisa uma cadeia de caracteres usando um fornecido **Expressão Regular** de objeto e retorna os resultados como uma matriz.|  
|[Método normalizar](../../javascript/reference/normalize-method-string-javascript.md)|Retorna o Formulário de Normalização Unicode de uma cadeia de caracteres especificada.|  
|[Método propertyIsEnumerable](../../javascript/reference/propertyisenumerable-method-object-javascript.md)|Retorna um valor booliano que indica se uma propriedade especificada faz parte de um objeto e se ela é enumerável.|  
|[Método Repeat](../../javascript/reference/repeat-method-string-javascript.md)|Retorna que um novo objeto de cadeia de caracteres com um valor igual à cadeia de caracteres original repetido o número de vezes especificado.|  
|[Método Replace](../../javascript/reference/replace-method-string-javascript.md)|Usa uma expressão regular para substituir o texto em uma cadeia de caracteres e retorna o resultado.|  
|[Método Search](../../javascript/reference/search-method-string-javascript.md)|Retorna a posição da primeira correspondência de subcadeia de caracteres em uma pesquisa de expressão regular.|  
|[Método slice (String)](../../javascript/reference/slice-method-string-javascript.md)|Retorna uma seção de uma cadeia de caracteres.|  
|[Método Small](../../javascript/reference/html-tag-methods-javascript.md)|Coloca o HTML \<pequeno > marcas ao redor do texto.|  
|[Método split](../../javascript/reference/split-method-string-javascript.md)|Retorna a matriz de cadeias de caracteres que é gerada quando uma cadeia de caracteres é separada em subcadeias de caracteres.|  
|[Método startsWith](../../javascript/reference/startswith-method-string-javascript.md)|Retorna um valor booliano que indica se a cadeia de caracteres ou cadeia secundária começa com a cadeia transmitida.|  
|[Método Strike](../../javascript/reference/html-tag-methods-javascript.md)|Coloca o HTML \<STRIKE > marcas ao redor do texto.|  
|[Método sub](../../javascript/reference/html-tag-methods-javascript.md)|Coloca o HTML \<SUB > marcas ao redor do texto.|  
|[Método substr](../../javascript/reference/substr-method-string-javascript.md)|Retorna uma subcadeia de caracteres que começa em um local especificado e tem um comprimento especificado.|  
|[Método substring](../../javascript/reference/substring-method-string-javascript.md)|Retorna a subcadeia de caracteres em um local especificado dentro de objeto `String`.|  
|[Método sup](../../javascript/reference/html-tag-methods-javascript.md)|Coloca o HTML \<SUP > marcas ao redor do texto.|  
|[Método toLocaleLowerCase](../../javascript/reference/tolocalelowercase-method-string-javascript.md)|Retorna uma cadeia de caracteres na qual todos os caracteres alfabéticos são convertidos em minúsculas, sempre levando em conta a localidade atual do ambiente de host.|  
|[Método toLocaleString](../../javascript/reference/tolocalestring-method-object-javascript.md)|Retorna um objeto convertido em uma cadeia de caracteres usando a localidade atual.|  
|[Método toLocaleUpperCase](../../javascript/reference/tolocaleuppercase-method-string-javascript.md)|Retorna uma cadeia de caracteres na qual todos os caracteres alfabéticos são convertidos em maiúsculas, sempre levando em conta a localidade atual do ambiente de host.|  
|[Método toLowerCase](../../javascript/reference/tolowercase-method-javascript.md)|Retorna uma cadeia de caracteres na qual todos os caracteres alfabéticos são convertidos em minúsculas.|  
|[Método toString](../../javascript/reference/tostring-method-string-1.md)|Retorna a cadeia de caracteres.|  
|[Método toUpperCase](../../javascript/reference/touppercase-method-string-javascript.md)|Retorna uma cadeia de caracteres na qual todos os caracteres alfabéticos são convertidos em maiúsculas.|  
|[Método trim](../../javascript/reference/trim-method-string-javascript.md)|Retorna uma cadeia de caracteres em que os caracteres de espaço à direita e à esquerda da cadeia e os caracteres terminadores de linha foram removidos.|  
|[Método valueOf](../../javascript/reference/valueof-method-string.md)|Retorna a cadeia de caracteres.|  
  
## <a name="see-also"></a>Consulte também  
 [Operador new](../../javascript/reference/new-operator-decrementjavascript.md)   
 [Aplicativo de exemplo de rolagem, movimento panorâmico e zoom](http://code.msdn.microsoft.com/ie/Scrolling-panning-and-6834aaf9)