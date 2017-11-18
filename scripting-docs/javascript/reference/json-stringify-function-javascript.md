---
title: "Função JSON stringify (JavaScript) | Microsoft Docs"
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
helpviewer_keywords: stringify method
ms.assetid: 0fafaf3b-c29b-46dc-b65b-ca223064a1d0
caps.latest.revision: "40"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3539bb003ed20a3ff7586e42466bf7c47165b83f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="jsonstringify-function-javascript"></a>Função JSON.stringify (JavaScript)
Converte um valor de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] em uma cadeia de caracteres JSON (JavaScript Object Notation).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
JSON.stringify(  
value [, replacer] [, space])  
```  
  
## <a name="parameters"></a>Parâmetros  
 `value`  
 Obrigatório. Um valor de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)], geralmente um objeto ou uma matriz, a ser convertido.  
  
 `replacer`  
 Opcional. Uma função ou matriz que transforma os resultados.  
  
 Se `replacer` for uma função, `JSON.stringify` chamará essa função, passando a chave e o valor de cada membro. O valor de retorno é usado em vez do valor original. Se a função retornar `undefined`, o membro será excluído. A chave para o objeto raiz é uma cadeia de caracteres vazia: "".  
  
 Se `replacer` for uma matriz, apenas os membros com valores de chaves nessa matriz serão convertidos. A ordem em que os membros são convertidos é a mesma ordem das chaves na matriz. A matriz `replacer` é ignorada quando o argumento `value` também é uma matriz.  
  
 `space`  
 Opcional. Adiciona recuo, espaço em branco e caracteres de quebra de linha ao texto JSON do valor de retorno para facilitar a sua leitura.  
  
 Se `space` for omitido, o texto do valor de retorno será gerado sem espaços em branco adicionais.  
  
 Se `space` for um número, o texto do valor de retorno será recuado com o número especificado de espaços em branco em cada nível. Se `space` for maior que 10, o texto será recuado em 10 espaços.  
  
 Se `space` for uma cadeia de caracteres não vazia como '\ t', o texto do valor de retorno será recuado com os caracteres na cadeia em cada nível.  
  
 Se `space` for uma cadeia com mais de 10 caracteres, os 10 primeiros caracteres serão usados.  
  
## <a name="return-value"></a>Valor de retorno  
 Uma cadeia de caracteres que contém o texto JSON.  
  
## <a name="exceptions"></a>Exceções  
  
|Exceção|Condição|  
|---------------|---------------|  
|[Argumento substituto inválido](../../javascript/misc/invalid-replacer-argument.md)|O argumento `replacer` não é uma função ou uma matriz.|  
|[Referência circular no argumento de valor não é compatível](../../javascript/misc/circular-reference-in-value-argument-not-supported.md)|O argumento `value` contém uma referência circular.|  
  
## <a name="remarks"></a>Comentários  
 Se `value` possuir um método `toJSON`, a função `JSON.stringify` usará o valor de retorno desse método. Se o valor de retorno do método `toJSON` for `undefined`, o membro não será convertido. Isso permite que um objeto determine sua própria representação JSON.  
  
 Valores que não possuem representações JSON, como `undefined`, não serão convertidos. Em objetos, eles serão ignorados. Em matrizes, eles serão substituídos por nulo.  
  
 Valores de cadeia de caracteres começam e terminam com aspas. Todos os caracteres Unicode podem ser incluídos entre aspas, com exceção dos caracteres que devem ser escapados com o uso de uma barra invertida. Os caracteres a seguir devem ser precedidos por uma barra invertida:  
  
-   Aspas (")  
  
-   Barra invertida (\\)  
  
-   Backspace (b)  
  
-   Formfeed (f)  
  
-   Nova linha (n)  
  
-   Retorno de carro (r)  
  
-   Tabulação horizontal (t)  
  
-   Quatro dígitos hexadecimais (uhhhh)  
  
## <a name="order-of-execution"></a>Ordem de execução  
 Durante o processo de serialização, se um método `toJSON` existir para o argumento `value`, `JSON.stringify` chamará primeiro o método `toJSON`. Se ele não existir, o valor original será usado. Em seguida, se um argumento `replacer` for fornecido, o valor (valor original ou valor de retorno de `toJSON`) será substituído pelo valor de retorno do argumento `replacer`. Por último, espaços em branco serão adicionados ao valor com base no argumento opcional `space` para gerar o texto JSON final.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa `JSON.stringify` para converter o objeto `contact` em um texto JSON. A matriz `memberfilter` é definida de forma que apenas os membros `surname` e `phone` sejam convertidos. O membro `firstname` é omitido.  
  
```JavaScript  
var contact = new Object();  
contact.firstname = "Jesper";  
contact.surname = "Aaberg";  
contact.phone = ["555-0100", "555-0120"];  
  
var memberfilter = new Array();  
memberfilter[0] = "surname";  
memberfilter[1] = "phone";  
var jsonText = JSON.stringify(contact, memberfilter, "\t");  
document.write(jsonText);  
// Output:   
// { "surname": "Aaberg", "phone": [ "555-0100", "555-0120" ] }  
```  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa `JSON.stringify` com uma matriz. A função `replaceToUpper` converte cada cadeia de caracteres da matriz para letras maiúsculas.  
  
```JavaScript  
var continents = new Array();  
continents[0] = "Europe";  
continents[1] = "Asia";  
continents[2] = "Australia";  
continents[3] = "Antarctica";  
continents[4] = "North America";  
continents[5] = "South America";  
continents[6] = "Africa";  
  
var jsonText = JSON.stringify(continents, replaceToUpper);  
  
function replaceToUpper(key, value) {  
    return value.toString().toUpperCase();  
}  
  
//Output:  
// "EUROPE,ASIA,AUSTRALIA,ANTARCTICA,NORTH AMERICA,SOUTH AMERICA,AFRICA"  
  
```  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa o método `toJSON` para converter valores de cadeia de caracteres para letras maiúsculas.  
  
```JavaScript  
var contact = new Object();   
contact.firstname = "Jesper";  
contact.surname = "Aaberg";  
contact.phone = ["555-0100", "555-0120"];  
  
contact.toJSON = function(key)  
 {  
    var replacement = new Object();  
    for (var val in this)  
    {  
        if (typeof (this[val]) === 'string')  
            replacement[val] = this[val].toUpperCase();  
        else  
            replacement[val] = this[val]  
    }  
    return replacement;  
};  
  
var jsonText = JSON.stringify(contact);  
document.write(jsonText);  
  
// Output:  
{"firstname":"JESPER","surname":"AABERG","phone":["555-0100","555-0120"]}  
  
'{"firstname":"JESPER","surname":"AABERG","phone":["555-0100","555-0120"]}'  
*/  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv58](../../javascript/reference/includes/jsv58-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Função JSON. Parse](../../javascript/reference/json-parse-function-javascript.md)   
 [Método toJSON (Data)](../../javascript/reference/tojson-method-date-javascript.md)   
 [Aplicativo de exemplo do leitor de feed (Windows Store)](http://code.msdn.microsoft.com/Feed-reader-sample-99d68cf8)