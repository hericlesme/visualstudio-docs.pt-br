---
title: Dinamicamente adicionando itens de Menu | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DYNAMICITEMSTART
- menu items, adding dynamically
- menus, adding dynamic items
ms.assetid: d281e9c9-b289-4d64-8d0a-094bac6c333c
caps.latest.revision: "37"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 1eaa8cc41e7b27d509e68d6785c34a9ae214ffd3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="dynamically-adding-menu-items"></a>Dinamicamente adicionando itens de Menu
Você pode adicionar itens de menu em tempo de execução, especificando o `DynamicItemStart` comando sinalizador em uma definição de botão do espaço reservado no arquivo de comando-tabela (. VSCT) do Visual Studio, em seguida, definir (no código) o número do menu de itens para exibir e manipular os comandos. Quando o VSPackage é carregado, o espaço reservado é substituído com os itens de menu dinâmico.  
  
 O Visual Studio usa listas dinâmicas o **usados recentemente** lista (MRU), que exibe os nomes de documentos que foram abertos recentemente, e o **Windows** lista, que exibe os nomes do windows que estão abertos no momento.   O `DynamicItemStart` sinalizador em uma definição de comando Especifica que o comando é um espaço reservado até que o VSPackage é aberto. Quando o VSPackage é aberto, o espaço reservado é substituído por 0 ou mais comandos que são criados em tempo de execução e adicionados à lista dinâmica. Você não poderá ver a posição no menu onde a lista dinâmica é exibida até que o VSPackage é aberto.  Para preencher a lista dinâmica, o Visual Studio solicitará o VSPackage para procurar um comando com uma ID de caracteres cujos primeiro são o mesmo que a ID do espaço reservado. Quando o Visual Studio encontra um comando, ele adiciona o nome do comando para a lista dinâmica. Incrementa a identificação e procura por outro comando correspondente para adicionar à lista dinâmica até que comandos não mais dinâmicas.  
  
 Este passo a passo mostra como definir o projeto de inicialização em uma solução do Visual Studio com um comando para o **Solution Explorer** barra de ferramentas. Ele usa um controlador de menu que tem uma lista suspensa dinâmica dos projetos na solução ativa. Para evitar esse comando apareça quando nenhuma solução está aberta ou quando a solução aberta tem apenas um projeto, o VSPackage é carregado apenas quando uma solução tiver vários projetos.  
  
 Para obter mais informações sobre arquivos. VSCT, consulte [tabela de comando do Visual Studio (. Arquivos VSCT)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
## <a name="creating-an-extension-with-a-menu-command"></a>Criando uma extensão com um comando de Menu  
  
1.  Crie um projeto do VSIX denominado `DynamicMenuItems`.  
  
2.  Quando o projeto for aberto, adicione um modelo de item de comando personalizado e denomine- **DynamicMenu**. Para obter mais informações, consulte [criando uma extensão com um comando de Menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
## <a name="setting-up-the-elements-in-the-vsct-file"></a>Configurando os elementos no arquivo. VSCT  
 Para criar um controlador de menu com itens de menu dinâmico em uma barra de ferramentas, você deve especificar os seguintes elementos:  
  
-   Dois grupos, um que contém o controlador de menu e outra que contém os itens de menu no menu suspenso de comando  
  
-   Elemento de um menu do tipo`MenuController`  
  
-   Dois botões, que atua como o espaço reservado para os itens de menu e outro que fornece o ícone e a dica de ferramenta na barra de ferramentas.  
  
1.  Em DynamicMenuPackage.vsct, defina as IDs de comando. Vá para a seção de símbolos e substitua os elementos IDSymbol o **guidDynamicMenuPackageCmdSet** GuidSymbol bloco. Você precisa definir IDSymbol elementos para os dois grupos, o controlador de menu, o comando de espaço reservado e o comando de âncora.  
  
    ```csharp  
    <GuidSymbol name="guidDynamicMenuPackageCmdSet" value="{ your GUID here }">  
        <IDSymbol name="MyToolbarItemGroup" value="0x1020" />  
        <IDSymbol name="MyMenuControllerGroup" value="0x1025" />  
        <IDSymbol name="MyMenuController" value ="0x1030"/>  
        <IDSymbol name="cmdidMyAnchorCommand" value="0x0103" />  
        <!-- NOTE: The following command expands at run time to some number of ids.  
         Try not to place command ids after it (e.g. 0x0105, 0x0106).  
         If you must add a command id after it, make the gap very large (e.g. 0x200) -->  
        <IDSymbol name="cmdidMyDynamicStartCommand" value="0x0104" />  
    </GuidSymbol>    
    ```  
  
2.  Na seção grupos, exclua os grupos existentes e adicione os dois grupos que você acabou de definir:  
  
    ```  
    <Groups>  
        <!-- The group that adds the MenuController on the Solution Explorer toolbar.   
             The 0x4000 priority adds this group after the group that contains the  
             Preview Selected Items button, which is normally at the far right of the toolbar. -->  
        <Group guid="guidDynamicMenuPackageCmdSet" id="MyToolbarItemGroup" priority="0x4000" >  
            <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_PROJWIN" />  
        </Group>  
        <!-- The group for the items on the MenuController drop-down. It is added to the MenuController submenu. -->  
        <Group guid="guidDynamicMenuPackageCmdSet" id="MyMenuControllerGroup" priority="0x4000" >  
            <Parent guid="guidDynamicMenuPackageCmdSet" id="MyMenuController" />  
        </Group>  
    </Groups>  
    ```  
  
     Adicione o MenuController. Defina o sinalizador de comando DynamicVisibility, porque não está sempre visível. O ButtonText não é exibida.  
  
    ```  
    <Menus>  
        <!-- The MenuController to display on the Solution Explorer toolbar.  
             Place it in the ToolbarItemGroup.-->  
        <Menu guid="guidDynamicMenuPackageCmdSet" id="MyMenuController" priority="0x1000" type="MenuController">  
            <Parent guid="guidDynamicMenuPackageCmdSet" id="MyToolbarItemGroup" />  
            <CommandFlag>DynamicVisibility</CommandFlag>  
            <Strings>  
               <ButtonText></ButtonText>  
           </Strings>  
        </Menu>  
    </Menus>  
    ```  
  
3.  Adicione dois botões, como um espaço reservado para os itens de menu dinâmico e outra como uma âncora para o MenuController.  
  
     O pai do botão de espaço reservado é a **MyMenuControllerGroup**. Adicione os sinalizadores de comando DynamicItemStart, DynamicVisibility e textoAltera para o botão do espaço reservado. O ButtonText não é exibida.  
  
     O botão de âncora contém o ícone e o texto de dica de ferramenta. O pai do botão âncora é também o **MyMenuControllerGroup**. Adicione o sinalizador de comando NoShowOnMenuController para certificar-se de que o botão, na verdade, não aparece no menu suspenso de controlador e o sinalizador de comando FixMenuController para torná-lo a âncora permanente.  
  
    ```  
    <!-- The placeholder for the dynamic items that expand to N items at runtime. -->  
    <Buttons>  
        <Button guid="guidDynamicMenuPackageCmdSet" id="cmdidMyDynamicStartCommand" priority="0x1000" >  
          <Parent guid="guidDynamicMenuPackageCmdSet" id="MyMenuControllerGroup" />  
          <CommandFlag>DynamicItemStart</CommandFlag>  
          <CommandFlag>DynamicVisibility</CommandFlag>  
          <CommandFlag>TextChanges</CommandFlag>  
          <!-- This text does not appear. -->  
          <Strings>  
            <ButtonText>Project</ButtonText>  
          </Strings>  
        </Button>  
  
        <!-- The anchor item to supply the icon/tooltip for the MenuController -->  
        <Button guid="guidDynamicMenuPackageCmdSet" id="cmdidMyAnchorCommand" priority="0x0000" >  
          <Parent guid="guidDynamicMenuPackageCmdSet" id="MyMenuControllerGroup" />  
          <!-- This is the icon that appears on the Solution Explorer toolbar. -->  
          <Icon guid="guidImages" id="bmpPicArrows"/>  
          <!-- Do not show on the menu controller's drop down list-->  
          <CommandFlag>NoShowOnMenuController</CommandFlag>  
          <!-- Become the permanent anchor item for the menu controller -->  
          <CommandFlag>FixMenuController</CommandFlag>  
          <!-- The text that appears in the tooltip.-->  
          <Strings>  
            <ButtonText>Set Startup Project</ButtonText>  
          </Strings>  
        </Button>  
    </Buttons>  
    ```  
  
4.  Adicionar um ícone para o projeto (na pasta de recursos) e, em seguida, adicionar a referência a ele no arquivo. VSCT. Neste passo a passo, usamos o ícone de setas que está incluído no modelo de projeto.  
  
5.  Adicione uma seção VisibilityConstraints fora da seção de comandos antes da seção de símbolos. (Você pode receber um aviso se você adicioná-lo depois de símbolos). Esta seção certifica-se de que o controlador de menu é exibido apenas quando uma solução com vários projetos é carregada.  
  
    ```  
    <VisibilityConstraints>  
         <!--Make the MenuController show up only when there is a solution with more than one project loaded-->  
        <VisibilityItem guid="guidDynamicMenuPackageCmdSet" id="MyMenuController" context="UICONTEXT_SolutionHasMultipleProjects"/>  
    </VisibilityConstraints>  
    ```  
  
## <a name="implementing-the-dynamic-menu-command"></a>Implementando o comando de menu dinâmico  
 Você cria uma classe de comando de menu dinâmico que herda de <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>. Nessa implementação, o construtor Especifica um predicado a ser usado para correspondência de comandos. Você deve substituir o <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.DynamicItemMatch%2A> método usar esse predicado para definir o <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.MatchedCommandId%2A> propriedade que identifica o comando a ser invocado.  
  
1.  Criar um nova classe arquivo c# chamado DynamicItemMenuCommand.cs e adicione uma classe denominada **DynamicItemMenuCommand** que herda de <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>:  
  
    ```csharp  
    class DynamicItemMenuCommand : OleMenuCommand  
    {  
  
    }  
  
    ```  
  
2.  Adicione o seguinte usando instruções:  
  
    ```csharp  
    using Microsoft.VisualStudio.Shell;  
    using Microsoft.VisualStudio.Shell.Interop;  
    using System.ComponentModel.Design;  
    ```  
  
3.  Adicione um campo particular para armazenar o predicado de correspondência:  
  
    ```csharp  
    private Predicate<int> matches;  
  
    ```  
  
4.  Adicione um construtor que herda o <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> construtor e especifica um manipulador de comandos e um <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> manipulador. Adicione um predicado para o comando de correspondência:  
  
    ```csharp  
    public DynamicItemMenuCommand(CommandID rootId, Predicate<int> matches, EventHandler invokeHandler, EventHandler beforeQueryStatusHandler)  
        : base(invokeHandler, null /*changeHandler*/, beforeQueryStatusHandler, rootId)  
    {  
        if (matches == null)  
        {  
            throw new ArgumentNullException("matches");  
        }  
  
        this.matches = matches;  
    }  
    ```  
  
5.  Substituir o <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.DynamicItemMatch%2A> método assim que ele chama as correspondências de predicado e conjuntos de <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.MatchedCommandId%2A> propriedade:  
  
    ```csharp  
    public override bool DynamicItemMatch(int cmdId)  
    {  
        // Call the supplied predicate to test whether the given cmdId is a match.  
        // If it is, store the command id in MatchedCommandid   
        // for use by any BeforeQueryStatus handlers, and then return that it is a match.  
        // Otherwise clear any previously stored matched cmdId and return that it is not a match.  
        if (this.matches(cmdId))  
        {  
            this.MatchedCommandId = cmdId;  
            return true;  
        }  
  
        this.MatchedCommandId = 0;  
        return false;  
    }  
    ```  
  
## <a name="adding-the-command"></a>Adicionando o comando  
 O construtor DynamicMenu é onde você configurar os comandos de menu, incluindo itens de menu e menus dinâmicos.  
  
1.  No DynamicMenuPackageGuids.cs, adicione o GUID do conjunto de comandos e a ID de comando:  
  
    ```csharp  
    public const string guidDynamicMenuPackageCmdSet = "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file  
    public const uint cmdidMyCommand = 0x104;  
    ```  
  
2.  No arquivo DynamicMenu.cs, adicione o seguinte usando instruções:  
  
    ```csharp  
    using EnvDTE;  
    using EnvDTE80;  
    using System.ComponentModel.Design;  
    ```  
  
3.  Na classe DynamicMenu, adicione um campo particular **dte2**.  
  
    ```csharp  
    private DTE2 dte2;  
    ```  
  
4.  Adicione um campo particular rootItemId:  
  
    ```csharp  
    private int rootItemId = 0;  
    ```  
  
5.  No construtor DynamicMenu, adicione o comando de menu. Na próxima seção vamos definir o manipulador de comando, o `BeforeQueryStatus` manipulador de eventos e o predicado de correspondência.  
  
    ```csharp  
    private DynamicMenu(Package package)  
    {  
        if (package == null)  
        {  
            throw new ArgumentNullException(nameof(package));  
        }  
  
        this.package = package;  
  
        OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
        if (commandService != null)  
        {  
            // Add the DynamicItemMenuCommand for the expansion of the root item into N items at run time.   
            CommandID dynamicItemRootId = new CommandID(new Guid(DynamicMenuPackageGuids.guidDynamicMenuPackageCmdSet), (int)DynamicMenuPackageGuids.cmdidMyCommand);  
            DynamicItemMenuCommand dynamicMenuCommand = new DynamicItemMenuCommand(dynamicItemRootId,  
                IsValidDynamicItem,  
                OnInvokedDynamicItem,  
                OnBeforeQueryStatusDynamicItem);  
                commandService.AddCommand(dynamicMenuCommand);  
                }  
  
        dte2 = (DTE2)this.ServiceProvider.GetService(typeof(DTE));  
    }  
    ```  
  
## <a name="implementing-the-handlers"></a>Implementando os manipuladores  
 Para implementar os itens de menu dinâmico em um controlador de menu, você deve tratar o comando quando um item dinâmico é clicado. Você também deve implementar a lógica que define o estado do item de menu. Adicione manipuladores para a classe DynamicMenu.  
  
1.  Para implementar o **definir o projeto de inicialização** de comando, adicione o **OnInvokedDynamicItem** manipulador de eventos. Ele procura o projeto cujo nome é o mesmo que o texto do comando que foi chamado e o define como o projeto de inicialização, definindo o caminho absoluto no <xref:EnvDTE.SolutionBuild.StartupProjects%2A> propriedade.  
  
    ```csharp  
    private void OnInvokedDynamicItem(object sender, EventArgs args)  
    {  
        DynamicItemMenuCommand invokedCommand = (DynamicItemMenuCommand)sender;  
        // If the command is already checked, we don't need to do anything  
        if (invokedCommand.Checked)  
            return;  
  
        // Find the project that corresponds to the command text and set it as the startup project  
        var projects = dte2.Solution.Projects;  
        foreach (Project proj in projects)  
        {  
            if (invokedCommand.Text.Equals(proj.Name))  
            {  
                dte2.Solution.SolutionBuild.StartupProjects = proj.FullName;  
                return;  
            }  
        }  
    }  
    ```  
  
2.  Adicionar o `OnBeforeQueryStatusDynamicItem` manipulador de eventos. Isso é chamado antes do manipulador de um `QueryStatus` eventos. Determina se o item de menu é um item de "real", ou seja, não o item do espaço reservado, e se o item já foi feito check (o que significa que o projeto já está definido como o projeto de inicialização).  
  
    ```csharp  
    private void OnBeforeQueryStatusDynamicItem(object sender, EventArgs args)  
    {  
        DynamicItemMenuCommand matchedCommand = (DynamicItemMenuCommand)sender;  
        matchedCommand.Enabled = true;  
        matchedCommand.Visible = true;  
  
        // Find out whether the command ID is 0, which is the ID of the root item.  
        // If it is the root item, it matches the constructed DynamicItemMenuCommand,  
         // and IsValidDynamicItem won't be called.  
        bool isRootItem = (matchedCommand.MatchedCommandId == 0);  
  
        // The index is set to 1 rather than 0 because the Solution.Projects collection is 1-based.  
        int indexForDisplay = (isRootItem ? 1 : (matchedCommand.MatchedCommandId - (int) DynamicMenuPackageGuids.cmdidMyCommand) + 1);  
  
        matchedCommand.Text = dte2.Solution.Projects.Item(indexForDisplay).Name;  
  
        Array startupProjects = (Array)dte2.Solution.SolutionBuild.StartupProjects;  
        string startupProject = System.IO.Path.GetFileNameWithoutExtension((string)startupProjects.GetValue(0));  
  
        // Check the command if it isn't checked already selected  
        matchedCommand.Checked = (matchedCommand.Text == startupProject);  
  
        // Clear the ID because we are done with this item.  
        matchedCommand.MatchedCommandId = 0;  
    }  
    ```  
  
## <a name="implementing-the-command-id-match-predicate"></a>Implementando o predicado de correspondência de ID de comando  
  
1.  Implemente o predicado de correspondência. É preciso determinar duas coisas: primeiro, se a ID de comando é válida (ele é maior que ou igual à ID de comando declarado) e o segundo Especifica um projeto possíveis (é menor do que o número de projetos na solução).  
  
    ```csharp  
    private bool IsValidDynamicItem(int commandId)  
    {  
        // The match is valid if the command ID is >= the id of our root dynamic start item   
        // and the command ID minus the ID of our root dynamic start item  
        // is less than or equal to the number of projects in the solution.  
        return (commandId >= (int)DynamicMenuPackageGuids.cmdidMyCommand) && ((commandId - (int)DynamicMenuPackageGuids.cmdidMyCommand) < dte2.Solution.Projects.Count);  
    }  
    ```  
  
## <a name="setting-the-vspackage-to-load-only-when-a-solution-has-multiple-projects"></a>Definindo o VSPackage carregar somente quando uma solução tiver vários projetos  
 Porque o **definir o projeto de inicialização** comando não faz sentido, a menos que a solução ativa tem mais de um projeto, você pode definir o VSPackage para carregar automaticamente apenas nesse caso. Você usa <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> junto com o contexto de interface do usuário <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids.SolutionHasMultipleProjects>. No arquivo DynamicMenuPackage.cs Adicione atributos a seguir à classe DynamicMenuPackage:  
  
```csharp  
[PackageRegistration(UseManagedResourcesOnly = true)]  
[InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]  
[ProvideMenuResource("Menus.ctmenu", 1)]  
[ProvideAutoLoad(UIContextGuids.SolutionHasMultipleProjects)]  
[Guid(DynamicMenuPackageGuids.PackageGuidString)]  
public sealed class DynamicMenuItemsPackage : Package  
{}  
```  
  
## <a name="testing-the-set-startup-project-command"></a>O comando de inicialização definir como projeto de teste  
 Agora você pode testar seu código.  
  
1.  Compile o projeto e comece a depuração. A instância experimental deve aparecer.  
  
2.  Na instância experimental, abra uma solução que tem mais de um projeto.  
  
     Você verá o ícone de seta a **Solution Explorer** barra de ferramentas. Quando você expandi-lo, itens de menu que representam os diferentes projetos na solução devem aparecer.  
  
3.  Quando você marca um dos projetos, torna-se o projeto de inicialização.  
  
4.  Quando você fecha a solução ou abre uma solução que tenha apenas um projeto, o ícone da barra de ferramentas deve desaparecer.  
  
## <a name="see-also"></a>Consulte também  
 [Comandos, Menus e barras de ferramentas](../extensibility/internals/commands-menus-and-toolbars.md)   
 [Como os VSPackages adicionam elementos da interface do usuário](../extensibility/internals/how-vspackages-add-user-interface-elements.md)