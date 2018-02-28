---
title: "Método toLocaleLowerCase (String) (JavaScript) | Microsoft Docs"
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
- toLocaleLowerCase
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- toLocaleLowerCase method
ms.assetid: add894d3-d14a-4dbc-a9b9-7ad1d3a2e581
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 642ced387e0d3b4cf763767ec147d6160ed7d36b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="tolocalelowercase-method-string-javascript"></a>Método toLocaleLowerCase (String) (JavaScript)
Converte todos os caracteres alfabéticos em minúsculas, levando em conta a localidade atual do ambiente de host.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
stringVar.toLocaleLowerCase( )  
```  
  
## <a name="remarks"></a>Comentários  
 Obrigatório `stringVar` referência é um `String` literal de cadeia de caracteres ou objeto.  
  
 O `toLocaleLowerCase` método converte os caracteres em uma cadeia de caracteres, levando em conta a localidade atual do ambiente de host. Na maioria dos casos, o resultado é o mesmo que o resultado da `toLowerCase` método. Os resultados diferentes se as regras para um idioma em conflito com os mapeamentos de casos Unicode regulares.  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Aplica-se a**: [objeto de cadeia de caracteres](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>Consulte também  
 [Método toLocaleUpperCase (String)](../../javascript/reference/tolocaleuppercase-method-string-javascript.md)   
 [Método toLowerCase](../../javascript/reference/tolowercase-method-javascript.md)