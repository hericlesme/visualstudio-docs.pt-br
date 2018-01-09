---
title: "Introdução ao Visual Basic no Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 12/08/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-acquisition
ms.tgt_pltfrm: 
ms.topic: tutorial
ms.devlang: vb
author: TerryGLee
ms.author: tglee
manager: ghogen
dev_langs: vb
ms.workload: multiple
ms.openlocfilehash: 1ceda9e53426255331c85996b54378a91324a3fa
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="getting-started-with-visual-basic-in-visual-studio"></a>Introdução ao Visual Basic no Visual Studio
Neste tutorial para o Visual Basic (VB), você usará o Visual Studio para criar e executar alguns aplicativos de console diferentes e explorar alguns recursos do [IDE (ambiente de desenvolvimento integrado)](visual-studio-ide.md) do Visual Studio enquanto isso.

Se você ainda não tiver instalado o Visual Studio, acesse a página [Downloads do Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) para instalá-lo gratuitamente.

## <a name="before-you-begin"></a>Antes de começar
Aqui está algumas perguntas frequentes rápidas para apresentar alguns conceitos principais.
### <a name="what-is-visual-basic"></a>O que é o Visual Basic?
Visual Basic é uma linguagem de programação fortemente tipada projetada para ser fácil de aprender. Ele é derivado do BASIC, cuja abreviação significa “Código de instrução simbólico com várias finalidades para iniciantes”.
### <a name="what-is-visual-studio"></a>O que é o Visual Studio?
Visual Studio é um pacote de desenvolvimento integrado de ferramentas de produtividade para desenvolvedores. Pense nele como um programa que você pode usar para criar programas e aplicativos.  
### <a name="what-is-a-console-app"></a>O que é um aplicativo do console?
Um aplicativo de console obtém a entrada e exibe a saída em uma janela de linha de comando, também conhecida como um console.
### <a name="what-is-net-core"></a>O que é o .NET Core?
O .NET Core é o próximo passo na evolução do .NET Framework. Enquanto o .NET Framework pode compartilhar o código entre linguagens de programação, o .NET Core agrega a capacidade de compartilhar o código entre plataformas. Melhor ainda, ele é um software livre. (Tanto o .NET Framework quanto o .NET Core incluem bibliotecas de funcionalidade predefinidas, bem como um CLR (Common Language Runtime), que atua como uma máquina virtual na qual o código será executado.)

## <a name="start-developing"></a>Começar a desenvolver
Pronto para começar a desenvolver? Vamos lá.

### <a name="create-a-project"></a>Criar um projeto
Primeiro, criaremos um projeto de aplicativo do Visual Basic. O tipo de projeto inclui todos os arquivos de modelo que você precisará, mesmo sem adicionar nada!

1. Abra o Visual Studio 2017.

2. Na barra de menus superior, selecione **Arquivo** > **Novo** > **Projeto...**.

3. Na caixa de diálogo **Novo Projeto**, no painel esquerdo, expanda **Visual Basic** e, em seguida, escolha **.NET Core**. No painel central, escolha **Aplicativo de Console (.NET Core)**. Em seguida, nomeie o arquivo como *HelloWorld*.  

   ![Modelo de projeto do aplicativo do console (.NET Core) na caixa de diálogo Novo projeto no IDE do Visual Studio](../ide/media/new-project-vb-dotnetcore-whatisyourname-console-app.png)

#### <a name="add-a-workgroup-optional"></a>Adicionar um grupo de trabalho (opcional)
Se o modelo de projeto **Aplicativo do Console (.NET Core)** não for exibido, você poderá obtê-lo adicionando a carga de trabalho **Desenvolvimento .NET Core de multiplataforma**. Você pode adicionar essa carga de trabalho de uma das duas maneiras, dependendo de quais atualizações do Visual Studio 2017 estão instaladas no seu computador.

##### <a name="option-1-use-the-new-project-dialog-box"></a>Opção 1: usar a caixa de diálogo Novo Projeto
1. Clique no link **Abrir o Instalador do Visual Studio** no painel esquerdo da caixa de diálogo **Novo Projeto**.

  ![Clique no link Abrir o Instalador do Visual Studio na caixa de diálogo Novo Projeto](../ide/media/vs-open-visual-studio-installer-generic.png)

