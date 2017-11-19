---
title: "Objeto de expressão regular (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: RegularExpression_JavaScript
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Regular Expression object
- regular expressions, RegExp object
- RegExp object, overview
ms.assetid: 346aa83e-a045-47ea-acae-b42c7b121534
caps.latest.revision: "21"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: df2d07e3b47e315ec804e5a7f20024dc2184eef0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="regular-expression-object-javascript"></a>Objeto Regular Expression (JavaScript)
Um objeto que contém um padrão de expressão regular com sinalizadores que identificam como aplicar o padrão.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
re = /pattern/[flags]  
```  
  
## <a name="syntax"></a>Sintaxe  
  
```  
re = new RegExp("pattern"[,"flags"])   
```  
  
## <a name="parameters"></a>Parâmetros  
 *Re*  
 Necessário. O nome da variável à qual o padrão de expressão regular é atribuído.  
  
 *padrão*  
 Necessário. O padrão da expressão regular a ser usada. Se você usar a Sintaxe 1, delimite o padrão por caracteres "/". Se usar a Sintaxe 2, coloque o padrão entre aspas.  
  
 `flags`  
 Opcional. Inclua o sinalizador entre aspas se você usar a Sintaxe 2. Os sinalizadores disponíveis, que podem ser combinados, são:  
  
-   g (pesquisa global por todas as ocorrências de *padrão*)  
  
-   i (ignorar maiúsculas e minúsculas)  
  
-   m (pesquisa em várias linhas)  
  
-   u (unicode), habilita EcmaScript 6 [recursos Unicode](../../javascript/advanced/special-characters-javascript.md). Com suporte apenas em [!INCLUDE[jsv12text](../../javascript/includes/jsv12text-md.md)].  
  
-   y (correspondência temporária), procura por correspondências na propriedade `lastIndex` da expressão regular (e não pesquisa nos índices mais adiante). Com suporte em [!INCLUDE[jsv12textExp](../../javascript/includes/jsv12textexp-md.md)].  
  
## <a name="remarks"></a>Comentários  
 O **Expressão Regular** objeto não deve ser confundido com global `RegExp` objeto. Embora pareçam iguais, eles são separados e distintos. As propriedades do **Expressão Regular** objeto contêm apenas informações sobre um determinado **Expressão Regular** instância, enquanto as propriedades do global `RegExp` objeto contém atualizado continuamente informações sobre cada correspondência conforme ela ocorre.  
  
 **Expressão regular** objetos armazenam padrões usados ao pesquisar cadeias de caracteres para combinações de caracteres. Após o **Expressão Regular** objeto é criado, ele é transmitido para um método de cadeia de caracteres ou uma cadeia de caracteres é passada para um dos métodos de expressão regular. Informações sobre a pesquisa mais recente são armazenadas no objeto global `RegExp`.  
  
 Use a Sintaxe 1 quando já conhecer a cadeia de caracteres de pesquisa. Use a Sintaxe 2 quando a cadeia de caracteres de pesquisa mudar com frequência ou for desconhecida, como as cadeias de caracteres provenientes de entradas do usuário.  
  
 O *padrão* argumento é compilado em um formato interno antes do uso. Para a sintaxe 1, *padrão* é compilado conforme o script é carregado. Para a sintaxe 2, *padrão* é compilado logo antes do uso, ou quando o **compilar** método é chamado.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso do **Expressão Regular** objeto por meio da criação de um objeto (re) que contém um padrão de expressão regular com seus sinalizadores associados. Nesse caso, o resultante **Expressão Regular** objeto é usado pelo `match` método:  
  
```JavaScript  
var s = "through the pages of the book";  
  
// Create regular expression pattern.  
var re = new RegExp("the", "i");  
  
// Attempt match on search string.  
var r = s.match(re);     
  
// Return first occurrence of "the".  
if(console && console.log) {  
    console.log(r);  
}  
  
// Output:  
//   
```  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir atualiza o padrão de expressão regular para pesquisar por várias instâncias.  
  
```JavaScript  
// Create regular expression pattern using the i and g flags.  
var re = new RegExp("the", "ig");  
  
// Attempt match on search string.  
var r = s.match(re);     
  
// Return the two occurrences of "the".  
if(console && console.log) {  
    console.log(r.length);  
    console.log(r);  
}  
  
// Output:  
// 2  
// [object Array] ["the", "the"]  
```  
  
## <a name="example"></a>Exemplo  
 Ao usar o sinalizador /y, se uma correspondência for bem-sucedida, ele atualiza `lastindex` para o índice do próximo caractere após a última correspondência. Se a correspondência falhar, ele redefine `lastindex` como 0.  
  
 O exemplo a seguir procura uma correspondência em um índice específico usando o sinalizador /y e a propriedade `lastIndex`.  
  
```JavaScript  
// Create regular expression pattern using the i and y flags.  
var re = new RegExp("the", "iy");  
  
// Set the lastIndex property and attempt a match  
// at the specified index.  
re.lastIndex = 20;  
var r = s.match(re);     
  
// No matches returned.  
if(console && console.log) {  
    console.log(r);  
}  
// Reset the lastIndex property and attempt a match.  
re.lastIndex = 21;  
var r = s.match(re);  
  
// Return occurrence of "the" starting at index 21.  
if(console && console.log) {  
    console.log(r);  
}  
  
// Output:  
// null  
// [object Array] ["the"]  
```  
  
<a name="js56jsobjregexpressionprop"></a>   
## <a name="properties"></a>Propriedades  
 [Propriedade global](../../javascript/reference/global-property-regular-expression-javascript.md) &#124; [propriedade ignoreCase](../../javascript/reference/ignorecase-property-regular-expression-javascript.md) &#124; [propriedade multiline](../../javascript/reference/multiline-property-regular-expression-javascript.md) &#124; [propriedade source](../../javascript/reference/source-property-regular-expression-javascript.md)  
  
<a name="js56jsobjregexpressionmeth"></a>   
## <a name="methods"></a>Métodos  
 [Método Compile](../../javascript/reference/compile-method-regular-expression-javascript.md) &#124; [método exec](../../javascript/reference/exec-method-regular-expression-javascript.md) &#124; [método de teste](../../javascript/reference/test-method-regular-expression-javascript.md)  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 O sinalizador u tem suporte no [!INCLUDE[jsv12text](../../javascript/includes/jsv12text-md.md)].  
  
 O sinalizador y tem suporte no [!INCLUDE[jsv12textExp](../../javascript/includes/jsv12textexp-md.md)].  
  
## <a name="see-also"></a>Consulte também  
 [Objeto RegExp](../../javascript/reference/regexp-object-javascript.md)   
 [Sintaxe de expressão regular (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)   
 [Objeto String](../../javascript/reference/string-object-javascript.md)