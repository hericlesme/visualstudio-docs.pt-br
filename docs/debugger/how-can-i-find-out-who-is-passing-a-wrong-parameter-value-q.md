---
title: Como posso descobrir quem está passando um valor de parâmetro incorreto? | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.parameters
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], parameters
- parameters [debugger]
- passing parameters, troubleshooting wrong values
- functions [debugger], detecting wrong parameter values
- parameter values, troubleshooting
ms.assetid: 1f1ae455-0e25-4e9d-b33f-53908f5bd6ce
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a46497e45acb4663822b1a7bc6e4ad5a4f09af11
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31472488"
---
# <a name="how-can-i-find-out-who-is-passing-a-wrong-parameter-value"></a>Como posso descobrir quem está passando um valor de parâmetro incorreto?
## <a name="problem-description"></a>Descrição do problema  
 O valor de parâmetro errado está sendo passado a uma de minhas funções. Essa função é chamada de todos os pontos Como posso descobrir o que está passando o valor errado?  
  
## <a name="solution"></a>Solução  
  
#### <a name="to-resolve-this-problem"></a>Para resolver esse problema  
  
1.  Defina um local de ponto de interrupção no início da função.  
  
2.  O ponto de interrupção e selecione **condição**.  
  
3.  No **condição de ponto de interrupção** caixa de diálogo, clique no **condição** caixa de seleção. Consulte [avançado pontos de interrupção](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression).  
  
4.  Digite uma expressão, como `Var==3`, na caixa de texto, onde `Var` é o nome do parâmetro que contém o valor incorreto, e `3` é o valor incorreto passado para ele.  
  
5.  Selecione o **é True** botão de opção e, em seguida, clique no **Okey** botão.  
  
6.  Agora, execute o programa novamente. O ponto de interrupção faz com que o programa pare no início da função quando o parâmetro `Var` tiver o valor `3`.  
  
7.  Use a janela Pilha de Chamadas para localizar a função de chamada e navegar até seu código-fonte. Para obter mais informações, consulte [como: usar a janela pilha de chamadas](../debugger/how-to-use-the-call-stack-window.md).  
  
## <a name="see-also"></a>Consulte também  
 [Perguntas frequentes de código nativo de depuração](../debugger/debugging-native-code-faqs.md)   
 [Pontos de interrupção](http://msdn.microsoft.com/en-us/fe4eedc1-71aa-4928-962f-0912c334d583)   
 [Depurando código nativo](../debugger/debugging-native-code.md)