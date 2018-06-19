---
title: Substitua o método (String) (JavaScript) | Microsoft Docs
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
- replace
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- replacing strings
- Replace method
ms.assetid: 5f0e4765-df4d-4887-bd09-efe5e58251bf
caps.latest.revision: 28
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 82894a5d7f92c8231a6ba3a1948369fb2c819a6d
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2018
ms.locfileid: "27719338"
---
# <a name="replace-method-string-javascript"></a>Método replace (Cadeia de Caracteres) (JavaScript)
Substitui texto em uma cadeia de caracteres usando uma expressão regular ou uma cadeia de caracteres de pesquisa.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
stringObj.replace(rgExp, replaceText)  
```  
  
## <a name="parameters"></a>Parâmetros  
 `stringObj`  
 Necessário. O literal de cadeia de caracteres ou objeto `String` no qual a substituição será feita. Essa cadeia de caracteres não for modificada com o **substituir** método. Em vez disso, o valor retornado desse método é a cadeia de caracteres gerada pela substituição.  
  
 `rgExp`  
 Necessário. Uma instância de um **Expressão Regular** objeto que contém o padrão de expressão regular e os sinalizadores aplicáveis. Também pode ser um literal de cadeia de caracteres ou objeto `String` que representa a expressão regular. Se `rgExp` não é uma instância de um **Expressão Regular** objeto, ele será convertido em uma cadeia de caracteres e uma pesquisa exata será feita para os resultados; não é feita nenhuma tentativa de converter a cadeia de caracteres em uma expressão regular.  
  
 `replaceText`  
 Necessário. Um literal de cadeia de caracteres ou objeto `String` que contém o texto a ser substituído para cada correspondência bem-sucedida de `rgExp` em `stringObj`. No [!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] ou versões posteriores, o argumento `replaceText` também pode ser uma função que retorna o texto de substituição.  
  
## <a name="return-value"></a>Valor de retorno  
 O resultado da **substituir** método é uma cópia de `stringObj` após a conclusão das substituições especificada foram feita.  
  
## <a name="remarks"></a>Comentários  
 Qualquer uma das seguintes variáveis de correspondência pode ser usada para identificar a correspondência mais recente e a cadeia de caracteres na qual ela foi originada. As variáveis de correspondência podem ser usadas na substituição de um texto quando a cadeia de caracteres de substituição precisa ser determinada dinamicamente.  
  
|Caracteres|Significado|  
|----------------|-------------|  
|**$$**|`$` ([!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] ou versões posteriores)|  
|**$&**|Especifica a parte de `stringObj` à qual o padrão inteiro corresponde. ([!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] ou versões posteriores)|  
|`$``|Especifica a parte de `stringObj` que precede a correspondência descrita por  **$&** . ([!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] ou versões posteriores)|  
|`$'`|Especifica a parte de `stringObj` que segue a correspondência descrita por  **$&** . ([!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] ou versões posteriores)|  
|`$`  ***n***|O  *n* th subcorrespondência capturada, onde  *n*  é um único dígito decimal de 1 a 9. ([!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] ou versões posteriores)|  
|`$`  ***nn***|O  *nn* th subcorrespondência capturada, onde  *nn*  é um número decimal com dois dígitos de 01 a 99. ([!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] ou versões posteriores)|  
  
 Se `replaceText` for uma função, para cada subcadeia de caracteres correspondida a função é chamada com os seguintes *m* + 3 argumentos onde *m* é o número de captura parênteses em esquerdo a `rgExp`. O primeiro argumento é a subcadeia de caracteres que foi correspondida. O próximo *m* argumentos são todos as capturas resultantes da pesquisa. Argumento *m* + 2 é o deslocamento dentro `stringObj` onde a correspondência ocorreu e o argumento *m* + 3 é `stringObj`. O resultado é o valor da cadeia de caracteres resultante da substituição de cada subcadeia de caracteres correspondida pelo valor retornado correspondente da chamada de função.  
  
 O **substituir** método atualiza as propriedades de global `RegExp` objeto.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso do **substituir** método para substituir todas as instâncias de "the" por "a".  
  
```JavaScript  
var s = "the batter hit the ball with the bat";  
  
// Replace "the" with "a".  
var re = /the/g;  
var result = s.replace(re, "a");  
document.write(result);  
// Output: a batter hit a ball with a bat  
```  
  
 Além disso, o **substituir** método também pode substituir subexpressões dentro do padrão. O exemplo a seguir troca cada par de palavras na cadeia de caracteres.  
  
```JavaScript  
  
var s = "The quick brown fox jumped over the lazy dog.";  
var re = /(\S+)(\s+)(\S+)/g;  
// Exchange each pair of words.  
var result = s.replace(re, "$3$2$1");  
document.write(result);  
  
// Output:  quick The fox brown over jumped lazy the dog.  
```  
  
 O exemplo a seguir, que funciona no [!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] ou posterior, mostra como usar uma função que retorna o texto de substituição. Ele substitui qualquer instância de um número seguido por “F” por uma conversão em Celsius.  
  
```JavaScript  
function f2c(s1) {  
    // Initialize pattern.  
    var test = /(\d+(\.\d*)?)F\b/g;  
  
    // Use a function for the replacement.  
    var s2 = s1.replace(test,  
      function($0,$1,$2)  
           {   
           return((($1-32) * 5/9) + "C");  
           }  
        )  
    return s2;  
}  
document.write(f2c("Water freezes at 32F and boils at 212F."));  
  
// Output: Water freezes at 0C and boils at 100C.  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Aplica-se a**: [objeto de cadeia de caracteres](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>Consulte também  
 [Método Exec (Expressão Regular)](../../javascript/reference/exec-method-regular-expression-javascript.md)   
 [Método match (String)](../../javascript/reference/match-method-string-javascript.md)   
 [Objeto RegExp](../../javascript/reference/regexp-object-javascript.md)   
 [Método Search (String)](../../javascript/reference/search-method-string-javascript.md)   
 [Método Test (Expressão Regular)](../../javascript/reference/test-method-regular-expression-javascript.md)   
 [Programação de expressão regular (JavaScript)](http://msdn.microsoft.com/en-us/3b62e27c-4f07-4726-a95b-6e841807bfaf)   
 [Alternação e subexpressões (JavaScript)](http://msdn.microsoft.com/en-us/c59dd3e8-7fee-493e-9123-065af1e651ae)   
 [Referências inversas (JavaScript)](http://msdn.microsoft.com/en-us/5d8dbd5a-cd03-4548-850b-9d7bad2c839a)   
 [Arrastar e soltar o aplicativo de exemplo do HTML5](http://code.msdn.microsoft.com/Drag-and-drop-e2701a72)