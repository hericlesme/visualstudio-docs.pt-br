---
title: 'Passo a passo: Criando um Item de projeto da coluna de Site com um modelo de projeto, parte 2 | Microsoft Docs'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], creating template wizards
- SharePoint project items, creating template wizards
- SharePoint development in Visual Studio, defining new project item types
ms.assetid: da14207d-ac09-41ba-b387-c7f881b2a366
caps.latest.revision: "54"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: a3c2ff276d6f432a4b3cabcaa4aa1b27b033676e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2"></a>Passo a passo: Criando um Item de projeto da coluna de Site com um modelo de projeto, parte 2
  Depois de definir um tipo personalizado do item de projeto do SharePoint e associá-lo a um modelo de projeto no Visual Studio, você também poderá fornecer um Assistente para o modelo. Você pode usar o Assistente para coletar informações de usuários quando eles usam o modelo para criar um novo projeto que contém o item de projeto. As informações que você coletar podem ser usadas para inicializar o item de projeto.  
  
 Neste passo a passo, você adicionará um Assistente para o modelo de projeto de coluna de Site que é demonstrado [passo a passo: Criando um Item de projeto da coluna de Site com um modelo de projeto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md). Quando um usuário cria um projeto de coluna de Site, o assistente coleta informações sobre a coluna de site (como seu tipo base e grupo) e adiciona informações ao arquivo Elements no novo projeto.  
  
 Este passo a passo demonstra as seguintes tarefas:  
  
-   Criando um Assistente para um tipo de item de projeto do SharePoint personalizado que está associado um modelo de projeto.  
  
-   Definindo um assistente personalizado da interface do usuário que se parece com os assistentes internos para projetos do SharePoint no Visual Studio.  
  
