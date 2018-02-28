---
title: "Método toString (Object) (JavaScript) | Microsoft Docs"
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
- toString
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- ToString method
ms.assetid: c4ae9da2-60c9-486f-b00a-9df03fda4a35
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 518f988486bb527220884052768e61d099dbd716
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="tostring-method-object-javascript"></a>Método toString (Object) (JavaScript)
Retorna uma representação em cadeia de caracteres de um objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
objectname.toString([radix])  
```  
  
## <a name="parameters"></a>Parâmetros  
 `objectname`  
 Necessário. Um objeto para o qual uma representação de cadeia de caracteres é procurada.  
  
 `radix`  
 Opcional. Especifica uma base para converter valores numéricos em cadeias de caracteres. Esse valor é usado apenas para números.  
  
## <a name="remarks"></a>Comentários  
 O **toString** método é um membro de todos os internos [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] objetos. Como ele se comporta depende do tipo de objeto:  
  
|Objeto|Comportamento|  
|------------|--------------|  
|Matriz|Elementos de um `Array` são convertidos em cadeias de caracteres. As cadeias de caracteres resultantes são concatenadas, separados por vírgulas.|  
|Boolean|Se o valor booliano é **true**, retorna "`true`". Caso contrário, retornará "`false`".|  
|Date|Retorna a representação textual da data.|  
|Erro|Retorna uma cadeia de caracteres que contém a mensagem de erro associada.|  
|Função|Retorna uma cadeia de caracteres do formulário a seguir, onde *functionname* é o nome da função cujo **toString** método foi chamado:<br /><br /> `function functionname( ) { [native code] }`|  
|Número|Retorna a representação textual do número.|  
|Cadeia de caracteres|Retorna o valor da `String` objeto.|  
|Padrão|Retorna `"[object objectname]"`, onde `objectname` é o nome do tipo de objeto.|  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso do **toString** método com um argumento de base. O valor de retorno da função mostrado abaixo é uma tabela de conversão de base.  
  
```JavaScript  
function CreateRadixTable (){  
   var s = "";  
  
   // Create table heading.  
   s += "Hex  Dec  Bin \n";  
  
   for (x = 0; x < 16; x++)  
   {  
      s += "   ";  
  
      // Convert to hexidecimal.  
      s += x.toString(16);  
      s += "     ";  
      if (x < 10) s += "  ";  
  
      // Convert to decimal.  
      s += x.toString(10);  
      s += "     ";  
  
      // Convert to binary.  
      s += x.toString(2);  
      s += "\n";  
   }  
  
   return(s);  
}  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
 **Aplica-se a**: [objeto de matriz](../../javascript/reference/array-object-javascript.md)&#124; [Objeto booliano](../../javascript/reference/boolean-object-javascript.md)&#124; [Data objeto](../../javascript/reference/date-object-javascript.md)&#124; [Erro objeto](../../javascript/reference/error-object-javascript.md)&#124; [Objeto de função](../../javascript/reference/function-object-javascript.md)&#124; [Número objeto](../../javascript/reference/number-object-javascript.md)&#124; [Objeto Object](../../javascript/reference/object-object-javascript.md)&#124; [Objeto de cadeia de caracteres](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Function](../../javascript/reference/function-statement-javascript.md)