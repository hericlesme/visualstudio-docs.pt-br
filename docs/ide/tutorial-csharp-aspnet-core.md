---
title: Introdução ao C# e ao ASP.NET Core no Visual Studio
description: Saiba como criar um aplicativo Web do ASP.NET Core no Visual Studio com C#, passo a passo.
ms.custom: ''
ms.date: 08/10/2018
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
ms.openlocfilehash: fb1532a76d9bc530146ba5a0f563bcaa9389226c
ms.sourcegitcommit: db94ca7a621879f98d4c6aeefd5e27da1091a742
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/13/2018
ms.locfileid: "42627167"
---
# <a name="tutorial-get-started-with-c-and-aspnet-core-in-visual-studio"></a>Tutorial: Introdução ao C# e ao ASP.NET Core no Visual Studio

Neste tutorial para desenvolvimento em C# com ASP.NET Core usando o Visual Studio, você criará um aplicativo Web ASP.NET Core em C#, fará alterações, explorará alguns recursos do IDE e executará o aplicativo.

Se você ainda não tiver instalado o Visual Studio, acesse a página [Downloads do Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) para instalá-lo gratuitamente.

## <a name="create-a-project"></a>Criar um projeto

Primeiro, você criará um projeto ASP.NET Core. O tipo de projeto vem com todos os arquivos de modelo, que você precisará para um site, mesmo sem você adicionar nada.

1. Abra o Visual Studio 2017.

2. Na barra de menus superior, escolha **Arquivo** > **Novo** > **Projeto**. 

3. Na caixa de diálogo **Novo Projeto** no painel esquerdo, expanda **Visual C#**, expanda **Web** e escolha **.NET Core**. No painel central, escolha **Aplicativo Web ASP.NET Core**. Em seguida, nomeie o arquivo *MyCoreApp* e escolha **OK**.

   ![Modelo de projeto do aplicativo Web do ASP.NET Core na caixa de diálogo Novo projeto no IDE do Visual Studio](../ide/media/csharp-aspnet-choose-template-name-mycoreapp-mvc.png)

### <a name="add-a-workload-optional"></a>Adicionar uma carga de trabalho (opcional)

Se o modelo de projeto **Aplicativo Web do ASP.NET Core** não for exibido, você poderá obtê-lo adicionando a carga de trabalho **Desenvolvimento ASP.NET e Web**. Você pode adicionar essa carga de trabalho de uma das duas maneiras, dependendo de quais atualizações do Visual Studio 2017 estão instaladas no seu computador.

#### <a name="option-1-use-the-new-project-dialog-box"></a>Opção 1: usar a caixa de diálogo Novo Projeto

1. Clique no link **Abrir o Instalador do Visual Studio** no painel esquerdo da caixa de diálogo **Novo Projeto**.

   ![Clique no link Abrir Instalador do Visual Studio na caixa de diálogo Novo Projeto](../ide/media/vs-open-visual-studio-installer-generic.png)

1. O Instalador do Visual Studio é iniciado. Escolha a carga de trabalho **ASP.NET e desenvolvimento para a Web** e, em seguida, selecione **Modificar**.

   ![Carga de trabalho de desenvolvimento multiplataforma do .NET Core no Instalador do Visual Studio](../ide/media/quickstart-aspnet-workload.png)

   (Talvez você precise fechar o Visual Studio antes de continuar a instalar a nova carga de trabalho.)

#### <a name="option-2-use-the-tools-menu-bar"></a>Opção 2: usar a barra de menus Ferramentas

1. Cancele a caixa de diálogo **Novo Projeto**. Em seguida, na barra de menus superior, escolha **Ferramentas** > **Obter Ferramentas e Recursos**.

1. O Instalador do Visual Studio é iniciado. Escolha a carga de trabalho **ASP.NET e desenvolvimento para a Web** e, em seguida, selecione **Modificar**.

   (Talvez você precise fechar o Visual Studio antes de continuar a instalar a nova carga de trabalho.)

### <a name="add-a-project-template"></a>Adicionar um modelo de projeto

