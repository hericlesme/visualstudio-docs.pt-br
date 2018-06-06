---
title: 'Passo a passo: Automatizar um aplicativo de um painel tarefa personalizada'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- task panes [Office development in Visual Studio], PowerPoint
- PowerPoint [Office development in Visual Studio], custom task panes
- automating Office applications
- custom task panes [Office development in Visual Studio], automating applications
- custom task panes [Office development in Visual Studio], PowerPoint
- task panes [Office development in Visual Studio], automating applications
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7af399ca55c1fc2355da508662fe67314a519070
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/05/2018
ms.locfileid: "34768073"
---
# <a name="walkthrough-automate-an-application-from-a-custom-task-pane"></a>Passo a passo: Automatizar um aplicativo de um painel tarefa personalizada
  Este passo a passo demonstra como criar um painel tarefa personalizada que automatiza o PowerPoint. O painel de tarefas personalizado insere datas em um slide quando o usuário clica em um <xref:System.Windows.Forms.MonthCalendar> controle que está no painel de tarefas personalizadas.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
 Embora este passo a passo usa PowerPoint especificamente, os conceitos demonstrados pelo passo a passo são aplicáveis a todos os aplicativos que estão listados acima.  
  
 Esta explicação passo a passo ilustra as seguintes tarefas:  
  
-   Projetando a interface do usuário do painel de tarefas personalizadas.  
  
-   Automatizar o PowerPoint do painel de tarefas personalizado.  
  
-   Exibir o painel de tarefas no PowerPoint.  
  
> [!NOTE]  
>  Seu computador pode mostrar diferentes nomes ou locais para alguns dos elementos de interface do usuário do Visual Studio nas instruções a seguir. A edição do Visual Studio que você possui e as configurações que você usa determinam esses elementos. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Você precisa dos seguintes componentes para concluir esta instrução passo a passo:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft PowerPoint 2010 ou [!INCLUDE[PowerPoint_15_short](../vsto/includes/powerpoint-15-short-md.md)].  
  
## <a name="create-the-add-in-project"></a>Criar o projeto de suplemento  
 A primeira etapa é criar um projeto de suplemento do VSTO para PowerPoint.  
  
### <a name="to-create-a-new-project"></a>Para criar um novo projeto  
  
