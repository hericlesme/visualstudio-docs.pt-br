---
title: Introdução ao C# e ao ASP.NET Core no Visual Studio
description: Saiba como criar um aplicativo Web do ASP.NET Core no Visual Studio com C#, passo a passo.
ms.custom: ''
ms.date: 09/17/2018
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: tutorial
ms.devlang: CSharp
author: TerryGLee
ms.author: tglee
manager: douge
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: d0e337ebb97b487adfd79be43ddc1301612ba090
ms.sourcegitcommit: 9765b3fcf89375ca499afd9fc42cf4645b66a8a2
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/20/2018
ms.locfileid: "46496110"
---
# <a name="tutorial-get-started-with-c-and-aspnet-core-in-visual-studio"></a>Tutorial: Introdução ao C# e ao ASP.NET Core no Visual Studio

Neste tutorial para desenvolvimento em C# com ASP.NET Core usando o Visual Studio, você criará um aplicativo Web ASP.NET Core em C#, fará alterações, explorará alguns recursos do IDE e então executará o aplicativo.

Se você ainda não tiver instalado o Visual Studio, acesse a página [Downloads do Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) para instalá-lo gratuitamente.

## <a name="create-a-project"></a>Criar um projeto

Primeiro, você criará um projeto ASP.NET Core. O tipo de projeto vem com todos os arquivos de modelo necessários para um site totalmente funcional, mesmo antes que você adicione qualquer coisa.

1. Abra o Visual Studio 2017.

2. Na barra de menus superior, escolha **Arquivo** > **Novo** > **Projeto**. 

3. Na caixa de diálogo **Novo Projeto** no painel esquerdo, expanda **Visual C#**, expanda **Web** e escolha **.NET Core**. No painel central, escolha **Aplicativo Web ASP.NET Core**. Em seguida, nomeie o arquivo *MyCoreApp* e escolha **OK**.

   ![Modelo de projeto do aplicativo Web do ASP.NET Core na caixa de diálogo Novo projeto no IDE do Visual Studio](../ide/media/csharp-aspnet-choose-template-name-razor-mycoreapp-file.png)

### <a name="add-a-workload-optional"></a>Adicionar uma carga de trabalho (opcional)

Se o modelo de projeto **Aplicativo Web do ASP.NET Core** não for exibido, você poderá obtê-lo adicionando a carga de trabalho **Desenvolvimento ASP.NET e Web**. Você pode adicionar essa carga de trabalho de uma das duas maneiras, dependendo de quais atualizações do Visual Studio 2017 estão instaladas no seu computador.

#### <a name="option-1-use-the-new-project-dialog-box"></a>Opção 1: usar a caixa de diálogo Novo Projeto

1. Clique no link **Abrir o Instalador do Visual Studio** no painel esquerdo da caixa de diálogo **Novo Projeto**.

   ![Clique no link Abrir Instalador do Visual Studio na caixa de diálogo Novo Projeto](../ide/media/open-visual-studio-installer-mycoreapp.png)

1. O Instalador do Visual Studio é iniciado. Escolha a carga de trabalho **ASP.NET e desenvolvimento para a Web** e, em seguida, selecione **Modificar**.

   ![Carga de trabalho de desenvolvimento multiplataforma do .NET Core no Instalador do Visual Studio](../ide/media/quickstart-aspnet-workload.png)

   (Talvez você precise fechar o Visual Studio antes de continuar a instalar a nova carga de trabalho.)

#### <a name="option-2-use-the-tools-menu-bar"></a>Opção 2: usar a barra de menus Ferramentas

1. Cancele a caixa de diálogo **Novo Projeto**. Em seguida, na barra de menus superior, escolha **Ferramentas** > **Obter Ferramentas e Recursos**.

1. O Instalador do Visual Studio é iniciado. Escolha a carga de trabalho **ASP.NET e desenvolvimento para a Web** e, em seguida, selecione **Modificar**.

   (Talvez você precise fechar o Visual Studio antes de continuar a instalar a nova carga de trabalho.)

### <a name="add-a-project-template"></a>Adicionar um modelo de projeto

1. Na caixa de diálogo **Novo Aplicativo Web ASP.NET Core**, escolha o modelo de projeto **Aplicativo Web**.

1. Verifique se o **ASP.NET Core 2.1** aparece no menu suspenso superior. Em seguida, escolha **OK**.

   ![Caixa de diálogo Novo Aplicativo Web ASP.NET Core](../ide/media/new-project-csharp-aspnet-razor-web-app.png)

### <a name="about-your-solution"></a>Sobre sua solução

