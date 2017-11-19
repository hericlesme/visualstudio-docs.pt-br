---
title: "Durante a chamada de uma função centenas de vezes, como sei qual chamada falhou? | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.functions
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- conditional breakpoints
- errors [debugger], function calls
- breakpoints, troubleshooting
- errors [debugger], finding which function call failed
- failures
- location breakpoint call failures
- errors [Visual Studio], function calls
- hit counts
- function calls, failure
- functions [debugger]
- Skip Count
ms.assetid: 66cfac86-f5be-4d3a-9329-d44cd74bc586
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cd02b4debeefbdbfff4e0889329eddab7fabe46a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="when-calling-a-function-hundreds-of-times-how-do-i-know-which-call-failed"></a>Durante a chamada de uma função centenas de vezes, como sei qual chamada falhou?
## <a name="problem-description"></a>Descrição do problema  
 Meu programa falha em uma chamada para uma determinada função, `CnvtV`. O programa provavelmente chama essa função algumas centenas de vezes antes de falhar. Se eu definir um ponto de interrupção de local em `CnvtV`, o programa parará em cada chamada a essa função, e eu não quero isso. Eu não sei quais condições causam a falha na chamada, portanto, não consigo definir um ponto de interrupção condicional. O que posso fazer?  
  
## <a name="solution"></a>Solução  
 Você pode definir um ponto de interrupção na função com o **contagem de ocorrências** campo com um valor tão alto que ele nunca seja atingido. Nesse caso, porque você acredita que a função `CnvtV` é chamada de algumas centenas de vezes, você pode definir **contagem de ocorrências** para 1000 ou mais. Execute o programa e aguarde a chamada falhar. Quando falhar, abra a janela Pontos de Interrupção e verifique a lista de pontos de interrupção. O ponto de interrupção definido em `CnvtV` aparece, seguido pela contagem de ocorrências e o número de iterações restantes:  
  
```  
CnvtV(int) (no condition) when hit count is equal to 1000 (currently 101)  
```  
  
 Agora você sabe que a função falha na 101a chamada. Se você redefinir o ponto de interrupção com uma contagem de ocorrências de 101 e executar o programa novamente, o programa de chamada parará na chamada para `CnvtV` que causou a falha.  
  
## <a name="see-also"></a>Consulte também  
 [Perguntas frequentes de código nativo de depuração](../debugger/debugging-native-code-faqs.md)   
 [Definir pontos de interrupção](http://msdn.microsoft.com/en-us/fe4eedc1-71aa-4928-962f-0912c334d583)   
 [Depurando código nativo](../debugger/debugging-native-code.md)