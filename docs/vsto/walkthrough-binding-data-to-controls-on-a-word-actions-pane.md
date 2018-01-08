---
title: "Passo a passo: Associando dados a controles em um painel de ações do Word | Microsoft Docs"
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
ms.assetid: 5ef72fc7-412b-4454-9890-4479a13ee7f9
caps.latest.revision: "64"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: be9a2b19a8c9c34390a359fd8e3350d6af654fde
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-binding-data-to-controls-on-a-word-actions-pane"></a>Instruções passo a passo: associando dados a controles em um painel de ações do Word
  Este passo a passo demonstra a associação de dados a controles em um painel de ações no Word. Os controles demonstram uma relação mestre/detalhes entre tabelas em um banco de dados do SQL Server.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Esta explicação passo a passo ilustra as seguintes tarefas:  
  
-   Criando um painel de ações com controles de formulários do Windows que estão associados a dados.  
  
-   Usando uma relação mestre/detalhes para exibir dados em controles.  
  
-   Mostre o painel de ações quando o aplicativo é aberto.  
  
> [!NOTE]  
>  Seu computador pode mostrar diferentes nomes ou locais para alguns dos elementos de interface do usuário do Visual Studio nas instruções a seguir. A edição do Visual Studio que você possui e as configurações que você usa determinam esses elementos. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Você precisa dos seguintes componentes para concluir esta instrução passo a passo:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] ou [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].  
  
-   Acesso a um servidor com o banco de dados de exemplo Northwind SQL Server.  
  
-   Permissões de leitura e gravação no banco de dados do SQL Server.  
  
## <a name="creating-the-project"></a>Criando o Projeto  
 A primeira etapa é criar um projeto de Documento do Word.  
  
#### <a name="to-create-a-new-project"></a>Para criar um novo projeto  
  
