---
title: Introdução a C# e ASP.NET Core no Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 12/11/2017
ms.technology:
- vs-acquisition
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
ms.openlocfilehash: b3760c922e540837d0e9452efc8d44762eeeb3af
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="getting-started-with-c-and-aspnet-in-visual-studio"></a>Introdução a C# e ASP.NET no Visual Studio
Neste tutorial para desenvolvimento em C# com ASP.NET Core usando o Visual Studio, você criará um aplicativo Web C# ASP.NET Core, adicionará código a ele, explorará alguns recursos do IDE e executará o aplicativo.

Se você ainda não tiver instalado o Visual Studio, acesse a página [Downloads do Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) para instalá-lo gratuitamente.

## <a name="before-you-begin"></a>Antes de começar
Aqui está algumas perguntas frequentes rápidas para apresentar alguns conceitos principais.
### <a name="what-is-c"></a>O que é C#?
[C#](/dotnet/csharp/getting-started/introduction-to-the-csharp-language-and-the-net-framework) é uma linguagem de programação fortemente tipada e orientada a objeto projetada para ser robusta e fácil de aprender.
### <a name="what-is-aspnet-core"></a>O que é ASP.NET Core?
O ASP.NET Core é uma estrutura de software livre e de multiplataforma para a compilação de aplicativos modernos conectados à Internet, como serviços e aplicativos Web. Aplicativos ASP.NET Core podem ser executados no .NET Core ou o .NET Framework. Você pode desenvolver e executar aplicativos ASP.NET Core de multiplataforma no Windows, Mac e Linux. O ASP.NET Core é um software livre no [GitHub](https://github.com/aspnet/home).
### <a name="what-is-visual-studio"></a>O que é o Visual Studio?
Visual Studio é um pacote de desenvolvimento integrado de ferramentas de produtividade para desenvolvedores. Pense nele como um programa que você pode usar para criar programas e aplicativos.  

## <a name="start-developing"></a>Começar a desenvolver
Pronto para começar a desenvolver? Vamos lá.

### <a name="create-a-project"></a>Criar um projeto
Primeiro, você criará um projeto ASP.NET Core. O tipo de projeto inclui todos os arquivos de modelo que você precisará, mesmo sem adicionar nada.

1. Abra o Visual Studio 2017.

2. Na barra de menus superior, selecione **Arquivo** > **Novo** > **Projeto...**.

3. Na caixa de diálogo **Novo Projeto** no painel esquerdo, expanda **Visual C#**, expanda **Web** e escolha **.NET Core**. No painel central, escolha **Aplicativo Web ASP.NET Core** nomeie o arquivo como *MyCoreApp* e escolha **OK**.   

   ![Modelo de projeto do aplicativo Web do ASP.NET Core na caixa de diálogo Novo projeto no IDE do Visual Studio](../ide/media/new-project-csharp-aspnet-mycoreapp.png)

#### <a name="add-a-workload-optional"></a>Adicionar uma carga de trabalho (opcional)
Se o modelo de projeto **Aplicativo Web do ASP.NET Core** não for exibido, você poderá obtê-lo adicionando a carga de trabalho **Desenvolvimento ASP.NET e Web**. Você pode adicionar essa carga de trabalho de uma das duas maneiras, dependendo de quais atualizações do Visual Studio 2017 estão instaladas no seu computador.

##### <a name="option-1-use-the-new-project-dialog-box"></a>Opção 1: usar a caixa de diálogo Novo Projeto
1. Clique no link **Abrir o Instalador do Visual Studio** no painel esquerdo da caixa de diálogo **Novo Projeto**.

  ![Clique no link Abrir o Instalador do Visual Studio na caixa de diálogo Novo Projeto](../ide/media/vs-open-visual-studio-installer-generic.png)

2. O Instalador do Visual Studio é iniciado. Escolha a carga de trabalho **ASP.NET e desenvolvimento para a Web** e, em seguida, selecione **Modificar**.

   ![Carga de trabalho de desenvolvimento multiplataforma do .NET Core no Instalador do Visual Studio](../ide/media/asp-dot-net-web-dev-workload.png)

##### <a name="option-2-use-the-tools-menu-bar"></a>Opção 2: usar a barra de menus Ferramentas
1. Cancele a caixa de diálogo **Novo Projeto** e, na barra de menus superior, escolha **Ferramentas** > **Obter Ferramentas e Recursos...**.

2. O Instalador do Visual Studio é iniciado. Escolha a carga de trabalho **ASP.NET e desenvolvimento para a Web** e, em seguida, selecione **Modificar**.   

#### <a name="add-a-project-template"></a>Adicionar um modelo de projeto
1. Na caixa de diálogo **Novo Aplicativo Web do ASP.NET Core**, escolha o modelo de projeto **Aplicativo Web (Modelo-Exibição-Controlador)**.  

2. Selecione **ASP.NET Core 2.0** no menu suspenso superior. (Se o **ASP.NET Core 2.0** não aparecer na lista, instale-o seguindo o link **Baixar** que deve aparecer em uma barra amarela próxima à parte superior da caixa de diálogo.) Escolha **OK**.

   ![Caixa de diálogo Novo Aplicativo Web ASP.NET Core](../ide/media/new-project-csharp-aspnet-web-app-mvc.png)

### <a name="about-your-solution"></a>Sobre sua solução
Essa solução segue o padrão de arquitetura MVC (Modelo-Exibição-Controlador) que separa um aplicativo em três componentes principais:

* **Modelos** são classes que representam os dados do aplicativo. As classes de modelo usam a lógica de validação para impor regras de negócio aos dados. Normalmente, os objetos de modelo recuperam e armazenam o estado do modelo em um banco de dados.
* **Exibições** são os componentes que exibem a interface do usuário do aplicativo. Em geral, essa interface do usuário exibe os dados de modelo.
* **Controladores** são classes que manipulam as solicitações do navegador. Elas recuperam dados de modelo e chamam modelos de exibição que retornam uma resposta. Em um aplicativo MVC, a exibição mostra apenas informações; o controlador manipula e responde à entrada e à interação do usuário.

O padrão MVC ajuda a criar aplicativos que são mais fáceis de testar e atualizar do que aplicativos monolíticos tradicionais.

### <a name="tour-your-solution"></a>Fazer tour da sua solução
1. O modelo de projeto cria uma solução com um único projeto ASP.NET Core chamado **MyCoreApp**. Expanda o nó do projeto para expor seu conteúdo.

    ![Gerenciador de Soluções do ASP.NET no Visual Studio](../ide/media/csharp-aspnet-solution-explorer-mycoreapp.png)

1. Abra o arquivo **HomeController.cs** da pasta **Controladores**.

      ![Arquivo HomeController.cs no Gerenciador de Soluções no Visual Studio](../ide/media/csharp-aspnet-solution-explorer-home-controller.png)

2. Exibir o **HomeController.cs**

  ![HomeController.cs na janela de código do Visual Studio](../ide/media/csharp-aspnet-home-controller-code.png)

4. O projeto também tem uma pasta **Exibições** que contém outras pastas que são mapeados para cada controlador (bem como uma para exibições **Compartilhadas**). Por exemplo, o arquivo de exibição CSHTML (uma extensão de HTML) para o caminho **/Home/About** seria em **Views/Home/About.cshtml**. Abra esse arquivo.

  ![Arquivo About.cshtml no Gerenciador de Soluções no Visual Studio](../ide/media/csharp-aspnet-solution-explorer-view-about.png)

5. Esse arquivo CSHTML usa a sintaxe Razor para renderizar HTML com base em uma combinação de marcas padrão e C# embutido.

  ![About.cshtml na janela de código do Visual Studio](../ide/media/csharp-aspnet-about-cshtml-code.png)

 >[!NOTE]
 > Para saber mais sobre isso, consulte a página [Guia de Introdução com C# e ASP.NET usando a sintaxe Razor](/aspnet/web-pages/overview/getting-started/introducing-razor-syntax-c).

6. A solução também contém uma pasta **wwwroot** que será a raiz do seu site da Web. Você pode colocar o conteúdo estático do site, como CSS, imagens e bibliotecas JavaScript, diretamente nos caminhos de que você deseja que eles estejam quando o site for implantado.

 ![Pasta wwwroot no Gerenciador de Soluções no Visual Studio](../ide/media/csharp-aspnet-solution-wwwroot.png)

7. Também há uma variedade de arquivos de configuração que servem para gerenciar o projeto, seus pacotes e o aplicativo no tempo de execução. Por exemplo, a [configuração](/aspnet/core/fundamentals/configuration) de aplicativo padrão é armazenada em **appsettings.json**. No entanto, você pode substituir algumas ou todas essas configurações por ambiente, fornecendo um arquivo **appsettings.Development.json** para o ambiente de **Desenvolvimento**.

 ![Arquivos de configuração no Gerenciador de Soluções no Visual Studio](../ide/media/csharp-aspnet-solution-explorer-config-files.png)

## <a name="run-and-debug-the-application"></a>Executar e depurar o aplicativo

1. Escolha o botão **IIS Express** no IDE para compilar e executar o aplicativo no modo de Depuração. (Como alternativa, pressione **F5** ou escolha **Depurar > Iniciar depuração** na barra de menus.)

  ![Clique no botão IIS Express no Visual Studio](../ide/media/csharp-aspnet-iis-express-button.png)

  > [!NOTE]
  > Se você receber uma mensagem de erro que diz **Não é possível se conectar ao servidor Web “IIS Express”**, feche o Visual Studio e abra-o usando a opção **Executar como administrador** clicando com o botão direito do mouse ou no menu de contexto. Em seguida, execute o aplicativo novamente.

1. O Visual Studio abre uma janela do navegador. Selecione **Sobre**.

 ![Selecione Sobre na janela do navegador para seu aplicativo](../ide/media/csharp-aspnet-browser-page.png)

 Entre outras coisas, a página Sobre no navegador renderiza o texto que é definido no arquivo HomeController.cs.

   ![Exiba o texto na página Sobre](../ide/media/csharp-aspnet-browser-page-about.png)

1. Mantenha a janela do navegador aberta e retorne ao Visual Studio. Abra **Controllers/HomeController.cs** se ainda não estiver aberto.

 ![Abra o arquivo HomeController.cs no Gerenciador de Soluções no Visual Studio](../ide/media/csharp-aspnet-solution-explorer-home-controller.png)

1. Definir um ponto de interrupção na primeira linha do método **Sobre**. Para fazer isso, clique na margem ou defina o cursor na linha e pressione **F9**.

  Essa linha define alguns dados na coleção **ViewData** que é renderizada na página CSHTML em **Views/Home/About.cshtml**.

 ![Defina um ponto de interrupção na primeira linha do método Sobre em About.cshtml.  ](../ide/media/csharp-aspnet-home-controller-code-set-breakpoint.png)

1. Retorne para o navegador e atualize a página Sobre. Isso disparará o ponto de interrupção no Visual Studio.

1. No Visual Studio, passe o mouse sobre o membro **ViewData** para exibir seus dados.

 ![Exiba o membro ViewData do método Sobre para obter mais informações](../ide/media/csharp-aspnet-home-controller-view-breakpoint-info.png)

1. Remova o ponto de interrupção do aplicativo usando o mesmo método que você usou para adicioná-lo.

1. Abra **Views/Home/About.cshtml**.

 ![Selecione About.cshtml no Gerenciador de Soluções](../ide/media/csharp-aspnet-solution-explorer-view-about.png)

1. Altere o texto **“adicional”** para **“alterado”** e salve o arquivo.

 ![Altere o texto que mostra “adicional” para “alterado”](../ide/media/csharp-aspnet-about-cshtml-code-change.png)

1. Retornar à janela do navegador para ver o texto atualizado. (Atualize o navegador se o texto que você alterou não aparecer.)

  ![Atualizar a janela do navegador para ver o texto alterado](../ide/media/csharp-aspnet-browser-page-about-changed.png)

1. Escolha o botão **Parar depuração** da barra de ferramentas para interromper a depuração. (Como alternativa, pressione **Shift**+**F5** ou escolha **Depurar** > **Parar depuração** na barra de menus.)

 ![Clique no botão Parar Depuração na barra de ferramentas](../ide/media/csharp-aspnet-stop-debugging.png)

## <a name="next-steps"></a>Próximas etapas

Parabéns por concluir este tutorial. Esperamos que você tenha aprendido um pouco sobre o C#, o ASP.NET Core e o IDE do Visual Studio. Para saber ainda mais, continue com o tutorial a seguir.

 > [!div class="nextstepaction"]
 > [Introdução ao ASP.NET Core MVC e ao Visual Studio](/aspnet/core/tutorials/first-mvc-app/start-mvc?tabs=aspnetcore2x)
