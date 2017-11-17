---
title: MenuCommands Vs. OleMenuCommands | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands, creating in VSPackages
- command buttons, creating and placing
- menus, creating commands
ms.assetid: 553d5e07-3e19-4aba-b490-6c7dd05fd82e
caps.latest.revision: "46"
manager: douge
ms.openlocfilehash: 1153d35c022f4734488e71c38f4dbc34418610f6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="menucommands-vs-olemenucommands"></a>MenuCommands Vs. OleMenuCommands
Você pode criar comandos de menu derivando de <xref:System.ComponentModel.Design.MenuCommand> ou <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> objeto e impementling os manipuladores de eventos apropriado. Na maioria dos casos, você pode usar <xref:System.ComponentModel.Design.MenuCommand>, conforme o VSPackage do modelo de projeto, mas, ocasionalmente, você talvez precise usar <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>.  
  
 Os comandos que um VSPackage disponibiliza para o IDE deve ser visíveis e habilitados antes que um usuário podem usá-los. Quando os comandos são criados em um arquivo. VSCT usando o modelo de projeto de pacote do Visual Studio, eles são visíveis e habilitados por padrão. Definir alguns sinalizadores de comando, como `DynamicItemStart`, pode alterar o comportamento padrão. A visibilidade, status habilitado e outras propriedades de um comando também podem ser alteradas no código em tempo de execução, acessando o <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> objeto que está associado com o comando.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Para acompanhar este passo a passo, você deve instalar o SDK do Visual Studio. Para obter mais informações, consulte [SDK do Visual Studio](../extensibility/visual-studio-sdk.md).  
  
## <a name="template-locations-for-the-visual-studio-package-template"></a>Locais de modelo para o modelo de pacote do Visual Studio  
 Você pode encontrar o modelo de pacote do Visual Studio no **novo projeto** caixa de diálogo em **Visual Basic / extensibilidade**, **c# / extensibilidade**, ou **outros Tipos de projeto / extensibilidade**.  
  
