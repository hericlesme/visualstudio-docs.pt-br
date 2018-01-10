---
title: "Visão geral do IDE do Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 11/09/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 5b289868d0cc27da76becf62a2bac51f02fa55c2
ms.sourcegitcommit: 5f436413bbb1e8aa18231eb5af210e7595401aa6
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2018
---
# <a name="visual-studio-ide-overview"></a>Visão geral do IDE do Visual Studio

O IDE (ambiente de desenvolvimento interativo) do Visual Studio é um painel de inicialização criativa que pode ser usado para exibir e editar quase todo tipo de código e, em seguida, para depurar, compilar e publicar aplicativos para Android, iOS, Windows, Web e nuvem. Há versões disponíveis para o Mac e Windows. Este tópico apresenta os recursos do IDE do Visual Studio. Vamos examinar algumas coisas que você pode fazer com o Visual Studio e como instalá-lo e usá-lo, criar um projeto simples, obter ponteiros no código de depuração e de implantação e fazer um tour pelas várias janelas de ferramentas.

## <a name="what-can-you-do-with-the-visual-studio-ide"></a>O que pode ser feito com o IDE do Visual Studio?

Você deseja criar um aplicativo para um telefone Android? Você pode fazer isso. E quanto à criação de um jogo de última geração com o C++? É possível fazer isso e muito, muito mais. O Visual Studio fornece modelos que ajudam você a criar sites, jogos, aplicativos de área de trabalho, aplicativos móveis, aplicativos para o Office e muito mais.

![Projetos do Visual Studio](../ide/media/VSIDE_Tour_Projects_List.png)

Se preferir, basta abrir algum código obtido praticamente de qualquer lugar e começar a trabalhar. Achou um projeto no GitHub que você gostou? Basta clonar o repositório, abri-lo no Visual Studio e começar a codificá-lo!

### <a name="create-mobile-apps"></a>Criar aplicativos móveis

É possível criar aplicativos móveis nativos para diferentes plataformas usando o Visual C# e o Xamarin ou o Visual C++ ou aplicativos híbridos usando o JavaScript com o Apache Cordova. É possível escrever jogos móveis para o Unity, Unreal, DirectX, Cocos e muito mais. O Visual Studio inclui um emulador do Android para ajudá-lo a executar e depurar aplicativos Android.

