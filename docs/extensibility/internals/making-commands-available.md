---
title: Disponibilizar comandos | Microsoft Docs
ms.date: 03/22/2018
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- menus [Visual Studio SDK], commands
- best practices, menu and toolbar commands
- toolbars [Visual Studio], best practices
- menu commands, best practices
ms.assetid: 3ffc4312-c6db-4759-a946-a4bb85f4a17a
caps.latest.revision: ''
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 88f29f575cc59b365978376f01f53f2624c31cd0
ms.sourcegitcommit: 768118d470da9c7164d2f23ca918dfe26a4be72f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/28/2018
---
# <a name="making-commands-available"></a>Disponibilizar comandos
Quando vários VSPackages são adicionados ao Visual Studio, a interface do usuário (UI) pode ficar sobrecarregada com comandos. Você pode programar o pacote para ajudar a reduzir esse problema, da seguinte maneira:

-   O pacote de programa para que ele é carregado apenas quando um usuário requê-lo.

-   O pacote de programa para que os comandos são exibidos somente quando elas podem ser necessárias no contexto do estado atual do ambiente de desenvolvimento integrado (IDE).

## <a name="delayed-loading"></a>Carregamento atrasado
 A maneira comum para habilitar carregamento atrasado é projetar o VSPackage para que os comandos são exibidos na interface do usuário, mas o próprio pacote não será carregado até que um usuário clica em um dos comandos. Para fazer isso, no arquivo. VSCT, crie comandos que não têm nenhum sinalizador de comando.

 O exemplo a seguir mostra a definição de um comando de menu de um arquivo. VSCT. Esse é o comando que é gerado pelo modelo de pacote Visual Studio quando o **comando de Menu** está selecionada no modelo.

```xml
<Button guid="guidTopLevelMenuCmdSet" id="cmdidTestCommand" priority="0x0100" type="Button">
  <Parent guid="guidTopLevelMenuCmdSet" id="MyMenuGroup" />
  <Icon guid="guidImages" id="bmpPic1" />
  <Strings>
    <CommandName>cmdidTestCommand</CommandName>
    <ButtonText>Test Command</ButtonText>
  </Strings>
</Button>

```

 No exemplo, se o grupo pai, `MyMenuGroup`, é um filho de um menu de nível superior, como o **ferramentas** menu, o comando ficará visível no menu, mas o pacote que executa o comando não será carregado até que o comando é clicado por um usuário. No entanto, por programação o comando para implementar o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface, você pode habilitar o pacote a ser carregado quando o menu que contém o comando primeiro é expandido.

 Observe que o carregamento atrasado também pode melhorar o desempenho de inicialização.

## <a name="current-context-and-the-visibility-of-commands"></a>Contexto atual e a visibilidade de comandos
 Você pode programar o VSPackage comandos seja visível ou oculto, dependendo do estado atual dos dados VSPackage ou as ações que são relevantes no momento. Você pode habilitar o VSPackage definir o estado de seus comandos, normalmente por meio de uma implementação do <xref:EnvDTE.IDTCommandTarget.QueryStatus%2A> método do <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface, mas isso requer o VSPackage ser carregadas antes que ele pode executar o código. Em vez disso, recomendamos que você habilite o IDE gerenciar a visibilidade dos comandos sem carregar o pacote. Para fazer isso, no arquivo. VSCT, associar comandos com um ou mais contextos de interface de usuário especiais. Nesses contextos de interface do usuário são identificados por um GUID conhecido como um *o contexto de comando GUID*.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] monitora as alterações que resultam de ações do usuário, como carregar um projeto ou indo de edição para a construção. Quando ocorrem alterações, a aparência do IDE automaticamente é modificada. A tabela a seguir mostra quatro principais contextos do IDE alteração-la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] monitores.

