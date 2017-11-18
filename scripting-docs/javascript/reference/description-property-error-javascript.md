---
title: Propriedade Description (erro) (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: Description
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- error handling, error description
- Description property
- errors, description
ms.assetid: ea727f1e-2041-4400-965c-67e6d47a1ff0
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6135951fdf65698ed48b9bbacdcc55c1aac22d41
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="description-property-error-javascript"></a>Propriedade description (erro) (JavaScript)
Retorna ou define a cadeia de caracteres descritiva associada a um erro específico.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
object  
.description [= stringExpression]  
```  
  
## <a name="parameters"></a>Parâmetros  
 *object*  
 Necessário. Qualquer instância de um `Error` objeto.  
  
 `stringExpression`  
 Opcional. Uma expressão de cadeia de caracteres que contém uma descrição do erro.  
  
## <a name="remarks"></a>Comentários  
 O **descrição** propriedade contém a cadeia de caracteres de mensagem de erro associada a um erro específico. Use o valor contido na propriedade para alertar um usuário a um erro.  
  
 O **descrição** e **mensagem** propriedades fornecem a mesma funcionalidade; o **descrição** propriedade fornece compatibilidade com versões anteriores; o  **mensagem** propriedade está em conformidade com o padrão ECMA.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso do **descrição** propriedade.  
  
```JavaScript  
try  
{  
// Cause an error:  
    x = y     
}  
catch(e)  
{  
// Prints "[object Error]":  
    document.write(e)  
    document.write (" ");  
// Prints 5009:  
    document.write((e.number & 0xFFFF))    
    document.write (" ");  
// Prints "'y' is undefined":  
    document.write(e.description);  
    document.write (" ");  
// Prints "'y' is undefined":  
    document.write(e.message)  
}  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
 **Aplica-se a**: [objeto Error](../../javascript/reference/error-object-javascript.md)  
  
## <a name="see-also"></a>Consulte também  
 [Propriedade Number (erro)](../../javascript/reference/number-property-error-javascript.md)   
 [Propriedade Message (erro)](../../javascript/reference/message-property-error-javascript.md)   
 [Propriedade name (Error)](../../javascript/reference/name-property-error-javascript.md)