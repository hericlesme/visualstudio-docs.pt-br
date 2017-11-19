---
title: 'Como: adicionar um painel tarefa personalizada a um aplicativo | Microsoft Docs'
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
- task panes [Office development in Visual Studio], adding to application
- custom task panes [Office development in Visual Studio], adding to application
ms.assetid: 67b4ed5b-d77e-4630-b851-34bb25bdc9b3
caps.latest.revision: "28"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1a39267da04be68793a2236250e5ed10efb01afd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-add-a-custom-task-pane-to-an-application"></a>Como adicionar um painel de tarefas personalizado a um aplicativo
  Você pode adicionar um painel tarefa personalizada para os aplicativos listados acima usando o suplemento do VSTO. Para obter mais informações, consulte [painéis de tarefas personalizados](../vsto/custom-task-panes.md).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
> [!NOTE]  
>  Seu computador pode mostrar diferentes nomes ou locais para alguns dos elementos de interface do usuário do Visual Studio nas instruções a seguir. A edição do Visual Studio que você possui e as configurações que você usa determinam esses elementos. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="adding-a-custom-task-pane-to-an-application"></a>Adicionando um painel tarefa personalizada a um aplicativo  
  
#### <a name="to-add-a-custom-task-pane-to-an-application"></a>Para adicionar um painel tarefa personalizada a um aplicativo  
  
1.  Abra ou crie um projeto de suplemento do VSTO para um dos aplicativos listados acima. Para obter mais informações, consulte [como: criar projetos do Office no Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  Sobre o **projeto** menu, clique em **adicionar controle de usuário**.  
  
3.  No **Adicionar Novo Item** caixa de diálogo, altere o nome do novo controle de usuário para **MyUserControl**e, em seguida, clique em **adicionar**.  
  
     O controle de usuário é aberto no designer.  
  
4.  Adicionar um ou mais controles de formulários do Windows do **caixa de ferramentas** para o controle de usuário.  
  
5.  Abra o **ThisAddIn.cs** ou **ThisAddIn** arquivo de código.  
  
6.  Adicione o seguinte código para o `ThisAddIn` classe. Esse código declara instâncias do `MyUserControl` e <xref:Microsoft.Office.Tools.CustomTaskPane> como membros de `ThisAddIn` classe.  
  
     [!code-vb[Trin_TaskPaneBasic#1](../vsto/codesnippet/VisualBasic/Trin_TaskPaneBasic/ThisAddIn.vb#1)]
     [!code-csharp[Trin_TaskPaneBasic#1](../vsto/codesnippet/CSharp/Trin_TaskPaneBasic/ThisAddIn.cs#1)]  
  
7.  Adicione o seguinte código ao manipulador de eventos do `ThisAddIn_Startup`. Esse código cria um novo <xref:Microsoft.Office.Tools.CustomTaskPane> adicionando o `MyUserControl` o objeto para o `CustomTaskPanes` coleção. O código também exibe o painel de tarefas.  
  
     [!code-vb[Trin_TaskPaneBasic#2](../vsto/codesnippet/VisualBasic/Trin_TaskPaneBasic/ThisAddIn.vb#2)]
     [!code-csharp[Trin_TaskPaneBasic#2](../vsto/codesnippet/CSharp/Trin_TaskPaneBasic/ThisAddIn.cs#2)]  
  
    > [!NOTE]  
    >  Esse código associa o painel de tarefas com a janela ativa no aplicativo. Para alguns aplicativos, você talvez queira modificar este código para garantir que o painel de tarefas é exibida com outros documentos ou itens no aplicativo. Para obter mais informações, consulte [painéis de tarefas personalizados](../vsto/custom-task-panes.md).  
  
## <a name="see-also"></a>Consulte também  
 [Personalização da interface do usuário do Office](../vsto/office-ui-customization.md)   
 [Painéis de tarefas personalizados](../vsto/custom-task-panes.md)   
 [Instruções passo a passo: automatizando um aplicativo de um painel de tarefas personalizado](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)  
  
  