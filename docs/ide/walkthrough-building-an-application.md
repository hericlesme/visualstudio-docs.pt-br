---
title: 'Passo a passo: Criando um aplicativo | Microsoft Docs'
ms.custom: 
ms.date: 09/25/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 485c8445f24dbd0aaec501649885df50d173347a
ms.sourcegitcommit: d6327b978661c0a745bf4b59f32d8171607803a3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2018
---
# <a name="walkthrough-building-an-application"></a>Instruções passo a passo: criando um aplicativo

Ao concluir este passo a passo, você ficará mais familiarizado com as várias opções que podem ser configuradas ao compilar aplicativos com o Visual Studio. Você criará uma configuração de build personalizada, ocultará determinadas mensagens de aviso e aumentará as informações de saída de build de um aplicativo de exemplo.

## <a name="install-the-sample-application"></a>Instalar o aplicativo de exemplo

Baixe o exemplo [Introdução à criação de aplicativos WPF](https://code.msdn.microsoft.com/Introduction-to-Building-b8d16419). Escolha C# ou Visual Basic. Depois de baixar o arquivo .zip, extraia-o e abra o arquivo **ExpenseItIntro.sln** usando o Visual Studio.

## <a name="create-a-custom-build-configuration"></a>Criar uma configuração de build personalizada

Ao criar uma solução, as configurações de build de depuração e versão e seus destinos de plataforma padrão são definidos para a solução automaticamente. Depois, é possível personalizar essas configurações ou criar suas próprias. As configurações de build especificam o tipo de build. As plataformas de build especificam o sistema operacional que um aplicativo tem como destino para a configuração. Para saber mais, consulte [Noções básicas sobre configurações de build](../ide/understanding-build-configurations.md), [Noções básicas sobre plataformas de build](../ide/understanding-build-platforms.md) e [Como definir as configurações de depuração e versão](../debugger/how-to-set-debug-and-release-configurations.md).

É possível alterar ou criar configurações e configurações de plataforma por meio da caixa de diálogo **Configuration Manager**. Neste procedimento, você criará uma configuração de build para testes.

### <a name="to-create-a-build-configuration"></a>Para criar uma configuração de build

1. Abra a caixa de diálogo **Configuration Manager**.

   ![Menu Build, comando do Configuration Manager](../ide/media/buildwalk_configurationmanagerdialogbox.png "BuildWalk_ConfigurationManagerDialogBox")  

1. Na lista **Configuração da solução ativa**, escolha **\<Nova....\>**.

1. Na caixa de diálogo **Nova Configuração da Solução**, nomeie a nova configuração `Test`, copie as configurações da configuração de Depuração existentes e, em seguida, escolha o botão **OK**.

   ![Caixa de diálogo Nova Configuração da Solução](../ide/media/buildwalk_newsolutionconfigdlgbox.png "BuildWalk_NewSolutionConfigDlgBox")  

1. Na lista **Plataforma da solução ativa**, escolha **\<Nova...\>**.

1. Na caixa de diálogo **Nova Plataforma de Solução**, escolha **x64** e não copie as configurações da plataforma x86.

   ![Caixa de diálogo Nova Plataforma da Solução](../ide/media/buildwalk_newsolutionplatform.png "BuildWalk_NewSolutionPlatform")  

1. Escolha o botão **OK**.

   A configuração da solução ativa foi alterada para Teste com a plataforma da solução ativa definida como x64.

   ![Configuration Manager com a configuração de Teste](../ide/media/buildwalk_configmanagertestconfig.png "BuildWalk_ConfigManagerTestconfig")  

1. Escolha **Fechar**.

É possível verificar ou alterar de forma rápida a configuração da solução ativa usando a lista **Configurações da Solução** na barra de ferramentas **Padrão**.
  
![Opção de Configuração da Solução na barra de ferramentas Padrão](../ide/media/buildwalk_standardtoolbarsolutioncongfig.png "BuildWalk_StandardToolbarSolutionCongfig")  
  
## <a name="build-the-application"></a>Compilar o aplicativo

Em seguida, você compilará a solução com a configuração de build personalizada.
  
### <a name="to-build-the-solution"></a>Para compilar a solução
  
-   Na barra de menus, escolha **Compilar** > **Compilar Solução**.
  
    A Janela de **Saída** exibe os resultados do build. O build foi bem-sucedido.
  
## <a name="hide-compiler-warnings"></a>Ocultar avisos do compilador

Em seguida, apresentaremos alguns códigos que fazem com que um aviso seja gerado pelo compilador.

1. No projeto de C#, abra o arquivo **ExpenseReportPage.xaml.cs**. No método **ExpenseReportPage**, adicione o seguinte código: `int i;`.

    OU

    No projeto do Visual Basic, abra o arquivo **ExpenseReportPage.xaml.vb**. No construtor personalizado **Public Sub New...**, adicione o seguinte código: `Dim i`.

1. Compile a solução.

A Janela de **Saída** exibe os resultados do build. O build foi bem-sucedido, mas foram gerados avisos:

![Janela de Saída do Visual Basic](../ide/media/buildwalk_vbbuildoutputwnd.png "BuildWalk_VBBuildOutputWnd")

![Janela de Saída do Visual C&#35;](../ide/media/buildwalk_csharpbuildoutputwnd.png "BuildWalk_CsharpBuildOutputWnd")

Temporariamente, é possível ocultar determinadas mensagens de aviso durante um build, em vez de deixá-las acumular a saída do build.

### <a name="to-hide-a-specific-c-warning"></a>Para ocultar um aviso específico de C#

1. No **Gerenciador de Soluções**, escolha o nó do projeto de nível superior.

1. Na barra de menus, escolha **Exibir**, **Páginas de Propriedade**.
  
     O **Designer de Projeto** é aberto.

1. Escolha a página **Build** e, em seguida, na caixa **Suprimir avisos**, especifique o número de aviso **0168**.
  
     ![Página Build, Designer de Projeto](../ide/media/buildwalk_csharpsupresswarnings.png "BuildWalk_CsharpSupressWarnings")  
  
     Para obter mais informações, consulte [Página Build, Designer de Projeto (C#)](../ide/reference/build-page-project-designer-csharp.md).

1. Compile a solução.
  
     A Janela de **Saída** exibe apenas informações de resumo do build.
  
     ![Janela de Saída, Avisos de Build do Visual C&#35;](../ide/media/buildwalk_visualcsharpbuildwarnings.png "BuildWalk_VisualCsharpBuildWarnings")  
  
### <a name="to-suppress-all-visual-basic-build-warnings"></a>Para suprimir todos os avisos de build do Visual Basic

1. No **Gerenciador de Soluções**, escolha o nó do projeto de nível superior.

1. Na barra de menus, escolha **Exibir**, **Páginas de Propriedade**.
  
     O **Designer de Projeto** é aberto.

1. Na página **Compilar**, marque a caixa de seleção **Desabilitar todos os avisos**.
  
     ![Página Compilar, Designer de Projeto](../ide/media/buildwalk_vbsupresswarnings.png "BuildWalk_VBSupressWarnings")  
  
     Para obter mais informações, consulte [Configurando avisos no Visual Basic](../ide/configuring-warnings-in-visual-basic.md).

1. Compile a solução.
  
 A Janela de **Saída** exibe apenas informações de resumo do build.
  
 ![Janela de Saída, Avisos de Build do Visual Basic](../ide/media/buildwalk_visualbasicbuildwarnings.png "BuildWalk_VisualBasicBuildWarnings")  
  
 Para obter mais informações, consulte [Como suprimir avisos do compilador](../ide/how-to-suppress-compiler-warnings.md).
  
## <a name="display-additional-build-details-in-the-output-window"></a>Exibir detalhes de build adicionais na Janela de Saída

É possível alterar a quantidade de informações sobre o processo de build exibidas na Janela de **Saída**. Geralmente, os detalhes de build são definidos como Mínimos, o que significa que a Janela de **Saída** exibe apenas um resumo do processo de build, junto com os avisos de prioridade alta ou erros. É possível exibir mais informações sobre o build usando a [Caixa de diálogo Opções, Projetos e Soluções, Compilar e Executar](../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md).
  
> [!IMPORTANT]
>  Se você exibir mais informações, o build levará mais tempo para ser concluído.
  
### <a name="to-change-the-amount-of-information-in-the-output-window"></a>Para alterar a quantidade de informações na Janela de Saída

1. Abra a caixa de diálogo **Opções**.
  
     ![Comando Opções no menu Ferramentas](../ide/media/exploreide-toolsoptionsmenu.png "ExploreIDE-ToolsOptionsmenu")  

1. Escolha a categoria **Projetos e Soluções** e, em seguida, a página **Compilar e Executar**.

1. Na lista **Detalhes da saída de build do projeto do MSBuild**, escolha **Normal** e, em seguida, o botão **OK**.

1. Na barra de menus, escolha **Build**, **Limpar Solução**.

1. Compile a solução e, em seguida, examine as informações na Janela de **Saída**.
  
     As informações do build incluem a hora de início do build (localizada no início) e ordem em que os arquivos foram processados. Essas informações também incluem a sintaxe real do compilador que o Visual Studio executa durante o build.
  
     Por exemplo, na compilação do C#, a opção [/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn) lista o código de aviso 1762, que foi especificado anteriormente neste tópico, juntamente com três outros avisos.
  
     No build do Visual Basic, [/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn) não inclui avisos específicos a serem excluídos e, portanto, nenhum aviso é exibido.
  
    > [!TIP]
    > É possível pesquisar o conteúdo da Janela de **Saída** se você exibir a caixa de diálogo **Localizar** escolhendo as teclas Ctrl+F.

Para obter mais informações, consulte [Como exibir, salvar e configurar arquivos de log de build](../ide/how-to-view-save-and-configure-build-log-files.md).
  
## <a name="create-a-release-build"></a>Criar um build da versão

É possível compilar uma versão do aplicativo de exemplo que é otimizada para enviá-lo. Para o build de versão, você especificará que o arquivo executável é copiado para um compartilhamento de rede antes do início do build.

Para obter mais informações, consulte [Como alterar o diretório de saída do build](../ide/how-to-change-the-build-output-directory.md) e [Criando e limpando projetos e soluções no Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md).

### <a name="to-specify-a-release-build-for-visual-basic"></a>Para especificar um build de versão para o Visual Basic

1. Abra o **Designer de Projeto**.
  
     ![Menu Exibir, comando Páginas de Propriedades](../ide/media/buildwalk_viewpropertypages.png "BuildWalk_ViewPropertyPages")  

1. Escolha a página **Compilar**.

1. Na lista **Configuração**, escolha **Versão**.

1. Na lista **Plataforma**, escolha **x86**.

1. Na caixa **Caminho de saída do build**, especifique um caminho de rede.

     Por exemplo, é possível especificar \\\myserver\builds.

    > [!IMPORTANT]
    > Uma caixa de mensagem poderá ser exibida, avisando que o compartilhamento de rede especificado pode não ser um local confiável. Se você confiar no local especificado, escolha o botão **OK** na caixa de mensagem.

1. Compile o aplicativo.

     ![Comando Compilar Solução no menu Compilar](../ide/media/exploreide-buildsolution.png "ExploreIDE-BuildSolution")  

### <a name="to-specify-a-release-build-for-c"></a>Para especificar um build de versão para C# #

1. Abra o **Designer de Projeto**.
  
     ![Menu Exibir, comando Páginas de Propriedades](../ide/media/buildwalk_viewpropertypages.png "BuildWalk_ViewPropertyPages")  

1. Escolha a página **Build**.

1. Na lista **Configuração**, escolha **Versão**.

1. Na lista **Plataforma**, escolha **x86**.

1. Na caixa **Caminho de saída**, especifique um caminho de rede.
  
     Por exemplo, você poderia especificar \\\myserver\builds.
  
    > [!IMPORTANT]
    > Uma caixa de mensagem poderá ser exibida, avisando que o compartilhamento de rede especificado pode não ser um local confiável. Se você confiar no local especificado, escolha o botão **OK** na caixa de mensagem.

1. Na **barra de ferramentas Padrão**, defina as Configurações da solução como **Versão** e as Plataformas da solução como **x86**.

1. Compile o aplicativo.

     ![Comando Compilar Solução no menu Compilar](../ide/media/exploreide-buildsolution.png "ExploreIDE-BuildSolution")  

   O arquivo executável é copiado para o caminho de rede especificado. O caminho será \\\myserver\builds\\*FileName*.exe.

Parabéns, você concluiu este passo a passo com êxito.
  
## <a name="see-also"></a>Consulte também

[Passo a passo: compilando um projeto (C++)](/cpp/ide/walkthrough-building-a-project-cpp)  
[Visão geral da pré-compilação de projeto de aplicativo Web ASP.NET](http://msdn.microsoft.com/b940abbd-178d-4570-b441-52914fa7b887)  
[Passo a passo: usando o MSBuild](../msbuild/walkthrough-using-msbuild.md)