2. O Instalador do Visual Studio é iniciado. Escolha a carga de trabalho **Desenvolvimento multiplaforma do .NET Core** e, em seguida, selecione **Modificar**.

   ![Carga de trabalho de desenvolvimento multiplaforma do .NET Core no Instalador do Visual Studio](../ide/media/dot-net-core-xplat-dev-workload.png)

##### <a name="option-2-use-the-tools-menu-bar"></a>Opção 2: usar a barra de menus Ferramentas
1. Cancele a caixa de diálogo **Novo Projeto** e, na barra de menus superior, escolha **Ferramentas** > **Obter Ferramentas e Recursos...**.

2. O Instalador do Visual Studio é iniciado. Escolha a carga de trabalho **Desenvolvimento multiplaforma do .NET Core** e, em seguida, selecione **Modificar**.   

## <a name="create-a-what-is-your-name-application"></a>Criar um aplicativo de “Qual é o seu nome”
Vamos criar um aplicativo que solicita o nome e o exibe juntamente com a data e a hora. Veja como:

1. Se ainda não estiver aberto, abra seu projeto *WhatIsYourName*.

2. Insira o código do Visual Basic a seguir imediatamente após o colchete de abertura que segue a linha `Sub Main(args As String())` e antes da linha `End Sub`:

     ```vb
     Console.WriteLine(vbCrLf + "What is your name? ")
     Dim name = Console.ReadLine()
     Dim currentDate = DateTime.Now
     Console.WriteLine($"{vbCrLf}Hello, {name}, on {currentDate:d} at {currentDate:t}")
     Console.Write(vbCrLf + "Press any key to exit... ")
     Console.ReadKey(True)
    ```

    Esse código substitui as instruções [Console.WriteLine](/dotnet/api/system.console.writeline?view=netframework-4.7.1), [Console.Write](/dotnet/api/system.console.write?view=netframework-4.7.1) e [Console.ReadKey]() existentes.

 ![Janela de código mostrando o código Qual é o seu nome](../ide/media/vb-codewindow-what-name.png)

3. Quando a janela do console é aberta, digite seu nome. A janela do console deve ser semelhante à captura de tela a seguir:       

   ![Janela do console mostrando Qual é o seu nome, a data e hora, e Pressione qualquer tecla para continuar a mensagem](../ide/media/vb-console-what-name.png)

5. Pressione qualquer tecla para fechar a janela de console.

## <a name="create-a-calculate-this-application"></a>Criar um aplicativo “Calcular isso”
1. Abra o Visual Studio 2017 e, na barra de menus superior, escolha **Arquivo** > **Novo** > **Projeto...**.

2. Na caixa de diálogo **Novo Projeto**, no painel esquerdo, expanda **Visual Basic** e, em seguida, escolha **.NET Core**. No painel central, escolha **Aplicativo de Console (.NET Core)**. Em seguida, nomeie o arquivo como *CalculateThis*.  

3. Insira o código a seguir entre as linhas `Module Program` e `End Module`:

   ```vb
   Public num1 As Integer
   Public num2 As Integer
   Public answer As Integer
   Sub Main()
       Console.WriteLine("Type a number and press Enter")
       num1 = Console.ReadLine()
       Console.WriteLine("Type another number to add to it and press Enter")
       num2 = Console.ReadLine()
       answer = num1 + num2
       Console.WriteLine("The answer is " & answer)
       Console.ReadLine()
   End Sub
   ```

  Sua janela de código deve se parecer com a captura de tela a seguir:

   ![Janela de código mostrando o código Calcular isso](../ide/media/vb-codewindow-calculate-this.png)

4. Clique em **CalculateThis** para executar o programa. A janela do console deve ser semelhante à captura de tela a seguir:       

    ![Janela do console mostrando o aplicativo CaluculateThis, que inclui solicitações de ações a serem tomadas.](../ide/media/vb-console-calculate-this.png)

Parabéns por concluir este tutorial.

## <a name="see-also"></a>Consulte também
* [Guia do Visual Basic](/dotnet/visual-basic/index)
* [Novidades no Visual Basic](/dotnet/visual-basic/getting-started/whats-new)
* [IntelliSense para arquivos de código do Visual Basic](visual-basic-specific-intellisense.md)
* [Referência da linguagem Visual Basic](/dotnet/visual-basic/language-reference/index)
* Curso em vídeo [Conceitos básicos do Visual Basic para iniciantes completos](https://mva.microsoft.com/en-us/training-courses/visual-basic-fundamentals-for-absolute-beginners-16507)
