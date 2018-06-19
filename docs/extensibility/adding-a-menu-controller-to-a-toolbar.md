---
title: Adicionar um controlador de Menu a uma barra de ferramentas | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- toolbars [Visual Studio], adding menu controllers
- menus, adding menu controllers to toolbars
- menu controllers, adding to toolbars
ms.assetid: 6af9b0b4-037f-404c-bb40-aaa1970768ea
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 63db98df400333216f5e753f8b6f82a61e785cd5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31104618"
---
# <a name="adding-a-menu-controller-to-a-toolbar"></a>Adicionar um controlador de Menu a uma barra de ferramentas
Este passo a passo se baseia o [adicionando uma barra de ferramentas para uma janela de ferramenta](../extensibility/adding-a-toolbar-to-a-tool-window.md) passo a passo e mostra como adicionar um controlador de menu na barra de ferramentas de janela de ferramenta. As etapas mostradas aqui também podem ser aplicadas para a barra de ferramentas é criada no [adicionando uma barra de ferramentas](../extensibility/adding-a-toolbar.md) passo a passo.  
  
 Um controlador de menu é um controle de divisão. O lado esquerdo do controlador menu mostra o último comando, e ele pode ser executado clicando nele. À direita do controlador de menu é uma seta que, quando clicado, abre uma lista de comandos adicionais. Quando você clicar em um comando na lista, o comando é executado, e substitui o comando no lado esquerdo do controlador de menu. Dessa forma, o controlador de menu opera como um botão de comando que sempre mostra o comando usado por último em uma lista.  
  
 Controladores de menu podem aparecer em menus, mas são geralmente usadas em barras de ferramentas.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 A partir do Visual Studio 2015, você não instalar o SDK do Visual Studio no Centro de download. Ele está incluído como um recurso opcional na instalação do Visual Studio. Você também pode instalar o SDK do VS posteriormente. Para obter mais informações, consulte [instalar o SDK do Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-menu-controller"></a>Criando um controlador de Menu  
  
#### <a name="to-create-a-menu-controller"></a>Para criar um controlador de menu  
  
1.  Siga os procedimentos descritos em [adicionando uma barra de ferramentas para uma janela de ferramenta](../extensibility/adding-a-toolbar-to-a-tool-window.md) para criar uma janela de ferramenta com uma barra de ferramentas.  
  
2.  No TWTestCommandPackage.vsct, vá para a seção de símbolos. No elemento GuidSymbol chamado **guidTWTestCommandPackageCmdSet**, declare o controlador de menu, grupo de controlador de menu e três itens de menu.  
  
    ```xml  
    <IDSymbol name="TestMenuController" value="0x1300" /><IDSymbol name="TestMenuControllerGroup" value="0x1060" /><IDSymbol name="cmdidMCItem1" value="0x0130" /><IDSymbol name="cmdidMCItem2" value="0x0131" /><IDSymbol name="cmdidMCItem3" value="0x0132" />  
    ```  
  
3.  Na seção de Menus, após a última entrada de menu, defina o controlador de menu como um menu.  
  
    ```xml  
    <Menu guid="guidTWTestCommandPackageCmdSet" id="TestMenuController" priority="0x0100" type="MenuController">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" />  
        <CommandFlag>IconAndText</CommandFlag>  
        <CommandFlag>TextChanges</CommandFlag>  
        <CommandFlag>TextIsAnchorCommand</CommandFlag>  
        <Strings>  
            <ButtonText>Test Menu Controller</ButtonText>  
            <CommandName>Test Menu Controller</CommandName>  
        </Strings>  
    </Menu>  
    ```  
  
     O `TextChanges` e `TextIsAnchorCommand` sinalizadores devem ser incluídos para habilitar o controlador de menu refletir o último comando selecionado.  
  
4.  Os grupos de seção, após a última entrada de grupo, adicione o grupo do controlador de menu.  
  
    ```xml  
    <Group guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" priority="0x000">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuController" />  
    </Group>  
    ```  
  
     Ao configurar o controlador de menu como o pai, todos os comandos colocados nesse grupo aparecerá no controlador de menu. O `priority` atributo for omitido, que define como o valor padrão de 0, pois ela será o único grupo no controlador de menu.  
  
5.  Na seção de botões, após a última entrada de botão, adicione um elemento de botão para cada um dos seus itens de menu.  
  
    ```xml  
    <Button guid="guidTWTestCommandPackageCmdSet" id="cmdidMCItem1" priority="0x0000" type="Button">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" />  
        <Icon guid="guidImages" id="bmpPic1" />  
        <CommandFlag>IconAndText</CommandFlag>  
        <Strings>  
            <ButtonText>MC Item 1</ButtonText>  
            <CommandName>MC Item 1</CommandName>  
        </Strings>  
    </Button>  
    <Button guid="guidTWTestCommandPackageCmdSet" id="cmdidMCItem2" priority="0x0100" type="Button">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" />  
        <Icon guid="guidImages" id="bmpPic2" />  
        <CommandFlag>IconAndText</CommandFlag>  
        <Strings>  
            <ButtonText>MC Item 2</ButtonText>  
            <CommandName>MC Item 2</CommandName>  
        </Strings>  
    </Button>  
    <Button guid="guidTWTestCommandPackageCmdSet" id="cmdidMCItem3" priority="0x0200" type="Button">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" />  
        <Icon guid="guidImages" id="bmpPicSearch" />  
        <CommandFlag>IconAndText</CommandFlag>  
        <Strings>  
            <ButtonText>MC Item 3</ButtonText>  
            <CommandName>MC Item 3</CommandName>  
        </Strings>  
    </Button>  
    ```  
  
6.  Neste ponto, você pode examinar o controlador de menu. Compile o projeto e comece a depuração. Você deve ver a instância experimental.  
  
    1.  No **exibição / outras janelas** menu, abrir **teste ToolWindow**.  
  
    2.  O controlador de menu é exibido na barra de ferramentas na janela da ferramenta.  
  
    3.  Clique na seta à direita do controlador de menu para ver os três comandos possíveis.  
  
     Observe que, quando você clica em um comando, o título do controlador menu muda para exibir esse comando. Na próxima seção, adicionaremos o código para ativar esses comandos.  
  
## <a name="implementing-the-menu-controller-commands"></a>Implementando os comandos de Menu controlador  
  
1.  Em TWTestCommandPackageGuids.cs, adicione IDs de comando para os itens de três menu após o IDs de comando existente.  
  
    ```csharp  
    public const int cmdidMCItem1 = 0x130;  
    public const int cmdidMCItem2 = 0x131;  
    public const int cmdidMCItem3 = 0x132;  
    ```  
  
2.  Em TWTestCommand.cs, adicione o seguinte código na parte superior da classe TWTestCommand.  
  
    ```csharp  
    private int currentMCCommand; // The currently selected menu controller command  
    ```  
  
3.  No construtor TWTestCommand, após a última chamada para o `AddCommand` método, adicione código para rotear os eventos para cada comando pelos mesmos manipuladores.  
  
    ```csharp  
    for (int i = TWTestCommandPackageGuids.cmdidMCItem1; i <=  
        TWTestCommandPackageGuids.cmdidMCItem3; i++)  
    {  
        CommandID cmdID = new  
        CommandID(new Guid(TWTestCommandPackageGuids.guidTWTestCommandPackageCmdSet), i);  
        OleMenuCommand mc = new OleMenuCommand(new  
          EventHandler(OnMCItemClicked), cmdID);  
        mc.BeforeQueryStatus += new EventHandler(OnMCItemQueryStatus);  
        commandService.AddCommand(mc);  
        // The first item is, by default, checked.   
        if (TWTestCommandPackageGuids.cmdidMCItem1 == i)  
        {  
            mc.Checked = true;  
            this.currentMCCommand = i;  
        }  
    }  
    ```  
  
4.  Adicione um manipulador de eventos para a classe TWTestCommand para marcar o comando selecionado como marcada.  
  
    ```csharp  
    private void OnMCItemQueryStatus(object sender, EventArgs e)  
    {  
        OleMenuCommand mc = sender as OleMenuCommand;  
        if (null != mc)  
        {  
            mc.Checked = (mc.CommandID.ID == this.currentMCCommand);  
        }  
    }  
    ```  
  
5.  Adicione um manipulador de eventos que exibe uma caixa de mensagem quando o usuário seleciona um comando no controlador de menu:  
  
    ```csharp  
    private void OnMCItemClicked(object sender, EventArgs e)  
    {  
        OleMenuCommand mc = sender as OleMenuCommand;  
        if (null != mc)  
        {  
            string selection;  
            switch (mc.CommandID.ID)  
            {  
                case c.cmdidMCItem1:  
                    selection = "Menu controller Item 1";  
                    break;  
  
                case TWTestCommandPackageGuids.cmdidMCItem2:  
                    selection = "Menu controller Item 2";  
                    break;  
  
                case TWTestCommandPackageGuids.cmdidMCItem3:  
                    selection = "Menu controller Item 3";  
                    break;  
  
                default:  
                    selection = "Unknown command";  
                    break;  
            }  
            this.currentMCCommand = mc.CommandID.ID;  
  
            IVsUIShell uiShell =  
              (IVsUIShell) ServiceProvider.GetService(typeof(SVsUIShell));  
            Guid clsid = Guid.Empty;  
            int result;  
            uiShell.ShowMessageBox(  
                       0,  
                       ref clsid,  
                       "Test Tool Window Toolbar Package",  
                       string.Format(CultureInfo.CurrentCulture,  
                                     "You selected {0}", selection),  
                       string.Empty,  
                       0,  
                       OLEMSGBUTTON.OLEMSGBUTTON_OK,  
                       OLEMSGDEFBUTTON.OLEMSGDEFBUTTON_FIRST,  
                       OLEMSGICON.OLEMSGICON_INFO,  
                       0,  
                       out result);  
        }  
    }  
    ```  
  
## <a name="testing-the-menu-controller"></a>Teste o controlador de Menu  
  
1.  Compile o projeto e comece a depuração. Você deve ver a instância experimental.  
  
2.  Abra o **teste ToolWindow** no **exibição / outras janelas** menu.  
  
     O controlador de menu é exibido na barra de ferramentas na janela de ferramenta e exibe **MC Item 1**.  
  
3.  Clique no botão de controlador do menu à esquerda da seta.  
  
     Você deverá ver três itens, o primeiro deles está selecionado e tem uma caixa de realce ao redor de seu ícone. Clique em **MC Item 3**.  
  
     Uma caixa de diálogo é exibida com a mensagem **você selecionou o controlador de Menu Item 3**. Observe que a mensagem correspondente ao texto do botão de controlador do menu. O botão de menu do controlador agora exibe **MC Item 3**.  
  
## <a name="see-also"></a>Consulte também  
 [Adicionando uma barra de ferramentas para uma janela de ferramenta](../extensibility/adding-a-toolbar-to-a-tool-window.md)   
 [Adicionar uma barra de ferramentas](../extensibility/adding-a-toolbar.md)