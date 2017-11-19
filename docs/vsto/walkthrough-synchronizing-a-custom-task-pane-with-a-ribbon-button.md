---
title: "Passo a passo: Sincronizando um painel tarefa personalizada com o botão faixa de opções | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom task panes [Office development in Visual Studio], showing and hiding
- showing custom task panes
- Ribbon [Office development in Visual Studio], custom task panes
- toggle buttons [Office development in Visual Studio]
- custom task panes [Office development in Visual Studio], synchronizing with Ribbon button
- user interfaces [Office development in Visual Studio], custom task panes
- synchronization [Office development in Visual Studio], custom task panes
- task panes [Office development in Visual Studio], showing and hiding
- custom task panes [Office development in Visual Studio], creating
- hiding custom task panes
- task panes [Office development in Visual Studio], creating
- task panes [Office development in Visual Studio], synchronizing with Ribbon button
ms.assetid: 00ce8b1e-1370-42f2-9dc9-609cada392f1
caps.latest.revision: "38"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ea382f4da2e89003f045976e44d186f7c5c8ba31
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button"></a>Instruções passo a passo: sincronizando um painel Tarefa Personalizada com uma botão de faixa de opções
  Este passo a passo demonstra como criar um painel tarefa personalizada que os usuários podem ocultar ou exibir um botão de alternância na faixa de opções. Você sempre deve criar um elemento de interface do usuário do usuário, como um botão, o que os usuários podem clicar para exibir ou ocultar o painel de tarefas, como aplicativos do Microsoft Office não fornecem uma maneira padrão para os usuários mostrar ou ocultar painéis de tarefas personalizados.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
 Embora este passo a passo usa o Excel especificamente, os conceitos demonstrados pelo passo a passo são aplicáveis a todos os aplicativos que estão listados acima.  
  
 Esta explicação passo a passo ilustra as seguintes tarefas:  
  
-   Projetando a interface do usuário do painel de tarefas personalizadas.  
  
-   Adicionar um botão de alternância para a faixa de opções.  
  
-   Sincronizando o botão de alternância com o painel de tarefas.  
  
> [!NOTE]  
>  Seu computador pode mostrar diferentes nomes ou locais para alguns dos elementos de interface do usuário do Visual Studio nas instruções a seguir. A edição do Visual Studio que você possui e as configurações que você usa determinam esses elementos. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Você precisa dos seguintes componentes para concluir esta instrução passo a passo:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   O Microsoft Excel ou Microsoft [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)].  
  
## <a name="creating-the-add-in-project"></a>Criando o projeto de suplemento  
 Nesta etapa, você criará um projeto de suplemento do VSTO para Excel.  
  
#### <a name="to-create-a-new-project"></a>Para criar um novo projeto  
  
