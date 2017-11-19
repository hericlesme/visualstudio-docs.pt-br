---
title: Propriedade Debug setnonusercodeexceptions | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 1dd2abee-a415-41bb-a359-017da62f9485
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3f53084d5580bc7b6b6c6356268dc60f519b2bd6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="debugsetnonusercodeexceptions-property"></a>Propriedade Debug.setNonUserCodeExceptions
Determina se todos os blocos de try-catch neste escopo devem ser tratados pelo depurador como manipulado pelo usuário. Exceções podem ser classificadas como lançada, sem tratamento do usuário ou sem tratamento.  
  
 Se essa propriedade é definida como `true` em um determinado escopo, o depurador pode determinar a executar alguma ação (por exemplo, quebra) em exceções lançadas dentro desse escopo, se o desenvolvedor deseja interromper as exceções não tratadas pelo usuário. Se essa propriedade é definida como `false` é o mesmo que a propriedade nunca foi definida.  
  
 Para obter mais informações sobre depuração, consulte [Active Script visão geral de depuração](http://go.microsoft.com/fwlink/p/?LinkId=249469).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Debug.setNonUserCodeExceptions [= bool];  
```  
  
## <a name="example"></a>Exemplo  
 O código a seguir mostra como definir essa propriedade.  
  
```JavaScript  
(function () {  
    Debug.setNonUserCodeExceptions = true;  
    try{  
        var x = null;  
        x.y();  
    } catch (e) {  
    // Catch the exception.  
    }  
})();  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]