---
title: "Passo a passo: Associando dados a controles em um painel de ações do Excel | Microsoft Docs"
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
- controls [Office development in Visual Studio], data binding
- actions panes [Office development in Visual Studio], data binding
- data binding [Office development in Visual Studio], smart documents
- data binding [Office development in Visual Studio], actions panes
- actions panes [Office development in Visual Studio], binding controls
- smart documents [Office development in Visual Studio], data binding
ms.assetid: 106c07bd-e931-4dc5-94dc-ca43900fe09d
caps.latest.revision: "63"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 11a9f55691416a1b7775e0ff9d392293d9fee33f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-binding-data-to-controls-on-an-excel-actions-pane"></a>Instruções passo a passo: associando dados a controles em um painel de ações do Excel
  Este passo a passo demonstra a associação de dados a controles em um painel de ações no Microsoft Office Excel. Os controles demonstram uma relação mestre/detalhes entre tabelas em um banco de dados do SQL Server.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Esta explicação passo a passo ilustra as seguintes tarefas:  
  
-   Adicionando controles a uma planilha.  
  
-   Criando um controle do painel Ações.  
  
-   Adicionando controles de formulários do Windows de dados associados a um controle de painel de ações.  
  
-   Mostrando o painel de ações quando o aplicativo é aberto.  
  
