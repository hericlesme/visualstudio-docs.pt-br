---
title: "Função Debug Write (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: Write
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: write method [JavaScript]
ms.assetid: fd1cfbb3-46cb-47cc-896c-a70d457dd413
caps.latest.revision: "22"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 74aad7a01e0dc166f22173cf193b312e1fd4d804
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="debugwrite-function-javascript"></a>Função Debug.write (JavaScript)
Envia as cadeias de caracteres para o depurador de scripts.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
Debug.write([str1 [, str2 [, ... [, strN]]]])  
```  
  
## <a name="parameters"></a>Parâmetros  
 *str1 str2,..., strN*  
 Opcional. Cadeias de caracteres para enviar para o depurador de scripts.  
  
## <a name="remarks"></a>Comentários  
 O `Debug.write` função envia cadeias de caracteres para a janela imediata de um depurador de script em tempo de execução. Se o script não está sendo depurado, o `Debug.write` função não tem nenhum efeito.  
  
 O `Debug.write` função é quase idêntica de `Debug.writeln` função. A única diferença é que o `Debug.writeln` função envia um caractere de nova linha depois que as cadeias de caracteres são enviadas.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa o `Debug.write` função para exibir o valor da variável na janela Immediate do depurador de script.  
  
> [!NOTE]
>  Para executar este exemplo, você deve ter instalado um depurador de script e o script deve ser executado no modo de depuração.  
>   
>  Internet Explorer 8 inclui o [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] depurador. Se você estiver usando uma versão anterior do Internet Explorer, consulte [como: habilitar e iniciar a depuração de Script do Internet Explorer](http://go.microsoft.com/fwlink/?LinkId=133801).  
  
```JavaScript  
var counter = 42;  
Debug.write("The value of counter is " + counter);  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Aplica-se a**: [objeto Debug](../../javascript/reference/debug-object-javascript.md)  
  
## <a name="see-also"></a>Consulte também  
 [Função Debug.writeln](../../javascript/reference/debug-writeln-function-javascript.md)