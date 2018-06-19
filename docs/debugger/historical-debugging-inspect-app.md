---
title: Verifique se seu aplicativo com depuração histórica | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 629b5d93-39b2-430a-b8ba-d2a47fdf2584
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d6a8e4ec27c73516d2eb4ea79ee8beee91dfd19c
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31476816"
---
# <a name="inspect-your-app-with-intellitrace-historical-debugging-in-visual-studio"></a>Verifique se seu aplicativo com depuração no Visual Studio histórica do IntelliTrace
Você pode usar [depuração histórica](../debugger/historical-debugging.md) retroceder e Avançar pela execução de seu aplicativo e inspecionar seu estado.  
  
Você pode usar o IntelliTrace no Visual Studio Enterprise edition, mas não nas edições Professional ou da comunidade.  
  
## <a name="navigate-your-code-with-historical-debugging"></a>Navegar pelo seu código com depuração histórica  
 Vamos começar com um programa simples que tem um erro. Em um aplicativo de console c#, adicione o seguinte código:  
  
```csharp  
static void Main(string[] args)  
{  
    int testInt = 0;  
    int resultInt = AddAll(testInt);  
    Console.WriteLine(resultInt);  
}  
private static int AddAll(int j)  
{  
    for (int i = 0; i < 20; i++)  
    {  
        j = AddInt(j);  
    }  
    return j;  
}  
  
private static int AddInt(int add)  
{  
    if (add == 10)  
    {  
        return add += 25;  
    }  
    return ++add;  
}  
```  
  
 Vamos supor que o valor esperado de `resultInt` depois de chamar `AddAll()` é 20 (o resultado do incremento dos `testInt` 20 vezes). (Também pressupomos que não é possível ver o bug em `AddInt()`). Mas o resultado é realmente 44. Como é possível encontrar o bug sem percorrendo `AddAll()` 10 vezes? Podemos usar depuração histórica para localizar o bug mais rápido e mais facilmente. Veja como:  
  
1.  Em **Ferramentas > Opções > IntelliTrace > geral**, certifique-se de que o IntelliTrace está habilitado e selecione **eventos do IntelliTrace e informações de chamadas**. Se você não selecionar essa opção, você não poderá ver a medianiz de navegação (como explicado abaixo).  
  
2.  Defina um ponto de interrupção a `Console.WriteLine(resultInt);` linha.  
  
3.  Inicie a depuração. O código é executado no ponto de interrupção. No **locais** janela, você pode ver que o valor de `resultInt` é 44.  
  
4.  Abra o **ferramentas de diagnóstico** janela (**Depurar > Ferramentas de diagnóstico Mostrar**). A janela de código deve ter esta aparência:  
  
     ![Janela de código no ponto de interrupção](../debugger/media/historicaldebuggingbreakpoint.png "HistoricalDebuggingBreakpoint")  
  
5.  Você verá uma seta dupla na margem esquerda, acima o ponto de interrupção. Essa área é chamada de exibir a navegação e é usada para depuração histórica. Clique na seta.  
  
     Na janela de código, você verá que a linha de código precedente (`int resultInt = AddIterative(testInt);`) é colorido rosa. Acima da janela, você verá uma mensagem que você está na depuração histórica.  
  
     A janela de código agora tem esta aparência:  
  
     ![janela de código no modo de depuração histórica](../debugger/media/historicaldebuggingback.png "HistoricalDebuggingBack")  
  
6.  Agora você pode percorrer o `AddAll()` método (**F11**, ou o **intervir** botão na medianiz navegação. Avançar uma etapa (**F10**, ou **ir para próxima chamada** na medianiz navegação. A linha rosa está agora no `j = AddInt(j);` linha. **F10** nesse caso, não passar para a próxima linha de código. Em vez disso, ele passa para a próxima chamada de função. Depuração histórica navega de uma chamada para outra, e ela ignora a linhas de código que não incluem uma chamada de função.  
  
7.  Intervir agora o `AddInt()` método. Você deve ver o bug nesse código imediatamente.  

## <a name="next-steps"></a>Próximas etapas

Este procedimento apenas uma pequena amostra do que você pode fazer com a depuração histórica.

- Para exibir instantâneos durante a depuração, consulte [exibir instantâneos usando IntelliTrace etapa-back](../debugger/how-to-use-intellitrace-step-back.md).
- Para obter mais informações sobre as diferentes configurações e os efeitos dos botões diferentes na medianiz navegação, consulte [funcionalidades do IntelliTrace](../debugger/intellitrace-features.md).