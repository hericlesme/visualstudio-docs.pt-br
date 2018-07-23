---
title: Depurar em tempo de Design - Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 02/21/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- debugging [Visual Studio], design-time
- breakpoints, design-time debugging
- Immediate window, design-time debugging
- design-time debugging
ms.assetid: 35bfdd2c-6f60-4be1-ba9d-55fce70ee4d8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f1235e6360ccc5f6c0677f7ec9acb1dd85cad226
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/20/2018
ms.locfileid: "39180172"
---
# <a name="debug-at-design-time-in-visual-studio"></a>Depurar em tempo de Design no Visual Studio

Em alguns cenários, você talvez queira depurar o código no design de tempo, em vez de enquanto o aplicativo está em execução. Você pode fazer isso usando o **imediato** janela. Se você quiser depurar o código XAML que interage com outro código, como o código de associação de dados, você pode usar **Debug** > **anexar ao processo** para fazer isso.
  
### <a name="debug-at-design-time-using-the-immediate-window"></a>Depurar em tempo de design usando a janela imediata  

Você pode usar o Visual Studio **imediato** janela para executar uma função ou sub-rotina enquanto seu aplicativo não está em execução. Se a função ou a sub-rotina contiverem um ponto de interrupção, o Visual Studio interromperá a execução no ponto apropriado. Então, você poderá usar o depurador do Windows para examinar o estado do programa. Esse recurso é chamado de depuração em tempo de design.  

O exemplo a seguir está no Visual Basic, mas o **imediato** janela também tem suporte em aplicativos c# e C++.
  
1.  Cole o seguinte código no aplicativo de console do Visual Basic:  
  
    ```vb  
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
  
3.  Abra o **imediato** janela (**Debug** > **Windows** > **imediato**) e digite o seguinte no janela: `?MyFunction<enter>`  
  
4.  Certifique-se de que o ponto de interrupção foi alcançado, e que a pilha de chamadas está correta.  
  
5.  Sobre o **Debug** menu, clique em **continuar**e verificar se você estiver no modo de design.  
  
6.  Digite o seguinte na **imediato** janela: `?MyFunction<enter>`  
  
7.  Digite o seguinte na **imediato** janela: `?MySub<enter>`  
  
8.  Verifique se o ponto de interrupção e examinar o valor da variável estática `i` no **Locals** janela. Deve ter o valor 3.  
  
9. Verifique se a pilha de chamadas está correta.  
  
10. Sobre o **Debug** menu, clique em **continuar**e verificar se você estiver no modo de design.  

## <a name="debug-at-design-time-from-the-xaml-designer"></a>Depurar em tempo de design do designer XAML

Ele pode ser útil depurar o código por trás do designer XAML em alguns cenários de associação de dados declarativa.

1. Em seu projeto, adicione uma nova página XAML, como *temp.xaml*. Deixe a nova página XAML vazia. 

1. Compile sua solução.

1. Abra *temp.xaml*, que carrega o designer (*UwpSurface.exe* em um aplicativo UWP, ou *XDesProc.exe*) para que você pode anexar a ela em etapas posteriores. 

1. Abra uma nova instância do Visual Studio. Na nova instância, abra o **anexar ao processo** caixa de diálogo (**Debug** > **anexar ao processo**), defina o **anexar a** campo para o tipo de código correto, como **Managed Code (CoreCLR)** ou o tipo de código correto com base na sua versão do .NET. Selecione o processo correto de designer na lista e escolha **Attach**.

    Para a UWP projetos direcionados ao build 16299 ou acima, é o processo do designer *UwpSurface.exe*. Para WPF ou versões anteriores ao 16299 UWP, é o processo do designer *XDesProc.exe*.

1. Enquanto conectado ao processo, alterne para seu projeto, abra o code-behind em que você deseja depurar e definir um ponto de interrupção.

1. Por fim, abra a página que contém o código XAML que inclui vinculação de dados.

    Por exemplo, você pode definir um ponto de interrupção no código de conversor de tipo para o XAML a seguir, que associa um TextBlock em tempo de design.

    ```xaml
    <TextBlock Text="{Binding title, ConverterParameter=lower, Converter={StaticResource StringFormatConverter}, Mode=TwoWay}"  />
    ```
   Quando a página for carregada, o ponto de interrupção é atingido.
  
## <a name="see-also"></a>Consulte também  
 [Segurança do depurador](../debugger/debugger-security.md)   
 [Noções básicas do depurador](../debugger/getting-started-with-the-debugger.md)
