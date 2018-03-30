---
title: Introdução ao depurador no Visual Studio | Microsoft Docs
ms.custom: H1Hack27Feb2017
ms.date: 02/07/2017
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: get-started-article
ms.assetid: 0b3138c4-b840-446a-a15c-10ed8e2dd050
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 171b07d453c81883354848f70458bab39daa313e
ms.sourcegitcommit: 29ef88fc7d1511f05e32e9c6e7433e184514330d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/29/2018
---
# <a name="get-started-with-the-visual-studio-debugger"></a>Introdução ao depurador do Visual Studio
O depurador do Visual Studio é fácil de usar em qualquer idioma. Aqui vamos mostrar como depurar um programa c# simple, mas você pode aplicar as mesmas etapas para o código em outras linguagens, como C++ e JavaScript.

Para assistir um vídeo mostrando recursos semelhantes, consulte [guia de Introdução com o depurador](https://www.youtube.com/watch?v=FtGCi5j30YU&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK&index=6).
  
##  <a name="BKMK_Start_debugging_a_VS_project"></a> Depurar um projeto c# básico  
 Vamos começar com um aplicativo de console c# simples (**arquivo > Novo > projeto**, em seguida, selecione **Visual C#** e **aplicativo de Console**). Se você nunca tiver trabalhado com o Visual Studio antes, consulte [passo a passo: criar um aplicativo simples](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md). O **principal** método apenas adiciona 1 a uma variável de inteiro de 10 vezes e imprime o resultado para o console:  
  
```csharp  
static void Main(string[] args)  
{  
    int testInt = 0;  
    for (int i = 1; i <= 10; i++)  
    {  
        testInt += 1;  
    }  
    Console.WriteLine(testInt);  
}  
```  
  
 Esse código de compilação **depurar** configuração. Essa configuração é definida por padrão. Para obter mais informações sobre as configurações, consulte [Noções básicas sobre configurações de compilação](../ide/understanding-build-configurations.md).  
  
 Execute este código no depurador, clicando em **Depurar > Iniciar depuração** (ou **iniciar** na barra de ferramentas ou **F5**). O aplicativo deve sair quase imediatamente, e você, na verdade, não é possível determinar se nada foi impresso na janela do Console.  
  
 Você pode interromper a execução tempo suficiente para ver a janela do Console, definindo um ponto de interrupção e, em seguida, passo a passo à frente. Para definir um ponto de interrupção, coloque o cursor `Console.WriteLine` de linha e clique em **Depurar > Novo ponto de interrupção > ponto de interrupção de função**, ou simplesmente clicar na margem esquerda na mesma linha. O ponto de interrupção deve ter esta aparência:  
  
 ![Definir um ponto de interrupção](../debugger/media/getstartedbreakpoint.png "GetStartedBreakpoint")  
  
 Para obter mais informações sobre pontos de interrupção, consulte [usando pontos de interrupção](../debugger/using-breakpoints.md).  
  
##  <a name="BKMK_Inspect_Variables"></a> Inspecionar variáveis  
 Depuração geralmente envolve a localização de variáveis que não contêm os valores esperados em um momento específico. Mostraremos algumas das maneiras que você pode inspecionar variáveis.  
  
 Inicie a depuração novamente. A execução é interrompida antes do `Console.WriteLine` código é executado. Você pode fazer com que ele execute passo a passo à frente (clique **Depurar > passar por** ou **F10**). Nesse caso, você pode ter escolhido **intervir** (**F11**) e obteve o mesmo resultado; vamos explicar a diferença mais tarde. A linha com a última chave do método deve ter desativado amarela. Observe a janela de Console. Você deve ver **10**.  
  
 Você pode focalizar o **testInt** variável para exibir o valor atual em uma dica de dados.  
  
 ![DBG&#95;Basics&#95;Data&#95;Tips](../debugger/media/dbg_basics_data_tips.png "DBG_Basics_Data_Tips")  
  
 A janela de código abaixo, você deve ver o **Autos**, **locais**, e **inspecionar** windows. Essas janelas mostram os valores atuais das variáveis no momento da execução. Ambos o **Autos** e **locais** mostra **testInt** com um valor de **10**.  
  
 ![Janela Autos durante a depuração](../debugger/media/getstartedwindows.png "GetStartedWindows")  
  
 Para obter mais informações sobre essas janelas, consulte [janelas de locais e Autos](../debugger/autos-and-locals-windows.md).  
  
 Vamos ver como o valor da variável muda conforme percorremos o programa. Defina um ponto de interrupção a `testInt += 1;` de linha e reinicie a depuração. Você deve ver que **testInt** no **locais** e **Autos** for windows **0**, e **i** é **1**. Quando você continua a depuração (**Depurar > continuar**, ou **continuar** na barra de ferramentas ou **F5**), você pode ver que o valor de **testInt** alterações em **1**, em seguida, **2**, e assim por diante. Quando você receber cansado de ver essas alterações, remova o ponto de interrupção (**Depurar > Alternar ponto de interrupção**, ou clique na margem) e continuar a depuração. Se você quiser remover todos os pontos de interrupção, clique em **Depurar > Excluir todos os pontos de interrupção**, ou **CTRL + SHIFT + F9**e clique em **Sim** na caixa de diálogo que pergunta **fazer você deseja remover todos os pontos de interrupção?** .  
  
## <a name="stepping-into-and-over-function-calls"></a>Passo a passo em e em chamadas de função  
 Você pode executar código na depurador instrução pela instrução (**intervir**) ou você pode executar código enquanto o depurador ignora funções (**passar por**) para obter rapidamente o código que você está mais interessado em ( código de função ainda é executado). Você pode alternar entre os dois métodos na mesma sessão de depuração.  
  
 Para ver a diferença entre **intervir** e **passar por**, precisamos adicionar um método que é chamado por outro método. Adicione um método para o aplicativo c# e chamá-lo de que o método Main. O código deve ter esta aparência:  
  
```csharp  
static void Main(string[] args)  
{  
    Method1();  
    Console.WriteLine("end");  
}  
  
private static void Method1()  
{  
    Console.WriteLine("in Method1");  
}  
```  
  
 Defina um ponto de interrupção a `Method1();` chamar o método Main e iniciar a depuração. Quando a execução é interrompida, clique em **Depurar > intervir** (ou **intervir** na barra de ferramentas ou **F11**). Quebras de execução novamente a primeira chave no Method1:  
  
 ![Depuração em código](../debugger/media/getstartedstepinto.png "GetStartedStepInto")  
  
 Parar a depuração e inicie novamente e, quando a execução é interrompida no ponto de interrupção, clique em **Depurar > passar por** (ou **passar por** na barra de ferramentas ou **F10**). A execução é interrompida novamente no `Console.WriteLine("end");`.  
  
 Se você quiser saber mais sobre a navegação de código com o depurador, consulte [navegar pelo código com o depurador](../debugger/navigating-through-code-with-the-debugger.md).