1.  Criar um projeto de suplemento do Excel com o nome **SynchronizeTaskPaneAndRibbon**, usando o modelo de projeto de suplemento do Excel. Para obter mais informações, consulte [como: criar projetos do Office no Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Abre o **ThisAddIn.cs** ou **ThisAddIn** arquivo de código e adiciona o **SynchronizeTaskPaneAndRibbon** projeto **Solution Explorer**.  
  
## <a name="adding-a-toggle-button-to-the-ribbon"></a>Adicionar um botão de alternância para a faixa de opções  
 Uma das diretrizes de design de aplicativo do Office é que os usuários sempre devem ter o controle de interface do usuário do aplicativo do Office. Para permitir que os usuários controlem o painel de tarefas, você pode adicionar um botão de alternância de faixa de opções que mostra e oculta o painel de tarefas. Para criar um botão de alternância, adicione um **faixa de opções (Visual Designer)** item ao projeto. O designer ajuda a adicionar e posicionar controles, definir propriedades de controle e tratar eventos de controle. Para obter mais informações, consulte [Designer da faixa de opções](../vsto/ribbon-designer.md).  
  
#### <a name="to-add-a-toggle-button-to-the-ribbon"></a>Para adicionar um botão de alternância para a faixa de opções  
  
1.  No menu **Projeto**, clique em **Adicionar Novo Item**.  
  
2.  No **Adicionar Novo Item** caixa de diálogo, selecione **faixa de opções (Visual Designer)**.  
  
3.  Alterar o nome da nova faixa de opções para **ManageTaskPaneRibbon**e clique em **adicionar**.  
  
     O **ManageTaskPaneRibbon.cs** ou **ManageTaskPaneRibbon.vb** arquivo é aberto no Designer de faixa de opções e exibe um guia padrão e o grupo.  
  
4.  No Designer de faixa de opções, clique em **group1**.  
  
5.  No **propriedades** janela, defina o **rótulo** propriedade **Gerenciador de tarefas do painel**.  
  
6.  Do **controles de faixa de opções do Office** guia do **caixa de ferramentas**, arraste um **ToggleButton** até o **Gerenciador de tarefas do painel** grupo.  
  
7.  Clique em **toggleButton1**.  
  
8.  No **propriedades** janela, defina o **rótulo** propriedade **Mostrar painel de tarefas**.  
  
## <a name="designing-the-user-interface-of-the-custom-task-pane"></a>Criando a Interface do usuário do painel de tarefas personalizados  
 Não há nenhum designer visual para painéis de tarefas personalizados, mas você pode criar um controle de usuário com o layout desejado. Posteriormente neste passo a passo, você irá adicionar o controle de usuário para o painel de tarefas.  
  
#### <a name="to-design-the-user-interface-of-the-custom-task-pane"></a>Para criar a interface do usuário do painel de tarefas personalizados  
  
1.  Sobre o **projeto** menu, clique em **adicionar controle de usuário**.  
  
2.  No **Adicionar Novo Item** caixa de diálogo, altere o nome do controle de usuário para **TaskPaneControl**e clique em **adicionar**.  
  
     O controle de usuário é aberto no designer.  
  
3.  Do **controles comuns** guia do **caixa de ferramentas**, arraste um **TextBox** controle para o controle de usuário.  
  
## <a name="creating-the-custom-task-pane"></a>Criando o painel de tarefas  
 Para criar o painel de tarefas personalizado quando o suplemento do VSTO inicia, adicione o controle de usuário para o painel de tarefas no <xref:Microsoft.Office.Tools.AddIn.Startup> manipulador de eventos do suplemento do VSTO. Por padrão, o painel de tarefas não será visível. Posteriormente neste passo a passo, você irá adicionar código que irá exibir ou ocultar o painel de tarefas quando o usuário clica no botão de alternância que você adicionou à faixa de opções.  
  
#### <a name="to-create-the-custom-task-pane"></a>Para criar o painel de tarefas  
  
1.  Em **Solution Explorer**, expanda **Excel**.  
  
2.  Clique com botão direito **ThisAddIn.cs** ou **ThisAddIn** e clique em **Exibir código**.  
  
3.  Adicione o seguinte código para o `ThisAddIn` classe. Esse código declara uma instância de `TaskPaneControl` como um membro de `ThisAddIn`.  
  
     [!code-csharp[Trin_TaskPaneRibbonSynchronize#1](../vsto/codesnippet/CSharp/Trin_TaskPaneRibbonSynchronize/ThisAddIn.cs#1)]
     [!code-vb[Trin_TaskPaneRibbonSynchronize#1](../vsto/codesnippet/VisualBasic/Trin_TaskPaneRibbonSynchronize/ThisAddIn.vb#1)]  
  
4.  Substitua o `ThisAddIn_Startup` manipulador de eventos com o código a seguir. Esse código adiciona o `TaskPaneControl` do objeto para o `CustomTaskPanes` campo, mas ele não exibe o painel de tarefas (por padrão, o <xref:Microsoft.Office.Tools.CustomTaskPane.Visible%2A> propriedade o <xref:Microsoft.Office.Tools.CustomTaskPane> classe é **false**). O código do Visual c# também anexa um manipulador de eventos para o <xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged> evento.  
  
     [!code-csharp[Trin_TaskPaneRibbonSynchronize#2](../vsto/codesnippet/CSharp/Trin_TaskPaneRibbonSynchronize/ThisAddIn.cs#2)]
     [!code-vb[Trin_TaskPaneRibbonSynchronize#2](../vsto/codesnippet/VisualBasic/Trin_TaskPaneRibbonSynchronize/ThisAddIn.vb#2)]  
  
5.  Adicione o seguinte método à classe `ThisAddIn`. Este método trata o <xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged> evento. Quando o usuário fechar o painel de tarefas clicando o **fechar** botão (X), essas atualizações de método, o estado de alternância botão na faixa de opções.  
  
     [!code-csharp[Trin_TaskPaneRibbonSynchronize#3](../vsto/codesnippet/CSharp/Trin_TaskPaneRibbonSynchronize/ThisAddIn.cs#3)]
     [!code-vb[Trin_TaskPaneRibbonSynchronize#3](../vsto/codesnippet/VisualBasic/Trin_TaskPaneRibbonSynchronize/ThisAddIn.vb#3)]  
  
6.  Adicione a seguinte propriedade para o `ThisAddIn` classe. Essa propriedade expõe particular `myCustomTaskPane1` objeto para outras classes. Posteriormente neste passo a passo, você irá adicionar código para o `MyRibbon` classe que usa essa propriedade.  
  
     [!code-csharp[Trin_TaskPaneRibbonSynchronize#4](../vsto/codesnippet/CSharp/Trin_TaskPaneRibbonSynchronize/ThisAddIn.cs#4)]
     [!code-vb[Trin_TaskPaneRibbonSynchronize#4](../vsto/codesnippet/VisualBasic/Trin_TaskPaneRibbonSynchronize/ThisAddIn.vb#4)]  
  
## <a name="hiding-and-showing-the-custom-task-pane-by-using-the-toggle-button"></a>Ocultando e mostrando o painel de tarefas usando o botão de alternância  
 A última etapa é adicionar o código que exibe ou oculta o painel de tarefas personalizado quando o usuário clica no botão de alternância na faixa de opções.  
  
#### <a name="to-display-and-hide-the-custom-task-pane-by-using-the-toggle-button"></a>Para exibir e ocultar o painel de tarefas usando o botão de alternância  
  
1.  No Designer de faixa de opções, clique duas vezes o **Mostrar painel de tarefas** botão de alternância.  
  
     O Visual Studio gera automaticamente um manipulador de eventos chamado `toggleButton1_Click`, que trata o <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> eventos do botão de alternância. O Visual Studio também abre o **MyRibbon.cs** ou **MyRibbon.vb** arquivo no Editor de códigos.  
  
2.  Substitua o `toggleButton1_Click` manipulador de eventos com o código a seguir. Quando o usuário clica no botão de alternância, este código exibe ou oculta o painel de tarefas, dependendo se o botão de alternância está pressionado ou não pressionado.  
  
     [!code-vb[Trin_TaskPaneRibbonSynchronize#5](../vsto/codesnippet/VisualBasic/Trin_TaskPaneRibbonSynchronize/ManageTaskPaneRibbon.vb#5)]
     [!code-csharp[Trin_TaskPaneRibbonSynchronize#5](../vsto/codesnippet/CSharp/Trin_TaskPaneRibbonSynchronize/ManageTaskPaneRibbon.cs#5)]  
  
## <a name="testing-the-add-in"></a>Testando o suplemento  
 Quando você executar o projeto, o Excel abre sem exibir o painel de tarefas. Clique no botão de alternância na faixa de opções para testar o código.  
  
#### <a name="to-test-your-vsto-add-in"></a>Para testar o suplemento do VSTO  
  
1.  Pressione F5 para executar o projeto.  
  
     Confirme que o Excel é aberto e o **Add-Ins** guia aparece na faixa de opções.  
  
2.  Clique o **Add-Ins** guia na faixa de opções.  
  
3.  No **Gerenciador de tarefas do painel** de grupo, clique no **Mostrar painel de tarefas** botão de alternância.  
  
     Verifique se o painel de tarefas é exibido e ocultado quando você clicar no botão de alternância como alternativa.  
  
4.  Quando o painel de tarefas estiver visível, clique no **fechar** botão (X) no canto do painel de tarefas.  
  
     Verifique se o botão de alternância aparece não seja pressionado.  
  
## <a name="next-steps"></a>Próximas etapas  
 Você pode aprender mais sobre como criar painéis de tarefas personalizados com estes tópicos:  
  
-   Crie um painel tarefa personalizada em um suplemento do VSTO para um aplicativo diferente. Para obter mais informações sobre os aplicativos que oferecem suporte a painéis de tarefas personalizados, consulte [painéis de tarefas personalizados](../vsto/custom-task-panes.md).  
  
-   Automatize um aplicativo de um painel tarefa personalizada. Para obter mais informações, consulte [passo a passo: automatizando um aplicativo a partir de um painel de tarefas personalizado](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md).  
  
-   Crie um painel tarefa personalizada para cada mensagem de email é aberto no Outlook. Para obter mais informações, consulte [passo a passo: exibindo painéis de tarefas personalizada com mensagens de email no Outlook](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md).  
  
## <a name="see-also"></a>Consulte também  
 [Painéis de tarefas personalizados](../vsto/custom-task-panes.md)   
 [Como: adicionar um painel tarefa personalizada a um aplicativo](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)   
 [Passo a passo: Automatizando um aplicativo a partir de um painel de tarefas personalizados](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)   
 [Passo a passo: Exibindo painéis tarefa personalizada com mensagens de email no Outlook](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md)   
 [Visão geral da faixa de opções](../vsto/ribbon-overview.md)  
  
  