1. Na caixa de diálogo **Novo Aplicativo Web do ASP.NET Core**, escolha o modelo de projeto **Aplicativo Web (Modelo-Exibição-Controlador)**.

1. Verifique se o **ASP.NET Core 2.0** aparece no menu suspenso superior. Em seguida, escolha **OK**.

   ![Caixa de diálogo Novo Aplicativo Web ASP.NET Core](../ide/media/new-project-csharp-aspnet-web-app-mvc.png)

### <a name="about-your-solution"></a>Sobre sua solução

Essa solução segue o padrão de arquitetura MVC (Modelo-Exibição-Controlador) que separa um aplicativo em três componentes principais:

* **Modelos** são classes que representam os dados do aplicativo. As classes de modelo usam a lógica de validação para impor regras de negócio aos dados. Normalmente, os objetos de modelo recuperam e armazenam o estado do modelo em um banco de dados.
* **Exibições** são os componentes que exibem a interface do usuário do aplicativo. Em geral, essa interface do usuário exibe os dados de modelo.
* **Controladores** são classes que manipulam as solicitações do navegador. Elas recuperam dados de modelo e chamam modelos de exibição que retornam uma resposta. Em um aplicativo MVC, a exibição mostra apenas informações; o controlador manipula e responde à entrada e à interação do usuário.

O padrão MVC ajuda a criar aplicativos que são mais fáceis de testar e atualizar do que aplicativos monolíticos tradicionais.

