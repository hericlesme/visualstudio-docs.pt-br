---
title: Matriz de objeto (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: Array
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Array object
- constructor property
ms.assetid: 08e5f552-0797-4b48-8164-609582fc18c9
caps.latest.revision: "27"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a48d0ab5bac9d532e8fe8e356f4ea4df9e377b02
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="array-object-javascript"></a>Objeto Array (JavaScript)
Dá suporte à criação de matrizes de quaisquer tipos de dados.  
  
## <a name="syntax"></a>Sintaxe  
  
```
arrayObj = new Array()  
arrayObj = new Array([size])  
arrayObj = new Array([element0[, element1[, ...[, elementN]]]])  
```  
  
## <a name="parameters"></a>Parâmetros  
 `arrayObj`  
 Obrigatório. O nome da variável à qual o objeto `Array` é atribuído.  
  
 `size`  
 Opcional. O tamanho da matriz. Como as matrizes são baseadas em zero, os elementos criados terão índices de zero a `size` -1.  
  
 `element0,...,elementN`  
 Opcional. Os elementos a serem colocados na matriz. Isso cria uma matriz com  *n*  + 1 elementos e um `length` de  *n*  + 1. Usando esta sintaxe, você precisa fornecer mais de um elemento.  
  
## <a name="remarks"></a>Comentários  
 Após uma matriz ser criada, você pode acessar os elementos individuais da matriz usando a notação []. Observe que as matrizes em [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] são baseadas em zero.  
  
```JavaScript  
var my_array = new Array();  
for (i = 0; i < 10; i++) {  
    my_array[i] = i;  
}  
x = my_array[4];  
document.write(x);  
  
// Output: 4  
```  
  
 Você pode passar um número inteiro de 32 bits sem sinal para o construtor `Array` para especificar o tamanho da matriz. Se o valor for negativo ou não for um inteiro, um erro em tempo de execução ocorrerá. Se você executar o código a seguir, verá este erro no Console.  
  
```JavaScript  
var arr = new Array(10);  
document.write(arr.length);  
  
// Output: 10  
  
// Don't do this  
var arr = new Array(-1);  
arr = new Array(1.50);   
```  
  
 Se um único valor for transmitido para o construtor `Array`, e ele não for um número, a propriedade `length` será definida como 1 e o valor do único elemento se tornará o único argumento transmitido.  
  
```npl  
var arr = new Array("one");  
document.write(arr.length);  
document.write("<br/>");  
document.write(arr[0]);  
  
// Output:  
1  
one  
  
```  
  
 As matrizes do JavaScript são matrizes esparsas, o que significa que nem todos os elementos em uma matriz podem conter dados. Em JavaScript, apenas os elementos que realmente contêm dados existem na matriz. Isso reduz a quantidade de memória usada pela matriz.  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
 Alguns membros nas listas a seguir foram introduzidos em versões posteriores. Para obter mais informações, consulte [informações de versão](../../javascript/reference/javascript-version-information.md) ou a documentação para os membros individuais.  
  
## <a name="properties"></a>Propriedades  
 A tabela a seguir lista as propriedades do objeto `Array`.  
  
|Propriedade|Descrição|  
|--------------|-----------------|  
|[Propriedade Constructor](../../javascript/reference/constructor-property-array.md)|Especifica a função que cria uma matriz.|  
|[Propriedade length (Array)](../../javascript/reference/length-property-array-javascript.md)|Retorna um valor inteiro que é uma unidade maior que o elemento mais alto definido em uma matriz.|  
|[Propriedade prototype](../../javascript/reference/prototype-property-array.md)|Retorna uma referência ao protótipo para uma matriz.|  
  
## <a name="functions"></a>Funções  
 A tabela a seguir descreve a função do objeto `Array`.  
  
|Função|Descrição|  
|--------------|-----------------|  
|[Função array.](../../javascript/reference/array-from-function-array-javascript.md)|Retorna uma matriz de um objeto que pode ser iterado ou semelhante a uma matriz.|  
|[Função Array.isArray](../../javascript/reference/array-isarray-function-javascript.md)|Retorna um valor booliano que indica se um objeto é uma matriz.|  
|[Função array.](../../javascript/reference/array-of-function-array-javascript.md)|Retorna uma matriz dos argumentos passados.|  
  
<a name="js56jsobjarraymeth"></a>   
## <a name="methods"></a>Métodos  
 A tabela a seguir lista os métodos do objeto `Array`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método concat (Array)](../../javascript/reference/concat-method-array-javascript.md)|Retorna uma nova matriz que consiste em uma combinação de duas matrizes.|  
