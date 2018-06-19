---
title: Método valueOf (Object) (JavaScript) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- valueOf
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- valueOf method
ms.assetid: c555e38b-f451-4341-8fcd-4c8b02906a2c
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 677b56fd6fc142ce175b130d2f83291c1ac9535f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641626"
---
# <a name="valueof-method-object-javascript"></a>Método valueOf (Object) (JavaScript)
Retorna o valor primitivo do objeto especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
object.valueOf( )  
```  
  
## <a name="remarks"></a>Comentários  
 Obrigatório `object` referência é qualquer intrínseca [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] objeto.  
  
 O `valueOf` método é definido de forma diferente para cada intrínseco [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] objeto.  
  
|Objeto|Valor de retorno|  
|------------|------------------|  
|Matriz|Retorna a instância de matriz.|  
|Boolean|O valor booliano.|  
|Date|O valor de hora armazenado em milissegundos desde a meia-noite de 1º de janeiro de 1970 UTC.|  
|Função|A função em si.|  
|Número|O valor numérico.|  
|Objeto|O próprio objeto. Esse é o padrão.|  
|Cadeia de caracteres|O valor da cadeia de caracteres.|  
  
 O **matemática** e `Error` objetos não tiverem um `valueOf` método.  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
 **Aplica-se a**: [objeto de matriz](../../javascript/reference/array-object-javascript.md)&#124; [Objeto booliano](../../javascript/reference/boolean-object-javascript.md)&#124; [Data objeto](../../javascript/reference/date-object-javascript.md)&#124; [Objeto de função](../../javascript/reference/function-object-javascript.md)&#124; [Número objeto](../../javascript/reference/number-object-javascript.md)&#124; [Objeto Object](../../javascript/reference/object-object-javascript.md)&#124; [Objeto de cadeia de caracteres](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>Consulte também  
 [Método toString (Object)](../../javascript/reference/tostring-method-object-javascript.md)