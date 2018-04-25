---
title: 'Início Rápido: Criar seu primeiro aplicativo da Plataforma Universal do Windows no Visual Studio com XAML e C# | Microsoft Docs'
ms.custom: ''
ms.date: 04/04/2018
ms.technology:
- vs-acquisition
ms.topic: quickstart
ms.devlang: CSharp
author: TerryGLee
ms.author: tglee
manager: douge
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: d1263b752a27522b9a551d8015689f60422984ad
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="quickstart-create-your-first-universal-windows-platform-application-in-visual-studio-with-xaml-and-c35"></a>Início Rápido: Criar seu primeiro aplicativo da Plataforma Universal do Windows no Visual Studio com XAML e C&#35;

Nesta introdução de 5 a 10 minutos ao IDE (ambiente de desenvolvimento integrado) do Visual Studio, você criará um aplicativo "Olá, Mundo" que poderá ser executado em qualquer dispositivo Windows 10. Para fazer isso, você usará um modelo de projeto da UWP (Plataforma Universal do Windows), a linguagem XAML e a linguagem de programação C#.

Se você ainda não tiver instalado o Visual Studio, acesse a página [Downloads do Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) para instalá-lo gratuitamente.

## <a name="create-a-project"></a>Criar um projeto

Primeiro, crie um projeto da Plataforma Universal do Windows. O tipo de projeto vem com todos os arquivos de modelo que você precisa, antes mesmo de você adicionar alguma coisa!

1. Abra o Visual Studio 2017.

2. Na barra de menus superior, selecione **Arquivo** > **Novo** > **Projeto...**.

3. No painel esquerdo da caixa de diálogo **Novo Projeto**, expanda **Visual C#** e, em seguida, escolha **Universal do Windows**. No painel do meio, escolha **Aplicativo em Branco (Universal do Windows)**. Em seguida, nomeie o projeto como *HelloWorld* e escolha **OK**.

   ![Modelo de projeto Universal do Windows na caixa de diálogo Novo Projeto no IDE do Visual Studio](../ide/media/new-project-csharp-uwp-helloworld.png)

   > [!NOTE]
   > Se o modelo de projeto **Aplicativo em Branco (Universal do Windows)** não for exibido, clique no link **Abrir Instalador do Visual Studio** no painel esquerdo da caixa de diálogo **Novo Projeto**.<br><br>![Clique no link Abrir instalador do Visual Studio na caixa de diálogo Novo Projeto](../ide/media/vb-open-visual-studio-installer-hello-world.png)<br><br>O Instalador do Visual Studio é iniciado. Escolha a carga de trabalho **Desenvolvimento na Plataforma Universal do Windows** e, em seguida, selecione **Modificar**.<br><br>![Carga de trabalho de desenvolvimento na Plataforma Universal do Windows no Instalador do Visual Studio](../ide/media/uwp-dev-workload.png)

4. Quando a caixa de diálogo **Novo projeto da Plataforma Universal do Windows** for exibida, escolha **OK**.

   ![Aceite as configurações padrão de Destino e de Versão mínima na caixa de diálogo Novo Projeto da Plataforma Universal do Windows](../ide/media/new-uwp-project-target-minver-dialog.png)

  > [!NOTE]
  > Se esta for a primeira vez que você usa o Visual Studio para criar um aplicativo UWP, uma caixa de diálogo **Configurações** poderá aparecer. Selecione **Modo do Desenvolvedor** e, em seguida, escolha **Sim**.<br><br>
 ![Habilitar o Modo do Desenvolvedor na caixa de diálogo Configurações da UWP](../ide/media/enable-developer-mode.png)<br><br>O Visual Studio instala um pacote de Modo do Desenvolvedor adicional. Quando o pacote de instalação for concluído, feche a caixa de diálogo **Configurações**.

## <a name="create-the-application"></a>Criar o aplicativo

É hora de começar a desenvolver. Você vai adicionar um controle de botão, adicionar uma ação para o botão e, em seguida, iniciar o aplicativo "Olá, Mundo" para ver sua aparência.

### <a name="add-a-button-to-the-design-canvas"></a>Adicionar um botão à tela de Design

1. No **Gerenciador de Soluções**, clique duas vezes em **MainPage.xaml** para abrir o modo divisão.

  ![Abra o MainPage.xaml no Gerenciador de Soluções ](../ide/media/uwp-solution-explorer-MainPage-xaml.png)

  Existem dois painéis: o **Designer XAML**, que inclui uma tela de design e o **Editor de XAML**, no qual você pode adicionar ou alterar o código.    

  ![O painel Designer XAML no editor de XAML](../ide/media/uwp-xaml-editor.png)

