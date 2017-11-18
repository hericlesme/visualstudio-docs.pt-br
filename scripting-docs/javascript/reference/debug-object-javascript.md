---
title: Objeto Debug (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: debug
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Debug object
- Debug object, about Debug object
ms.assetid: 42a367ec-beb1-4e59-8342-34c326eca042
caps.latest.revision: "19"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6286e5db853daa97e43f36a1467abe90cbced5c8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="debug-object-javascript"></a>Objeto Debug (JavaScript)
Um objeto global intrínseco que envia saída para um depurador.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Debug.function  
```  
  
## <a name="remarks"></a>Comentários  
 Você não instanciar o objeto de depuração. Você pode acessar todas as suas propriedades e métodos chamando `function`.  
  
 Há diferentes maneiras de depurar o Internet Explorer e [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] aplicativos. Em [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] aplicativos, o `write` e `writeln` funções do `Debug` objeto cadeias de caracteres de exibição no Visual Studio **saída** janela de tempo de execução. Para obter mais informações sobre como depurar [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] aplicativos, consulte [depurar aplicativos Universal do Windows no Visual Studio](/visualstudio/debugger/debugging-windows-store-and-windows-universal-apps.md).  
  
 Para depurar scripts do Internet Explorer, você deve ter instalado um depurador de script e o script deve ser executado no modo de depuração. Internet Explorer 8 e versões posteriores incluem a [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] depurador. Se você estiver usando uma versão anterior do Internet Explorer, consulte [como: habilitar e iniciar a depuração de Script do Internet Explorer](http://go.microsoft.com/fwlink/?LinkId=133801).  
  
 Se o script não está sendo depurado, as funções não têm efeito.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa o `write` função para exibir o valor da variável.  
  
```JavaScript  
var counter = 42;  
Debug.write("The value of counter is " + counter);  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## <a name="constants"></a>Constantes  
 [Constantes de depuração](../../javascript/reference/debug-constants.md)  
  
## <a name="properties"></a>Propriedades  
 [Propriedade Debug debuggerenabled](../../javascript/reference/debug-debuggerenabled-property.md) &#124; [Propriedade Debug. setnonusercodeexceptions](../../javascript/reference/debug-setnonusercodeexceptions-property.md)  
  
## <a name="functions"></a>Funções  
 [Função Debug mstraceasynccallbackstarting](../../javascript/reference/debug-mstraceasynccallbackstarting-function.md) &#124; [Mstraceasynccallbackcompleted função](../../javascript/reference/debug-mstraceasynccallbackcompleted-function.md) &#124; [Mstraceasyncoperationcompleted função](../../javascript/reference/debug-mstraceasyncoperationcompleted-function.md) &#124; [Mstraceasyncoperationstarting função](../../javascript/reference/debug-mstraceasyncoperationstarting-function.md) &#124; [Msupdateasynccallbackrelation função](../../javascript/reference/debug-msupdateasynccallbackrelation-function.md) &#124; [Função Debug](../../javascript/reference/debug-write-function-javascript.md) &#124; [Função Debug. writeln](../../javascript/reference/debug-writeln-function-javascript.md)  
  
## <a name="see-also"></a>Consulte também  
 [Instrução debugger](../../javascript/reference/debugger-statement-javascript.md)