|[Método Entries](../../javascript/reference/entries-method-array-javascript.md)|Retorna um iterador que contém os pares de chave/valor da matriz.|  
|[Método every](../../javascript/reference/every-method-array-javascript.md)|Verifica se uma função de retorno de chamada definida retorna `true` para todos os elementos de uma matriz.|  
|[Método Fill](../../javascript/reference/fill-method-array-javascript.md)|Preenche uma matriz com um valor especificado.|  
|[Método Filter](../../javascript/reference/filter-method-array-javascript.md)|Chama uma função de retorno de chamada definida em cada elemento de uma matriz e retorna uma matriz de valores para a qual a função de retorno de chamada retorna `true`.|  
|[Método findIndex](../../javascript/reference/findindex-method-array-javascript.md)|Retorna um valor de índice para o primeiro elemento da matriz que atende aos critérios de teste especificados em uma função de retorno de chamada.|  
|[Método forEach](../../javascript/reference/foreach-method-array-javascript.md)|Chama uma função de retorno de chamada definida para cada elemento de uma matriz.|  
|[Método hasOwnProperty](../../javascript/reference/hasownproperty-method-object-javascript.md)|Retorna um valor booliano que indica se um objeto tem uma propriedade com o nome especificado.|  
|[Método indexOf (Array)](../../javascript/reference/indexof-method-array-javascript.md)|Retorna o índice da primeira ocorrência de um valor em uma matriz.|  
|[Método isPrototypeOf](../../javascript/reference/isprototypeof-method-object-javascript.md)|Retorna um valor booliano que indica se um objeto existe na cadeia de protótipo de outro objeto.|  
|[Método join](../../javascript/reference/join-method-array-javascript.md)|Retorna um objeto `String` que consiste em todos os elementos de uma matriz concatenada.|  
|[Método Keys](../../javascript/reference/keys-method-array-javascript.md)|Retorna um iterador que contém os valores de índice da matriz.|  
|[Método lastIndexOf (Array)](../../javascript/reference/lastindexof-method-array-javascript.md)|Retorna o índice da última ocorrência de um valor especificado em uma matriz.|  
|[Método Map](../../javascript/reference/map-method-array-javascript.md)|Chama uma função de retorno de chamada definida em cada elemento de uma matriz e retorna uma matriz que contém os resultados.|  
|[Método pop](../../javascript/reference/pop-method-array-javascript.md)|Remove o último elemento de uma matriz e o retorna.|  
|[Método propertyIsEnumerable](../../javascript/reference/propertyisenumerable-method-object-javascript.md)|Retorna um valor booliano que indica se uma propriedade especificada faz parte de um objeto e se ela é enumerável.|  
|[Método push](../../javascript/reference/push-method-array-javascript.md)|Acrescenta novos elementos a uma matriz e retorna o novo comprimento dessa matriz.|  
|[Método reduce](../../javascript/reference/reduce-method-array-javascript.md)|Acumula um único resultado ao chamar uma função de retorno de chamada definida para todos os elementos de uma matriz. O valor retornado da função de retorno de chamada é o resultado acumulado e é fornecido como um argumento na próxima chamada para a função de retorno de chamada.|  
|[Método reduceRight](../../javascript/reference/reduceright-method-array-javascript.md)|Acumula um único resultado ao chamar uma função de retorno de chamada definida para todos os elementos de uma matriz, em ordem decrescente. O valor retornado da função de retorno de chamada é o resultado acumulado e é fornecido como um argumento na próxima chamada para a função de retorno de chamada.|  
|[Método reverse](../../javascript/reference/reverse-method-javascript.md)|Retorna um objeto `Array` com os elementos invertidos.|  
|[Método SHIFT](../../javascript/reference/shift-method-array-javascript.md)|Remove o primeiro elemento de uma matriz e o retorna.|  
|[Método slice (Array)](../../javascript/reference/slice-method-array-javascript.md)|Retorna uma seção de uma matriz.|  
|[Método some](../../javascript/reference/some-method-array-javascript.md)|Verifica se uma função de retorno de chamada definida retorna `true` para qualquer elemento de uma matriz.|  
|[Método Sort](../../javascript/reference/sort-method-array-javascript.md)|Retorna um objeto `Array` com os elementos classificados.|  
|[Método splice](../../javascript/reference/splice-method-array-javascript.md)|Remove elementos de uma matriz e, se necessário, insere novos elementos em seu local, retornando os elementos excluídos.|  
|[Método toLocaleString](../../javascript/reference/tolocalestring-method-object-javascript.md)|Retorna uma cadeia de caracteres usando a localidade atual.|  
|[Método toString](../../javascript/reference/tostring-method-array.md)|Retorna uma representação em cadeia de caracteres de uma matriz.|  
|[Método unshift](../../javascript/reference/unshift-method-array-javascript.md)|Insere novos elementos no início de uma matriz.|  
|[Método valueOf](../../javascript/reference/valueof-method-array.md)|Obtém uma referência para a matriz.|  
|[Método Values](../../javascript/reference/values-method-array-javascript.md)|Retorna um iterador que contém os valores da matriz.|  
  
## <a name="see-also"></a>Consulte também  
 [Aplicativo de exemplo de rolagem, movimento panorâmico e zoom](http://code.msdn.microsoft.com/ie/Scrolling-panning-and-6834aaf9)