|Tipo de contexto|Descrição|
|---------------------|-----------------|
|Tipo de projeto ativo|Para a maioria dos tipos de projeto, isso `GUID` valor é o mesmo que o GUID do VSPackage que implementa o projeto. No entanto, [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] projetos usam o tipo de projeto `GUID` como o valor.|
|Janela ativa|Normalmente, isso é a última janela do documento ativo que estabelece o contexto de interface do usuário atual para associações de chave. No entanto, ele também pode ser uma janela de ferramenta que tenha uma tabela de chave de associação que se parece com o navegador da Web interno. Para janelas de documento com várias guias, como o editor de HTML, cada guia tem um contexto de outro comando `GUID`.|
|Serviço de idioma ativo|O serviço de idioma que está associado com o arquivo que está sendo exibido em um editor de texto.|
|Janela da ferramenta ativa|Uma janela de ferramenta que está aberto e tem o foco.|

 Uma área de contexto principais quinto é o estado da interface do usuário do IDE. Contextos de interface do usuário são identificados pelo contexto do comando ativo `GUID`s, da seguinte maneira:

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionBuilding_guid>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Debugging_guid>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Dragging_guid>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.FullScreenMode_guid>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.DesignMode_guid>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.NoSolution_guid>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_guid>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.EmptySolution_guid>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasSingleProject_guid>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasMultipleProjects_guid>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.CodeWindow_guid>

 Esses GUIDs são marcados como ativos ou inativos, dependendo do estado atual do IDE. Vários contextos de interface do usuário podem estar ativos ao mesmo tempo.

### <a name="hiding-and-displaying-commands-based-on-context"></a>Ocultando e exibindo comandos com base no contexto
 Você pode exibir ou ocultar um comando de pacote no IDE sem carregar o pacote propriamente dito. Para fazer isso, defina o comando no arquivo. VSCT do pacote usando o `DefaultDisabled`, `DefaultInvisible`, e `DynamicVisibility` comando sinalizadores e adicionando um ou mais [VisibilityItem](../../extensibility/visibilityitem-element.md) elementos para o [ VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) seção. Quando um contexto de comando especificado `GUID` se torna ativo, o comando será exibido sem carregar o pacote.

### <a name="custom-context-guids"></a>GUIDs de contexto personalizado
 Se um contexto de comando apropriado que GUID não estiver definido, você pode definir um no seu VSPackage e programa para ser ativos ou inativos conforme necessário para controlar a visibilidade dos seus comandos. Use o <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> serviço para:

-   Registrar os GUIDs de contexto (chamando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> método).

-   Obter o estado de um contexto de `GUID` (chamando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> método).

-   Ativar contexto `GUID`s e desativar (chamando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> método).

    > [!CAUTION]
    > Certifique-se de que o VSPackage não afeta o estado de qualquer contexto existente GUID porque outros VSPackages pode dependem deles.

## <a name="example"></a>Exemplo
 O exemplo a seguir de um comando VSPackage demonstra a visibilidade dinâmica de um comando que é gerenciado pelo contextos de comando sem carregar o VSPackage.

 O comando é definido para ser habilitado e exibido sempre que existe uma solução; ou seja, sempre que um contexto do comando seguinte GUIDs está ativo:

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_EmptySolution>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionHasMultipleProjects>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionHasSingleProject>

No exemplo, observe que cada sinalizador de comando é um separado [comando sinalizador](../../extensibility/command-flag-element.md) elemento.

```xml
<Button guid="guidDynamicVisibilityCmdSet" id="cmdidMyCommand"
        priority="0x0100" type="Button">
  <Parent guid="guidDynamicVisibilityCmdSet" id="MyMenuGroup" />
  <Icon guid="guidImages" id="bmpPic1" />
  <CommandFlag>DefaultDisabled</CommandFlag>
  <CommandFlag>DefaultInvisible</CommandFlag>
  <CommandFlag>DynamicVisibility</CommandFlag>
  <Strings>
    <CommandName>cmdidMyCommand</CommandName>
    <ButtonText>My Command name</ButtonText>
  </Strings>
</Button>
```

Além disso, observe que cada contexto de interface do usuário deve ser fornecido em um separado `VisibilityItem` elemento, da seguinte maneira.

```xml
<VisibilityConstraints>
  <VisibilityItem guid="guidDynamicVisibilityCmdSet"
                  id="cmdidMyCommand" context="UICONTEXT_EmptySolution" />
  <VisibilityItem guid="guidDynamicVisibilityCmdSet"
                      id="cmdidMyCommand" context="UICONTEXT_SolutionHasSingleProject" />
  <VisibilityItem guid="guidDynamicVisibilityCmdSet"
                  id="cmdidMyCommand" context="UICONTEXT_SolutionHasMultipleProjects" />
</VisibilityConstraints>
```

## <a name="see-also"></a>Consulte também

- [MenuCommands Vs. OleMenuCommands](../../extensibility/menucommands-vs-olemenucommands.md)
- [Como os VSPackages adicionam elementos da interface do usuário](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Roteamento de comando em VSPackages](../../extensibility/internals/command-routing-in-vspackages.md)
- [Adicionar itens de menu dinamicamente](../../extensibility/dynamically-adding-menu-items.md)