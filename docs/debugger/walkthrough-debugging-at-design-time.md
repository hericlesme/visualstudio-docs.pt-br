---
title: Depuração no tempo de Design - Visual Studio | Microsoft Docs
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
ms.openlocfilehash: c569ba018cfaa65cf2fec3edcf0676ef374db225
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
---
# <a name="debug-at-design-time-in-visual-studio"></a>Depuração no tempo de Design no Visual Studio

Em alguns cenários, convém depurar o código no design de tempo, em vez de enquanto o aplicativo está em execução. Você pode fazer isso usando o **imediato** janela. Se você deseja depurar código XAML que interage com outros código, como código de associação de dados, você pode usar **depurar** > **anexar ao processo** para fazer isso.
  
### <a name="debug-at-design-time-using-the-immediate-window"></a>Depuração no tempo de design usando a janela imediata  

Você pode usar o Visual Studio **imediato** janela para executar uma função ou sub-rotina enquanto o seu aplicativo não está em execução. Se a função ou a sub-rotina contiverem um ponto de interrupção, o Visual Studio interromperá a execução no ponto apropriado. Então, você poderá usar o depurador do Windows para examinar o estado do programa. Esse recurso é chamado de depuração em tempo de design.  

O exemplo a seguir é no Visual Basic, mas o **imediato** janela também tem suporte em aplicativos c# e C++.
  
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
  
3.  Abra o **imediato** janela (**depurar** > **Windows** > **imediato**) e digite o seguinte no janela: `?MyFunction<enter>`  
  
4.  Certifique-se de que o ponto de interrupção foi alcançado, e que a pilha de chamadas está correta.  
  
5.  Sobre o **depurar** menu, clique em **continuar**e verifique se que ainda está no modo de design.  
  
6.  Digite o seguinte no **imediato** janela: `?MyFunction<enter>`  
  
7.  Digite o seguinte no **imediato** janela: `?MySub<enter>`  
  
8.  Verifique se o ponto de interrupção e examine o valor da variável estática `i` no **locais** janela. Deve ter o valor 3.  
  
9. Verifique se a pilha de chamadas está correta.  
  
10. Sobre o **depurar** menu, clique em **continuar**e verifique se que ainda está no modo de design.  

## <a name="debug-at-design-time-from-the-xaml-designer"></a>Depuração no tempo de design do designer XAML

Ele pode ser útil depurar o código por trás do designer XAML em alguns cenários de associação de dados declarativa.

1. No seu projeto, adicione uma nova página do XAML, como *temp.xaml*. A nova página XAML deixe em branco. 

1. Compile sua solução.

1. Abra *temp.xaml*, que carrega o designer (*UwpSurface.exe* em um aplicativo UWP, ou *XDesProc.exe*) para que você possa se conectar a ele em etapas posteriores. 

1. Abra uma nova instância do Visual Studio. Na nova instância, abra o **anexar ao processo** caixa de diálogo (**depurar** > **anexar ao processo**), defina o **anexar a** campo para o tipo de código correta, tal como **código gerenciado (CoreCLR)** ou o tipo de código correta com base em sua versão do .NET. Selecione o processo de designer correto na lista e escolha **Attach**.

    Para UWP 16299 de compilação de projetos de destino ou superior, o processo de designer é *UwpSurface.exe*. Para WPF ou versões anteriores ao 16299 UWP, é o processo de designer *XDesProc.exe*.

1. Enquanto conectado ao processo, alterne para o seu projeto, abra o code-behind em que você deseja depurar e definir um ponto de interrupção.

1. Por fim, abra a página que contém o código XAML que inclui a associação de dados.

    Por exemplo, você pode definir um ponto de interrupção no código de conversor de tipo para o XAML a seguir, que associa um TextBlock em tempo de design.

    ```xaml
    <TextBlock Text="{Binding title, ConverterParameter=lower, Converter={StaticResource StringFormatConverter}, Mode=TwoWay}"  />
    ```
   Quando a página for carregada, o ponto de interrupção é atingido.
  
## <a name="see-also"></a>Consulte também  
 [Segurança do depurador](../debugger/debugger-security.md)   
 [Noções básicas do depurador](../debugger/debugger-basics.md)
