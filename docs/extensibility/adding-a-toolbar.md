---
title: Adicionando uma barra de ferramentas | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- toolbars [Visual Studio], adding to IDE
- IDE, adding toolbars
ms.assetid: 17302c25-6f59-4e97-8c85-54f95336a07f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c4a9a28ef3fced7cc2dab1f14b2854f2ca27d362
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="adding-a-toolbar"></a>Adicionando uma barra de ferramentas
Este passo a passo mostra como adicionar uma barra de ferramentas para o Visual Studio IDE.  
  
 Uma barra de ferramentas é uma faixa horizontal ou vertical que contém botões que estão associados a comandos. Dependendo da sua implementação, uma barra de ferramentas no IDE pode ser reposicionada, encaixada em qualquer lado da janela principal do IDE ou feita permaneça na frente de outras janelas.  
  
 Além disso, os usuários podem adicionar comandos a uma barra de ferramentas ou removê-los dela usando o **personalizar** caixa de diálogo. Normalmente, as barras de ferramentas no VSPackages são personalizáveis do usuário. O IDE manipula toda a personalização e o VSPackage responde aos comandos. O VSPackage não precisa saber onde um comando estiver localizado fisicamente.  
  
 Para obter mais informações sobre menus, consulte [comandos, Menus e barras de ferramentas](../extensibility/internals/commands-menus-and-toolbars.md).  
  
## <a name="prerequisites"></a>Pré-requisitos  
 A partir do Visual Studio 2015, você não instalar o SDK do Visual Studio no Centro de download. Ele está incluído como um recurso opcional na instalação do Visual Studio. Você também pode instalar o SDK do VS posteriormente. Para obter mais informações, consulte [instalar o SDK do Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-an-extension-with-a-toolbar"></a>Criando uma extensão com uma barra de ferramentas  
 Crie um projeto do VSIX denominado `IDEToolbar`. Adicionar um modelo de item de comando de menu chamado **ToolbarTestCommand**. Para obter informações sobre como fazer isso, consulte [criando uma extensão com um comando de Menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
## <a name="creating-a-toolbar-for-the-ide"></a>Criando uma barra de ferramentas para o IDE  
  
1.  No ToolbarTestCommandPackage.vsct, procure a seção de símbolos. No elemento GuidSymbol chamado guidToolbarTestCommandPackageCmdSet, adicione declarações para uma barra de ferramentas e barra de ferramentas, da seguinte maneira.  
  
    ```xml  
    <IDSymbol name="Toolbar" value="0x1000" />  
    <IDSymbol name="ToolbarGroup" value="0x1050" />  
  
    ```  
  
2.  Na parte superior da seção de comandos, crie uma seção de Menus. Adicione um elemento de Menu para a seção de Menus para definir sua barra de ferramentas.  
  
    ```xml  
    <Menus>  
        <Menu guid="guidToolbarTestCommandPackageCmdSet" id="Toolbar"  
            type="Toolbar" >  
            <CommandFlag>DefaultDocked</CommandFlag>  
            <Strings>  
                <ButtonText>Test Toolbar</ButtonText>  
                <CommandName>Test Toolbar</CommandName>  
            </Strings>  
          </Menu>  
    </Menus>  
    ```  
  
     Barras de ferramentas não podem ser aninhadas como submenus. Portanto, não é necessário atribuir um grupo pai. Além disso, você não precisa definir uma prioridade, porque o usuário pode mover as barras de ferramentas. Normalmente, o posicionamento inicial de uma barra de ferramentas é definido por meio de programação, mas as alterações subsequentes pelo usuário são persistentes.  
  
3.  No [grupos](../extensibility/groups-element.md) seção, após a entrada de grupo existente, definir um [grupo](../extensibility/group-element.md) elemento para conter os comandos da barra de ferramentas.  
  
    ```xml  
    <Group guid="guidToolbarTestCommandPackageCmdSet" id="ToolbarGroup"  
          priority="0x0000">  
      <Parent guid="guidToolbarTestCommandPackageCmdSet" id="Toolbar"/>  
    </Group>  
    ```  
  
4.  Exibir o botão na barra de ferramentas. Na seção de botões, substitua o bloco pai no botão na barra de ferramentas. O bloco de botão resultante deve ter esta aparência:  
  
    ```xml  
    <Button guid="guidToolbarTestCommandPackageCmdSet" id="ToolbarTestCommandId" priority="0x0100" type="Button">  
        <Parent guid= "guidToolbarTestCommandPackageCmdSet" id="ToolbarGroup" />  
                <Icon guid="guidImages" id="bmpPic1" />  
        <Strings>  
            <ButtonText>Invoke ToolbarTestCommand</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
     Por padrão, se uma barra de ferramentas não tem nenhum comando, ele não aparece.  
  
5.  Compile o projeto e comece a depuração. A instância experimental deve aparecer.  
  
6.  Clique com botão direito a barra de menus do Visual Studio para obter uma lista das barras de ferramentas. Selecione **barra de ferramentas de teste**.  
  
7.  Agora você deve ver a barra de ferramentas como um ícone à direita de localização no ícone de arquivos. Quando você clicar no ícone, você verá uma caixa de mensagem que diz **ToolbarTestCommandPackage. Dentro de IDEToolbar.ToolbarTestCommand.MenuItemCallback()**.  
  
## <a name="see-also"></a>Consulte também  
 [Comandos, menus e barras de ferramentas](../extensibility/internals/commands-menus-and-toolbars.md)