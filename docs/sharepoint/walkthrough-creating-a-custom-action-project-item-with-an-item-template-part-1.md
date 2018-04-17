---
title: 'Passo a passo: Criando um Item de projeto de ação personalizada com um modelo de Item, parte 1 | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, creating custom templates
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint development in Visual Studio, defining new project item types
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e690d18bae72b59234f2f90cbcf903b9941df7d6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1"></a>Passo a passo: Criando um Item de projeto de ação personalizada com um modelo de Item, parte 1
  Você pode estender o sistema de projeto do SharePoint no Visual Studio, crie seu próprio projeto tipos de item. Este passo a passo, você criará um item de projeto que pode ser adicionado a um projeto do SharePoint para criar uma ação personalizada em um site do SharePoint. A ação personalizada adiciona um item de menu para o **ações do Site** menu do site do SharePoint.  
  
 Este passo a passo demonstra as seguintes tarefas:  
  
-   Criando uma extensão do Visual Studio que define um novo tipo de item de projeto do SharePoint para uma ação personalizada. O novo tipo de item de projeto implementa vários recursos personalizados:  
  
    -   Um menu de atalho que serve como ponto de partida para as tarefas adicionais relacionadas ao item de projeto, como exibir um designer para a ação personalizada no Visual Studio.  
  
    -   Código que é executado quando um desenvolvedor altera certas propriedades do item de projeto e o projeto que o contém.  
  
    -   Um ícone personalizado que aparece ao lado do item de projeto no **Gerenciador de soluções**.  
  
-   Criar um modelo de item do Visual Studio para o item de projeto.  
  
-   Criando um pacote de extensão de Visual Studio (VSIX) para implantar o modelo de item de projeto e o assembly de extensão.  
  
-   Depurando e testando o item de projeto.  
  
 Este é um passo a passo autônoma. Depois de concluir este passo a passo, você pode melhorar o item de projeto com a adição de um Assistente para o modelo de item. Para obter mais informações, consulte [passo a passo: Criando um Item de projeto de ação personalizado com um modelo de Item, parte 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md).  
  
