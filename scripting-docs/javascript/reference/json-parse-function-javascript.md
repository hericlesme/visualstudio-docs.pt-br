---
title: "Função JSON Parse (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: JSON.parse
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- parse JSON method
- JSON.parse method
ms.assetid: 20f00d31-5ab5-4c3c-ab49-2534fc39a9b4
caps.latest.revision: "41"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3d66aee32a191c8cc1879c9436788c196c05e7bd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="jsonparse-function-javascript"></a>Função JSON.parse (JavaScript)
Converte uma cadeia de caracteres JSON (JavaScript Object Notation) em um objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
JSON.parse(text [, reviver])  
```  
  
## <a name="parameters"></a>Parâmetros  
 `text`  
 Obrigatório. Uma cadeia de caracteres JSON válida.  
  
 `reviver`  
 Opcional. Uma função que transforma os resultados. Essa função é chamada para cada membro do objeto. Se um membro contiver objetos aninhados, esses serão transformados antes do objeto pai. Para cada membro, ocorre o seguinte:  
  
-   Se `reviver` retorna um valor válido, o valor do membro é substituído pelo valor transformado.  
  
-   Se `reviver` retorna o mesmo valor que recebeu, o valor do membro não é modificado.  
  
-   Se `reviver` retorna `null` ou `undefined`, o membro é excluído.  
  
## <a name="return-value"></a>Valor de retorno  
 Um objeto ou uma matriz.  
  
## <a name="exceptions"></a>Exceções  
 Se essa função provoca um erro do analisador [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] (como "SCRIPT1014: caractere inválido"), o texto de entrada não está em conformidade com a sintaxe JSON. Para corrigir o erro, siga um destes procedimentos:  
  
-   Modifique o argumento `text` de forma que ele atenda à sintaxe JSON. Para obter mais informações, consulte o [notação de sintaxe BNF](http://go.microsoft.com/fwlink/?LinkId=125203) de objetos JSON.  
  
     Por exemplo, se a resposta estiver no formato JSONP em vez de JSON puro, experimente este código no objeto de resposta:  
  
    ```JavaScript  
    var fixedResponse = response.responseText.replace(/\\'/g, "'");  
    var jsonObj = JSON.parse(fixedResponse);  
    ```  
  
-   Certifique-se de que o argumento de `text` tenha sido serializado por uma implementação compatível com JSON, como `JSON.stringify`.  
  
-   Execute o `text` argumento em um validador JSON como [JSLint](http://www.jslint.com/) para ajudar a identificar erros de sintaxe.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa `JSON.parse` para converter uma cadeia de caracteres JSON em um objeto.  
  
```JavaScript  
var jsontext = '{"firstname":"Jesper","surname":"Aaberg","phone":["555-0100","555-0120"]}';  
var contact = JSON.parse(jsontext);  
document.write(contact.surname + ", " + contact.firstname);  
document.write(contact.phone[1]);  
// Output:  
// Aaberg, Jesper  
// 555-0100  
```  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir converte uma matriz em uma cadeia de caracteres JSON usando `JSON.stringify` e, em seguida, converte a cadeia de caracteres de volta para uma matriz usando `JSON.parse`.  
  
```JavaScript  
var arr = ["a", "b", "c"];  
var str = JSON.stringify(arr);  
document.write(str);  
document.write ("<br/>");  
  
var newArr = JSON.parse(str);  
  
while (newArr.length > 0) {  
    document.write(newArr.pop() + "<br/>");  
}  
  
// Output:  
// ["a","b","c"]  
// c  
// b  
// a  
```  
  
## <a name="example"></a>Exemplo  
 A função `reviver` é geralmente usada para transformar a representação JSON de cadeias de caracteres de data no formato ISO (International Organization for Standardization) em objetos `Date` no formato UTC (Horário Coordenado Universal). Este exemplo usa `JSON.parse` para desserializar uma cadeia de caracteres de data com formatação ISO. A função `dateReviver` retorna objetos `Date` para os membros que são formatados como cadeias de caracteres de data ISO.  
  
```JavaScript  
var jsontext = '{ "hiredate": "2008-01-01T12:00:00Z", "birthdate": "2008-12-25T12:00:00Z" }';  
var dates = JSON.parse(jsontext, dateReviver);  
document.write(dates.birthdate.toUTCString());  
  
function dateReviver(key, value) {  
    var a;  
    if (typeof value === 'string') {  
        a = /^(\d{4})-(\d{2})-(\d{2})T(\d{2}):(\d{2}):(\d{2}(?:\.\d*)?)Z$/.exec(value);  
        if (a) {  
            return new Date(Date.UTC(+a[1], +a[2] - 1, +a[3], +a[4],  
                            +a[5], +a[6]));  
        }  
    }  
    return value;  
};  
  
// Output:  
// Thu, 25 Dec 2008 12:00:00 UTC  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv58](../../javascript/reference/includes/jsv58-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Função JSON. stringify](../../javascript/reference/json-stringify-function-javascript.md)   
 [Método toJSON (Data)](../../javascript/reference/tojson-method-date-javascript.md)   
 [Aplicativo de exemplo do modelo hub (Windows Store)](http://code.msdn.microsoft.com/Hub-template-sample-with-4b70002d)