-   Criar dois *comandos do SharePoint* que são usados para chamar o site do SharePoint local enquanto o assistente está em execução. Comandos do SharePoint são métodos que podem ser usados por extensões do Visual Studio para chamar APIs no modelo de objeto de servidor do SharePoint. Para obter mais informações, consulte [chamando os modelos de objeto do SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
-   Usando parâmetros substituíveis para inicializar os arquivos de projeto do SharePoint com os dados coletados no assistente.  
  
-   Criando um novo arquivo. snk em cada instância de projeto nova coluna de Site. Esse arquivo é usado para assinar o projeto de saída para que o assembly de solução do SharePoint pode ser implantado no cache de assembly global.  
  
-   Depuração e teste o assistente.  
  
> [!NOTE]  
>  Você pode baixar um exemplo que contém os projetos concluídos, código e outros arquivos para este passo a passo no seguinte local: [http://go.microsoft.com/fwlink/?LinkId=191369](http://go.microsoft.com/fwlink/?LinkId=191369).  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Para executar este passo a passo, você deve primeiro criar a solução SiteColumnProjectItem Concluindo [passo a passo: Criando um Item de projeto da coluna de Site com um modelo de projeto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).  
  
 Você também precisará dos seguintes componentes no computador de desenvolvimento para concluir este passo a passo:  
  
-   Edições com suporte do Windows, o SharePoint e o Visual Studio. Para obter mais informações, consulte [requisitos para desenvolver soluções do SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   O SDK do Visual Studio. Este passo a passo usa o **projeto VSIX** modelo no SDK para criar um pacote do VSIX para implantar o item de projeto. Para obter mais informações, consulte [estendendo as ferramentas do SharePoint no Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
 Conhecimento sobre os conceitos a seguir é útil, mas não necessário para concluir o passo a passo:  
  
-   Assistentes para modelos de projeto e item no Visual Studio. Para obter mais informações, consulte [como: usar assistentes com modelos de projeto](../extensibility/how-to-use-wizards-with-project-templates.md) e <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> interface.  
  
-   Colunas de site do SharePoint. Para obter mais informações, consulte [colunas](http://go.microsoft.com/fwlink/?LinkId=183547).  
  
##  <a name="wizardcomponents"></a>Noções básicas sobre o Assistente de componentes  
 O assistente que é demonstrado neste passo a passo contém vários componentes. A tabela a seguir descreve esses componentes.  
  
|Componente|Descrição|  
|---------------|-----------------|  
|Implementação de Assistente|Esta é uma classe denominada `SiteColumnProjectWizard`, que implementa o <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> interface. Essa interface define os métodos que o Visual Studio chama quando o assistente inicia e termina e em determinados momentos enquanto o assistente é executado.|  
|Assistente de interface do usuário|Esta é uma janela com base em WPF, denominada `WizardWindow`. Esta janela inclui dois controles de usuário, denominados `Page1` e `Page2`. Esses controles de usuário representam as duas páginas do assistente.<br /><br /> Neste passo a passo, o <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> método da implementação do assistente exibe o Assistente de interface do usuário.|  
|Modelo de dados do Assistente|Esta é uma classe intermediária, denominada `SiteColumnWizardModel`, que fornece uma camada entre o Assistente de interface de usuário e a implementação do assistente. Este exemplo usa essa classe para ajudar a abstrair a implementação do assistente e o Assistente de interface do usuário do outro; Essa classe não é um componente obrigatório de todos os assistentes.<br /><br /> Neste passo a passo, a implementação de assistente passa um `SiteColumnWizardModel` objeto para a janela do assistente quando ele exibe o Assistente de interface do usuário. O Assistente de interface de usuário usa métodos do objeto para salvar os valores dos controles na interface de usuário e realizar tarefas como verificar se a URL do site de entrada é válida. Depois que o usuário concluir o assistente, a implementação de assistente usa a `SiteColumnWizardModel` objeto para determinar o estado final da interface do usuário.|  
|Assinatura do gerente de projeto|Esta é uma classe auxiliar, chamada `ProjectSigningManager`, que é usada pela implementação do Assistente para criar um novo arquivo de key.snk em cada nova instância de projeto.|  
|comandos do SharePoint|Esses são os métodos que são usados pelo modelo de dados do Assistente para chamar o site do SharePoint local enquanto o assistente está em execução. Como os comandos do SharePoint devem ter como destino o .NET Framework 3.5, esses comandos são implementados em um assembly diferente do restante do código do assistente.|  
  
## <a name="creating-the-projects"></a>Criando os Projetos  
 Para concluir este passo a passo, você precisa adicionar vários projetos na solução de SiteColumnProjectItem que você criou na [passo a passo: Criando um Item de projeto da coluna de Site com um modelo de projeto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md):  
  
-   Um projeto WPF. Você implementará o <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> interface e defina o Assistente de interface de usuário neste projeto.  
  
-   Um projeto de biblioteca de classe que define os comandos do SharePoint. Este projeto deve usar o.NET Framework 3.5.  
  
 Criando projetos para iniciar o passo a passo.  
  
#### <a name="to-create-the-wpf-project"></a>Para criar o projeto WPF  
  
1.  Em [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], abra a solução SiteColumnProjectItem.  
  
2.  Em **Solution Explorer**, abra o menu de atalho para o **SiteColumnProjectItem** nó da solução, escolha **adicionar**e, em seguida, escolha **novo projeto**.  
  
3.  Na parte superior de **adicionar novo projeto** caixa de diálogo caixa, certifique-se de que **.NET Framework 4.5** for escolhido na lista de versões do .NET Framework.  
  
4.  Expanda o **Visual C#** nó ou o **Visual Basic** nó e escolha o **Windows** nó.  
  
5.  Na lista de modelos de projeto, escolha **biblioteca de controle de usuário do WPF**, nomeie o projeto **ProjectTemplateWizard**e, em seguida, escolha o **Okey** botão.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Adiciona o **ProjectTemplateWizard** projeto à solução e abre o arquivo de Usercontrol1 padrão.  
  
6.  Exclua o arquivo de Usercontrol1 do projeto.  
  
#### <a name="to-create-the-sharepoint-commands-project"></a>Para criar o projeto de comandos do SharePoint  
  
1.  Em **Solution Explorer**, abra o menu de atalho para o nó da solução SiteColumnProjectItem, escolha **adicionar**e, em seguida, escolha **novo projeto**.  
  
2.  Na parte superior do **adicionar novo projeto** caixa de diálogo caixa, escolha **.NET Framework 3.5** na lista de versões do .NET Framework.  
  
3.  Expanda o **Visual C#** nó ou o **Visual Basic** nó e, em seguida, escolha o **Windows** nó.  
  
4.  Escolha o **biblioteca de classes** modelo de projeto, nomeie o projeto **SharePointCommands**e, em seguida, escolha o **Okey** botão.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Adiciona o **SharePointCommands** projeto à solução e abre o arquivo de código Class1 padrão.  
  
5.  Exclua o arquivo de código Class1 do projeto.  
  
## <a name="configuring-the-projects"></a>Configurando projetos  
 Antes de criar o assistente, você deve adicionar alguns arquivos de código e referências de assembly para os projetos.  
  
#### <a name="to-configure-the-wizard-project"></a>Configurar o projeto de Assistente  
  
1.  Em **Solution Explorer**, abra o menu de atalho para o **ProjectTemplateWizard** nó do projeto e escolha **propriedades**.  
  
2.  No **Project Designer**, escolha o **aplicativo** guia para um projeto Visual c# ou o **compilar** guia para um projeto do Visual Basic.  
  
3.  Certifique-se de que a estrutura de destino é definida como o .NET Framework 4.5, não o perfil de cliente do .NET Framework 4.5.  
  
     Para obter mais informações, consulte [Como definir uma versão do .NET Framework como destino](../ide/how-to-target-a-version-of-the-dotnet-framework.md).  
  
4.  Abra o menu de atalho para o **ProjectTemplateWizard** de projeto, escolha **adicionar**e, em seguida, escolha **Novo Item**.  
  
5.  Escolha o **janela (WPF)** item, o nome do item **WizardWindow**e, em seguida, escolha o **adicionar** botão.  
  
6.  Adicionar dois **controle de usuário (WPF)** itens para o projeto e nomeá-los **Página1** e **Página2**.  
  
7.  Adicionar os quatro arquivos de código ao projeto e forneça os seguintes nomes:  
  
    -   SiteColumnProjectWizard  
  
    -   SiteColumnWizardModel  
  
    -   ProjectSigningManager  
  
    -   CommandIds  
  
8.  Abra o menu de atalho para o **ProjectTemplateWizard** nó do projeto e escolha **adicionar referência**.  
  
9. Expanda o **Assemblies** nó, escolha o **extensões** nó e, em seguida, selecione as caixas de seleção ao lado dos seguintes assemblies:  
  
    -   EnvDTE  
  
    -   Microsoft.VisualStudio.OLE.Interop  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   Microsoft.VisualStudio.Shell.11.0  
  
    -   Microsoft.VisualStudio.Shell.Interop.10.0  
  
    -   Microsoft.VisualStudio.Shell.Interop.11.0  
  
    -   Microsoft.VisualStudio.TemplateWizardInterface  
  
10. Escolha o **Okey** botão para adicionar os assemblies para o projeto.  
  
11. Em **Gerenciador de soluções**, sob o **referências** pasta para o **ProjectTemplateWizard** do projeto, escolha **EnvDTE**.  
  
12. No **propriedades** janela, altere o valor da **Embed Interop Types** propriedade **False**.  
  
13. Se você estiver desenvolvendo um projeto do Visual Basic, importar o namespace ProjectTemplateWizard para seu projeto usando o **Project Designer**.  
  
     Para obter mais informações, consulte [como: Adicionar ou remover Namespaces importados &#40; Visual Basic &#41; ](../ide/how-to-add-or-remove-imported-namespaces-visual-basic.md).  
  
#### <a name="to-configure-the-sharepointcommands-project"></a>Configurar o projeto SharePointCommands  
  
1.  Em **Solution Explorer**, escolha o **SharePointCommands** nó do projeto.  
  
2.  Na barra de menus, escolha **projeto**, **Add Existing Item**.  
  
3.  No **Add Existing Item** caixa de diálogo, navegue até a pasta que contém os arquivos de código para o projeto ProjectTemplateWizard e, em seguida, escolha o **CommandIds** arquivo de código.  
  
4.  Clique na seta ao lado de **adicionar** botão e, em seguida, escolha o **adicionar como vínculo** opção no menu que aparece.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Adiciona o arquivo de código para o **SharePointCommands** projeto como um link. O arquivo de código está localizado no **ProjectTemplateWizard** projeto, mas o código no arquivo também é compilado no **SharePointCommands** projeto.  
  
5.  No **SharePointCommands** de projeto, adicione outro arquivo de código que é chamado de comandos.  
  
6.  Escolha o projeto SharePointCommands e, em seguida, na barra de menus, escolha **projeto**, **adicionar referência**.  
  
7.  Expanda o **Assemblies** nó, escolha o **extensões** nó e, em seguida, selecione as caixas de seleção ao lado dos seguintes assemblies:  
  
    -   Microsoft. SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Commands  
  
8.  Escolha o **Okey** botão para adicionar os assemblies para o projeto.  
  
## <a name="creating-the-wizard-model-signing-manager-and-sharepoint-command-ids"></a>Criando o modelo de Assistente de assinatura Gerenciador e IDs de comando do SharePoint  
 Adicione código ao projeto ProjectTemplateWizard para implementar os seguintes componentes no exemplo:  
  
-   As IDs de comando do SharePoint. Essas cadeias de caracteres identificam os comandos do SharePoint que usa o assistente. Posteriormente neste passo a passo, você adicionará código ao projeto SharePointCommands para implementar os comandos.  
  
-   O modelo de dados do assistente.  
  
-   O Gerenciador de autenticação do projeto.  
  
 Para obter mais informações sobre esses componentes, consulte [Noções básicas sobre os componentes do assistente](#wizardcomponents).  
  
#### <a name="to-define-the-sharepoint-command-ids"></a>Para definir as IDs de comando do SharePoint  
  
1.  No projeto ProjectTemplateWizard, abra o arquivo de código CommandIds e substitua todo o conteúdo deste arquivo com o código a seguir.  
  
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#5](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/commandids.cs#5)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#5](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/commandids.vb#5)]  
  
#### <a name="to-create-the-wizard-model"></a>Para criar o modelo de Assistente  
  
1.  Abra o arquivo de código SiteColumnWizardModel e substitua todo o conteúdo deste arquivo com o código a seguir.  
  
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#6](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/sitecolumnwizardmodel.vb#6)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#6](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/sitecolumnwizardmodel.cs#6)]  
  
#### <a name="to-create-the-project-signing-manager"></a>Para criar o Gerenciador de autenticação do projeto  
  
1.  Abra o arquivo de código ProjectSigningManager e substitua todo o conteúdo deste arquivo com o código a seguir.  
  
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#8](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/projectsigningmanager.vb#8)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#8](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/projectsigningmanager.cs#8)]  
  
## <a name="creating-the-wizard-ui"></a>Criando o Assistente de interface do usuário  
 Adicionar o XAML para definir a interface do usuário da janela do assistente e os controles de usuário de dois que fornecem a interface do usuário para as páginas do assistente e adicione código para definir o comportamento dos controles de usuário e a janela. O assistente que você criar se parece com o Assistente interno para projetos do SharePoint no Visual Studio.  
  
> [!NOTE]  
>  Nas etapas a seguir, o projeto terá alguns erros de compilação depois de adicionar o XAML ou código ao seu projeto. Esses erros desaparecerá quando você adiciona o código em etapas posteriores.  
  
#### <a name="to-create-the-wizard-window-ui"></a>Para criar a janela do Assistente da interface do usuário  
  
1.  No projeto ProjectTemplateWizard, abra o menu de atalho para o arquivo WizardWindow.xaml e, em seguida, escolha **abrir** para abrir a janela no designer.  
  
2.  Na exibição do designer XAML, substitua o XAML atual com o XAML a seguir. O XAML que define uma interface do usuário que inclui um título, um <xref:System.Windows.Controls.Grid> que contém as páginas do assistente e botões de navegação na parte inferior da janela.  
  
     [!code-xml[SPExtensibility.ProjectItem.SiteColumn#10](../sharepoint/codesnippet/Xaml/sitecolumnprojectitem/projecttemplatewizard/wizardwindow.xaml#10)]  
  
    > [!NOTE]  
    >  A janela que é criada neste XAML é derivada de <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> classe base. Quando você adiciona uma caixa de diálogo personalizada do WPF para o Visual Studio, é recomendável que você deriva a caixa de diálogo desta classe ter um estilo consistente com outras caixas de diálogo do Visual Studio e para evitar problemas de caixa de diálogo modal que possam ocorrer. Para obter mais informações, consulte [criando e gerenciando caixas de diálogo modais](/visualstudio/extensibility/creating-and-managing-modal-dialog-boxes).  
  
3.  Se você estiver desenvolvendo um projeto do Visual Basic, remova o `ProjectTemplateWizard` namespace do `WizardWindow` nome da classe a `x:Class` atributo do `Window` elemento. Esse elemento é na primeira linha do XAML. Quando terminar, a primeira linha deve parecer com o exemplo a seguir.  
  
    ```  
    <Window x:Class="WizardWindow"  
    ```  
  
4.  Abra o arquivo code-behind para o arquivo WizardWindow.xaml.  
  
5.  Substitua o conteúdo desse arquivo, exceto para o `using` declarações na parte superior do arquivo, com o código a seguir.  
  
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#4](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/wizardwindow.xaml.vb#4)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#4](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/wizardwindow.xaml.cs#4)]  
  
#### <a name="to-create-the-first-wizard-page-ui"></a>Para criar a primeira página do Assistente da interface do usuário  
  
1.  No projeto ProjectTemplateWizard, abra o menu de atalho para o arquivo Page1 e, em seguida, escolha **abrir** para abrir o controle de usuário no designer.  
  
2.  Na exibição do designer XAML, substitua o XAML atual com o XAML a seguir. O XAML que define uma interface do usuário que inclui uma caixa de texto onde os usuários podem inserir a URL dos sites locais que deseja usar para depuração. A interface do usuário também inclui botões de opção com a qual os usuários podem especificar se o projeto está em modo seguro.  
  
     [!code-xml[SPExtensibility.ProjectItem.SiteColumn#11](../sharepoint/codesnippet/Xaml/sitecolumnprojectitem/projecttemplatewizard/page1.xaml#11)]  
  
3.  Se você estiver desenvolvendo um projeto do Visual Basic, remova o `ProjectTemplateWizard` namespace do `Page1` nome da classe a `x:Class` atributo do `UserControl` elemento. Essa é a primeira linha do XAML. Quando terminar, a primeira linha deve ser semelhante ao seguinte.  
  
    ```  
    <UserControl x:Class="Page1"  
    ```  
  
4.  Substitua o conteúdo do arquivo Page1, exceto para o `using` declarações na parte superior do arquivo, com o código a seguir.  
  
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#2](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/page1.xaml.vb#2)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#2](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/page1.xaml.cs#2)]  
  
#### <a name="to-create-the-second-wizard-page-ui"></a>Para criar a segunda página do Assistente da interface do usuário  
  
1.  No projeto ProjectTemplateWizard, abra o menu de atalho para o arquivo Page2.xaml e, em seguida, escolha **abrir**.  
  
     O controle de usuário é aberto no designer.  
  
2.  No modo de exibição XAML, substitua o XAML atual com o XAML a seguir. O XAML define uma interface do usuário que inclui uma lista suspensa para escolher o tipo de base de uma caixa de texto para especificar o nome da coluna de site, a coluna de site e uma caixa de combinação para especificar um grupo interno ou personalizado em que a coluna de site são exibidos na Galeria.  
  
     [!code-xml[SPExtensibility.ProjectItem.SiteColumn#12](../sharepoint/codesnippet/Xaml/sitecolumnprojectitem/projecttemplatewizard/page2.xaml#12)]  
  
3.  Se você estiver desenvolvendo um projeto do Visual Basic, remova o `ProjectTemplateWizard` namespace do `Page2` nome da classe a `x:Class` atributo do `UserControl` elemento. Essa é a primeira linha do XAML. Quando terminar, a primeira linha deve ser semelhante ao seguinte.  
  
    ```  
    <UserControl x:Class="Page2"  
    ```  
  
4.  Substitua o conteúdo do arquivo de code-behind para o arquivo Page2.xaml, exceto para o `using` declarações na parte superior do arquivo, com o código a seguir.  
  
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#3](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/page2.xaml.vb#3)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#3](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/page2.xaml.cs#3)]  
  
## <a name="implementing-the-wizard"></a>Implementando o Assistente  
 Definir a funcionalidade principal do assistente Implementando o <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> interface. Essa interface define os métodos que o Visual Studio chama quando o assistente inicia e termina e em determinados momentos enquanto o assistente é executado.  
  
#### <a name="to-implement-the-wizard"></a>Para implementar o Assistente  
  
1.  No projeto ProjectTemplateWizard, abra o arquivo de código SiteColumnProjectWizard.  
  
2.  Substitua todo o conteúdo deste arquivo com o código a seguir.  
  
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#7](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/sitecolumnprojectwizard.vb#7)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#7](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/sitecolumnprojectwizard.cs#7)]  
  
## <a name="creating-the-sharepoint-commands"></a>Criando os comandos do SharePoint  
 Crie dois comandos personalizados que chamam o modelo de objeto de servidor do SharePoint. Um comando determina se a URL do site que o usuário digita no assistente é válida. Outro comando obtém todos os tipos de campo do site do SharePoint especificado para que os usuários podem selecionar qual delas usar como base para sua nova coluna de site.  
  
#### <a name="to-define-the-sharepoint-commands"></a>Para definir os comandos do SharePoint  
  
1.  No **SharePointCommands** de projeto, abra o arquivo de código de comandos.  
  
2.  Substitua todo o conteúdo deste arquivo com o código a seguir.  
  
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#9](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/sharepointcommands/commands.vb#9)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#9](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/sharepointcommands/commands.cs#9)]  
  
## <a name="checkpoint"></a>Ponto de verificação  
 Nesse ponto no passo a passo, todo o código para que o assistente está agora no projeto. Crie o projeto para certificar-se de que ele foi compilado sem erros.  
  
#### <a name="to-build-your-project"></a>Para compilar o projeto  
  
1.  Na barra de menus, escolha **Compilar**, **Compilar Solução**.  
  
## <a name="removing-the-keysnk-file-from-the-project-template"></a>Removendo o arquivo key.snk do modelo de projeto  
 Em [passo a passo: Criando um Item de projeto da coluna de Site com um modelo de projeto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md), o modelo de projeto que você criou contém um arquivo de key.snk que é usado para assinar cada instância de projeto da coluna de Site. Este arquivo key.snk não é necessário porque o assistente agora gera um novo arquivo key.snk para cada projeto. Remova o arquivo key.snk do modelo de projeto e remover referências a esse arquivo.  
  
#### <a name="to-remove-the-keysnk-file-from-the-project-template"></a>Para remover o arquivo key.snk do modelo de projeto  
  
1.  No **Gerenciador de soluções**, sob o **SiteColumnProjectTemplate** nó, abra o menu de atalho para o **key.snk** file e, em seguida, escolha **excluir**.  
  
2.  Na caixa de diálogo de confirmação que aparece, escolha o **Okey** botão.  
  
3.  Sob o **SiteColumnProjectTemplate** nó, abra o arquivo SiteColumnProjectTemplate.vstemplate e, em seguida, remova o seguinte elemento dele.  
  
    ```  
    <ProjectItem ReplaceParameters="false" TargetFileName="key.snk">key.snk</ProjectItem>  
    ```  
  
4.  Salve e feche o arquivo.  
  
5.  Sob o **SiteColumnProjectTemplate** nó, abra o arquivo ProjectTemplate.csproj ou ProjectTemplate.vbproj e, em seguida, remova a seguinte `PropertyGroup` elemento dele.  
  
    ```  
    <PropertyGroup>  
      <SignAssembly>true</SignAssembly>  
      <AssemblyOriginatorKeyFile>key.snk</AssemblyOriginatorKeyFile>  
    </PropertyGroup>  
    ```  
  
6.  Remova a seguinte `None` elemento.  
  
    ```  
    <None Include="key.snk" />  
    ```  
  
7.  Salve e feche o arquivo.  
  
## <a name="associating-the-wizard-with-the-project-template"></a>Associando o assistente com o modelo de projeto  
 Agora que você implementou o assistente, você deve associar o assistente com o **coluna Site** modelo de projeto. Há três procedimentos que devem ser concluídas para fazer isso:  
  
1.  Assine o assembly de assistente com um nome forte.  
  
2.  Obter token de chave pública para o assembly do assistente.  
  
3.  Adicione uma referência ao assembly do assistente no arquivo. vstemplate para o **coluna Site** modelo de projeto.  
  
#### <a name="to-sign-the-wizard-assembly-with-a-strong-name"></a>Para assinar o assembly de assistente com um nome forte  
  
1.  Em **Solution Explorer**, abra o menu de atalho para o **ProjectTemplateWizard** do projeto e, em seguida, escolha **propriedades**.  
  
2.  Sobre o **assinatura** guia, selecione o **assinar o assembly** caixa de seleção.  
  
3.  No **escolher um arquivo de chave de nome forte** , escolha  **\<novo... >**.  
  
4.  No **criar chave de nome forte** caixa de diálogo, digite um nome para o novo arquivo de chave, limpe o **proteger o arquivo de chaves com uma senha** caixa de seleção e, em seguida, escolha o **Okey** botão.  
  
5.  Abra o menu de atalho para o **ProjectTemplateWizard** do projeto e, em seguida, escolha **Build** para criar o arquivo ProjectTemplateWizard.dll.  
  
#### <a name="to-get-the-public-key-token-for-the-wizard-assembly"></a>Para obter a chave pública token para o assembly do Assistente  
  
1.  Sobre o **Menu Iniciar**, escolha **todos os programas**, escolha **Microsoft Visual Studio**, escolha **ferramentas do Visual Studio**e, em seguida, escolha  **Prompt de comando do desenvolvedor**.  
  
     Abre uma janela de Prompt de comando do Visual Studio.  
  
2.  Execute o seguinte comando, substituindo *PathToWizardAssembly* com o caminho completo para o assembly ProjectTemplateWizard.dll criado para o projeto ProjectTemplateWizard no computador de desenvolvimento:  
  
    ```  
    sn.exe -T PathToWizardAssembly  
    ```  
  
     O token de chave pública para o assembly ProjectTemplateWizard.dll é gravado para a janela de Prompt de comando do Visual Studio.  
  
3.  Mantenha a janela de Prompt de comando do Visual Studio aberta. Você precisará do token de chave pública durante o próximo procedimento.  
  
#### <a name="to-add-a-reference-to-the-wizard-assembly-in-the-vstemplate-file"></a>Para adicionar uma referência ao assembly do assistente no arquivo. vstemplate.  
  
1.  Em **Solution Explorer**, expanda o **SiteColumnProjectTemplate** nó do projeto e abra o arquivo SiteColumnProjectTemplate.vstemplate.  
  
2.  No final do arquivo, adicione o seguinte `WizardExtension` elemento entre o `</TemplateContent>` e `</VSTemplate>` marcas. Substitua o *seu token* valor o `PublicKeyToken` atributo com o token de chave pública que você obteve no procedimento anterior.  
  
    ```  
    <WizardExtension>  
      <Assembly>ProjectTemplateWizard, Version=1.0.0.0, Culture=neutral, PublicKeyToken=your token</Assembly>  
      <FullClassName>ProjectTemplateWizard.SiteColumnProjectWizard</FullClassName>  
    </WizardExtension>  
    ```  
  
     Para obter mais informações sobre o `WizardExtension` elemento, consulte [elemento WizardExtension &#40; Modelos do Visual Studio &#41; ](/visualstudio/extensibility/wizardextension-element-visual-studio-templates).  
  
3.  Salve e feche o arquivo.  
  
## <a name="adding-replaceable-parameters-to-the-elementsxml-file-in-the-project-template"></a>Adicionando parâmetros substituíveis no arquivo Elements no modelo de projeto  
 Adicione vários parâmetros substituíveis no arquivo Elements no projeto SiteColumnProjectTemplate. Esses parâmetros são inicializados no `RunStarted` método o `SiteColumnProjectWizard` classe definido anteriormente. Quando um usuário cria um projeto de coluna de Site, o Visual Studio substitui automaticamente esses parâmetros no arquivo Elements no novo projeto com os valores que elas especificadas no assistente.  
  
 Um parâmetro de substituição é um token que começa e termina com o caractere de cifrão ($). Além de definir seus próprios parâmetros substituíveis, você pode usar parâmetros internos que são definidos e inicializados pelo sistema de projeto do SharePoint. Para obter mais informações, consulte [parâmetros substituíveis](../sharepoint/replaceable-parameters.md).  
  
#### <a name="to-add-replaceable-parameters-to-the-elementsxml-file"></a>Para adicionar parâmetros substituíveis ao arquivo Elements.  
  
1.  No projeto SiteColumnProjectTemplate, substitua o conteúdo do arquivo Elements XML a seguir.  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">  
      <Field ID="{$guid5$}"   
             Name="$fieldname$"   
             DisplayName="$fieldname$"   
             Type="$selectedfieldtype$"   
             Group="$selectedgrouptype$">  
      </Field>  
    </Elements>  
    ```  
  
     O novo XML altera os valores da `Name`, `DisplayName`, `Type`, e `Group` atributos para os parâmetros substituíveis personalizados.  
  
2.  Salve e feche o arquivo.  
  
## <a name="adding-the-wizard-to-the-vsix-package"></a>Adicionando o assistente ao pacote VSIX  
 Para implantar o assistente com o pacote do VSIX que contém o modelo de projeto da coluna de Site, adicione referências para o projeto do assistente e o projeto de comandos do SharePoint para o arquivo source.extension.vsixmanifest no projeto do VSIX.  
  
#### <a name="to-add-the-wizard-to-the-vsix-package"></a>Para adicionar o Assistente para o pacote VSIX  
  
1.  Em **Solution Explorer**, no **SiteColumnProjectItem** de projeto, abra o menu de atalho para o **source.extension.vsixmanifest** file e, em seguida, escolha **Abrir**.  
  
     O Visual Studio abrirá o arquivo no editor de manifesto.  
  
2.  Sobre o **ativos** guia do editor, escolha o **novo** botão.  
  
     O **adicionar novo ativo** caixa de diálogo é aberta.  
  
3.  No **tipo** , escolha **Microsoft.VisualStudio.Assembly**.  
  
4.  No **fonte** , escolha **um projeto na solução atual**.  
  
5.  No **projeto** , escolha **ProjectTemplateWizard**e, em seguida, escolha o **Okey** botão.  
  
6.  Sobre o **ativos** guia do editor, escolha o **novo** novamente.  
  
     O **adicionar novo ativo** caixa de diálogo é aberta.  
  
7.  No **tipo** , digite **SharePoint.Commands.v4**.  
  
8.  No **fonte** , escolha **um projeto na solução atual**.  
  
9. No **projeto** , escolha o **SharePointCommands** do projeto e, em seguida, escolha o **Okey** botão.  
  
10. Na barra de menus, escolha **criar**, **compilar solução**e, em seguida, certifique-se de que a solução seja criada sem erros.  
  
## <a name="testing-the-wizard"></a>O Assistente de teste  
 Agora você está pronto para testar o assistente. Primeiro, inicie a depuração da solução SiteColumnProjectItem na instância experimental do Visual Studio. Em seguida, teste o Assistente para o projeto de coluna de Site na instância experimental do Visual Studio. Por fim, compile e execute o projeto para verificar se a coluna de site funciona conforme o esperado.  
  
#### <a name="to-start-debugging-the-solution"></a>Para iniciar a depuração da solução  
  
1.  Reinicie o Visual Studio com credenciais administrativas e, em seguida, abra a solução de SiteColumnProjectItem.  
  
2.  No projeto ProjectTemplateWizard, abra o arquivo de código SiteColumnProjectWizard e, em seguida, adicione um ponto de interrupção para a primeira linha do código no `RunStarted` método.  
  
3.  Na barra de menus, escolha **depurar**, **exceções**.  
  
4.  No **exceções** caixa de diálogo caixa, certifique-se de que o **Thrown** e **manipulado pelo usuário** caixas de seleção para **Common Language Runtime Exceptions**serão eliminadas e, em seguida, escolha o **Okey** botão.  
  
5.  Iniciar a depuração, escolhendo o **F5** chave ou, na barra de menus, escolhendo **depurar**, **iniciar depuração**.  
  
     Visual Studio instala a extensão para %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Site Column\1.0 e inicia uma instância experimental do Visual Studio. Você testará o item de projeto nesta instância do Visual Studio.  
  
#### <a name="to-test-the-wizard-in-visual-studio"></a>Para testar o assistente no Visual Studio  
  
1.  Na instância experimental do Visual Studio, na barra de menus, escolha **arquivo**, **novo**, **projeto**.  
  
2.  Expanda o **Visual C#** nó ou o **Visual Basic** nó (dependendo da linguagem que dá suporte a seu modelo de projeto), expanda o **SharePoint** nó e, em seguida, escolha o **2010** nó.  
  
3.  Na lista de modelos de projeto, escolha **coluna Site**, nomeie o projeto **SiteColumnWizardTest**e, em seguida, escolha o **Okey** botão.  
  
4.  Verifique se que o código em outra instância do Visual Studio para no ponto de interrupção que você definiu anteriormente no `RunStarted` método.  
  
5.  Continuar a depuração do projeto, escolhendo o **F5** chave ou, na barra de menus, escolhendo **depurar**, **continuar**.  
  
6.  No **Assistente de personalização do SharePoint**, insira a URL do site que você deseja usar para depuração e, em seguida, escolha o **próximo** botão.  
  
7.  Na segunda página do **Assistente de personalização do SharePoint**, faça as seguintes seleções:  
  
    -   No **tipo** , escolha **booliano**.  
  
    -   No **grupo** , escolha **personalizado Sim colunas**.  
  
    -   No **nome** , digite **coluna do meu Sim**e, em seguida, escolha o **concluir** botão.  
  
     Em **Solution Explorer**, um novo projeto é exibido e contém um item de projeto chamado **Field1**, e o Visual Studio abrirá o arquivo do projeto Elements no editor.  
  
8.  Verifique se Elements contém os valores que você especificou no assistente.  
  
#### <a name="to-test-the-site-column-in-sharepoint"></a>Para testar a coluna de site do SharePoint  
  
1.  Na instância experimental do Visual Studio, pressione a tecla F5.  
  
     A coluna de site é empacotada e implantada para o SharePoint site que o **URL do Site** Especifica a propriedade do projeto. O navegador da web abre a página padrão deste site.  
  
    > [!NOTE]  
    >  Se o **desabilitado de depuração de Script** caixa de diálogo for exibida, escolha o **Sim** botão para continuar a depuração do projeto.  
  
2.  Sobre o **ações do Site** menu, escolha **configurações do Site**.  
  
3.  Na página de configurações do Site, em **galerias**, escolha o **Site colunas** link.  
  
4.  Na lista de colunas de site, verifique se um **personalizado Sim colunas** grupo contém uma coluna denominada **coluna do meu Sim**e, em seguida, feche o navegador da web.  
  
## <a name="cleaning-up-the-development-computer"></a>Limpando o computador de desenvolvimento  
 Depois de concluir o teste de item de projeto, remova o modelo de projeto da instância experimental do Visual Studio.  
  
#### <a name="to-clean-up-the-development-computer"></a>Para limpar o computador de desenvolvimento  
  
1.  Na instância experimental do Visual Studio, na barra de menus, escolha **ferramentas**, **extensões e atualizações**.  
  
     A caixa de diálogo **Extensões e Atualizações** é aberta.  
  
2.  Na lista de extensões, escolha **coluna Site**e, em seguida, escolha o **desinstalação** botão.  
  
3.  Na caixa de diálogo que aparece, escolha o **Sim** botão para confirmar que você deseja desinstalar a extensão e, em seguida, escolha o **reiniciar agora** botão para concluir a desinstalação.  
  
4.  Feche a instância experimental do Visual Studio e a instância em que a solução CustomActionProjectItem estiver aberta.  
  
     Para obter informações sobre como implantar [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] extensões, consulte [envio extensões do Visual Studio](/visualstudio/extensibility/shipping-visual-studio-extensions).  
  
## <a name="see-also"></a>Consulte também  
 [Passo a passo: Criando um Item de projeto da coluna de Site com um modelo de projeto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)   
 [Definindo tipos de Item de projeto do SharePoint personalizado](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Criando modelos de projeto e modelos de Item para itens de projeto do SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Referência de esquema de modelo do Visual Studio](/visualstudio/extensibility/visual-studio-template-schema-reference)   
 [Como usar assistentes com modelos do projeto](../extensibility/how-to-use-wizards-with-project-templates.md)  
  
  