---
title: "Guia de início rápido: criar seu primeiro aplicativo de console no Visual Studio com o Visual Basic | Microsoft Docs"
ms.custom: 
ms.date: 12/10/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-acquisition
ms.tgt_pltfrm: 
ms.topic: quickstart
ms.devlang: vb
author: TerryGLee
ms.author: tglee
manager: ghogen
dev_langs: vb
ms.workload: multiple
ms.openlocfilehash: 2573e1a2344b858b721fb234d6b228b421a36550
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/05/2018
---
# <a name="quickstart-create-your-first-console-app-in-visual-studio-with-visual-basic"></a>Guia de início rápido: criar seu primeiro aplicativo de console no Visual Studio com o Visual Basic
Nesta introdução de 5 a 10 minutos ao IDE (ambiente de desenvolvimento integrado) do Visual Studio, você criará um aplicativo simples do Visual Basic que é executado no console.

Se você ainda não tiver instalado o Visual Studio, acesse a página [Downloads do Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) para instalá-lo gratuitamente.

## <a name="create-a-project"></a>Criar um projeto
Primeiro, você criará um projeto de aplicativo do Visual Basic. O tipo de projeto inclui todos os arquivos de modelo que você precisará, mesmo sem adicionar nada!

1. Abra o Visual Studio 2017.

2. Na barra de menus superior, selecione **Arquivo** > **Novo** > **Projeto...**.

3. Na caixa de diálogo **Novo Projeto**, no painel esquerdo, expanda **Visual Basic** e, em seguida, escolha **.NET Core**. No painel central, escolha **Aplicativo de Console (.NET Core)**. Em seguida, nomeie o projeto como *HelloWorld*.

   ![Modelo de projeto do aplicativo do console (.NET Core) na caixa de diálogo Novo projeto no IDE do Visual Studio](../ide/media/new-project-vb-dotnetcore-helloworld-console-app.png)

     Se você não vir o modelo de projeto do **Aplicativo de Console (.NET Core)**, clique no link **Abrir Instalador do Visual Studio** no painel esquerdo da caixa de diálogo **Novo Projeto**.

   ![Clique no link Abrir o Instalador do Visual Studio na caixa de diálogo Novo Projeto](../ide/media/vb-open-visual-studio-installer-hello-world.png)

     O Instalador do Visual Studio é iniciado. Escolha a carga de trabalho **Desenvolvimento multiplaforma do .NET Core** e, em seguida, selecione **Modificar**.

     ![Carga de trabalho de desenvolvimento multiplaforma do .NET Core no Instalador do Visual Studio](../ide/media/dot-net-core-xplat-dev-workload.png)

## <a name="create-the-application"></a>Criar o aplicativo
Depois de selecionar o modelo de projeto do Visual Basic e nomear o projeto, o Visual Studio criará um aplicativo “Olá, Mundo” simples para você. Ele chama o método <xref:System.Console.WriteLine%2A> para exibir a cadeia de caracteres literal "Hello World!" na janela do console.

![Exibir o código Olá, Mundo padrão do modelo](../ide/media/vb-console-helloworld-template.png)

Se clicar no botão **HelloWorld** no IDE, você poderá executar o programa no modo de depuração.

  ![Clique no botão Olá, Mundo para executar o programa no modo de depuração](../ide/media/vb-console-hello-world-button.png)

Quando você faz isso, a janela do console se torna visível somente por um momento antes de ser fechada. Isso acontece porque o método `Main` é encerrado após a execução de sua instrução única e, portanto, o aplicativo é encerrado.

### <a name="add-some-code"></a>Adicionar código
Vamos adicionar alguns códigos para pausar o aplicativo e, em seguida, solicitar a entrada do usuário.

1. Adicione o seguinte código imediatamente após a chamada ao método <xref:System.Console.WriteLine%2A>:

   ```vb
   Console.Write("Press any key to continue...")
   Console.ReadKey(true)
   ```
   Isso pausa o programa até que você pressione uma tecla.

2. Na barra de menus, selecione **Compilar** > **Compilar Solução**.

   Isso compila seu programa em uma IL (linguagem intermediária) que é convertida em um código binário por um compilador JIT (Just-In-Time).

## <a name="run-the-application"></a>Executar o aplicativo
1. Clique no botão **HelloWorld** na barra de ferramentas.

   ![Clique no botão Olá, Mundo para executar o programa da barra de ferramentas](../ide/media/vb-console-hello-world-button.png)

2. Pressione qualquer tecla para fechar a janela de console.

   ![Janela de console mostrando Olá, Mundo e Pressione qualquer tecla para continuar](../ide/media/vb-console-hello-world-press-any-key.png)

Parabéns por concluir este guia de início rápido! Esperamos que você tenha aprendido um pouco sobre o Visual Basic e sobre o IDE do Visual Studio. Se quiser se aprofundar mais, continue com um tutorial na seção **Tutoriais** do sumário.

## <a name="see-also"></a>Consulte também
* [Guia de início rápido: criar um aplicativo “Olá, Mundo” do Windows Forms no Visual Studio com o Visual Basic](quickstart-visual-basic-winforms.md)
* [Tutorial: introdução ao Visual Basic no Visual Studio](tutorial-visual-basic-console.md)
* [IntelliSense para arquivos de código do Visual Basic](visual-basic-specific-intellisense.md)
