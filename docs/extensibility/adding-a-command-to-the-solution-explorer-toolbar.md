---
title: Adicionar um comando na barra de ferramentas do Gerenciador de soluções | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- toolbars [Visual Studio], adding buttons
- buttons [Visual Studio], adding to Solution Explorer
- Solution Explorer, adding buttons
ms.assetid: f6411557-2f4b-4e9f-b02e-fce12a6ac7e9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f6f732900ff3e73decb1dc01d5c131e26ba50669
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="adding-a-command-to-the-solution-explorer-toolbar"></a>Adicionar um comando na barra de ferramentas do Gerenciador de soluções
Este passo a passo mostra como adicionar um botão para o **Solution Explorer** barra de ferramentas.  
  
 Qualquer comando em um menu ou barra de ferramentas é chamado um botão no Visual Studio. Quando o botão é clicado, o código no manipulador de comando é executado. Normalmente, os comandos relacionados são agrupados juntos para formar um grupo. Menus ou barras de ferramentas atuam como contêineres para grupos. A prioridade determina a ordem na qual os comandos individuais em um grupo aparecem no menu ou na barra de ferramentas. Você pode impedir que um botão que está sendo exibido na barra de ferramentas ou menu controlando sua visibilidade. Um comando que é listado em um `<VisibilityConstraints>` seção do arquivo. VSCT aparece somente no contexto associado. A visibilidade não pode ser aplicada a grupos.  
  
 Para obter mais informações sobre menus, comandos da barra de ferramentas e arquivos. VSCT, consulte [comandos, Menus e barras de ferramentas](../extensibility/internals/commands-menus-and-toolbars.md).  
  
