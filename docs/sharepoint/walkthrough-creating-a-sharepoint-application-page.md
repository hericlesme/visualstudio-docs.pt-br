---
title: 'Passo a passo: Criando uma página de aplicativo do SharePoint | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- application pages [SharePoint development in Visual Studio], developing
- application pages [SharePoint development in Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 21191ec585b83099aefad4f1c43949ba94cfc4ec
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-creating-a-sharepoint-application-page"></a>Instruções passo a passo: criando uma página de aplicativo do SharePoint
 
Uma página de aplicativo é uma forma especializada de uma página ASP.NET. Páginas de aplicativos têm conteúdo que é mesclado com uma página mestre do SharePoint. Para obter mais informações, consulte [criando páginas de aplicativo para o SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).

Este passo a passo mostra como criar uma página de aplicativo e depurá-lo usando um site do SharePoint local. Esta página mostra todos os itens que cada usuário tenha criado ou modificado em todos os sites no farm de servidores.

Esta explicação passo a passo ilustra as seguintes tarefas:

- Criando um projeto do SharePoint.
- Adicionando uma página de aplicativo para o projeto do SharePoint.
- Adicionando controles do ASP.NET para a página de aplicativo.
- Adicionando código por trás dos controles do ASP.NET.
- Testando a página de aplicativo.

> [!NOTE]
> Seu computador pode mostrar diferentes nomes ou locais para alguns dos elementos de interface do usuário do Visual Studio nas instruções a seguir. A edição do Visual Studio que você possui e as configurações que você usa determinam esses elementos. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Pré-requisitos

- Edições com suporte do Windows e do SharePoint. Para obter mais informações, consulte [requisitos para desenvolver soluções do SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).

## <a name="creating-a-sharepoint-project"></a>Criando um Projeto do SharePoint

Primeiro, crie um **projeto vazio do SharePoint**. Posteriormente, você adicionará um **página de aplicativo** item a este projeto.

1. Inicie o [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Abra o **novo projeto** caixa de diálogo caixa, expanda o **Office/SharePoint** nó no idioma que você deseja usar e, em seguida, escolha o **soluções do SharePoint** nó.

3. No **modelos do Visual Studio instalado** painel, escolha o **SharePoint 2010 - projeto vazio** modelo. Nomeie o projeto **MySharePointProject**e, em seguida, escolha o **Okey** botão.

     O **Assistente de personalização do SharePoint** é exibida. Este assistente permite que você selecione o site que você usará para depurar o projeto e o nível de confiança da solução.

4. Escolha o **implantar como uma solução de farm** botão de opção e, em seguida, escolha o **concluir** botão para aceitar o site padrão local do SharePoint.

## <a name="creating-an-application-page"></a>Criando uma Página de Aplicativo

Para criar uma página de aplicativo, adicione um **página de aplicativo** item ao projeto.

1. Em **Solution Explorer**, escolha o **MySharePointProject** projeto.

2. Na barra de menus, escolha **projeto**, **Adicionar Novo Item**.

3. No **Adicionar Novo Item** caixa de diálogo caixa, escolha o **página de aplicativos (somente solução de Farm** modelo.

4. Nomeie a página **SearchItems**e, em seguida, escolha o **adicionar** botão.

     O designer Visual Web Developer exibe a página de aplicativo em **fonte** modo em que você pode ver os elementos da página HTML. O designer exibe a marcação de vários <xref:System.Web.UI.WebControls.Content> controles. Cada controle é mapeado para um <xref:System.Web.UI.WebControls.ContentPlaceHolder> controle que é definido na página principal do aplicativo padrão.

## <a name="designing-the-layout-of-the-application-page"></a>Projetando o Layout da Página do Aplicativo

O item de página de aplicativo permite que você use um designer para adicionar os controles do ASP.NET para a página de aplicativo. Esse designer é o mesmo designer usado no Visual Web Developer. Adicionar um rótulo, uma lista de botões de opção e uma tabela para o **fonte** exibir do designer e, em seguida, definir propriedades, como faria ao criar qualquer página do ASP.NET padrão.

1. Na barra de menus, escolha **Exibir**, **Caixa de Ferramentas**.

2. No nó de padrão de **caixa de ferramentas**, execute uma das seguintes etapas:

    - Abra o menu de atalho para o **rótulo** item, escolha **cópia**, abra o menu de atalho para a linha abaixo o **PlaceHolderMain** conteúdo controle no designer e, em seguida, Escolha **colar**.

    - Arraste o **rótulo** item do **caixa de ferramentas** no corpo do **PlaceHolderMain** controle de conteúdo.

3. Repita a etapa anterior para adicionar um **DropDownList** item e um **tabela** item para o **PlaceHolderMain** controle de conteúdo.

4. No designer, altere o valor da `Text` atributo do controle de rótulo para **Mostrar todos os itens**.

5. No designer, substitua o `<asp:DropDownList>` elemento com o XML a seguir.

    ```xml
    <asp:DropDownList ID="DropDownList1" runat="server" AutoPostBack="true"
     OnSelectedIndexChanged="DropDownList1_SelectedIndexChanged">
        <asp:ListItem Text="Created by me" Value="Author"></asp:ListItem>
        <asp:ListItem Text="Modified by me" Value="Editor"></asp:ListItem>
    </asp:DropDownList>
    ```

## <a name="handling-the-events-of-controls-on-the-page"></a>Tratando os Eventos de Controles na Página

Lidar com controles em uma página de aplicativo como faria com qualquer página ASP.NET. Neste procedimento, você irá manipular o `SelectedIndexChanged` eventos da lista suspensa.

1. Sobre o **exibição** menu, escolha **código**.

     O arquivo de código da página de aplicativo é aberto no Editor de códigos.

2. Adicione o seguinte método à classe `SearchItems`. Esse código manipula a <xref:System.Web.UI.WebControls.ListControl.SelectedIndexChanged> eventos do <xref:System.Web.UI.WebControls.DropDownList> chamando um método que você criar posteriormente neste passo a passo.

     [!code-vb[SP_ApplicationPage#5](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#5)]
     [!code-csharp[SP_ApplicationPage#5](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#5)]

3. Adicione as seguintes instruções para a parte superior do arquivo de código de página do aplicativo.

     [!code-vb[SP_ApplicationPage#1](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#1)]
     [!code-csharp[SP_ApplicationPage#1](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#1)]

4. Adicione o seguinte método à classe `SearchItems`. Esse método itera em todos os sites no farm de servidores e procura por itens criados ou modificados pelo usuário atual.

     [!code-vb[SP_ApplicationPage#2](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#2)]
     [!code-csharp[SP_ApplicationPage#2](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#2)]

5. Adicione o seguinte método à classe `SearchItems`. Esse método exibe os itens criados ou modificados pelo usuário atual na tabela.

     [!code-vb[SP_ApplicationPage#3](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#3)]
     [!code-csharp[SP_ApplicationPage#3](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#3)]

## <a name="testing-the-application-page"></a>Testando a Página do Aplicativo

Quando você executar o projeto, abre o site do SharePoint e a página de aplicativo é exibida.

1. Em **Solution Explorer**, abra o menu de atalho para a página de aplicativo e, em seguida, escolha **definir como Item de inicialização**.

2. Pressione a tecla F5.

     Abre o site do SharePoint.

3. Na página do aplicativo, escolha o **modificado por mim** opção.

     A página de aplicativo atualiza e exibe todos os itens que você tenha modificado em todos os sites no farm de servidores.

4. Na página do aplicativo, escolha **criadas por mim** na lista.

     A página de aplicativo atualiza e exibe todos os itens que você criou em todos os sites no farm de servidores.

## <a name="next-ateps"></a>Próxima ateps

Para obter mais informações sobre páginas de aplicativo do SharePoint, consulte [criando páginas de aplicativo para o SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).

Você pode aprender mais sobre como criar conteúdo de página do SharePoint usando o Designer Visual estes tópicos:

- [Criando Web Parts do SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md).

- [Criando controles reutilizáveis para Web Parts ou páginas de aplicativo](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md).

## <a name="see-also"></a>Consulte também

[Como criar uma página de aplicativo](../sharepoint/how-to-create-an-application-page.md)  
[Tipo de página de layouts de aplicativo](http://go.microsoft.com/fwlink/?LinkID=169274)