## <a name="creating-a-command"></a>Criar um comando  
 Todos os comandos, grupos de comando, menus, barras de ferramentas e janelas de ferramentas são definidas no arquivo. VSCT. Para obter mais informações, consulte [tabela de comando do Visual Studio (. Arquivos VSCT)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
 Se você estiver criando um VSPackage usando o modelo de pacote, selecione **comando de Menu** para criar um arquivo. VSCT e definir um comando de menu padrão. Para obter mais informações, consulte [criando uma extensão com um comando de Menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
#### <a name="to-add-a-command-to-the-ide"></a>Para adicionar um comando ao IDE  
  
1.  Abra o arquivo. VSCT.  
  
2.  No `Symbols` seção, localize o [GuidSymbol](../extensibility/guidsymbol-element.md) elemento que contém os grupos e comandos.  
  
3.  Criar um [IDSymbol](../extensibility/idsymbol-element.md) elemento para cada menu, grupo ou comando que você deseja adicionar, conforme mostrado no exemplo a seguir.  
  
     <!--FIXME [!CODE [ButtonGroup#01](../CodeSnippet/VS_Snippets_VSSDK/buttongroup#01)]  -->
    ```xaml  
    <GuidSymbol name="guidButtonGroupCmdSet" value="{f69209e9-975a-4543-821d-1f4a2c52d737}">
      <IDSymbol name="MyMenuGroup" value="0x1020" />
      <IDSymbol name="cmdidMyCommand" value="0x0100" />
    </GuidSymbol>
    ```  
  
    O `name` atributos do `GuidSymbol` e `IDSymbol` elementos fornecem o par de GUID:ID para cada novo menu, o grupo ou o comando. O `guid` representa um conjunto de comandos que está definido para o VSPackage. Você pode definir vários conjuntos de comandos. Cada par de GUID:ID deve ser exclusivo.  
  
4.  No [botões](../extensibility/buttons-element.md) seção, crie um [botão](../extensibility/button-element.md) elemento para definir o comando, conforme mostrado no exemplo a seguir.  
  
     <!--FIXME [!CODE [ButtonGroup#03](../CodeSnippet/VS_Snippets_VSSDK/buttongroup#03)]  -->
    ```xaml  
    <Button guid="guidButtonGroupCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">
      <Parent guid="guidButtonGroupCmdSet" id="MyMenuGroup" />
      <Icon guid="guidImages" id="bmpPic1" />
      <Strings>
        <CommandName>cmdidMyCommand</CommandName>
        <ButtonText>My Command name</ButtonText>
      </Strings>
    </Button>
    ```  
  
    1.  Definir o `guid` e `id` campos para corresponder GUID:ID do novo comando.  
  
    2.  Definir o `priority` atributo.  
  
         O `priority` atributo é usado pela. VSCT para determinar o local do botão entre os outros objetos no respectivo grupo pai.  
  
         Comandos que têm valores de prioridade inferiores são exibidos acima ou à esquerda de comandos que têm valores de prioridade mais altos. São permitidos valores de prioridade duplicados, mas a posição relativa de comandos que têm a mesma prioridade é determinada pela ordem na qual VSPackages são processados em tempo de execução e ordem não pode ser predeterminado.  
  
         A omissão de `priority` atributo define seu valor como 0.  
  
    3.  Definir o `type` atributo. Na maioria dos casos, seu valor será `"Button"`. Para obter descrições dos outros tipos de botão válidos, consulte [elemento Button](../extensibility/button-element.md).  
  
5.  Na definição do botão, crie um [cadeias de caracteres](../extensibility/strings-element.md) elemento que contém um [ButtonText](../extensibility/buttontext-element.md) elemento para conter o nome do menu como ele aparece no IDE e um [CommandName](../extensibility/commandname-element.md) elemento para conter o nome do comando que é usado para acessar o menu no **comando** janela.  
  
     Se a cadeia de caracteres de texto do botão inclui o caractere '&', o usuário pode abrir o menu pressionando a tecla ALT mais o caractere ou imediatamente após o '&'.  
  
     Adicionando um `Tooltip` elemento fará com que o texto contido sejam exibidas quando um usuário coloca o ponteiro sobre o botão.  
  
6.  Adicionar uma [ícone](../extensibility/icon-element.md) elemento para especificar o ícone, se houver, para ser exibido com o comando. Ícones são necessários para os botões na barra de ferramentas, mas não para itens de menu. O `guid` e `id` do `Icon` elemento deve corresponder aos de um [Bitmap](../extensibility/bitmap-element.md) elemento definido no `Bitmaps` seção.  
  
7.  Adicione sinalizadores de comando, conforme apropriado, para alterar a aparência e comportamento do botão. Para fazer isso, adicione um [CommandFlag](../extensibility/command-flag-element.md) elemento na definição do menu.  
  
8.  Defina o grupo pai do comando. O grupo pai pode ser um grupo que você cria, um grupo de outro pacote ou um grupo do IDE. Por exemplo, para adicionar o comando a barra de ferramentas de edição da Visual Studio, ao lado de **comentário** e **Remover comentário** botões, definir o pai para guidStdEditor:IDG_VS_EDITTOOLBAR_COMMENT. Se o pai for um grupo definido pelo usuário, ele deve ser o filho de um menu, uma barra de ferramentas ou uma janela de ferramenta que aparece no IDE.  
  
     Você pode fazer isso de duas maneiras, dependendo de seu projeto:  
  
    -   No `Button` elemento, criar um [pai](../extensibility/parent-element.md) elemento e defina seu `guid` e `id` campos para o Guid e a ID do grupo que hospedará o comando, também conhecido como o *grupo pai primário*.  
  
         O exemplo a seguir define um comando que será exibido em um menu definido pelo usuário.  
  
         <!--FIXME [!CODE [TopLevelMenu#03](../CodeSnippet/VS_Snippets_VSSDK/toplevelmenu#03)]  -->
        ```xaml  
        <Button guid="guidTopLevelMenuCmdSet" id="cmdidTestCommand" priority="0x0100" type="Button">
          <Parent guid="guidTopLevelMenuCmdSet" id="MyMenuGroup" />
          <Icon guid="guidImages" id="bmpPic1" />
          <Strings>
            <CommandName>cmdidTestCommand</CommandName>
            <ButtonText>Test Command</ButtonText>
          </Strings>
        </Button>
        ```  
  
    -   Você pode omitir o `Parent` elemento se o comando deve ser posicionado usando o posicionamento de comando. Criar um [CommandPlacements](../extensibility/commandplacements-element.md) elemento antes do `Symbols` seção e, em seguida, adicione um [CommandPlacement](../extensibility/commandplacement-element.md) elemento que tem o `guid` e `id` do comando, um `priority`e um pai, conforme mostrado no exemplo a seguir.  
  
         <!-- FIXME [!CODE [ButtonGroup#04](../CodeSnippet/VS_Snippets_VSSDK/buttongroup#04)] -->  
        ```xaml  
        <CommandPlacements>
          <CommandPlacement guid="guidButtonGroupCmdSet" id="cmdidMyCommand" priority="0x105">
            <Parent guid="guidButtonGroupCmdSet" id="MyMenuGroup" />
          </CommandPlacement>
        </CommandPlacements>
        ```  
  
         Criar vários posicionamentos de comando que têm o mesmo GUID:ID e tem diferentes pais faz com que um menu seja exibido em vários locais. Para obter mais informações, consulte [CommandPlacements](../extensibility/commandplacements-element.md) elemento.  
  
     Para obter mais informações sobre grupos de comando e paternidade, consulte [criando grupos reutilizável de botões](../extensibility/creating-reusable-groups-of-buttons.md).  
  
 Neste ponto, o comando ficará visível no IDE, mas não terá nenhuma funcionalidade. Se o comando foi criado pelo modelo do pacote, ele terá um manipulador de clique que exibe uma mensagem por padrão.  
  
## <a name="handling-the-new-command"></a>O novo comando de tratamento  
 A maioria dos comandos em código gerenciado podem ser tratados pelo gerenciado pacote MPF (estrutura) por meio da associação de comando com um <xref:System.ComponentModel.Design.MenuCommand> objeto ou <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> objeto e implementar seus manipuladores de eventos.  
  
 Para o código que usa o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface diretamente para a manipulação de comandos, você deve implementar o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface e seus métodos. Os dois métodos mais importantes são <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> e <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>.  
  
1.  Obter o <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> da instância, conforme mostrado no exemplo a seguir.  
  
     [!code-csharp[ButtonGroup#21](../extensibility/codesnippet/CSharp/menucommands-vs-olemenucommands_5.cs)]  
  
2.  Criar um <xref:System.ComponentModel.Design.CommandID> objeto que tem como seus parâmetros o GUID e a ID do comando para manipular, conforme mostrado no exemplo a seguir.  
  
     [!code-csharp[ButtonGroup#22](../extensibility/codesnippet/CSharp/menucommands-vs-olemenucommands_6.cs)]  
  
     O modelo de pacote do Visual Studio fornece duas coleções, `GuidList` e `PkgCmdIDList`, para manter os GUIDs e IDs de comandos. Esses são preenchidas automaticamente para os comandos que são adicionados pelo modelo, mas para os comandos que você adicionar manualmente, você também deverá adicionar a entrada de ID para o `PkgCmdIdList` classe.  
  
     Como alternativa, você pode preencher o <xref:System.ComponentModel.Design.CommandID> objeto usando o valor de cadeia de caracteres bruta de GUID e o valor de inteiro da ID.  
  
3.  Criar uma instância em um <xref:System.ComponentModel.Design.MenuCommand> ou <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> objeto que especifica o método que trata o comando junto com o <xref:System.ComponentModel.Design.CommandID>, conforme mostrado no exemplo a seguir.  
  
     [!code-csharp[ButtonGroup#23](../extensibility/codesnippet/CSharp/menucommands-vs-olemenucommands_7.cs)]  
  
     O <xref:System.ComponentModel.Design.MenuCommand> é apropriado para comandos estáticos. Exibe do item de menu dinâmico exige QueryStatus manipuladores de eventos. O <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> adiciona o <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> evento que ocorre quando o menu de host do comando é abertas e algumas outras propriedades, como <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.Text%2A>.  
  
     Comandos criados pelo modelo de pacote são passados por padrão para um <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> objeto o `Initialize()` método da classe de pacote.  
  
4.  O <xref:System.ComponentModel.Design.MenuCommand> é apropriado para comandos estáticos. Exibe do item de menu dinâmico exige QueryStatus manipuladores de eventos. O <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> adiciona o <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> evento que ocorre quando o menu de host do comando é abertas e algumas outras propriedades, como <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.Text%2A>.  
  
     Comandos criados pelo modelo de pacote são passados por padrão para um <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> objeto o `Initialize()` método da classe de pacote. O Assistente do Visual Studio implementa o `Initialize` método usando `MenuCommand`. Para exibições de item de menu dinâmico, você deve alterar isso para `OleMenuCommand`, conforme é mostrado na próxima etapa. Além disso, para alterar o texto do item de menu, você deve adicionar um sinalizador de comando textoAltera para o botão de comando de menu no arquivo. VSCT, conforme é mostrado no exemplo a seguir  
  
     <!--FIXME [!CODE [MenuText#02](../CodeSnippet/VS_Snippets_VSSDK/menutext#02)]-->  
    ```xaml  
    <Button guid="guidMenuTextCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">
      <Parent guid="guidMenuTextCmdSet" id="MyMenuGroup" />
      <Icon guid="guidImages" id="bmpPic1" />
      <CommandFlag>TextChanges</CommandFlag>
      <Strings>
        <CommandName>cmdidMyCommand</CommandName>
        <ButtonText>My Command name</ButtonText>
      </Strings>
    </Button>
    ```
  
5.  Passe o novo comando de menu para o <xref:System.ComponentModel.Design.IMenuCommandService.AddCommand%2A> método o <xref:System.ComponentModel.Design.IMenuCommandService> interface. Isso é feito por padrão para comandos criados pelo modelo de pacote, conforme mostrado no exemplo a seguir  
  
     [!code-csharp[ButtonGroup#24](../extensibility/codesnippet/CSharp/menucommands-vs-olemenucommands_9.cs)]  
  
6.  Implemente o método que trata o comando.  
  
#### <a name="to-implement-querystatus"></a>Para implementar QueryStatus  
  
1.  O evento QueryStatus ocorre antes que um comando é exibido. Isso permite que as propriedades desse comando para ser defina no manipulador de eventos antes de alcançar o usuário. Somente os comandos que são adicionados como <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> objetos podem acessar este método.  
  
     Adicionar uma `EventHandler` o objeto para o <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> evento no <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> objeto que é criado para tratar o comando, conforme mostrado no exemplo a seguir (`menuItem` é o <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> instância).  
  
     [!code-csharp[MenuText#14](../extensibility/codesnippet/CSharp/menucommands-vs-olemenucommands_10.cs)]
     [!code-vb[MenuText#14](../extensibility/codesnippet/VisualBasic/menucommands-vs-olemenucommands_10.vb)]  
  
     O `EventHandler` objeto recebe o nome de um método que é chamado quando o status do comando de menu é consultado.  
  
2.  Implemente o método de manipulador de status de consulta para o comando. O `object` `sender` parâmetro pode ser convertido em um <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> objeto, que é usado para definir os vários atributos do comando de menu, incluindo o texto. A tabela a seguir mostra as propriedades no <xref:System.ComponentModel.Design.MenuCommand> classe (que a classe MPF <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> deriva) que correspondam ao <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> sinalizadores.  
  
    |Propriedade MenuCommand|Sinalizador OLECMDF|  
    |--------------------------|------------------|  
    |<xref:System.ComponentModel.Design.MenuCommand.Checked%2A> = `true`|<xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>|  
    |<xref:System.ComponentModel.Design.MenuCommand.Visible%2A> = `false`|<xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>|  
    |<xref:System.ComponentModel.Design.MenuCommand.Enabled%2A> = `true`|<xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>|  
  
     Para alterar o texto de um comando de menu, use o <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.Text%2A> propriedade o <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> do objeto, como mostrado no exemplo a seguir.  
  
     [!code-csharp[MenuText#11](../extensibility/codesnippet/CSharp/menucommands-vs-olemenucommands_11.cs)]
     [!code-vb[MenuText#11](../extensibility/codesnippet/VisualBasic/menucommands-vs-olemenucommands_11.vb)]  
  
 MPF controla automaticamente no caso de grupos desconhecidos ou sem suportados. A menos que um comando foi adicionado para o <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> usando o <xref:System.ComponentModel.Design.IMenuCommandService.AddCommand%2A> método, o comando não é suportado.  
  
### <a name="handling-commands-by-using-the-iolecommandtarget-interface"></a>Manipulando comandos usando a Interface IOleCommandTarget  
 Para o código que usa o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> diretamente a interface, o VSPackage deve implementar o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> e <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> métodos do <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface. Se o VSPackage implementa uma hierarquia de projeto, o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> métodos do <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interface deve ser implementada em vez disso.  
  
 Tanto o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> e <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> métodos destinam-se para receber um conjunto único comando `GUID` e uma matriz de IDs de comando como entrada. É recomendável que VSPackages suporta completamente esse conceito de várias IDs em uma chamada. No entanto, como um VSPackage não é chamado de outros VSPackages, você pode assumir que a matriz de comando contém apenas uma ID de comando porque o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> e <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> métodos são executados em uma ordem bem definida. Para obter mais informações sobre roteamento, consulte [roteamento de comando VSPackages](../extensibility/internals/command-routing-in-vspackages.md).  
  
 Para o código que usa o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface diretamente para a manipulação de comandos, você deve implementar o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método VSPackage da seguinte forma para lidar com comandos.  
  
##### <a name="to-implement-the-querystatus-method"></a>Para implementar o método QueryStatus  
  
1.  Retornar <xref:Microsoft.VisualStudio.VSConstants.S_OK> para comandos válidos.  
  
2.  Definir o `cmdf` elemento o `prgCmds` parâmetro.  
  
     O valor da `cmdf` elemento é a união lógica de valores da <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> enumeração, combinada com a lógica OR (`|`) operador.  
  
     Use a enumeração apropriada, com base no status do comando:  
  
    -   Se o comando é suportado:  
  
         `prgCmds[0].cmdf = OLECMDF_SUPPORTED;`  
  
    -   Se o comando deve ser invisível no momento:  
  
         `prgCmds[0].cmdf |= OLECMDF_INVISIBLE;`  
  
    -   Se o comando é ativado e parece ter clicado:  
  
         `prgCmds[0].cmdf |= OLECMDF_LATCHED;`  
  
         No caso do processamento de comandos que são hospedados em um menu do tipo `MenuControllerLatched`, o primeiro comando que é marcado pelo `OLECMDF_LATCHED` sinalizador é o comando padrão que é exibido, o menu de inicialização. Para obter mais informações sobre `MenuController` menu tipos, consulte [elemento Menu](../extensibility/menu-element.md).  
  
    -   Se o comando está habilitado no momento:  
  
         `prgCmds[0].cmdf |= OLECMDF_ENABLED;`  
  
    -   Se o comando é parte de um menu de atalho e é ocultado por padrão:  
  
         `prgCmds[0] cmdf |= OLECMDF_DEFHIDEONCTXMENU`  
  
    -   Se o comando usa o `TEXTCHANGES` sinalizador, defina o `rgwz` elemento do `pCmdText` parâmetro para o novo texto do comando e definir o `cwActual` elemento do `pCmdText` parâmetro para o tamanho da cadeia de caracteres de comando.  
  
     Para condições de erro, o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método deve lidar com casos de erro a seguir:  
  
    -   Se o GUID é desconhecido ou sem suporte, retorne `OLECMDERR_E_UNKNOWNGROUP`.  
  
    -   Se o GUID é conhecido, mas a ID de comando é desconhecido ou sem suporte, retorne `OLECMDERR_E_NOTSUPPORTED`.  
  
 A implementação VSPackage o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> método também deve retornar códigos de erro específicos, dependendo se o comando é suportado e se o comando foi resolvido com êxito.  
  
##### <a name="to-implement-the-exec-method"></a>Para implementar o método Exec  
  
-   Se o comando `GUID` é desconhecido, retornar `OLECMDERR_E_UNKNOWNGROUP`.  
  
-   Se o `GUID` é conhecido, mas o comando ID é desconhecido, retorne `OLECMDERR_E_NOTSUPPORTED`.  
  
-   Se o `GUID` e ID corresponder o par de GUID:ID que é usada pelo comando no arquivo. VSCT de comando, execute o código que está associado com o comando e retornar <xref:Microsoft.VisualStudio.VSConstants.S_OK>.  
  
## <a name="see-also"></a>Consulte também  
 [Referência de esquema XML do VSCT](../extensibility/vsct-xml-schema-reference.md)   
 [Ampliar menus e comandos](../extensibility/extending-menus-and-commands.md)