Esta solução segue o padrão de design da **Página do Razor**. Ele é diferente do padrão de design [Model-View-Controller (MVC)](/aspnet/core/tutorials/first-mvc-app/start-mvc?view=aspnetcore-2.1&tabs=aspnetcore2x) que é simplificado para incluir o código do modelo e do controlador na própria página do Razor.

## <a name="tour-your-solution"></a>Fazer tour da sua solução

 1. O modelo de projeto cria uma solução com um único projeto ASP.NET Core chamado _MyCoreApp_. Escolha a guia **Gerenciador de Soluções** para exibir seu conteúdo.

    ![A solução do Gerenciador de Soluções do ASP.NET no Visual Studio para o Razor Pages é denominada MyCoreApp](../ide/media/csharp-aspnet-razor-solution-explorer-mycoreapp.png)

 1. Expanda a pasta **Páginas** e depois *About.cshtml*.

     ![O arquivo About.cshtml no Gerenciador de Soluções do Visual Studio](../ide/media/csharp-aspnet-razor-solution-explorer-aboutcshtml.png)

 1. Visualize o arquivo **About.cshtml** no editor de códigos.

     ![Visualizar o arquivo About.cshtml no editor de códigos do Visual Studio](../ide/media/csharp-aspnet-razor-aboutcshtml-mycoreapp-code.png)

 1. Escolha o arquivo **About.cshtml.cs**.

     ![Escolher o arquivo About.cs no editor de códigos do Visual Studio](../ide/media/csharp-aspnet-razor-solution-explorer-aboutcshtmlcs.png)

 1. Visualize o arquivo **About.cs** no editor de códigos.

     ![Visualizar o arquivo About.cshtml no editor de códigos do Visual Studio](../ide/media/csharp-aspnet-razor-aboutcshtmlcs-mycoreapp-code.png)

 1. O projeto também contém a pasta **wwwroot** que é a raiz do site. Expanda a pasta para exibir seu conteúdo.

     ![Pasta wwwroot no Gerenciador de Soluções no Visual Studio](../ide/media/csharp-aspnet-razor-solution-explorer-wwwroot.png)

    Você pode colocar o conteúdo do site estático, como CSS, imagens e bibliotecas JavaScript, diretamente nos caminhos em que deseja.

 1. O projeto também contém os arquivos de configuração que gerenciam o aplicativo web em tempo de execução. A [configuração](/aspnet/core/fundamentals/configuration) de aplicativo padrão é armazenada em *appsettings.json*. No entanto, você pode substituir essas configurações usando *appsettings.Development.json*. Expanda o arquivo **appsettings.json** para exibir o arquivo **appsettings.Development.json**.

     ![Arquivos de configuração no Gerenciador de Soluções no Visual Studio](../ide/media/csharp-aspnet-razor-solution-explorer-appsettingsjson.png)

## <a name="run-debug-and-make-changes"></a>Executar, depurar e fazer alterações

1. Escolha o botão **IIS Express** no IDE para compilar e executar o aplicativo no modo de Depuração. Como alternativa, pressione **F5** ou escolha **Depurar** > **Iniciar depuração** na barra de menus.

     ![Selecionar o botão IIS Express no Visual Studio](../ide/media/csharp-aspnet-razor-iisexpress.png)

     > [!NOTE]
     > Se você receber uma mensagem de erro que diz **Não é possível se conectar ao servidor Web “IIS Express”**, feche o Visual Studio e abra-o usando a opção **Executar como administrador** clicando com o botão direito do mouse ou no menu de contexto. Em seguida, execute o aplicativo novamente.

1. O Visual Studio abre uma janela do navegador. Você deve vê-los na **Página Inicial** e nas páginas **Sobre** e **Contato** na barra de menus. Se isso não ocorrer, escolha o item de menu "hambúrguer" para exibi-los.

    ![Selecione o item de menu "hambúrguer" na barra de menu em seu aplicativo web](../ide/media/csharp-aspnet-razor-browser-page.png)

1. Escolha **Sobre** na barra de menus.

   ![Selecione Sobre na barra de menus da janela do navegador do seu aplicativo](../ide/media/csharp-aspnet-razor-browser-page-about-menu.png)

   Entre outras coisas, a página **Sobre** no navegador renderiza o texto definido no arquivo *About.cshtml*.

   ![Exiba o texto na página Sobre](../ide/media/csharp-aspnet-razor-browser-page-about.png)

1. Mantenha a janela do navegador aberta e retorne ao Visual Studio.