1.  Criar um projeto de suplemento do VSTO PowerPoint com o nome **MyAddIn**, usando o modelo de projeto de suplemento do PowerPoint. Para obter mais informações, consulte [como: projetos do Office criar no Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Abre o **ThisAddIn.cs** ou **ThisAddIn** arquivo de código e adiciona o **MyAddIn** projeto **Gerenciador de soluções**.  
  
## <a name="design-the-user-interface-of-the-custom-task-pane"></a>Design de interface do usuário do painel de tarefas personalizados  
 Não há nenhum designer visual para painéis de tarefas personalizados, mas você pode criar um controle de usuário com o layout desejado. Posteriormente neste passo a passo, você irá adicionar o controle de usuário para o painel de tarefas.  
  
#### <a name="to-design-the-user-interface-of-the-custom-task-pane"></a>Para criar a interface do usuário do painel de tarefas personalizados  
  
1.  Sobre o **projeto** menu, clique em **adicionar controle de usuário**.  
  
2.  No **Adicionar Novo Item** caixa de diálogo, altere o nome do controle de usuário para **MyUserControl**e clique em **adicionar**.  
  
     O controle de usuário é aberto no designer.  
  
3.  Do **controles comuns** guia do **caixa de ferramentas**, arraste um **MonthCalendar** controle para o controle de usuário.  
  
     Se o **MonthCalendar** controle é maior do que a superfície de design do controle de usuário, redimensionar o controle de usuário para ajustar o **MonthCalendar** controle.  
  
## <a name="automate-powerpoint-from-the-custom-task-pane"></a>Automatizar o PowerPoint do painel de tarefas personalizados  
 A finalidade do suplemento do VSTO é colocar uma data selecionada no primeiro slide da apresentação ativa. Use o <xref:System.Windows.Forms.MonthCalendar.DateChanged> eventos do controle para adicionar a data selecionada sempre que ele é alterado.  
  
### <a name="to-automate-powerpoint-from-the-custom-task-pane"></a>Para automatizar o PowerPoint do painel de tarefas personalizados  
  
1.  No designer, clique duas vezes o <xref:System.Windows.Forms.MonthCalendar> controle.  
  
     O **MyUserControl.cs** ou **MyUserControl.vb** arquivo é aberto e um manipulador de eventos para o <xref:System.Windows.Forms.MonthCalendar.DateChanged> evento será criado.  
  
2.  Adicione o seguinte código para a parte superior do arquivo. Esse código cria um alias para o <xref:Microsoft.Office.Core> e <xref:Microsoft.Office.Interop.PowerPoint> namespaces.  
  
     [!code-csharp[Trin_TaskPaneMonthCalendar#1](../vsto/codesnippet/CSharp/Trin_TaskPaneMonthCalendar/MyUserControl.cs#1)]
     [!code-vb[Trin_TaskPaneMonthCalendar#1](../vsto/codesnippet/VisualBasic/Trin_TaskPaneMonthCalendar/MyUserControl.vb#1)]  
  
3.  Adicione o seguinte código para o `MyUserControl` classe. Esse código declara um <xref:Microsoft.Office.Interop.PowerPoint.Shape> objeto como um membro de `MyUserControl`. As etapas a seguir, você usará isso <xref:Microsoft.Office.Interop.PowerPoint.Shape> para adicionar uma caixa de texto a um slide da apresentação ativa.  
  
     [!code-csharp[Trin_TaskPaneMonthCalendar#2](../vsto/codesnippet/CSharp/Trin_TaskPaneMonthCalendar/MyUserControl.cs#2)]
     [!code-vb[Trin_TaskPaneMonthCalendar#2](../vsto/codesnippet/VisualBasic/Trin_TaskPaneMonthCalendar/MyUserControl.vb#2)]  
  
4.  Substitua o `monthCalendar1_DateChanged` manipulador de eventos com o código a seguir. Esse código adiciona uma caixa de texto para o primeiro slide da apresentação ativa e, em seguida, adiciona a data atualmente selecionada à caixa de texto. Esse código usa o `Globals.ThisAddIn` objeto para acessar o modelo de objeto do PowerPoint.  
  
     [!code-csharp[Trin_TaskPaneMonthCalendar#3](../vsto/codesnippet/CSharp/Trin_TaskPaneMonthCalendar/MyUserControl.cs#3)]
     [!code-vb[Trin_TaskPaneMonthCalendar#3](../vsto/codesnippet/VisualBasic/Trin_TaskPaneMonthCalendar/MyUserControl.vb#3)]  
  
5.  Em **Solution Explorer**, com o botão direito do **MyAddIn** do projeto e, em seguida, clique em **criar**. Verifique se o projeto é compilado sem erros.  
  
## <a name="display-the-custom-task-pane"></a>Exibir o painel de tarefas personalizados  
 Para exibir o painel de tarefas personalizado quando o suplemento do VSTO inicia, adicione o controle de usuário para o painel de tarefas no <xref:Microsoft.Office.Tools.AddIn.Startup> manipulador de eventos do suplemento do VSTO.  
  
### <a name="to-display-the-custom-task-pane"></a>Para exibir o painel de tarefas personalizados  
  
1.  Em **Solution Explorer**, expanda **PowerPoint**.  
  
2.  Clique com botão direito **ThisAddIn.cs** ou **ThisAddIn** e clique em **Exibir código**.  
  
3.  Adicione o seguinte código para o `ThisAddIn` classe. Esse código declara instâncias do `MyUserControl` e <xref:Microsoft.Office.Tools.CustomTaskPane> como membros de `ThisAddIn` classe.  
  
     [!code-vb[Trin_TaskPaneMonthCalendar#4](../vsto/codesnippet/VisualBasic/Trin_TaskPaneMonthCalendar/ThisAddIn.vb#4)]
     [!code-csharp[Trin_TaskPaneMonthCalendar#4](../vsto/codesnippet/CSharp/Trin_TaskPaneMonthCalendar/ThisAddIn.cs#4)]  
  
4.  Substitua o `ThisAddIn_Startup` manipulador de eventos com o código a seguir. Esse código cria um novo <xref:Microsoft.Office.Tools.CustomTaskPane> adicionando o `MyUserControl` o objeto para o `CustomTaskPanes` coleção. O código também exibe o painel de tarefas.  
  
     [!code-vb[Trin_TaskPaneMonthCalendar#5](../vsto/codesnippet/VisualBasic/Trin_TaskPaneMonthCalendar/ThisAddIn.vb#5)]
     [!code-csharp[Trin_TaskPaneMonthCalendar#5](../vsto/codesnippet/CSharp/Trin_TaskPaneMonthCalendar/ThisAddIn.cs#5)]  
  
## <a name="test-the-add-in"></a>Testar o suplemento  
 Quando você executar o projeto, o PowerPoint é aberto e o suplemento do VSTO exibe o painel de tarefas. Clique o <xref:System.Windows.Forms.MonthCalendar> controle para testar o código.  
  
### <a name="to-test-your-vsto-add-in"></a>Para testar o suplemento do VSTO  
  
1.  Pressione **F5** para executar o projeto.  
  
2.  Confirme se o painel de tarefas é visível.  
  
3.  Clique em uma data de <xref:System.Windows.Forms.MonthCalendar> controle no painel de tarefas.  
  
     A data é inserida no primeiro slide da apresentação ativa.  
  
## <a name="next-steps"></a>Próximas etapas  
 Você pode aprender mais sobre como criar painéis de tarefas personalizados com estes tópicos:  
  
-   Crie um painel tarefa personalizada em um suplemento do VSTO para um aplicativo diferente. Para obter mais informações sobre os aplicativos que oferecem suporte a painéis de tarefas personalizados, consulte [painéis de tarefas personalizados](../vsto/custom-task-panes.md).  
  
-   Crie um botão de faixa de opções que pode ser usado para ocultar ou exibir um painel tarefa personalizada. Para obter mais informações, consulte [passo a passo: sincronizar um painel tarefa personalizada com o botão faixa de opções](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md).  
  
-   Crie um painel tarefa personalizada para cada mensagem de email é aberto no Outlook. Para obter mais informações, consulte [passo a passo: exibir painéis de tarefas personalizada com mensagens de email no Outlook](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md).  
  
## <a name="see-also"></a>Consulte também  
 [Painéis de tarefas personalizados](../vsto/custom-task-panes.md)   
 [Como: adicionar um painel tarefa personalizada a um aplicativo](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)   
 [Passo a passo: Sincronizar um painel tarefa personalizada com o botão faixa de opções](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md)   
 [Passo a passo: Exibir painéis de tarefas personalizada com mensagens de email no Outlook](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md)  
  
  