> [!NOTE]  
>  Você pode baixar um exemplo que contém os projetos concluídos, código e outros arquivos para este passo a passo no seguinte local: [ http://go.microsoft.com/fwlink/?LinkId=191369 ](http://go.microsoft.com/fwlink/?LinkId=191369).  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Você precisará dos seguintes componentes no computador de desenvolvimento para concluir este passo a passo:  
  
-   Edições com suporte do Microsoft Windows, SharePoint e do Visual Studio. Para obter mais informações, consulte [requisitos para desenvolver soluções do SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   O [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]. Este passo a passo usa o **projeto VSIX** modelo no SDK para criar um pacote do VSIX para implantar o item de projeto. Para obter mais informações, consulte [estendendo as ferramentas do SharePoint no Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
 Conhecimento sobre os conceitos a seguir é útil, mas não necessário para concluir o passo a passo:  
  
-   Ações personalizadas no SharePoint. Para obter mais informações, consulte [ação personalizada](http://go.microsoft.com/fwlink/?LinkId=177800).  
  
-   Modelos de item no Visual Studio. Para obter mais informações, consulte [Criando modelos de item e de projeto](/visualstudio/ide/creating-project-and-item-templates).  
  
## <a name="creating-the-projects"></a>Criando os Projetos  
 Para concluir este passo a passo, você precisa criar três projetos:  
  
-   Um projeto do VSIX. Este projeto cria o pacote do VSIX para implantar o item de projeto do SharePoint.  
  
-   Um projeto de modelo de item. Este projeto cria um modelo de item que pode ser usado para adicionar o item de projeto do SharePoint para um projeto do SharePoint.  
  
-   Um projeto de biblioteca de classe. Este projeto implementa uma extensão do Visual Studio que define o comportamento do item de projeto do SharePoint.  
  
 Criando projetos para iniciar o passo a passo.  
  
#### <a name="to-create-the-vsix-project"></a>Para criar o projeto do VSIX  
  
1.  Inicie o [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Na barra de menus, escolha **Arquivo**, **Novo**, **Projeto**.  
  
3.  Na lista na parte superior do **novo projeto** caixa de diálogo caixa, certifique-se de que **.NET Framework 4.5** está selecionado.  
  
4.  No **novo projeto** caixa de diálogo caixa, expanda o **Visual C#** ou **Visual Basic** nós e, em seguida, escolha o **extensibilidade** nó.  
  
    > [!NOTE]  
    >  O **extensibilidade** nó estará disponível somente se você instalar o SDK do Visual Studio. Para obter mais informações, consulte a seção pré-requisitos neste tópico.  
  
5.  Escolha o **projeto VSIX** modelo.  
  
6.  No **nome** , digite **CustomActionProjectItem**e, em seguida, escolha o **Okey** botão.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Adiciona o **CustomActionProjectItem** projeto **Gerenciador de soluções**.  
  
#### <a name="to-create-the-item-template-project"></a>Para criar o projeto de modelo de item  
  
1.  Em **Solution Explorer**, abra o menu de atalho para o nó da solução, escolha **adicionar**e, em seguida, escolha **novo projeto**.  
  
2.  Na lista na parte superior do **novo projeto** caixa de diálogo caixa, certifique-se de que **.NET Framework 4.5** está selecionado.  
  
3.  No **novo projeto** caixa de diálogo caixa, expanda o **Visual C#** ou **Visual Basic** nós e, em seguida, escolha o **extensibilidade** nó.  
  
4.  Na lista de modelos de projeto, escolha o **modelo de Item do c#** ou **modelo de Item do Visual Basic** modelo.  
  
5.  No **nome** , digite **ItemTemplate**e, em seguida, escolha o **Okey** botão.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Adiciona o **ItemTemplate** projeto à solução.  
  
#### <a name="to-create-the-extension-project"></a>Para criar o projeto de extensão  
  
1.  Em **Solution Explorer**, abra o menu de atalho para o nó da solução, escolha **adicionar**e, em seguida, escolha **novo projeto**.  
  
2.  Na lista na parte superior do **novo projeto** caixa de diálogo caixa, certifique-se de que **.NET Framework 4.5** está selecionado.  
  
3.  No **novo projeto** caixa de diálogo caixa, expanda o **Visual C#** ou **Visual Basic** nós, escolha o **Windows** nó e, em seguida, escolha o  **A biblioteca de classe** modelo de projeto.  
  
4.  No **nome** , digite **ProjectItemDefinition**e, em seguida, escolha o **Okey** botão.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Adiciona o **ProjectItemDefinition** projeto à solução e abre o arquivo de código Class1 padrão.  
  
5.  Exclua o arquivo de código Class1 do projeto.  
  
## <a name="configuring-the-extension-project"></a>Configurando o projeto de extensão  
 Antes de escrever código para definir o tipo de item de projeto do SharePoint, você precisa adicionar arquivos de código e referências de assembly para o projeto de extensão.  
  
#### <a name="to-configure-the-project"></a>Configurar o projeto  
  
1.  Em **Solution Explorer**, abra o menu de atalho para o **ProjectItemDefinition** do projeto, escolha **adicionar**, escolha **Novo Item**.  
  
2.  Na lista de itens de projeto, escolha **arquivo de código**.  
  
3.  No **nome** , digite o nome **personalizada de** com apropriada a extensão de nome de arquivo e, em seguida, escolha o **adicionar** botão.  
  
4.  Em **Solution Explorer**, abra o menu de atalho para o **ProjectItemDefinition** do projeto e, em seguida, escolha **adicionar referência**.  
  
5.  No **Gerenciador de referências - ProjectItemDefinition** caixa de diálogo caixa, escolha o **Assemblies** nó e, em seguida, escolha o **Framework** nó.  
  
6.  Marque a caixa de seleção ao lado de cada um dos seguintes assemblies:  
  
    -   System.ComponentModel.Composition  
  
    -   System.Windows.Forms  
  
7.  Escolha o **extensões** nó, selecione a caixa de seleção ao lado de assembly Microsoft.VisualStudio.Sharepoint e, em seguida, escolha o **Okey** botão.  
  
## <a name="defining-the-new-sharepoint-project-item-type"></a>Definir o novo tipo de Item de projeto do SharePoint  
 Criar uma classe que implementa o <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> interface para definir o comportamento do novo tipo de item de projeto. Implemente esta interface sempre que você deseja definir um novo tipo de item de projeto.  
  
#### <a name="to-define-the-new-sharepoint-project-item-type"></a>Para definir o novo tipo de item de projeto do SharePoint  
  
1.  No projeto ProjectItemDefinition, abra o arquivo de código personalizada.  
  
2.  Substitua o código neste arquivo com o código a seguir.  
  
     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#1](../sharepoint/codesnippet/CSharp/customactionprojectitem/projectitemtypedefinition/customaction.cs#1)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#1](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/projectitemdefinition/customaction.vb#1)]  
  
## <a name="creating-an-icon-for-the-project-item-in-solution-explorer"></a>Criando um ícone para o Item de projeto no Gerenciador de soluções  
 Quando você cria um item de projeto do SharePoint personalizado, você pode associar uma imagem (um ícone ou bitmap) com o item de projeto. A imagem exibida ao lado do item de projeto no **Gerenciador de soluções**.  
  
 No procedimento a seguir, você cria um ícone para o item de projeto e insere o ícone no assembly de extensão. Esse ícone é referenciado pelo <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemIconAttribute> do `CustomActionProjectItemTypeProvider` classe que você criou anteriormente.  
  
#### <a name="to-create-a-custom-icon-for-the-project-item"></a>Para criar um ícone personalizado para o item de projeto  
  
1.  Em **Solution Explorer**, abra o menu de atalho para o **ProjectItemDefinition** de projeto, escolha **adicionar**e, em seguida, escolha **Novo Item...** .  
  
2.  Na lista de itens de projeto, escolha o **arquivo de ícone** item.  
  
    > [!NOTE]  
    >  Em projetos do Visual Basic, você deve escolher o **geral** nó para exibir o **arquivo de ícone** item.  
  
3.  No **nome** , digite **CustomAction_SolutionExplorer.ico**e, em seguida, escolha o **adicionar** botão.  
  
     O novo ícone é aberto no **Editor de imagem**.  
  
4.  Edite a versão de 16x16 do arquivo de ícone de forma que ele tem um design que você pode reconhecer e, em seguida, salve o arquivo de ícone.  
  
5.  Em **Solution Explorer**, escolha **CustomAction_SolutionExplorer.ico**.  
  
6.  No **propriedades** janela, clique na seta ao lado de **ação de compilação** propriedade.  
  
7.  Na lista que aparece, escolha **recurso inserido**.  
  
## <a name="checkpoint"></a>Ponto de verificação  
 Nesse ponto no passo a passo, todo o código para o item de projeto está agora no projeto. Crie o projeto para verificar se ele foi compilado sem erros.  
  
#### <a name="to-build-your-project"></a>Para compilar o projeto  
  
1.  Abra o menu de atalho para o **ProjectItemDefinition** do projeto e escolha **criar**.  
  
## <a name="creating-a-visual-studio-item-template"></a>Criando um modelo de Item do Visual Studio  
 Para habilitar outros desenvolvedores a usar o item de projeto, você deve criar um modelo de projeto ou o modelo de item. Os desenvolvedores usar esses modelos no Visual Studio para criar uma instância do seu item de projeto, criando um novo projeto, ou adicionando um item a um projeto existente. Para este passo a passo, use o projeto ItemTemplate para configurar o item de projeto.  
  
#### <a name="to-create-the-item-template"></a>Para criar o modelo de item  
  
1.  Exclua o arquivo de código Class1 do projeto ItemTemplate.  
  
2.  No projeto ItemTemplate, abra o arquivo ItemTemplate.vstemplate.  
  
3.  Substitua o conteúdo do arquivo pelo XML a seguir e, em seguida, salve e feche o arquivo.  
  
    > [!NOTE]  
    >  O XML a seguir é para um modelo de item do Visual c#. Se você estiver criando um modelo de item do Visual Basic, substitua o valor da `ProjectType` elemento com `VisualBasic`.  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <VSTemplate Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Item">  
      <TemplateData>  
        <DefaultName>CustomAction</DefaultName>  
        <Name>Custom Action</Name>  
        <Description>SharePoint Custom Action by Contoso</Description>  
        <ProjectType>CSharp</ProjectType>  
        <SortOrder>1000</SortOrder>  
        <Icon>ItemTemplate.ico</Icon>  
        <ProvideDefaultName>true</ProvideDefaultName>  
      </TemplateData>  
      <TemplateContent>  
        <ProjectItem ReplaceParameters="true" TargetFileName="$fileinputname$\Elements.xml">Elements.xml</ProjectItem>  
        <ProjectItem ReplaceParameters="true" TargetFileName="$fileinputname$\SharePointProjectItem.spdata">CustomAction.spdata</ProjectItem>  
      </TemplateContent>  
    </VSTemplate>  
    ```  
  
     Esse arquivo define o conteúdo e o comportamento do modelo de item. Para obter mais informações sobre o conteúdo desse arquivo, consulte [referência de esquema de modelo do Visual Studio](/visualstudio/extensibility/visual-studio-template-schema-reference).  
  
4.  Em **Solution Explorer**, abra o menu de atalho para o **ItemTemplate** de projeto, escolha **adicionar**e, em seguida, escolha **Novo Item**.  
  
5.  No **Adicionar Novo Item** caixa de diálogo caixa, escolha o **arquivo de texto** modelo.  
  
6.  No **nome** , digite **CustomAction.spdata**e, em seguida, escolha o **adicionar** botão.  
  
7.  Adicione o seguinte XML para o arquivo CustomAction.spdata e, em seguida, salve e feche o arquivo.  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <ProjectItem Type="Contoso.CustomAction" DefaultFile="Elements.xml"   
     xmlns="http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel">  
      <Files>  
        <ProjectItemFile Source="Elements.xml" Target="$fileinputname$\" Type="ElementManifest" />  
      </Files>  
    </ProjectItem>  
    ```  
  
     Este arquivo contém informações sobre os arquivos contidos no item de projeto. O `Type` atributo do `ProjectItem` elemento deve ser definido para a mesma cadeia de caracteres que é passada para o <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> na definição de item de projeto (o `CustomActionProjectItemTypeProvider` classe que você criou anteriormente neste passo a passo). Para obter mais informações sobre o conteúdo de arquivos. spdata, consulte [referência de esquema de Item de projeto do SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md).  
  
8.  Em **Solution Explorer**, abra o menu de atalho para o **ItemTemplate** de projeto, escolha **adicionar**e, em seguida, escolha **Novo Item**.  
  
9. No **Adicionar Novo Item** caixa de diálogo caixa, escolha o **arquivo XML** modelo.  
  
10. No **nome** , digite **Elements**e, em seguida, escolha o **adicionar** botão.  
  
11. Substitua o conteúdo do arquivo Elements pelo XML a seguir e, em seguida, salve e feche o arquivo.  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>  
    <Elements Id="$guid8$" xmlns="http://schemas.microsoft.com/sharepoint/">  
      <CustomAction Id="Replace this with a GUID or some other unique string"  
                    GroupId="SiteActions"  
                    Location="Microsoft.SharePoint.StandardMenu"  
                    Sequence="1000"  
                    Title="Replace this with your title"  
                    Description="Replace this with your description" >  
        <UrlAction Url="~site/Lists/Tasks/AllItems.aspx"/>  
      </CustomAction>  
    </Elements>  
    ```  
  
     Esse arquivo define uma ação personalizada padrão que cria um item de menu a **ações do Site** menu do site do SharePoint. Quando um usuário escolhe o item de menu, a URL especificada no `UrlAction` elemento abre no navegador da web. Para obter mais informações sobre os elementos XML que você pode usar para definir uma ação personalizada, consulte [definições de ação personalizado](http://go.microsoft.com/fwlink/?LinkId=177801).  
  
12. Opcionalmente, abra o arquivo ItemTemplate.ico e modificá-lo para que ele tem um design que você pode reconhecer. Este ícone será exibido ao lado do item de projeto no **Adicionar Novo Item** caixa de diálogo.  
  
13. Em **Solution Explorer**, abra o menu de atalho para o **ItemTemplate** do projeto e, em seguida, escolha **descarregar projeto**.  
  
14. Abra o menu de atalho para o **ItemTemplate** projeto novamente e, em seguida, escolha **Editar ItemTemplate.csproj** ou **ItemTemplate.vbproj editar**.  
  
15. Localize o seguinte `VSTemplate` elemento no arquivo de projeto.  
  
    ```  
    <VSTemplate Include="ItemTemplate.vstemplate">  
    ```  
  
16. Substituir `VSTemplate` elemento com o XML a seguir e, depois, salve e feche o arquivo.  
  
    ```  
    <VSTemplate Include="ItemTemplate.vstemplate">  
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>  
    </VSTemplate>  
    ```  
  
     O `OutputSubPath` elemento Especifica pastas adicionais no caminho no qual o modelo de item é criado quando você compila o projeto. As pastas especificadas aqui Certifique-se de que o modelo de item estará disponível somente quando os clientes abrir o **Adicionar Novo Item** caixa de diálogo caixa, expanda o **SharePoint** nó e, em seguida, escolha o **2010**  nó.  
  
17. Em **Solution Explorer**, abra o menu de atalho para o **ItemTemplate** do projeto e, em seguida, escolha **recarregar projeto**.  
  
## <a name="creating-a-vsix-package-to-deploy-the-project-item"></a>Criando um pacote do VSIX para implantar o Item de projeto  
 Para implantar a extensão, use o projeto do VSIX em sua solução para criar um pacote do VSIX. Primeiro, configure o pacote VSIX, modificando o arquivo source.extension.vsixmanifest que está incluído no projeto do VSIX. Em seguida, crie o pacote do VSIX por compilar a solução.  
  
#### <a name="to-configure-and-create-the-vsix-package"></a>Para configurar e criar o pacote VSIX  
  
1.  Em **Solution Explorer**, abra o menu de atalho para o **source.extension.vsixmanifest** de arquivos no projeto CustomActionProjectItem e, em seguida, escolha **abrir**.  
  
     O Visual Studio abrirá o arquivo no editor de manifesto. O arquivo source.extension.vsixmanifest é a base para o arquivo extension.vsixmanifest que necessitam de todos os pacotes VSIX. Para obter mais informações sobre esse arquivo, consulte [1.0 referência do esquema de extensão de VSIX](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
2.  No **nome do produto** , digite **Item de projeto de ação personalizado**.  
  
3.  No **autor** , digite **Contoso**.  
  
4.  No **descrição** , digite **do SharePoint de um item de projeto que representa uma ação personalizada**.  
  
5.  Sobre o **ativos** guia, escolha o **novo** botão.  
  
     O **adicionar novo ativo** caixa de diálogo é exibida.  
  
6.  No **tipo** , escolha **Microsoft.VisualStudio.ItemTemplate**.  
  
    > [!NOTE]  
    >  Esse valor corresponde do `ItemTemplate` elemento no arquivo extension.vsixmanifest. Este elemento identifica a subpasta no pacote do VSIX que contém o modelo de item de projeto. Para obter mais informações, consulte [ItemTemplate Element (esquema de VSX)](http://msdn.microsoft.com/en-us/1d489e54-c1c5-4f96-a510-6c2640867ff0).  
  
7.  No **fonte** , escolha **um projeto na solução atual**.  
  
8.  No **projeto** , escolha **ItemTemplate**e, em seguida, escolha o **Okey** botão.  
  
9. No **ativos** guia, escolha o **novo** novamente.  
  
     O **adicionar novo ativo** caixa de diálogo é exibida.  
  
10. No **tipo** , escolha **Microsoft.VisualStudio.MefComponent**.  
  
    > [!NOTE]  
    >  Esse valor corresponde do `MefComponent` elemento no arquivo extension.vsixmanifest. Este elemento Especifica o nome de um assembly de extensão do pacote VSIX. Para obter mais informações, consulte [MEFComponent Element (esquema de VSX)](http://msdn.microsoft.com/en-us/8a813141-8b73-44c9-b80b-ca85bbac9551).  
  
11. No **fonte** , escolha **um projeto na solução atual**.  
  
12. No **projeto** , escolha **ProjectItemDefinition**.  
  
13. Escolha o botão **OK**.  
  
14. Na barra de menus, escolha **criar**, **compilar solução**e, em seguida, certifique-se de que o projeto é compilado sem erros.  
  
15. Certifique-se de que a pasta de saída de compilação do projeto CustomActionProjectItem contém o arquivo CustomActionProjectItem.vsix.  
  
     Por padrão, a pasta de saída de compilação é o. pasta \bin\debug sob a pasta que contém o projeto CustomActionProjectItem.  
  
## <a name="testing-the-project-item"></a>O Item de projeto de teste  
 Agora você está pronto para testar o item de projeto. Primeiro, inicie a depuração da solução CustomActionProjectItem na instância experimental do Visual Studio. Em seguida, teste o **ação personalizada** item de projeto em um projeto do SharePoint na instância experimental do Visual Studio. Por fim, compilar e executar o projeto do SharePoint para verificar se a ação personalizada funciona conforme o esperado.  
  
#### <a name="to-start-debugging-the-solution"></a>Para iniciar a depuração da solução  
  
1.  Reinicie o Visual Studio com credenciais administrativas e, em seguida, abra a solução de CustomActionProjectItem.  
  
2.  Abra o arquivo de código personalizada e, em seguida, adicione um ponto de interrupção para a primeira linha do código no `InitializeType` método.  
  
3.  Escolha o **F5** tecla para iniciar a depuração.  
  
     Visual Studio instala a extensão para %UserProfile%\AppData\Local\Microsoft\VisualStudio\10.0Exp\Extensions\Contoso\Custom Item\1.0 de projeto de ação e inicia uma instância experimental do Visual Studio. Você testará o item de projeto nesta instância do Visual Studio.  
  
#### <a name="to-test-the-project-item-in-visual-studio"></a>Para testar o item de projeto no Visual Studio  
  
1.  Na instância experimental do Visual Studio, na barra de menus, escolha **arquivo**, **novo**, **projeto**.  
  
2.  Expanda **Visual C#** ou **Visual Basic** (dependendo da linguagem que dá suporte a seu modelo de item), expanda **SharePoint**e, em seguida, escolha o **2010**  nó.  
  
3.  Na lista de modelos de projeto, escolha **projeto do SharePoint 2010**.  
  
4.  No **nome** , digite **CustomActionTest**e, em seguida, escolha o **Okey** botão.  
  
5.  No **Assistente de personalização do SharePoint**, insira a URL do site que você deseja usar para depuração e, em seguida, escolha o **concluir** botão.  
  
6.  Em **Solution Explorer**, abra o menu de atalho para o nó do projeto, escolha **adicionar**e, em seguida, escolha **Novo Item**.  
  
7.  No **Adicionar Novo Item** caixa de diálogo caixa, escolha o **2010** nó sob o **SharePoint** nó.  
  
     Verifique o **ação personalizada** item aparece na lista de itens de projeto.  
  
8.  Escolha o **ação personalizada** item e, em seguida, escolha o **adicionar** botão.  
  
     O Visual Studio adiciona um item chamado **CustomAction1** no seu projeto e abre o Elements arquivo no editor.  
  
9. Verifique se que o código em outra instância do Visual Studio para no ponto de interrupção que você definiu anteriormente no `InitializeType` método.  
  
10. Escolha o **F5** tecla para continuar a depuração do projeto.  
  
11. Na instância experimental do Visual Studio, no **Solution Explorer**, abra o menu de atalho para o **CustomAction1** nó e, em seguida, escolha **Designer de exibição da ação personalizada**.  
  
12. Verifique se uma caixa de mensagem é exibida e, em seguida, escolha o **Okey** botão.  
  
     Você pode usar esse menu de atalho para fornecer opções adicionais ou comandos para desenvolvedores, como exibir um designer para a ação personalizada.  
  
13. Na barra de menus, escolha **exibição**, **saída**.  
  
     O **saída** janela será aberta.  
  
14. Em **Solution Explorer**, abra o menu de atalho para o **CustomAction1** item e, em seguida, altere seu nome para **MyCustomAction**.  
  
     No **saída** janela, uma mensagem de confirmação é exibida. Essa mensagem é gravada o <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemNameChanged> manipulador de eventos que você definiu no `CustomActionProjectItemTypeProvider` classe. Você pode manipular esse evento e outros eventos de item de projeto para implementar o comportamento personalizado quando o desenvolvedor modifica o item de projeto.  
  
#### <a name="to-test-the-custom-action-in-sharepoint"></a>Para testar a ação personalizada no SharePoint  
  
1.  Na instância experimental do Visual Studio, abra o arquivo de Elements. XML que é um filho de **MyCustomAction** item de projeto.  
  
2.  No arquivo Elements, faça as seguintes alterações e, em seguida, salve o arquivo:  
  
    -   No `CustomAction` elemento, defina o `Id` de atributo para um GUID ou outra cadeia de caracteres alguns exclusiva como mostra o exemplo a seguir:  
  
        ```  
        Id="cd85f6a7-af2e-44ab-885a-0c795b52121a"  
        ```  
  
    -   No `CustomAction` elemento, defina o `Title` atributo, como mostra o exemplo a seguir:  
  
        ```  
        Title="SharePoint Developer Center"  
        ```  
  
    -   No `CustomAction` elemento, defina o `Description` atributo, como mostra o exemplo a seguir:  
  
        ```  
        Description="Opens the SharePoint Developer Center Web site."  
        ```  
  
    -   No `UrlAction` elemento, defina o `Url` atributo, como mostra o exemplo a seguir:  
  
        ```  
        Url="http://msdn.microsoft.com/sharepoint/default.aspx"  
        ```  
  
3.  Pressione a tecla F5.  
  
     A ação personalizada é embalada e implantada no site do SharePoint que é especificado no **URL do Site** propriedade do projeto. O navegador da web abre a página padrão deste site.  
  
    > [!NOTE]  
    >  Se o **desabilitado de depuração de Script** caixa de diálogo for exibida, escolha o **Sim** botão para continuar a depuração do projeto.  
  
4.  No **ações do Site** menu, escolha **SharePoint Developer Center**, verifique se o navegador abre o site http://msdn.microsoft.com/sharepoint/default.aspxe, em seguida, feche o navegador da web.  
  
## <a name="cleaning-up-the-development-computer"></a>Limpando o computador de desenvolvimento  
 Depois de concluir o teste de item de projeto, remova o modelo de item de projeto da instância experimental do Visual Studio.  
  
#### <a name="to-clean-up-the-development-computer"></a>Para limpar o computador de desenvolvimento  
  
1.  Na instância experimental do Visual Studio, na barra de menus, escolha **ferramentas**, **extensões e atualizações**.  
  
     A caixa de diálogo **Extensões e Atualizações** é aberta.  
  
2.  Na lista de extensões, escolha **Item de projeto de ação personalizado**e, em seguida, escolha o **desinstalação** botão.  
  
3.  Na caixa de diálogo que aparece, escolha o **Sim** botão para confirmar que você deseja desinstalar a extensão.  
  
4.  Escolha o **reiniciar agora** botão para concluir a desinstalação.  
  
5.  Feche a instância experimental do Visual Studio e a instância em que a solução CustomActionProjectItem estiver aberta.  
  
## <a name="next-steps"></a>Próximas etapas  
 Depois de concluir este passo a passo, você pode adicionar um Assistente para o modelo de item. Quando um usuário adiciona um item de projeto de ação personalizada para um projeto do SharePoint, o assistente coleta informações sobre a ação (como o local e a URL para navegar quando a ação é escolhida) e adiciona informações ao arquivo Elements no novo item de projeto. Para obter mais informações, consulte [passo a passo: Criando um Item de projeto de ação personalizado com um modelo de Item, parte 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md).  
  
## <a name="see-also"></a>Consulte também  
 [Passo a passo: Criando um Item de projeto de ação personalizada com um modelo de Item, parte 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)   
 [Definindo tipos de Item de projeto do SharePoint personalizado](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Criando modelos de projeto e modelos de Item para itens de projeto do SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Usando o serviço de projeto do SharePoint](../sharepoint/using-the-sharepoint-project-service.md)   
 [Referência de esquema de modelo do Visual Studio](/visualstudio/extensibility/visual-studio-template-schema-reference)   
 [Editor de imagens para ícones](/cpp/windows/image-editor-for-icons)   
 [Criando um ícone ou outra imagem &#40;Editor de imagens para ícones&#41;](/cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)  
  
  