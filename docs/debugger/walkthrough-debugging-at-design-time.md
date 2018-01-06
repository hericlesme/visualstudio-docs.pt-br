---
title: 'Passo a passo: Depurando em tempo de Design | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugging [Visual Studio], design-time
- breakpoints, design-time debugging
- Immediate window, design-time debugging
- design-time debugging
ms.assetid: 35bfdd2c-6f60-4be1-ba9d-55fce70ee4d8
caps.latest.revision: "20"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 5869279a7bafb11368b7fb232e6ca68ca7d98478
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-debugging-at-design-time"></a>Instruções passo a passo: depurando na hora de design
Você pode usar o Visual Studio **imediato** janela para executar uma função ou sub-rotina enquanto o seu aplicativo não está em execução. Se a função ou a sub-rotina contiverem um ponto de interrupção, o Visual Studio interromperá a execução no ponto apropriado. Então, você poderá usar o depurador do Windows para examinar o estado do programa. Esse recurso é chamado de depuração em tempo de design.  
  
 O procedimento a seguir exibe como usar esse recurso.  
  
### <a name="to-hit-breakpoints-from-the-immediate-window"></a>Para usar pontos de interrupção da janela Imediato  
  
1.  Cole o seguinte código no aplicativo de console do Visual Basic:  
  
    ```  
    Module Module1  
  
        Sub Main()  
            MySub()  
        End Sub  
  
        Function MyFunction() As Decimal  
            Static i As Integer  
            i = i + 1  
            Dim s As String  
  
            s = "Add Breakpoint here"  
            Return 4  
        End Function  
  
        Sub MySub()  
            MyFunction()  
        End Sub  
    End Module  
    ```  
  
2.  Defina um ponto de interrupção na linha em que se lê `s="Add BreakPoint Here"`.  
  
3.  Digite o seguinte no **imediato** janela:`?MyFunction<enter>`  
  
4.  Certifique-se de que o ponto de interrupção foi alcançado, e que a pilha de chamadas está correta.  
  
5.  Sobre o **depurar** menu, clique em **continuar**e verifique se que ainda está no modo de design.  
  
6.  Digite o seguinte no **imediato** janela:`?MyFunction<enter>`  
  
7.  Digite o seguinte no **imediato** janela:`?MySub<enter>`  
  
8.  Verifique se o ponto de interrupção e examine o valor da variável estática `i` no **locais** janela. Deve ter o valor 3.  
  
9. Verifique se a pilha de chamadas está correta.  
  
10. Sobre o **depurar** menu, clique em **continuar**e verifique se que ainda está no modo de design.  
  
## <a name="see-also"></a>Consulte também  
 [Segurança do depurador](../debugger/debugger-security.md)   
 [Noções básicas do depurador](../debugger/debugger-basics.md)