> [!NOTE]
>  Use arquivos de tabela de comando XML (. VSCT) em vez de arquivos de configuração (.ctc) de tabela de comando para definir como os menus e comandos são exibidos no seu VSPackages. Para obter mais informações, consulte [tabela de comando do Visual Studio (. Arquivos VSCT)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
## <a name="prerequisites"></a>Pré-requisitos  
 A partir do Visual Studio 2015, você não instalar o SDK do Visual Studio no Centro de download. Ele está incluído como um recurso opcional na instalação do Visual Studio. Você também pode instalar o SDK do VS posteriormente. Para obter mais informações, consulte [instalar o SDK do Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-an-extension-with-a-menu-command"></a>Criando uma extensão com um comando de Menu  
 Crie um projeto do VSIX denominado `SolutionToolbar`. Adicionar um modelo de item de comando de menu chamado **ToolbarButton**. Para obter informações sobre como fazer isso, consulte [criando uma extensão com um comando de Menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
## <a name="adding-a-button-to-the-solution-explorer-toolbar"></a>Adicionar um botão na barra de ferramentas do Gerenciador de soluções  
 Esta seção do passo a passo mostra como adicionar um botão de **Solution Explorer** barra de ferramentas. Quando o botão é clicado, o código no método de retorno de chamada é executado.  
  
1.  No arquivo ToolbarButtonPackage.vsct, vá para o `<Symbols>` seção. O `<GuidSymbol>` nó contém o grupo de menus e o comando que foi gerado pelo modelo de pacote. Adicionar um `<IDSymbol>` elemento para esse nó para declarar o grupo que manterá seu comando.  
  
    ```xml  
    <IDSymbol name="SolutionToolbarGroup" value="0x0190"/>  
    ```  
  
2.  No `<Groups>` seção, após a entrada de grupo existente, definir o novo grupo é declarado na etapa anterior.  
  
    ```xml  
    <Group guid="guidToolbarButtonPackageCmdSet"  
           id="SolutionToolbarGroup" priority="0xF000">  
            <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_PROJWIN"/>  
          </Group>  
    ```  
  
     Definir o pai par GUID:ID como `guidSHLMainMenu` e `IDM_VS_TOOL_PROJWIN` coloca esse grupo **Gerenciador de soluções** barra de ferramentas e definir um valor de prioridade alta coloca após os outros grupos de comando.  
  
3.  No `<Buttons>` seção, altere a ID do pai do gerado `<Button>` entrada para refletir o grupo que você definiu na etapa anterior. A modificação `<Button>` elemento deve ter esta aparência:  
  
    ```xml  
    <Button guid="guidToolbarButtonPackageCmdSet" id="ToolbarButtonId" priority="0x0100" type="Button">  
        <Parent guid="guidToolbarButtonPackageCmdSet" id="SolutionToolbarGroup" />  
        <Icon guid="guidImages" id="bmpPicStrikethrough" />  
        <Strings>  
            <ButtonText>Invoke ToolbarButton</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
4.  Compile o projeto e comece a depuração. A instância experimental aparece.  
  
     O **Solution Explorer** barra de ferramentas deve exibir o botão de comando novo à direita dos botões existentes. O ícone do botão é o tachado.  
  
5.  Clique no botão novo.  
  
     Uma caixa de diálogo com a mensagem **ToolbarButtonPackage dentro de SolutionToolbar.ToolbarButton.MenuItemCallback()** devem ser exibidos.  
  
## <a name="controlling-the-visibility-of-a-button"></a>Controlando a visibilidade de um botão  
 Esta seção do passo a passo mostra como controlar a visibilidade de um botão da barra de ferramentas. Definindo um contexto para um ou mais projetos de `<VisibilityConstraints>` seção do arquivo SolutionToolbar.vsct, você restringir um botão para aparecem somente quando um projeto ou projetos são abertos.  
  
#### <a name="to-display-a-button-when-one-or-more-projects-are-open"></a>Para exibir um botão quando um ou mais projetos estão abertos  
  
1.  No `<Buttons>` seção do ToolbarButtonPackage.vsct, adicionar dois sinalizadores de comando para existente `<Button>` elemento, entre o `<Strings>` e `<Icons>` marcas.  
  
    ```xml  
    <CommandFlag>DefaultInvisible</CommandFlag>  
    <CommandFlag>DynamicVisibility</CommandFlag>  
    ```  
  
     O `DefaultInvisible` e `DynamicVisibility` sinalizadores devem ser definidos isso que as entradas na `<VisibilityConstraints>` seção entre em vigor.  
  
2.  Criar um `<VisibilityConstraints>` seção que tem duas `<VisibilityItem>` entradas. Colocar a nova seção logo após o fechamento `</Commands>` marca.  
  
    ```xml  
    <VisibilityConstraints>  
        <VisibilityItem guid="guidToolbarButtonPackageCmdSet"  
              id="ToolbarButtonId"  
              context="UICONTEXT_SolutionHasSingleProject" />  
        <VisibilityItem guid="guidToolbarButtonPackageCmdSet"  
              id="ToolbarButtonId"  
              context="UICONTEXT_SolutionHasMultipleProjects" />  
    </VisibilityConstraints>  
    ```  
  
     Cada item de visibilidade representa uma condição em que o botão especificado é exibido. Para aplicar várias condições, você deve criar várias entradas para o mesmo botão.  
  
3.  Compile o projeto e comece a depuração. A instância experimental aparece.  
  
     O **Solution Explorer** barra de ferramentas não contém o botão tachado.  
  
4.  Abra qualquer solução que contém um projeto.  
  
     Botão Tachado aparece na barra de ferramentas à direita dos botões existentes.  
  
5.  Sobre o **arquivo** menu, clique em **fechar solução**. O botão desaparecerá da barra de ferramentas.  
  
 A visibilidade do botão é controlada pelo [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] até que o VSPackage é carregado. Depois que o VSPackage for carregado, a visibilidade do botão é controlada pelo VSPackage.  Para obter mais informações, consulte [MenuCommands Vs. OleMenuCommands](../extensibility/menucommands-vs-olemenucommands.md).  
  
## <a name="see-also"></a>Consulte também  
 [Comandos, menus e barras de ferramentas](../extensibility/internals/commands-menus-and-toolbars.md)