---
title: Adicionando um Submenu a um Menu | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- context menus
- submenus, cascading
- cascading submenus
- menus, creating cascading submenus
ms.assetid: 692600cb-d052-40e2-bdae-4354ae7c6c84
caps.latest.revision: "43"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 150252dceaff2d194af8f59d92fdaf39cdae259c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="adding-a-submenu-to-a-menu"></a>Adicionando um Submenu a um Menu
Este passo a passo se baseia a demonstração no [adicionar um Menu a barra de menus do Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) , mostrando como adicionar um submenu de **TestMenu** menu.  
  
 Um submenu é um secundário menu que aparece no menu de outro. Um submenu pode ser identificado pela seta que acompanha seu nome. Clicando no nome faz com que o submenu e os comandos a serem exibidos.  
  
 Este passo a passo cria um submenu em um menu na barra de menus do Visual Studio e coloca um novo comando no submenu. Passo a passo também implementa o novo comando.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 A partir do Visual Studio 2015, você não instalar o SDK do Visual Studio no Centro de download. Ele está incluído como um recurso opcional na instalação do Visual Studio. Você também pode instalar o SDK do VS posteriormente. Para obter mais informações, consulte [instalar o SDK do Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="adding-a-submenu-to-a-menu"></a>Adicionando um Submenu a um Menu  
  
1.  Siga as etapas em [adicionar um Menu a barra de menus do Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) para criar o item de menu e de projeto. As etapas neste passo a passo presumem que o nome do projeto VSIX é `TopLevelMenu`.  
  
2.  Abra TestCommandPackage.vsct. No `<Symbols>` seção, adicione um `<IDSymbol>` elemento para o submenu, uma para o grupo de submenu e outro para o comando, todos os `<GuidSymbol>` nó chamado "guidTopLevelMenuCmdSet". Este é o mesmo nó que contém o `<IDSymbol>` elemento para o menu de nível superior.  
  
    ```xml  
    <IDSymbol name="SubMenu" value="0x1100"/>  
    <IDSymbol name="SubMenuGroup" value="0x1150"/>  
    <IDSymbol name="cmdidTestSubCommand" value="0x0105"/>  
    ```  
  
3.  Adicionar o submenu recém-criado para o `<Menus>` seção.  
  
    ```xml  
    <Menu guid="guidTestCommandPackageCmdSet" id="SubMenu" priority="0x0100" type="Menu">  
        <Parent guid="guidTestCommandPackageCmdSet" id="MyMenuGroup"/>  
        <Strings>  
            <ButtonText>Sub Menu</ButtonText>  
            <CommandName>Sub Menu</CommandName>  
        </Strings>  
    </Menu>  
    ```  
  
     O par GUID/ID do pai Especifica o grupo de menu que foi gerado em [adicionar um Menu a barra de menus do Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md), e é um filho do menu de nível superior.  
  
4.  Adicionar o grupo de menu definido na etapa 2 para o `<Groups>` seção e torná-lo um filho do submenu.  
  
    ```xml  
    <Group guid="guidTestCommandPackageCmdSet" id="SubMenuGroup" priority="0x0000">  
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenu"/>  
    </Group>  
    ```  
  
5.  Adicionar um novo `<Button>` elemento para o `<Buttons>` seção para definir o comando criado na etapa 2 como um item no submenu.  
  
    ```xml  
    <Button guid="guidTestCommandPackageCmdSet" id="cmdidTestSubCommand" priority="0x0000" type="Button">  
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenuGroup" />  
        <Icon guid="guidImages" id="bmpPic2" />  
        <Strings>  
           <CommandName>cmdidTestSubCommand</CommandName>  
           <ButtonText>Test Sub Command</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
6.  Compile a solução e inicie a depuração. Você deve ver a instância experimental.  
  
7.  Clique em **TestMenu** para ver um submenu novo chamado **submenu**. Clique em **submenu** para abrir o submenu e verá um novo comando, **teste subcomando**. Observe que clicar em **teste subcomando** não fará nada.  
  
## <a name="adding-a-command"></a>Adicionando um comando  
  
1.  Abra TestCommand.cs e adicione a seguinte ID de comando após a ID de comando existente.  
  
    ```csharp  
    public const int cmdidTestSubCmd = 0x105;  
    ```  
  
2.  Adicione o subcomando. Localize o construtor de comando. Adicione as linhas a seguir logo após a chamada para o `AddCommand` método.  
  
    ```csharp  
    CommandID subCommandID = new CommandID(CommandSet, (int)TestCommandPackageGuids.cmdidTestSubCmd);  
    MenuCommand subItem = new MenuCommand(  
        new EventHandler(SubItemCallback), subCommandID);  
    commandService.AddCommand(subItem);  
  
    ```  
  
     O `SubItemCallback` manipulador de comando será definido posteriormente. Agora, o construtor deve ser assim:  
  
    ```csharp  
    private TestCommand(Package package)  
            {  
                if (package == null)  
                {  
                    throw new ArgumentNullException("package");  
                }  
  
                this.package = package;  
  
                OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
                if (commandService != null)  
                {  
                    var menuCommandID = new CommandID(CommandSet, CommandId);  
                    var menuItem = new MenuCommand(this.MenuItemCallback, menuCommandID);  
                    commandService.AddCommand(menuItem);  
                    CommandID subCommandID = new CommandID(CommandSet, cmdidTestSubCmd);  
                    MenuCommand subItem = new MenuCommand(  
                        new EventHandler(SubItemCallback), subCommandID);  
                    commandService.AddCommand(subItem);  
                }  
    ```  
  
3.  Adicione SubItemCallback(). Esse é o método é chamado quando o novo comando no submenu é clicado.  
  
    ```csharp  
    private void SubItemCallback(object sender, EventArgs e)  
    {  
        IVsUIShell uiShell = (IVsUIShell)this.ServiceProvider.GetService(  
            typeof(SVsUIShell));  
        Guid clsid = Guid.Empty;  
        int result;  
        uiShell.ShowMessageBox(  
            0,  
            ref clsid,  
            "TestCommand",  
            string.Format(CultureInfo.CurrentCulture,  
            "Inside TestCommand.SubItemCallback()",  
            this.ToString()),  
            string.Empty,  
            0,  
            OLEMSGBUTTON.OLEMSGBUTTON_OK,  
            OLEMSGDEFBUTTON.OLEMSGDEFBUTTON_FIRST,  
            OLEMSGICON.OLEMSGICON_INFO,  
            0,  
            out result);  
    }  
    ```  
  
4.  Compile o projeto e comece a depuração. A instância experimental deve aparecer.  
  
5.  Sobre o **TestMenu** menu, clique em **submenu** e, em seguida, clique em **teste subcomando**. Uma caixa de mensagem deve aparecer e exibir o texto "Teste comando dentro de TestCommand.SubItemCallback()".  
  
## <a name="see-also"></a>Consulte também  
 [Adicionar um Menu a barra de menus do Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)   
 [Comandos, menus e barras de ferramentas](../extensibility/internals/commands-menus-and-toolbars.md)