> [!NOTE]  
>  Seu computador pode mostrar diferentes nomes ou locais para alguns dos elementos de interface do usuário do Visual Studio nas instruções a seguir. A edição do Visual Studio que você possui e as configurações que você usa determinam esses elementos. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Você precisa dos seguintes componentes para concluir esta instrução passo a passo:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] ou [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
-   Acesso a um servidor com o banco de dados de exemplo Northwind SQL Server.  
  
-   Permissões de leitura e gravação no banco de dados do SQL Server.  
  
## <a name="creating-the-project"></a>Criando o Projeto  
 A primeira etapa é criar um projeto de pasta de trabalho do Excel.  
  
#### <a name="to-create-a-new-project"></a>Para criar um novo projeto  
  
1.  Criar um projeto de pasta de trabalho do Excel com o nome **meu painel de ações do Excel**. No assistente, selecione **criar um novo documento**. Para obter mais informações, consulte [como: criar projetos do Office no Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio abre a nova pasta de trabalho do Excel no designer e adiciona o **meu painel de ações do Excel** projeto **Gerenciador de soluções**.  
  
## <a name="adding-a-new-data-source-to-the-project"></a>Adicionando uma nova fonte de dados ao projeto  
  
#### <a name="to-add-a-new-data-source-to-the-project"></a>Para adicionar uma nova fonte de dados ao projeto  
  
1.  Se o **fontes de dados** janela não estiver visível, exibir, na barra de menus, escolhendo **exibição**, **outras janelas**, **fontes de dados**.  
  
2.  Escolha **adicionar nova fonte de dados** para iniciar o **Assistente de configuração de fonte de dados**.  
  
3.  Selecione **banco de dados** e, em seguida, clique em **próximo**.  
  
4.  Selecione uma conexão de dados para o banco de dados do SQL Server de exemplo Northwind, ou adicionar uma nova conexão usando o **nova Conexão** botão.  
  
5.  Clique em **Avançar**.  
  
6.  Desmarque a opção para salvar a conexão se estiver selecionada e clique **próximo**.  
  
7.  Expanda o **tabelas** nó o **objetos de banco de dados** janela.  
  
8.  Marque a caixa de seleção ao lado de **fornecedores** tabela.  
  
9. Expanda o **produtos** de tabela e selecione **ProductName**, **SupplierID**, **QuantityPerUnit**, e **UnitPrice**.  
  
10. Clique em **Finalizar**.  
  
 O assistente adiciona o **fornecedores** tabela e **produtos** de tabela para o **fontes de dados** janela. Ele também adiciona um conjunto de dados tipado ao seu projeto que está visível no **Gerenciador de soluções**.  
  
## <a name="adding-controls-to-the-worksheet"></a>Adicionando controles a planilha  
 Em seguida, adicione um <xref:Microsoft.Office.Tools.Excel.NamedRange> controle e um <xref:Microsoft.Office.Tools.Excel.ListObject> controle para a primeira planilha.  
  
#### <a name="to-add-a-namedrange-control-and-a-listobject-control"></a>Para adicionar um controle NamedRange e um controle ListObject  
  
1.  Verifique o **Meus Pane.xlsx de ações do Excel** pasta de trabalho é aberta no designer do Visual Studio, com `Sheet1` exibida.  
  
2.  No **fontes de dados** janela, expanda o **fornecedores** tabela.  
  
3.  Clique na seta suspensa no **nome da empresa** nó e, em seguida, clique **NamedRange**.  
  
4.  Arraste **nome da empresa** do **fontes de dados** janela à célula **A2** em `Sheet1`.  
  
     Um <xref:Microsoft.Office.Tools.Excel.NamedRange> controle chamado `CompanyNameNamedRange` é criado e o texto \<CompanyName > aparece na célula **A2**. Ao mesmo tempo, uma <xref:System.Windows.Forms.BindingSource> chamado `suppliersBindingSource`, um adaptador de tabela e um <xref:System.Data.DataSet> são adicionados ao projeto. O controle está vinculado a <xref:System.Windows.Forms.BindingSource>, que por sua vez é associado a <xref:System.Data.DataSet> instância.  
  
5.  No **fontes de dados** janela, role para baixo, após as colunas que estão sob o **fornecedores** tabela. Na parte inferior da lista é o **produtos** tabela; aqui é porque ele é um filho do **fornecedores** tabela. Selecione esta opção **produtos** tabela, não uma que seja do mesmo nível como o **fornecedores** de tabela e, em seguida, clique na seta suspensa exibida.  
  
6.  Clique em **ListObject** na lista suspensa e, em seguida, arraste o **produtos** tabela para a célula **A6** em `Sheet1`.  
  
     Um <xref:Microsoft.Office.Tools.Excel.ListObject> controle chamado `ProductNameListObject` é criado na célula **A6**. Ao mesmo tempo, uma <xref:System.Windows.Forms.BindingSource> denominado `productsBindingSource` e um adaptador de tabela são adicionados ao projeto. O controle está vinculado a <xref:System.Windows.Forms.BindingSource>, que por sua vez é associado a <xref:System.Data.DataSet> instância.  
  
7.  C# somente, selecione **suppliersBindingSource** na bandeja do componente e altere o **modificadores** propriedade **interno** no **propriedades** janela.  
  
## <a name="adding-controls-to-the-actions-pane"></a>Adicionando controles para o painel de ações  
 Em seguida, você precisa de um controle de painel de ações que contém uma caixa de combinação.  
  
#### <a name="to-add-an-actions-pane-control"></a>Para adicionar um controle de painel de ações  
  
1.  Selecione o **meu painel de ações do Excel** project no **Gerenciador de soluções**.  
  
2.  No menu **Projeto**, clique em **Adicionar Novo Item**.  
  
3.  No **Adicionar Novo Item** caixa de diálogo, selecione **controle do painel Ações**, nomeie-o **ActionsControl**e clique em **adicionar**.  
  
#### <a name="to-add-data-bound-windows-forms-controls-to-an-actions-pane-control"></a>Para adicionar controles de formulários do Windows de dados associados a um controle de painel de ações  
  
1.  Do **controles comuns** guias do **caixa de ferramentas**, arraste um <xref:System.Windows.Forms.ComboBox> controle para o controle de painel de ações.  
  
2.  Alterar o **tamanho** propriedade **171, 21**.  
  
3.  Redimensione o controle de usuário para se ajustar a caixa de combinação.  
  
## <a name="binding-the-control-on-the-actions-pane-to-data"></a>Vinculando o controle no painel Ações para dados  
 Nesta seção, você definirá a fonte de dados do <xref:System.Windows.Forms.ComboBox> à mesma fonte de dados como o <xref:Microsoft.Office.Tools.Excel.NamedRange> controle na planilha.  
  
#### <a name="to-set-data-binding-properties-of-the-control"></a>Para definir as propriedades de associação de dados do controle  
  
1.  Clique com botão direito do controle do painel Ações e, em seguida, clique em **Exibir código**.  
  
2.  Adicione o seguinte código para o <xref:System.Windows.Forms.UserControl.Load> eventos do controle de painel de ações.  
  
     [!code-vb[Trin_VstcoreActionsPaneExcel#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ActionsControl.vb#1)]
     [!code-csharp[Trin_VstcoreActionsPaneExcel#1](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ActionsControl.cs#1)]  
  
3.  Em c#, você deve criar um manipulador de eventos para o `ActionsControl`. Você pode colocar esse código no `ActionsControl` construtor. Para obter mais informações sobre como criar manipuladores de eventos, consulte [como: criar manipuladores de eventos em projetos do Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreActionsPaneExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ActionsControl.cs#2)]  
  
## <a name="showing-the-actions-pane"></a>Mostrando o painel de ações  
 O painel de ações não estiver visível até que você adicione o controle em tempo de execução.  
  
#### <a name="to-show-the-actions-pane"></a>Para mostrar o painel de ações  
  
1.  Em **Solution Explorer**, clique com botão direito ThisWorkbook ou ThisWorkbook.cs e, em seguida, clique em **Exibir código**.  
  
2.  Criar uma nova instância do controle de usuário no `ThisWorkbook` classe.  
  
     [!code-csharp[Trin_VstcoreActionsPaneExcel#3](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#3)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#3)]  
  
3.  No <xref:Microsoft.Office.Tools.Excel.Workbook.Startup> manipulador de eventos do `ThisWorkbook`, adicione o controle para o painel de ações.  
  
     [!code-csharp[Trin_VstcoreActionsPaneExcel#4](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#4)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#4)]  
  
## <a name="testing-the-application"></a>Testando o aplicativo  
 Agora você pode testar o documento para verificar se o painel de ações é aberto quando o documento for aberto, e que os controles tenham uma relação mestre/detalhes.  
  
#### <a name="to-test-your-document"></a>Para testar o documento  
  
1.  Pressione F5 para executar o projeto.  
  
2.  Confirme se o painel de ações está visível.  
  
3.  Selecione uma empresa na caixa de listagem. Verifique se o nome da empresa é listado no <xref:Microsoft.Office.Tools.Excel.NamedRange> controle e que os detalhes do produto são listados no <xref:Microsoft.Office.Tools.Excel.ListObject> controle.  
  
4.  Selecione várias empresas para verificar o nome da empresa e detalhes do produto alterar conforme apropriado.  
  
## <a name="next-steps"></a>Próximas etapas  
 Estas são algumas tarefas que podem vir a seguir:  
  
-   Associando dados a controles no Word. Para obter mais informações, consulte [passo a passo: vinculação de dados a controles em um painel de ações do Word](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md).  
  
-   Implantar o projeto. Para obter mais informações, consulte [implantar uma solução Office pelo ClickOnce usando](../vsto/deploying-an-office-solution-by-using-clickonce.md).  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral do painel de ações](../vsto/actions-pane-overview.md)   
 [Como: gerenciar o controle Layout em painéis de ações](../vsto/how-to-manage-control-layout-on-actions-panes.md)   
 [Associando dados a controles em soluções do Office](../vsto/binding-data-to-controls-in-office-solutions.md)  
  
  