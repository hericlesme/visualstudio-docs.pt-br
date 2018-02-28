---
title: "número de propriedade (Error) (JavaScript) | Microsoft Docs"
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
- Number
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Number property
ms.assetid: 8697e20b-a2b0-4e26-85c0-ab07ddfe8281
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bbc229e7d0572e1a3dbed056b344da7ff9ce7292
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="number-property-error-javascript"></a>Propriedade number (erro) (JavaScript)
Retorna ou define o valor numérico associado a um erro específico. O `Error` é de propriedade padrão do objeto **número**.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
object  
.number [= errorNumber]  
```  
  
## <a name="parameters"></a>Parâmetros  
 *Object*  
 Qualquer instância do `Error` objeto.  
  
 *errorNumber*  
 Um inteiro que representa um erro.  
  
## <a name="remarks"></a>Comentários  
 Um número de erro é um valor de 32 bits. A palavra de 16 bits superior é o código de facilidade e a palavra inferior é o código de erro. Para determinar o código de erro, use o `&` (bit a bit e) operador combinar a propriedade de número com o número hexadecimal `0xFFFF`.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir faz com que uma exceção seja gerada e exibe o código de erro que é derivado do número do erro.  
  
```JavaScript  
try  
    {  
    // Cause an error.  
    var x = y;  
    }  
catch(e)  
    {  
    document.write ("Error Code: ");  
    document.write (e.number & 0xFFFF)  
    document.write ("<br />");  
  
    document.write ("Facility Code: ")  
    document.write(e.number>>16 & 0x1FFF)  
    document.write ("<br />");  
  
    document.write ("Error Message: ")  
    document.write (e.message)  
    }  
```  
  
## <a name="example"></a>Exemplo  
 A saída desse código é da seguinte maneira.  
  
```JavaScript  
Error Code: 5009  
Facility Code: 10  
Error Message: 'y' is undefined  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
 **Aplica-se a**: [objeto Error](../../javascript/reference/error-object-javascript.md)  
  
## <a name="see-also"></a>Consulte também  
 [Propriedade Description (erro)](../../javascript/reference/description-property-error-javascript.md)   
 [Propriedade Message (erro)](../../javascript/reference/message-property-error-javascript.md)   
 [Propriedade name (Error)](../../javascript/reference/name-property-error-javascript.md)