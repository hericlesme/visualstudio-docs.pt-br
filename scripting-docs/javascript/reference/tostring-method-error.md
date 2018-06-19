---
title: Método toString (Error) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 5d6d9712-c06d-4b31-9bc9-e46f6bb5cd38
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d774ff8c0f5338f4178b2262bf8ac8cadc074453
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640586"
---
# <a name="tostring-method-error"></a>Método toString (Error)
Retorna uma representação de cadeia de caracteres de erro.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
error.toString()  
```  
  
## <a name="parameters"></a>Parâmetros  
 `date`  
 Necessário. O erro para representar como uma cadeia de caracteres.  
  
## <a name="return-value"></a>Valor de retorno  
 Retorna "Erro:" e a mensagem de erro.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso do `toString` método com um erro.  
  
```JavaScript  
var myError = new Error();  
myError.message = "My Error";  
var errorString = myError.toString();  
document.write(errorString);  
  
// Output: Error: My Error  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]