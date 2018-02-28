---
title: "depurador de instrução (JavaScript) | Microsoft Docs"
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
- debugger_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- debugger statement
ms.assetid: c6d2e193-c1f7-4fb3-8a4e-cc9823174ae4
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9e64e860cebd065f357857484e932b4aea3f05ea
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="debugger-statement-javascript"></a>Instrução debugger (JavaScript)
Suspende a execução.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
debugger  
```  
  
## <a name="remarks"></a>Comentários  
 Você pode colocar `debugger` instruções em qualquer lugar em procedimentos para suspender a execução. Usando o `debugger` instrução é semelhante à configuração de um ponto de interrupção no código.  
  
 O `debugger` instrução suspende a execução, mas não feche quaisquer arquivos ou desmarca todas as variáveis.  
  
> [!NOTE]
>  O `debugger` instrução não tem nenhum efeito a menos que o script está sendo depurado.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa o `debugger` instrução suspender a execução de cada iteração por meio de `for` loop.  
  
> [!NOTE]
>  Para executar este exemplo, você deve ter instalado um depurador de script e o script deve ser executado no modo de depuração.  
>   
>  Internet Explorer 8 inclui o [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] depurador. Se você estiver usando uma versão anterior do Internet Explorer, consulte [como: habilitar e iniciar a depuração de Script do Internet Explorer](http://go.microsoft.com/fwlink/?LinkId=133801).  
  
```JavaScript  
for(i = 1; i<5; i++) {  
   // Print i to the Output window.  
   Debug.write("loop index is " + i);  
   // Wait for user to resume.  
   debugger  
}  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [JavaScript instruções](../../javascript/reference/javascript-statements.md)   
 [Compilação Condicional](../../javascript/advanced/conditional-compilation-javascript.md)