2. Escolha **Caixa de ferramentas** para abrir a janela de submenu Caixa de Ferramentas.

  ![Clique na Caixa de Ferramentas para abrir a janela de submenu Caixa de Ferramentas](../ide/media/uwp-toolbox.png)

  (Se a opção Caixa de Ferramentas não for exibida, ela poderá ser aberta na barra de menus. Para fazer isso, escolha **Exibição** > **Barra de Ferramentas**. Ou pressione **Ctrl**+**Alt**+**X**.)

3. Clique no ícone **Fixar** para encaixar a janela Caixa de Ferramentas.

  ![Clique no ícone de pino para encaixar a janela Caixa de Ferramentas](../ide/media/uwp-toolbox-autohide.png)

4. Clique no controle de **Botão** e, em seguida, arraste-o para a tela de design.

   ![Clique no controle de Botão e arraste-o para a tela de Design](../ide/media/uwp-toolbox-add-button-control.png)

  Se você examinar o código no Editor de XAML, verá que o botão também foi adicionado lá:

  ![Clique no controle de Botão e arraste-o para a tela de Design](../ide/media/uwp-xaml-control-code-window.png)

### <a name="add-a-label-to-the-button"></a>Adicionar um rótulo para o botão

1. No Editor de XAML, altere o valor de Conteúdo do Botão de "Botão" para "Olá, Mundo!"

   ![Altere o valor do conteúdo do botão para Olá, Mundo](../ide/media/uwp-change-button-text-in-xaml-code-window.png)

2. Observe que o botão no Designer XAML também é alterado.

   ![O botão é alterado para Olá, Mundo na tela de design](../ide/media/uwp-button-text-change-in-design-canvas.png)

### <a name="add-an-event-handler"></a>Adicionar um manipulador de eventos

O termo "Manipulador de eventos" parece complicado, mas é apenas outro nome para o código que é chamado quando ocorre um evento. Nesse caso, ele adiciona uma ação para o "Olá, Mundo!" .

1. Clique duas vezes no controle de botão na tela de design.

2.  Edite o código do manipulador de eventos em *MainPage.xaml.cs*, a página code-behind.

 É aqui que as coisas ficam interessantes. O manipulador de eventos padrão tem esta aparência:

   ![O manipulador de eventos Button_Click padrão ](../ide/media/uwp-button-click-code.png)

 Vamos alterá-lo, para que fique assim:

    ![O novo manipulador de eventos Button_Click assíncrono ](../ide/media/uwp-add-hello-world-async-code.png)

  Aqui está o código a ser copiado e colado:

  ```C#
  private async void Button_Click(object sender, RoutedEventArgs e)
         {
             MediaElement mediaElement = new MediaElement();
             var synth = new Windows.Media.SpeechSynthesis.SpeechSynthesizer();
             Windows.Media.SpeechSynthesis.SpeechSynthesisStream stream = await synth.SynthesizeTextToStreamAsync("Hello, World!");
             mediaElement.SetSource(stream, stream.ContentType);
             mediaElement.Play();
         }
  ```

#### <a name="what-did-we-just-do"></a>O que nós acabamos de fazer?

O código usa algumas APIs do Windows para criar um objeto de sintetização de voz e, em seguida, fornece um texto para ele dizer. (Para obter mais informações de como usar SpeechSynthesis, veja <xref:System.Speech.Synthesis>.)

## <a name="run-the-application"></a>Executar o aplicativo

É hora de criar, implantar e iniciar o aplicativo UWP "Olá, Mundo" para ver como ele é e como ele soa. Veja como.

1. Escolha **Computador Local** para iniciar o aplicativo.

   ![Clique em um computador local para iniciar e depurar seu aplicativo UWP](../ide/media/uwp-start-or-debug.png "Clique em um computador local para iniciar e depurar seu aplicativo UWP")

   (Como alternativa, você pode escolher **Depurar** > **Iniciar Depuração** na barra de menus ou pressionar **F5** para iniciar seu aplicativo.)

2. Veja o aplicativo, que aparece logo depois que uma tela inicial desaparece. O aplicativo deve ser semelhante a este:

   ![Um aplicativo UWP "Olá, Mundo"](../ide/media/uwp-hello-world-app.png)

3. Clique no botão **Olá, Mundo**.

 Seu dispositivo Windows 10 dirá literalmente "Olá, Mundo!"

4. Para fechar o aplicativo, clique no botão **Parar Depuração** na barra de ferramentas. (Como alternativa, escolha **Depurar** > **Parar depuração** na barra de menus ou pressione **Shift** + **F5**.)

## <a name="next-steps"></a>Próximas etapas

Parabéns por concluir este Guia de Início Rápido! Esperamos que você tenha aprendido algumas noções básicas sobre a UWP e o IDE do Visual Studio. Para saber mais, continue com o tutorial a seguir:

> [!div class="nextstepaction"]
> [Criar uma interface do usuário](/windows/uwp/design/basics/xaml-basics-ui)