É possível aproveitar o poder da nuvem para seus aplicativos móveis criando serviços de aplicativos do Azure. Os serviços de aplicativos do Azure permitem que os aplicativos armazenem dados na nuvem, autentiquem usuários com segurança e escalem ou reduzam verticalmente seus recursos de forma automática para acomodar as necessidades do aplicativo e dos negócios. Para saber mais, consulte [Desenvolvimento de aplicativos móveis](https://www.visualstudio.com/vs/mobile-app-development/).

### <a name="create-cloud-apps-for-azure"></a>Criar aplicativos na nuvem para o Azure

O Visual Studio oferece um pacote de ferramentas que permite criar aplicativos habilitados para a nuvem com facilidade da plataforma Microsoft Azure. É possível configurar, compilar, depurar, empacotar e implantar aplicativos e serviços no Microsoft Azure diretamente por meio do IDE. Para obter as Ferramentas do Azure para .NET, selecione a carga de trabalho **desenvolvimento do Azure** ao instalar o Visual Studio. Para obter mais informações, consulte [Ferramentas do Visual Studio para o Azure](https://www.visualstudio.com/vs/azure-tools/).

Você pode aproveitar os serviços do Azure em seus aplicativos usando Serviços Conectados como:

- [Serviços Móveis do Azure](http://azure.microsoft.com/documentation/services/mobile-services/)

- [Armazenamento do Azure](http://azure.microsoft.com/documentation/services/storage/)

O [HockeyApp](https://www.visualstudio.com/hockey-app/) ajuda você a distribuir versões beta, coletar relatórios de falha em tempo real e obter comentários de usuários reais. Além disso, você pode integrar as APIs REST do Office 365 ao seu próprio aplicativo para se conectar aos dados armazenados na nuvem. Para obter mais informações, confira [estes exemplos do GitHub](https://github.com/OfficeDev/?utf8=%E2%9C%93&query=o365).

[Application Insights](https://marketplace.visualstudio.com/items?itemName=VisualStudioOnlineApplicationInsights.application-insights) ajuda a detectar e diagnosticar problemas de qualidade em seus aplicativos e serviços Web. O Application Insights também ajudará a entender o que os usuários realmente fazem com seu aplicativo para que você possa otimizar a experiência do usuário.

### <a name="create-apps-for-the-web"></a>Criar aplicativos para a Web

A Internet impulsiona nosso mundo moderno e o Visual Studio pode ajudá-lo a escrever aplicativos para ele. É possível criar aplicativos Web usando o ASP.NET, Node.js, Python, JavaScript e TypeScript. O Visual Studio reconhece estruturas Web como Angular, jQuery, Express e muito mais. O ASP.NET Core e o .NET Core são executados nos sistemas operacionais Windows, Mac e Linux. O [ASP.NET Core](http://www.asp.net/core/overview) é uma atualização importante para MVC, WebAPI e SignalR e é executado no Windows, no Mac e no Linux.  O ASP.NET Core foi projetado desde o princípio para fornecer a você uma pilha .NET enxuta e combinável para compilar serviços e aplicativos Web modernos baseados em nuvem.

Para obter mais informações, consulte [Ferramentas da Web modernas](https://www.visualstudio.com/vs/modern-web-tooling/).

### <a name="build-cross-platform-apps-and-games"></a>Criar jogos e aplicativos de plataforma cruzada

É possível usar o Visual Studio para criar aplicativos e jogos para o Android, iOS, Linux, Windows e outros dispositivos. Saiba mais sobre isso em [Cross-Platform Mobile Development](../cross-platform/cross-platform-mobile-development-in-visual-studio.md) (Desenvolvimento Móvel Multiplataforma). Os Aplicativos Universais do Windows ajudam você a aproveitar o código em várias plataformas. Consulte [Aplicativos Universais do Windows](https://dev.windows.com/en-us/windows-apps) para obter mais informações.

Escolha as ferramentas necessárias com base nos requisitos dos aplicativos e na linguagem que deseja usar:

- [Xamarin para Visual Studio](../cross-platform/build-apps-with-native-ui-using-xamarin-in-visual-studio.md): uma base de código comum em C# para todos os dispositivos.

- [Ferramentas do Visual Studio para Apache Cordova](../cross-platform/visual-studio-tools-for-apache-cordova.md): uma base de código comum para HTML, CSS e JavaScript ou Typescript.

- [Ferramentas do Visual Studio para Unity](../cross-platform/visual-studio-tools-for-unity.md): desenvolvimento de jogos 2D/3D em C#.

- [C++ para desenvolvimento multiplataforma](../cross-platform/visual-cpp-for-cross-platform-mobile-development.md): aplicativos e bibliotecas de códigos compartilhados em C++.

- [Emulador do Visual Studio para Android](../cross-platform/visual-studio-emulator-for-android.md): depure e teste aplicativos Android, independentemente do IDE.

[Crie jogos usando o Visual Studio](https://www.visualstudio.com/vs/game-development/) com ferramentas de desenvolvimento de jogos como DirectX, Unity, Unreal, Cocos e muito mais.

O Visual Studio pode fazer ajudar você a fazer muito mais coisas. Para obter uma lista mais completa, consulte [IDE do Visual Studio](https://www.visualstudio.com/vs/).

## <a name="install-the-visual-studio-ide"></a>Instalar o IDE do Visual Studio

Para começar, baixe o Visual Studio e instale-o no sistema. É possível baixá-lo em [Visual Studio 2017](https://www.visualstudio.com/vs/visual-studio-2017/).

Agora o Visual Studio está mais leve do que nunca! O instalador modular permite escolher e instalar *cargas de trabalho*, que são grupos de recursos necessários para a linguagem de programação ou para a plataforma de sua preferência. Essa estratégia ajuda a manter a superfície de instalação do Visual Studio menor do que nunca, o que significa que ele é instalado e atualizado mais rapidamente também.

Para seguir as etapas para criar um programa abaixo, selecione e instale a carga de trabalho **Desenvolvimento da Plataforma Universal do Windows**.

![Instalador do Visual Studio](../ide/media/vside_tour_install_dialog.png)

Além do desempenho aprimorado de instalação, o Visual Studio 2017 também apresenta tempos de inicialização e de carregamento do IDE mais curtos.

Para saber mais sobre como configurar o Visual Studio no sistema, consulte [Instalar o Visual Studio 2017](../install/install-visual-studio.md).

## <a name="sign-in"></a>Entrar

Ao iniciar o Visual Studio pela primeira vez, opcionalmente, é possível entrar usando sua conta da Microsoft ou sua conta corporativa ou de estudante. Estar conectado permite sincronizar as configurações do Visual Studio, como layouts de janela, em vários dispositivos. Ele também o conecta automaticamente aos serviços que podem ser necessários, como as assinaturas do Azure e o Visual Studio Team Services.

## <a name="create-a-program"></a>Criar um programa

Uma boa maneira de aprender sobre algo é usá-lo! Vamos nos aprofundar e criar um novo programa simples.

1. Abra o Visual Studio. No menu, escolha **Arquivo**, **Novo**, **Projeto**.

  ![captura de tela](../ide/media/VSIDE_Tour_NewProject1.png)

  Como alternativa, é possível criar um novo projeto usando a Página de Início. Para obter mais informações, consulte [Aproveite o Poder da Página Inicial Reprojetada (blog)](https://blogs.msdn.microsoft.com/visualstudio/2016/11/29/harness-the-power-of-the-redesigned-start-page/).

1. A caixa de diálogo **Novo Projeto** mostra vários modelos de projeto. Escolha a categoria **Universal do Windows** em **Visual C#**, escolha o modelo **Aplicativo em Branco (Universal do Windows)** e, em seguida, o botão **OK**.

  ![captura de tela](../ide/media/VSIDE_Tour_NewProject2.png)

  Isso cria um novo projeto de aplicativo em branco Universal do Windows usando o Visual C# e XAML como as linguagens de programação. Aguarde um pouco enquanto o Visual Studio configura o projeto para você. Se você precisar fornecer alguma informação, basta aceitar os valores padrão por enquanto.

1. Na caixa de diálogo **Novo Projeto Universal do Windows**, aceite os padrões escolhendo **OK**.

1. Em breve, você deverá ver algo parecido com a captura de tela a seguir. Os arquivos de projeto são listados no lado direito em uma janela chamada Gerenciador de Soluções.

  ![captura de tela](../ide/media/VSIDE_Tour_NewProject3.png)

1. No Gerenciador de Soluções, escolha o pequeno triângulo preto ao lado do arquivo MainPage.xaml para expandi-lo e você deverá ver um arquivo MainPage.xaml.cs abaixo dele. Escolha esse arquivo (que contém o código C#) para abri-lo.

  O código C# em MainPage.xaml.cs é exibido no editor de código no lado esquerdo da tela. Observe que a sintaxe do código é colorizada automaticamente para indicar diferentes tipos de código, como instruções ou comentários. Além disso, pequenas linhas verticais tracejadas no código indicam a correspondência de chaves e os números de linha ajudam a localizar o código posteriormente. É possível escolher os pequenos sinais de subtração demarcados para recolher ou expandir o código. Esse recurso de estrutura de tópicos do código permite ocultar os códigos desnecessários, ajudando a minimizar a desordem na tela.

  ![](../ide/media/VSIDE_Tour_NewProject3a.png)

  Há outros menus e outras janelas de ferramentas disponíveis, mas por enquanto, vamos seguir em frente.

1. Adicione um botão ao formulário XAML para fornecer aos usuários uma maneira de interagir com seu aplicativo. Para fazer isso, abra o arquivo MainPage.xaml. Isso mostra uma exibição dividida: um designer acima, para colocar os controles visualmente e uma exibição de código abaixo, que mostra o código XAML por atrás do designer. Ao executar o programa mais tarde, o que você verá no designer se tornará uma janela que será vista pelos usuários, um "formulário", sendo que o XAML subjacente determinará o que será exibido no formulário.

1. No lado esquerdo da tela, escolha a guia **Caixa de Ferramentas** para abrir a Caixa de Ferramentas. A Caixa de Ferramentas contém diversos controles visuais que podem ser adicionados a formulários. Por enquanto, vamos apenas adicionar um controle de botão.

1. Expanda a seção **Controles XAML Comuns** e, em seguida, arraste o controle de Botão para fora até a parte central do formulário. (A localização exata não é importante.)

  ![captura de tela](../ide/media/VSIDE_Tour_Toolbox.png)

  Quando terminar, você deverá ver algo parecido com o mostrado a seguir.

  ![captura de tela](../ide/media/VSIDE_Tour_XAMLButton.png)

  O botão está no designer e seu código subjacente (realçado) é adicionado automaticamente ao código XAML do designer.

1. Vamos alterar um pouco do código XAML. Renomeie o texto no código do botão de `Button` para `Hello!`.

  ![captura de tela](../ide/media/VSIDE_Tour_XAMLButton2.png)

1. Agora, inicie o aplicativo. É possível fazer isso ao clicar no botão **Iniciar** (![botão Iniciar](../ide/media/VSIDE_StartButton.png)) na barra de ferramentas ou na tecla **F5** ou, no menu, escolhendo **Depurar**, **Iniciar Depuração**.

  ![captura de tela](../ide/media/VSIDE_Tour_RunButton.png)

  O aplicativo inicia seu processo de build e as mensagens de status são exibidas na janela de Saída. Em breve, você deverá ver o formulário exibido com o botão nele. Agora você tem um aplicativo em execução.

  ![captura de tela](../ide/media/VSIDE_Tour_RunProject.png)

  Obviamente, ele não executa muitas ações no momento, mas é possível adicionar mais funcionalidades a ele mais tarde se desejar.

1. Quando terminar de executar o programa, escolha o botão Parar (![botão Parar](../ide/media/VSIDE_StopButton.png)) na barra de ferramentas para interrompê-lo.

Vamos recapitular o que você fez até agora: você criou um novo projeto Universal do Windows do C# no Visual Studio, exibiu seu código, adicionou um controle ao designer, alterou uma parte do código XAML e, por fim, executou o projeto. Embora o processo tenha sido simplificado para este exemplo, isso mostra algumas partes comuns do IDE do Visual Studio que você usará para desenvolver seus próprios aplicativos. Se desejar obter mais detalhes sobre esse exemplo, consulte [Criar um aplicativo “Olá, mundo” (XAML)](/windows/uwp/get-started/create-a-hello-world-app-xaml-universal).

## <a name="debug-test-and-improve-your-code"></a>Depurar, testar e melhorar o código

Nada acontece de forma perfeita o tempo todo. Quando você escrever o código, é necessário executá-lo e testá-lo para verificar o desempenho e se há bugs. O depurador de última geração do Visual Studio permite depurar o código em execução no projeto local, em um dispositivo remoto ou em um emulador, como aqueles para os dispositivos Android ou Windows Phone. Você pode percorrer o código em uma declaração por vez e inspecionar variáveis à medida que avança, você pode percorrer aplicativos com multithread e pode definir pontos de interrupção que são atingidos somente quando uma condição especificada for verdadeira. É possível monitorar os valores de variáveis enquanto o código é executado e muito mais. Tudo isso pode ser gerenciado no próprio editor de código, para que você não precise deixar o código.

![Depuração](../ide/media/VSIDE_Tour_Debugging.png)

Para testes, o Visual Studio oferece testes de unidade, IntelliTest, testes de carga e desempenho e muito mais. Para obter mais detalhes sobre o processo de depuração do Visual Studio, consulte [Tour pelos recursos do depurador](../debugger/debugger-feature-tour.md). Para saber mais sobre testes, consulte [Testing Tools and Scenarios](../test/developer-testing-scenarios.md) (Ferramentas de teste e cenários). Para saber mais sobre como melhorar o desempenho de seus aplicativos, consulte [Tour pelos recursos de criação de perfil](../profiling/profiling-feature-tour.md).

## <a name="deploy-your-finished-application"></a>Implantar o aplicativo concluído

Quando o aplicativo estiver pronto para ser implantado em usuários ou em clientes, o Visual Studio fornecerá as ferramentas para fazer isso, independentemente de você estar implantando na Microsoft Store, em um site do SharePoint ou com as tecnologias do InstallShield ou do Windows Installer. Ele é todo acessível por meio do IDE. Para obter mais informações, consulte [Implantação de aplicativos, serviços e componentes](../deployment/deploying-applications-services-and-components.md).

## <a name="quick-tour-of-the-ide"></a>Tour rápido pelo IDE

Para fornecer uma visão geral visual de alto nível do Visual Studio, a imagem a seguir mostra o Visual Studio com um projeto aberto, juntamente com várias janelas de ferramentas essenciais que provavelmente você usará:

- O [Gerenciador de Soluções](../ide/solutions-and-projects-in-visual-studio.md) permite exibir, navegar e gerenciar os arquivos de código. O Gerenciador de Soluções pode ajudar a organizar o código agrupando os arquivos em projetos e soluções.

- A janela [Editor](../ide/writing-code-in-the-code-and-text-editor.md), em que você provavelmente passará a maior parte do tempo, mostra o código e permite a edição do código-fonte e a criação de uma interface do usuário.

- A janela [Saída](../ide/reference/output-window.md) é onde o Visual Studio envia suas notificações, como mensagens de erro e de depuração, avisos do compilador, mensagens de status de publicação e mais. Cada fonte de mensagem tem uma guia própria.

- O [Team Explorer (VSTS)](/vsts/user-guide/work-team-explorer) permite que você controle itens de trabalho e compartilhe código com outras pessoas usando tecnologias de controle de versão como [Git](https://git-scm.com/) e [TFVC (Controle de Versão do Team Foundation)](/vsts/tfvc/overview).

- O [Cloud Explorer](/azure/vs-azure-tools-resources-managing-with-cloud-explorer) permite exibir e gerenciar seus recursos do Azure, como máquinas virtuais, tabelas, bancos de dados SQL e muito mais. Se uma determinada operação requer o portal do Azure, o Cloud Explorer fornece links que levam você até o local no portal do Azure que você precisa ir.

![O IDE do Visual Studio](../ide/media/visualstudioide.png)

Veja a seguir algumas outras funcionalidades de produtividade comuns do Visual Studio:

- A caixa de pesquisa [Início Rápido](../ide/reference/quick-launch-environment-options-dialog-box.md) é uma ótima maneira de encontrar rapidamente o que você precisa no Visual Studio. Comece inserindo o nome de qualquer coisa que esteja procurando e o Visual Studio listará resultados que levam você exatamente para o local desejado. O Início Rápido também mostra os links que iniciam o Instalador do Visual Studio para qualquer carga de trabalho ou componente individual.

  ![Caixa de pesquisa Início Rápido](../ide/media/VSIDE_Tour_QuickLaunch.png)

- [Refatoração](../ide/refactoring-in-visual-studio.md) inclui operações como renomeação inteligente de variáveis, mover linhas de código selecionadas para uma função distinta, mover o código para outros locais, reordenação de parâmetros de função e muito mais.

 ![Refatoração](../ide/media/VSIDE_refactor.png)

- **IntelliSense** é um termo abrangente para um conjunto de recursos populares que exibe informações de tipo sobre seu código diretamente no editor e, em alguns casos, escreve pequenos pedaços de código pra você. É como ter a documentação básica embutida no editor, o que evita que você tenha que consultar informações de tipo em uma janela de ajuda separada. Os recursos do IntelliSense variam de acordo com a linguagem. Para obter mais informações, veja [IntelliSense do Visual C#](../ide/visual-csharp-intellisense.md), [IntelliSense do Visual C++](../ide/visual-cpp-intellisense.md), [IntelliSense do JavaScript](../ide/javascript-intellisense.md) e [IntelliSense específico do Visual Basic](../ide/visual-basic-specific-intellisense.md). A ilustração a seguir mostra alguns recursos do IntelliSense em funcionamento:

  ![Lista de membros do Visual Studio](../ide/media/vs2017_Intellisense.png)

- **Rabiscos** são sublinhados vermelhos ondulados que alertam você sobre erros ou problemas potenciais no código em tempo real durante a digitação. Isso permite que você os corrija imediatamente sem esperar que o erro seja descoberto durante a compilação ou o tempo de execução. Se você passar o mouse sobre o rabisco, verá informações adicionais sobre o erro. Uma lâmpada também podem aparecer na margem esquerda com sugestões de como corrigir o erro. Para obter mais informações, consulte [Ações Rápidas](../ide/quick-actions.md).

 ![Rabiscos](../ide/media/vs2017_squiggle.png)

- A janela [Hierarquia de Chamada](../ide/reference/call-hierarchy.md) pode ser aberta no menu de contexto do editor de texto para mostrar os métodos que chamam e que são chamados pelo método sob o cursor (ponto de inserção).

 ![Janela de Hierarquia de Chamada](../ide/media/VSIDE_call_hierarchy.png)

- [CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md) habilita a localizar referências e alterações em seu código, bugs vinculados, itens de trabalho, análises de código e testes de unidade, tudo sem sair do editor.

 ![CodeLens](../ide/media/codelensoverview.png)

- A janela [Espiar Definição](../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md) mostra uma definição de método ou de tipo embutida, sem navegar para fora de seu contexto atual.

 ![Espiar Definição](../ide/media/VSIDE_peek_definition.png)

- A opção de menu de contexto **Ir para Definição** leva você diretamente para o local em que a função ou o objeto estão definidos. Outros comandos de navegação também estão disponíveis clicando com o botão direito do mouse no editor.

 ![Ir para Definição](../ide/media/VSIDE_go_to_definition.png)

- Uma ferramenta relacionada, o [Pesquisador de Objetos](http://msdn.microsoft.com/f89acfc5-1152-413d-9f56-3dc16e3f0470), permite a inspeção de assemblies do .NET ou do Windows Runtime no sistema para ver quais tipos eles contêm e quais membros (propriedades, métodos, eventos, etc.) esses tipos contêm.

  ![Pesquisador de Objetos mostrando System.Timer](../ide/media/objectbrowser.png)

## <a name="manage-your-source-code-and-collaborate-with-others"></a>Gerenciar seu código-fonte e colaborar com outros

É possível gerenciar o código-fonte em repositórios Git hospedados por qualquer provedor, incluindo o GitHub. Se preferir, use o [VSTS (Visual Studio Team Services)](/vsts/index) para gerenciar o código junto com bugs e itens de trabalho de todo o projeto. Consulte [Introdução ao Git e VSTS (Team Services)](/vsts/git/gitquickstart?tabs=visual-studio) para obter mais informações sobre o gerenciamento de repositórios Git no Visual Studio usando o Team Explorer. O Visual Studio também tem outros recursos de controle do código-fonte internos. Para saber mais sobre eles, consulte [Novos Recursos do Git no Visual Studio 2017 (blog)](https://blogs.msdn.microsoft.com/visualstudioalm/2017/03/06/new-git-features-in-visual-studio-2017/).

O Visual Studio Team Services é um serviço baseado em nuvem para hospedar projetos de software e permitir a colaboração em equipes. O VSTS oferece suporte a sistemas Git e Team Foundation Source Control, bem como as metodologias de desenvolvimento Agile, CMMI e Scrum. O TFVC (Controle de Versão do Team Foundation) usa um repositório de servidor único e centralizado para arquivos de versão e de controle. É sempre feito check-in das alterações locais no servidor central em que outros desenvolvedores podem obter as alterações mais recentes.

O TFS (Team Foundation Server) é o hub de gerenciamento do ciclo de vida do aplicativo para o Visual Studio. Ele habilita a participação de todos os envolvidos com o processo de desenvolvimento usando uma única solução. O TFS também é útil para gerenciar equipes e projetos heterogêneos.

Se você tiver uma conta do Visual Studio Team Services ou um Team Foundation Server na rede, conecte-se a ela por meio da janela do Team Explorer no Visual Studio. Nessa janela você pode fazer check-in ou check-out de código no controle do código-fonte, gerenciar itens de trabalho, iniciar compilações e acessar salas da equipe e espaços de trabalho. É possível abrir o Team Explorer na caixa **Início Rápido** ou no menu principal, em **Exibir, Team Explorer** ou em **Equipe, Gerenciar Conexões**.

A seguinte imagem mostra a janela do Team Explorer em uma solução que é hospedada no VSTS.

![Team Explorer para Visual Studio](../ide/media/vs2017_teamexplorer.png)

Também é possível automatizar o processo de build para compilar o código que os desenvolvedores de sua equipe fizeram check-in no controle de versão. Por exemplo, será possível criar um ou mais projetos à noite ou sempre que o check-in do código for feito. Confira [Continuous integration on any platform](https://www.visualstudio.com/en-us/docs/build/overview) (Integração contínua em qualquer plataforma) para obter mais informações.

## <a name="connect-to-services-databases-and-cloud-based-resources"></a>Conectar a serviços, bancos de dados e recursos baseados em nuvem

A nuvem é fundamental para o mundo conectado de hoje e o Visual Studio fornece os meios para aproveitá-lo. Por exemplo, o recurso Serviços Conectados permite conectar seu aplicativo aos serviços. Seus aplicativos podem usá-lo para armazenar os dados no armazenamento do Azure, entre outras coisas.

![Serviços conectados](../ide/media/VSIDE_Tour_Connected_Services.png)

A escolha de um serviço na página **Serviços Conectados** inicia um Assistente dos Serviços Conectados, que configura o projeto e baixa os pacotes NuGet necessários para ajudá-lo a começar a codificar no serviço.

É possível exibir e gerenciar seus recursos de nuvem baseados no Azure no Visual Studio usando o [Cloud Explorer](/azure/vs-azure-tools-resources-managing-with-cloud-explorer). O Cloud Explorer mostra os recursos do Azure em todas as contas gerenciadas na assinatura do Azure à qual você está conectado. É possível obter o Cloud Explorer selecionando a carga de trabalho para **Desenvolvimento do Azure** no Instalador do Visual Studio.

![Cloud Explorer](../ide/media/VSIDE_CloudExplorer.png)

O **Gerenciador de Servidores** ajuda você a procurar e a gerenciar ativos e instâncias do SQL Server locais, remotos e no Azure, no Salesforce.com, no Office 365 e em sites. Para abrir o Gerenciador de Servidores, no menu principal, escolha **Exibir**, **Gerenciador de Servidores**. Consulte [Adicionar novas conexões](../data-tools/add-new-connections.md) para obter mais informações sobre como usar o Gerenciador de Servidores.

O [SSDT (SQL Server Data Tools)](/sql/ssdt/download-sql-server-data-tools-ssdt) é um ambiente de desenvolvimento avançado do SQL Server, Banco de Dados SQL do Azure e Azure SQL Data Warehouse. Ele permite compilar, depurar, manter e refatorar bancos de dados. Você pode trabalhar com um projeto de banco de dados ou diretamente com uma instância local ou não de banco de dados conectado.

O **Pesquisador de Objetos do SQL Server** no Visual Studio fornece uma exibição dos objetos de banco de dados semelhante ao SQL Server Management Studio. O Pesquisador de Objetos do SQL Server permite realizar trabalhos leves de design e administração de banco de dados, incluindo edição de dados de tabela, comparação de esquemas e execução de consultas usando menus contextuais diretamente no Pesquisador de Objetos do SQL Server e muito mais.

![Pesquisador de Objetos do SQL Server](../ide/media/vs2015_sqlobjectexplorer.png)

## <a name="extend-visual-studio"></a>Estenda o Visual Studio
Se o Visual Studio não tiver a funcionalidade exata de que você precisa, será possível adicioná-la! É possível personalizar o IDE de acordo com o estilo e fluxo de trabalho, adicionar suporte para ferramentas externas que ainda não estão integradas ao Visual Studio e modificar a funcionalidade existente para aumentar a produtividade. Para encontrar a versão mais recente das Ferramentas de Extensibilidade do Visual Studio (SDK do VS), confira [Visual Studio SDK](../extensibility/visual-studio-sdk.md) (SDK do Visual Studio).

Você pode usar o Plataforma de Compilador .NET (Roslyn) para escrever seus próprios analisadores e geradores de código. Encontre tudo o que você precisa em [Roslyn](https://github.com/dotnet/Roslyn).

Encontre [extensões existentes](https://marketplace.visualstudio.com/vs) para o Visual Studio criadas pelos desenvolvedores da Microsoft, bem como pela nossa comunidade de desenvolvimento.

Para saber mais sobre como estender o Visual Studio, consulte [Estender o IDE do Visual Studio](https://www.visualstudio.com/vs/extend/).

## <a name="learn-more-and-find-out-whats-new"></a>Saiba mais e descubra as novidades

Se você nunca usou o Visual Studio antes, veja a [Introdução ao desenvolvimento com o Visual Studio](../ide/get-started-developing-with-visual-studio.md) ou confira os cursos gratuitos do Visual Studio disponíveis na [Microsoft Virtual Academy](https://mva.microsoft.com/product-training/visual-studio-courses#!index=2&lang=1033). Se você quiser conferir as novas funcionalidades no Visual Studio 2017, consulte [Novidades no Visual Studio 2017](../ide/whats-new-in-visual-studio.md).

Parabéns por concluir o tour pelo IDE do Visual Studio! Esperamos que você tenha aprendido algo útil sobre alguns de seus principais recursos.

## <a name="see-also"></a>Consulte também

* [Visual Studio IDE](https://www.visualstudio.com/vs/)
* [Downloads do Visual Studio](https://www.visualstudio.com/downloads/)
* [O blog do Visual Studio](https://blogs.msdn.microsoft.com/visualstudio/)
* [Fóruns do Visual Studio](https://social.msdn.microsoft.com/Forums/vstudio/en-US/home?category=visualstudio%2Cvsarch%2Cvsdbg%2Cvstest%2Cvstfs%2Cvsdata%2Cvsappdev%2Cvisualbasic%2Cvisualcsharp%2Cvisualc)
* [Microsoft Virtual Academy](https://mva.microsoft.com/)
* [Channel 9](https://channel9.msdn.com/)