## <a name="tour-your-solution"></a>Fazer tour da sua solução

 1. O modelo de projeto cria uma solução com um único projeto ASP.NET Core chamado **MyCoreApp**. Expanda o nó do projeto para expor seu conteúdo.

    ![Gerenciador de Soluções do ASP.NET no Visual Studio](../ide/media/csharp-aspnet-solution-explorer-mycoreapp-mvc.png)

 1. Abra o arquivo *HomeController.cs* da pasta **Controladores**.

     ![Arquivo HomeController.cs no Gerenciador de Soluções no Visual Studio](../ide/media/csharp-aspnet-solution-explorer-home-controller.png)

 1. Exiba o arquivo *HomeController.cs*.

     ![HomeController.cs na janela de código do Visual Studio](../ide/media/csharp-aspnet-home-controller-code.png)

 1. O projeto também tem uma pasta **Exibições** que contém as subpastas que são mapeadas para cada controlador. Por exemplo, o arquivo de exibição CSHTML (uma extensão de HTML) para o caminho */Home/About* seria em *Views/Home/About.cshtml*. Abra esse arquivo.

     ![Arquivo About.cshtml no Gerenciador de Soluções no Visual Studio](../ide/media/csharp-aspnet-solution-explorer-view-about.png)

    Esse arquivo CSHTML usa a sintaxe Razor para renderizar HTML com base em uma combinação de marcas padrão e C# embutido.

     ![About.cshtml na janela de código do Visual Studio](../ide/media/csharp-aspnet-about-cshtml-code.png)

    >[!NOTE]
    > Para saber mais sobre o Razor, confira a página [Introdução ao C# e ao ASP.NET Core no Visual Studio usando a sintaxe Razor](/aspnet/web-pages/overview/getting-started/introducing-razor-syntax-c).

 1. O projeto também contém uma pasta **wwwroot** que é a raiz do site. Expanda a pasta para exibir seu conteúdo.

     ![Pasta wwwroot no Gerenciador de Soluções no Visual Studio](../ide/media/csharp-aspnet-solution-wwwroot.png)

    Você pode colocar o conteúdo do site estático, como CSS, imagens e bibliotecas JavaScript, diretamente nos caminhos em que deseja.

 1. Há vários arquivos de configuração que gerenciam o projeto, seus pacotes e o aplicativo no tempo de execução. Por exemplo, a [configuração](/aspnet/core/fundamentals/configuration) de aplicativo padrão é armazenada em *appsettings.json*. No entanto, você pode substituir essas configurações usando *appsettings.Development.json*. Expanda o arquivo **appsettings.json** para exibir o arquivo **appsettings.Development.json**.

     ![Arquivos de configuração no Gerenciador de Soluções no Visual Studio](../ide/media/csharp-aspnet-solution-explorer-config-files.png)

## <a name="run-debug-and-make-changes"></a>Executar, depurar e fazer alterações

1. Escolha o botão **IIS Express** no IDE para compilar e executar o aplicativo no modo de Depuração. (Como alternativa, pressione **F5** ou escolha **Depurar > Iniciar depuração** na barra de menus.)

     ![Selecionar o botão IIS Express no Visual Studio](../ide/media/csharp-aspnet-iis-express-button.png)

     > [!NOTE]
     > Se você receber uma mensagem de erro que diz **Não é possível se conectar ao servidor Web “IIS Express”**, feche o Visual Studio e abra-o usando a opção **Executar como administrador** clicando com o botão direito do mouse ou no menu de contexto. Em seguida, execute o aplicativo novamente.

1. O Visual Studio abre uma janela do navegador. Selecione **Sobre**.

   ![Selecione Sobre na janela do navegador para seu aplicativo](../ide/media/csharp-aspnet-browser-page.png)

   Entre outras coisas, a página **Sobre** no browser renderiza o texto definido no arquivo *HomeController.cs*.

   ![Exiba o texto na página Sobre](../ide/media/csharp-aspnet-browser-page-about.png)

1. Mantenha a janela do navegador aberta e retorne ao Visual Studio. Abra *Controllers/HomeController.cs* se ainda não estiver aberto.

   ![Abra o arquivo HomeController.cs no Gerenciador de Soluções no Visual Studio](../ide/media/csharp-aspnet-solution-explorer-home-controller.png)

1. Definir um ponto de interrupção na primeira linha do método **Sobre**. Para fazer isso, clique na margem ou defina o cursor na linha e pressione **F9**.

   Essa linha define alguns dados na coleção **ViewData** que é renderizada na página CSHTML em *Views/Home/About.cshtml*.

   ![Defina um ponto de interrupção na primeira linha do método Sobre em About.cshtml.  ](../ide/media/csharp-aspnet-home-controller-code-set-breakpoint.png)

1. Retorne ao browser e atualize a página **Sobre**. Isso disparará o ponto de interrupção no Visual Studio.

1. No Visual Studio, passe o mouse sobre o membro **ViewData** para exibir seus dados.

   ![Exiba o membro ViewData do método Sobre para obter mais informações](../ide/media/csharp-aspnet-home-controller-view-breakpoint-info.png)

1. Remova o ponto de interrupção do aplicativo usando o mesmo método que você usou para adicioná-lo.

1. Abra *Views/Home/About.cshtml*.

   ![Selecione About.cshtml no Gerenciador de Soluções](../ide/media/csharp-aspnet-solution-explorer-view-about.png)

1. Altere o texto **“adicional”** para **“alterado”** e salve o arquivo.

   ![Altere o texto que mostra “adicional” para “alterado”](../ide/media/csharp-aspnet-about-cshtml-code-change.png)

1. Retornar à janela do navegador para ver o texto atualizado. (Atualize o navegador se o texto que você alterou não aparecer.)

    ![Atualizar a janela do navegador para ver o texto alterado](../ide/media/csharp-aspnet-browser-page-about-changed.png)

1. Escolha o botão **Parar depuração** da barra de ferramentas para interromper a depuração. (Como alternativa, pressione **Shift**+**F5** ou escolha **Depurar** > **Parar depuração** na barra de menus.)

   ![Selecionar o botão Parar Depuração na barra de ferramentas](../ide/media/csharp-aspnet-stop-debugging.png)

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
> [Criar um aplicativo Web MVC com o ASP.NET Core](/aspnet/core/tutorials/first-mvc-app/start-mvc?view=aspnetcore-2.1&tabs=aspnetcore2x)
>
> [!div class="nextstepaction"]
> [Criar um aplicativo Web Páginas Razor com o ASP.NET Core](/aspnet/core/tutorials/razor-pages/?view=aspnetcore-2.1)

## <a name="see-also"></a>Consulte também

[Publicar seu aplicativo Web no Serviço de Aplicativo do Azure usando o Visual Studio](..//deployment/quickstart-deploy-to-azure.md)