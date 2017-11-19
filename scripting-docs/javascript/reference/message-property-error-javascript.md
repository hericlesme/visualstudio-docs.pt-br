---
title: Propriedade Message (erro) (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: message
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: Message property
ms.assetid: 8cab0392-e0db-4714-827c-47ab04e8b4f2
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9dbd2db6c6d31dc48d90c3b07d2388eacf73ae7a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="message-property-error-javascript"></a>Propriedade message (erro) (JavaScript)
Retorna uma cadeia de caracteres de mensagem de erro.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
errorObj.message  
```  
  
## <a name="parameters"></a>Parâmetros  
 `errorObj`  
 Necessário. Instância do `Error` objeto.  
  
## <a name="remarks"></a>Comentários  
 O `message` propriedade retorna uma cadeia de caracteres que contém uma mensagem de erro associada a um erro específico.  
  
 O `description` e `message` propriedades fornecem a mesma funcionalidade. O `description` propriedade com versões anteriores oferece compatibilidade; o `message` propriedade está em conformidade com o padrão ECMA.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir faz com que uma exceção seja lançada TypeError e exibe o nome do erro e sua mensagem.  
  
```JavaScript  
try  
{  
    // Cause an error.  
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
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
 **Aplica-se a**: [objeto Error](../../javascript/reference/error-object-javascript.md)  
  
## <a name="see-also"></a>Consulte também  
 [Propriedade Description (erro)](../../javascript/reference/description-property-error-javascript.md)   
 [Propriedade name (Error)](../../javascript/reference/name-property-error-javascript.md)