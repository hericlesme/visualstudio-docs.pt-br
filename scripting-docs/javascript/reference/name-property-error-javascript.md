---
title: Propriedade Name (erro) (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: name
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Name property
- name property, error name
ms.assetid: 94df2d6b-f1a1-4931-a956-0a930cb87f76
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1a12157b4c467499fab23f7c4cb1be91e9ac5440
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="name-property-error-javascript"></a>Propriedade name (erro) (JavaScript)
Retorna o nome de um erro.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
errorObj.  
name  
  
```  
  
## <a name="parameters"></a>Parâmetros  
 `errorObj`  
 Necessário. Instância do `Error` objeto.  
  
## <a name="remarks"></a>Comentários  
 O **nome** propriedade retorna o tipo de exceção ou o nome de um erro. Quando ocorre um erro de tempo de execução, a propriedade name é definida para um dos seguintes tipos de exceção nativo:  
  
|Tipo de exceção|Significado|  
|--------------------|-------------|  
|ConversionError|Este erro ocorre quando há uma tentativa de converter um objeto em algo para que ele não pode ser convertido.|  
|RangeError|Esse erro ocorre quando uma função é fornecida com um argumento que tenha excedido seu intervalo permitido. Por exemplo, esse erro ocorre se você tenta construir um `Array` objeto com um comprimento que não é um inteiro positivo válido.|  
|ReferenceError|Esse erro ocorre quando uma referência inválida foi detectada. Este erro ocorrerá, por exemplo, se uma referência esperada for `null`.|  
|RegExpError|Esse erro ocorre quando ocorre um erro de compilação com uma expressão regular. Depois que a expressão regular é compilada, no entanto, esse erro não pode ocorrer. Este exemplo ocorrerá, por exemplo, quando uma expressão regular é declarada com um padrão que tem uma sintaxe inválida ou sinalizadores que **,**, **g**, ou **m**, ou se ele contém o mesmo sinalizador mais de uma vez.|  
|SyntaxError|Esse erro ocorre quando o texto de origem é analisado e esse texto de origem não segue a sintaxe correta. Este erro ocorrerá, por exemplo, se o `eval` função é chamada com um argumento que não é um texto de programa válido.|  
|TypeError|Este erro ocorre quando o tipo real de um operando não corresponde ao tipo esperado. Um exemplo de quando esse erro ocorre é uma chamada de função feita em algo que não é um objeto ou não dá suporte a chamada.|  
|URIError|Esse erro ocorre quando um ilegal indicador URI (Uniform Resource) é detectado. Por exemplo, este é o erro ocorre quando um caractere ilegal é encontrado em uma cadeia de caracteres que está sendo codificada ou decodificada.|  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir faz com que uma exceção seja lançada TypeError e exibe o nome do erro e sua mensagem.  
  
```JavaScript  
try  
{  
    var x = y;  
}  
catch(e)  
{  
    document.write ("Error Message: " + e.message);  
    document.write ("<br />");  
    document.write ("Error Code: ");  
    document.write (e.number & 0xFFFF)  
    document.write ("<br />");  
    document.write ("Error Name: " + e.name);  
}  
```  
  
## <a name="example"></a>Exemplo  
 A saída desse código é da seguinte maneira.  
  
```JavaScript  
Error Message: 'y' is undefined  
Error Code: 5009  
Error Name: TypeError  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Aplica-se a**: [objeto Error](../../javascript/reference/error-object-javascript.md)  
  
## <a name="see-also"></a>Consulte também  
 [Propriedade Description (erro)](../../javascript/reference/description-property-error-javascript.md)   
 [Propriedade Message (erro)](../../javascript/reference/message-property-error-javascript.md)   
 [Propriedade number (Error)](../../javascript/reference/number-property-error-javascript.md)