1.  Criar um projeto de documento do Word com o nome **meu painel de ações do Word**. No assistente, selecione **criar um novo documento**.  
  
     Para obter mais informações, consulte [como: criar projetos do Office no Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio abre o novo documento do Word no designer e adiciona o **meu painel de ações do Word** projeto **Gerenciador de soluções**.  
  
## <a name="adding-controls-to-the-actions-pane"></a>Adicionando controles para o painel de ações  
 Para este passo a passo, você precisa de um controle de painel de ações que contém os controles de formulários do Windows associados a dados. Adicionar uma fonte de dados para o projeto e, em seguida, arraste os controles do **fontes de dados** janela para o controle do painel Ações.  
  
#### <a name="to-add-an-actions-pane-control"></a>Para adicionar um controle de painel de ações  
  
1.  Selecione o **meu painel de ações do Word** project no **Gerenciador de soluções**.  
  
2.  No menu **Projeto**, clique em **Adicionar Novo Item**.  
  
3.  No **Adicionar Novo Item** caixa de diálogo, selecione **controle do painel Ações**, nomeie-o **ActionsControl**e, em seguida, clique em **adicionar**.  
  
#### <a name="to-add-a-data-source-to-the-project"></a>Para adicionar uma fonte de dados ao projeto  
  
1.  Se o **fontes de dados** janela não estiver visível, exibir, na barra de menus, escolhendo **exibição**, **outras janelas**, **fontes de dados**.  
  
    > [!NOTE]  
    >  Se **Mostrar fontes de dados** não estiver disponível, clique no documento do Word e, em seguida, verifique novamente.  
  
2.  Clique em **adicionar nova fonte de dados** para iniciar o **Assistente de configuração de fonte de dados**.  
  
3.  Selecione **banco de dados** e, em seguida, clique em **próximo**.  
  
4.  Selecione uma conexão de dados para o banco de dados do SQL Server de exemplo Northwind, ou adicionar uma nova conexão usando o **nova Conexão** botão.  
  
5.  Clique em **Avançar**.  
  
6.  Desmarque a opção para salvar a conexão se estiver selecionada e clique **próximo**.  
  
7.  Expanda o **tabelas** nó o **objetos de banco de dados** janela.  
  
8.  Marque a caixa de seleção ao lado de **fornecedores** e **produtos** tabelas.  
  
9. Clique em **Finalizar**.  
  
 O assistente adiciona o **fornecedores** tabela e **produtos** de tabela para o **fontes de dados** janela. Ele também adiciona um conjunto de dados tipado ao seu projeto que está visível no **Gerenciador de soluções**.  
  
#### <a name="to-add-data-bound-windows-forms-controls-to-an-actions-pane-control"></a>Para adicionar controles de formulários do Windows de dados associados a um controle de painel de ações  
  
1.  No **fontes de dados** janela, expanda o **fornecedores** tabela.  
  
2.  Clique na seta suspensa no **nome da empresa** nó e selecione **ComboBox**.  
  
3.  Arraste **CompanyName** do **fontes de dados** janela para o controle do painel Ações.  
  
     Um <xref:System.Windows.Forms.ComboBox> controle é criado no controle do painel Ações. Ao mesmo tempo, uma <xref:System.Windows.Forms.BindingSource> chamado `SuppliersBindingSource`, um adaptador de tabela e um <xref:System.Data.DataSet> são adicionados ao projeto na bandeja do componente.  
  
4.  Selecione `SuppliersBindingNavigator` no **componente** bandeja e pressione DELETE. Você não usará o `SuppliersBindingNavigator` neste passo a passo.  
  
    > [!NOTE]  
    >  Excluindo o `SuppliersBindingNavigator` não remove todo o código que foi gerado para ele. Você pode remover esse código.  
  
5.  Mover a caixa de combinação para que ele esteja sob o rótulo e altere o **tamanho** propriedade **171, 21**.  
  
6.  No **fontes de dados** janela, expanda o **produtos** tabela que é um filho do **fornecedores** tabela.  
  
7.  Clique na seta suspensa no **ProductName** nó e selecione **ListBox**.  
  
8.  Arraste **ProductName** para o controle do painel Ações.  
  
     Um <xref:System.Windows.Forms.ListBox> controle é criado no controle do painel Ações. Ao mesmo tempo, uma <xref:System.Windows.Forms.BindingSource> denominado `ProductBindingSource` e um adaptador de tabela são adicionados ao projeto na bandeja do componente.  
  
9. Mover a caixa de listagem para que ele esteja sob o rótulo e altere o **tamanho** propriedade **171,95**.  
  
10. Arraste um <xref:System.Windows.Forms.Button> do **caixa de ferramentas** para o painel de ações controlar e coloque-o abaixo da caixa de listagem.  
  
11. Clique com botão direito do <xref:System.Windows.Forms.Button>, clique em **propriedades** no menu de atalho e altere as propriedades a seguir.  
  
    |Propriedade|Valor|  
    |--------------|-----------|  
    |**Nome**|**Inserir**|  
    |**Texto**|**Inserir**|  
  
12. Redimensione o controle de usuário para ajustar os controles.  
  
## <a name="setting-up-the-data-source"></a>Configurando a fonte de dados  
 Para configurar a fonte de dados, adicione código para o <xref:System.Windows.Forms.UserControl.Load> eventos do controle de painel Ações para preencher o controle com dados do <xref:System.Data.DataTable>e defina o <xref:System.Windows.Forms.Binding.DataSource%2A> e <xref:System.Windows.Forms.BindingSource.DataMember%2A> propriedades para cada controle.  
  
#### <a name="to-load-the-control-with-data"></a>Para carregar o controle com dados  
  
1.  No <xref:System.Windows.Forms.UserControl.Load> manipulador de eventos do `ActionsControl` de classe, adicione o código a seguir.  
  
     [!code-vb[Trin_VstcoreActionsPaneWord#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#1)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#1](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#1)]  
  
2.  Em c#, você deve anexar o manipulador de eventos para o <xref:System.Windows.Forms.UserControl.Load> evento. Você pode colocar esse código no `ActionsControl` construtor, após a chamada a `InitializeComponent`. Para obter mais informações sobre como criar manipuladores de eventos, consulte [como: criar manipuladores de eventos em projetos do Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#33](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#33)]  
  
#### <a name="to-set-data-binding-properties-of-the-controls"></a>Para definir as propriedades de associação de dados dos controles  
  
1.  Selecione o `CompanyNameComboBox` controle.  
  
2.  No **propriedades** janela, clique no botão à direita do **DataSource** propriedade e selecione **suppliersBindingSource**.  
  
3.  Clique no botão à direita do **DisplayMember** propriedade e selecione **CompanyName**.  
  
4.  Expanda o **DataBindings** propriedade, clique no botão à direita do **texto** propriedade e selecione **nenhum**.  
  
5.  Selecione o `ProductNameListBox` controle.  
  
6.  No **propriedades** janela, clique no botão à direita do **DataSource** propriedade e selecione **productsBindingSource**.  
  
7.  Clique no botão à direita do **DisplayMember** propriedade e selecione **ProductName**.  
  
8.  Expanda o **DataBindings** propriedade, clique no botão à direita do **SelectedValue** propriedade e selecione **nenhum**.  
  
## <a name="adding-a-method-to-insert-data-into-a-table"></a>Adicionando um método para inserir dados em uma tabela  
 A próxima tarefa é ler os dados os controles associados e popular uma tabela no documento do Word. Primeiro, crie um procedimento para formatar os cabeçalhos da tabela e, em seguida, adicione o `AddData` método para criar e formatar uma tabela do Word.  
  
#### <a name="to-format-the-table-headings"></a>Para formatar os títulos de tabela  
  
1.  No `ActionsControl` classe, crie um método para formatar os títulos da tabela.  
  
     [!code-vb[Trin_VstcoreActionsPaneWord#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#2)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#2](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#2)]  
  
#### <a name="to-create-the-table"></a>Para criar a tabela  
  
1.  No `ActionsControl` da classe, escrever um método que cria uma tabela se um existe e adicionar dados no painel Ações para a tabela.  
  
     [!code-vb[Trin_VstcoreActionsPaneWord#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#3)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#3](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#3)]  
  
#### <a name="to-insert-text-into-a-word-table"></a>Para inserir texto em uma tabela do Word  
  
1.  Adicione o seguinte código para o <xref:System.Windows.Forms.Control.Click> manipulador de eventos do **inserir** botão.  
  
     [!code-vb[Trin_VstcoreActionsPaneWord#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#4)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#4](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#4)]  
  
2.  Em c#, você deve criar um manipulador de eventos para o <xref:System.Windows.Forms.Control.Click> eventos do botão.  Você pode colocar esse código no <xref:System.Windows.Forms.UserControl.Load> manipulador de eventos do `ActionsControl` classe.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#5](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#5)]  
  
## <a name="showing-the-actions-pane"></a>Mostrando o painel de ações  
 O painel de ações ficará visível após controles sejam adicionados a ela.  
  
#### <a name="to-show-the-actions-pane"></a>Para mostrar o painel de ações  
  
1.  Em **Solution Explorer**, clique com botão direito **ThisDocument. vb** ou **ThisDocument.cs**e, em seguida, clique em **Exibir código** no menu de atalho.  
  
2.  Criar uma nova instância do controle na parte superior do `ThisDocument` classe para que ele se parece com o exemplo a seguir.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#6](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#6)]
     [!code-vb[Trin_VstcoreActionsPaneWord#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#6)]  
  
3.  Adicione código para o <xref:Microsoft.Office.Tools.Word.Document.Startup> manipulador de eventos do `ThisDocument` para que ele se parece com o exemplo a seguir.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#7](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#7)]
     [!code-vb[Trin_VstcoreActionsPaneWord#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#7)]  
  
## <a name="testing-the-application"></a>Testando o aplicativo  
 Agora você pode testar o documento para verificar se o painel de ações é exibido quando o documento é aberto. Testar a relação mestre/detalhes dos controles no painel Ações e certifique-se de que os dados são preenchidos em uma palavra de tabela quando o **inserir** botão é clicado.  
  
#### <a name="to-test-your-document"></a>Para testar o documento  
  
1.  Pressione F5 para executar o projeto.  
  
2.  Confirme se o painel de ações está visível.  
  
3.  Selecione uma empresa na caixa de combinação e verifique os itens a **produtos** alteração da caixa de lista.  
  
4.  Selecionar um produto, clique em **inserir** no painel Ações e verificar se os detalhes do produto são adicionados à tabela no Word.  
  
5.  Inserir produtos adicionais de várias empresas.  
  
## <a name="next-steps"></a>Próximas etapas  
 Este passo a passo mostra as Noções básicas de associação de dados a controles em um painel de ações no Word. Estas são algumas tarefas que podem vir a seguir:  
  
-   Associando dados a controles no Excel. Para obter mais informações, consulte [passo a passo: vinculação de dados a controles em um painel de ações do Excel](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md).  
  
-   Implantar o projeto. Para obter mais informações, consulte [implantar uma solução Office pelo ClickOnce usando](../vsto/deploying-an-office-solution-by-using-clickonce.md).  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral do painel de ações](../vsto/actions-pane-overview.md)   
 [Como: adicionar um painel de ações a documentos do Word ou pastas de trabalho do Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [Associando dados a controles em soluções do Office](../vsto/binding-data-to-controls-in-office-solutions.md)  
  
  