1. No Visual Studio, escolha **About.cshtml**. Em seguida, exclua a palavra _alterado_ e, em seu lugar, adicione as palavras _arquivo e diretório_.

    ![Alterar o texto no arquivo About.cshtml](../ide/media/csharp-aspnet-razor-aboutcshtml-mycoreapp-code-changed.png)

1. Escolha **About.cshtml.cs**. Em seguida, limpe as diretivas `using` na parte superior do arquivo usando o seguinte atalho:

   Escolha uma das diretivas `using` esmaecidas, e será exibida a lâmpada [Ações Rápidas](../ide/quick-actions.md) logo abaixo da seta ou na margem esquerda. Escolha a lâmpada e, em seguida, escolha **Remover Usings Desnecessários**.

   ![Remover usos desnecessários no arquivo About.cshtml.cs](../ide/media/csharp-aspnet-razor-remove-unnecessary-usings.png)

     O Visual Studio exclui as diretivas `using` desnecessárias do arquivo.

1. Em seguida, no método `OnGet()`, altere o corpo para o código a seguir:

     ```csharp
     public void OnGet()
     {
         string directory = Environment.CurrentDirectory;
     Message = String.Format("Your directory is {0}.", directory);
     }
    ```
1. Observe que dois sublinhados ondulados são exibidos sob **Ambiente** e **Cadeia de caracteres**. Os sublinhados ondulados são exibidos porque esses tipos não estão no escopo.

   ![Os erros são marcados com sublinhados ondulados no método OnGet](../ide/media/csharp-aspnet-razor-add-new-on-get-method.png)

    Abra a barra de ferramentas **Lista de Erros** para ver os mesmos erros listados. (Se a barra de ferramentas **Lista de Erros** não for exibida, escolha **Exibir** > **Lista de Erros** na barra de menus superior.)

   ![Lista de Erros no Visual Studio](../ide/media/csharp-aspnet-razor-error-list.png)

1. Vamos corrigir isso. No editor de códigos, coloque o cursor na linha que contém o erro e escolha a lâmpada Ações Rápidas na margem esquerda. No menu suspenso, escolha **using System;** para adicionar essa diretiva no topo do arquivo e resolver os erros.

   ![Adicionar a diretiva "using System;"](../ide/media/csharp-aspnet-razor-add-usings.png)

1. Pressione **Ctrl**+**S** para salvar as alterações e atualizar o aplicativo no navegador da web.

1. Na parte superior do site, escolha **Sobre** para ver as alterações.

   ![Exibir a página Sobre atualizada que inclui o texto alterado](../ide/media/csharp-aspnet-razor-browser-page-about-changed.png)

1. Feche o navegador da web, pressione **Shift**+**F5** para interromper o modo de depuração e, em seguida, feche o Visual Studio.

## <a name="quick-answers-faq"></a>Perguntas frequentes com respostas rápidas

Aqui estão algumas perguntas frequentes rápidas para destacar alguns conceitos principais.

### <a name="what-is-c"></a>O que é C#?

[C#](/dotnet/csharp/getting-started/introduction-to-the-csharp-language-and-the-net-framework) é uma linguagem de programação fortemente tipada e orientada a objeto projetada para ser robusta e fácil de aprender.

### <a name="what-is-aspnet-core"></a>O que é ASP.NET Core?

O ASP.NET Core é uma estrutura de software livre e de multiplataforma para a compilação de aplicativos modernos conectados à Internet, como serviços e aplicativos Web. Aplicativos ASP.NET Core podem ser executados no .NET Core ou o .NET Framework. Você pode desenvolver e executar aplicativos ASP.NET Core de multiplataforma no Windows, Mac e Linux. O ASP.NET Core é um software livre no [GitHub](https://github.com/aspnet/home).

### <a name="what-is-visual-studio"></a>O que é o Visual Studio?

Visual Studio é um pacote de desenvolvimento integrado de ferramentas de produtividade para desenvolvedores. Pense nele como um programa que você pode usar para criar programas e aplicativos.

## <a name="next-steps"></a>Próximas etapas

Parabéns por concluir este tutorial. Esperamos que você tenha aprendido um pouco sobre o C#, o ASP.NET Core e o IDE do Visual Studio. Para saber mais sobre como criar um aplicativo Web ou site em C# com o ASP.NET, continue com os tutoriais a seguir:

> [!div class="nextstepaction"]
> [Criar um aplicativo Web Páginas Razor com o ASP.NET Core](/aspnet/core/tutorials/razor-pages/?view=aspnetcore-2.1)

## <a name="see-also"></a>Consulte também

[Publicar seu aplicativo Web no Serviço de Aplicativo do Azure usando o Visual Studio](..//deployment/quickstart-deploy-to-azure.md)