---
title: Função Debug writeln (JavaScript) | Microsoft Docs
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
- writeln
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- writeIn method
ms.assetid: c3aad0cd-0486-4161-9ba6-31d672da72af
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 848760e59632b05605de2d73615a2b025df363da
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636276"
---
# <a name="debugwriteln-function-javascript"></a>Função Debug.writeln (JavaScript)
Envia as cadeias de caracteres para o depurador de script, seguido por um caractere de nova linha.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
Debug.writeln([str1 [, str2 [, ... [, strN]]]])  
```  
  
## <a name="parameters"></a>Parâmetros  
 *str1 str2,..., strN*  
 Opcional. Cadeias de caracteres para enviar para o depurador de scripts.  
  
## <a name="remarks"></a>Comentários  
 O `Debug.writeln` função envia cadeias de caracteres, seguidas por um caractere de nova linha, a janela imediata do Microsoft Script Debugger em tempo de execução. Se o script não está sendo depurado, o `Debug.writeln` função não tem nenhum efeito.  
  
 O `Debug.writeln` função é quase idêntica de `Debug.write` função. A única diferença é que o `Debug.write` função não envia um caractere de nova linha depois de enviar as cadeias de caracteres.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa o `Debug.writeln` função para exibir o valor da variável na janela Immediate do depurador de Script do Microsoft.  
  
> [!NOTE]
>  Para executar este exemplo, você deve ter instalado um depurador de script e o script deve ser executado no modo de depuração.  
>   
>  Internet Explorer 8 inclui o [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] depurador. Se você estiver usando uma versão anterior do Internet Explorer, consulte [como: habilitar e iniciar a depuração de Script do Internet Explorer](http://go.microsoft.com/fwlink/?LinkId=133801).  
  
```JavaScript  
var counter = 42;  
Debug.writeln("The value of counter is " + counter);  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Aplica-se a**: [objeto Debug](../../javascript/reference/debug-object-javascript.md)  
  
## <a name="see-also"></a>Consulte também  
 [Função Debug.write](../../javascript/reference/debug-write-function-javascript.md)