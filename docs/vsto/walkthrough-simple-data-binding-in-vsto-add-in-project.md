---
title: 'Passo a passo: Associação de dados simples no VSTO suplemento projeto | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Office development in Visual Studio], binding data
- data binding [Office development in Visual Studio], Word
- data [Office development in Visual Studio], simple binding data
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7288cf17f7870747399116a1b779c2fa3b67205f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-simple-data-binding-in-vsto-add-in-project"></a>Passo a passo: Associando dados simples no projeto de suplemento do VSTO
  Você pode associar dados a controles de host e controles de formulários do Windows em projetos de suplemento do VSTO. Este passo a passo demonstra como adicionar controles a um documento do Microsoft Office Word e associar os controles de dados em tempo de execução.  
  
 [!INCLUDE[appliesto_wdallapp](../vsto/includes/appliesto-wdallapp-md.md)]  
  
 Esta explicação passo a passo ilustra as seguintes tarefas:  
  
-   Adicionando um <xref:Microsoft.Office.Tools.Word.ContentControl> para um documento em tempo de execução.  
  
-   Criando um <xref:System.Windows.Forms.BindingSource> que conecta o controle a uma instância de um conjunto de dados.  
  
-   Permitir que o usuário rolar os registros e exibi-los no controle.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Você precisa dos seguintes componentes para concluir esta instrução passo a passo:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] ou [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].  
  
-   Acesso a uma instância em execução do SQL Server 2005 ou SQL Server 2005 Express que tem o `AdventureWorksLT` o banco de dados de exemplo está anexado a ele. Você pode baixar o `AdventureWorksLT` do banco de dados de [site da CodePlex](http://go.microsoft.com/fwlink/?LinkId=115611). Para obter mais informações sobre como anexar um banco de dados, consulte os tópicos a seguir:  
  
    -   Para anexar um banco de dados usando o SQL Server Management Studio ou o SQL Server Management Studio Express, consulte [como: anexar um banco de dados (SQL Server Management Studio)](http://msdn.microsoft.com/en-us/b4efb0ae-cfe6-4d81-a4b4-6e4916885caa).  
  
    -   Para anexar um banco de dados usando a linha de comando, consulte [como: anexar um arquivo de banco de dados SQL Server Express](http://msdn.microsoft.com/en-us/0f8e42b5-7a8c-4c30-8c98-7d2bdc8dcc68).  
  
## <a name="creating-a-new-project"></a>Criando um novo projeto  
 A primeira etapa é criar um projeto de suplemento do VSTO do Word.  
  
#### <a name="to-create-a-new-project"></a>Para criar um novo projeto  
  
1.  Criar um projeto de suplemento do VSTO Word com o nome **preenchendo documentos a partir de um banco de dados**, usando o Visual Basic ou c#.  
  
     Para obter mais informações, consulte [como: criar projetos do Office no Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     O Visual Studio abre o arquivo ThisAddIn ou ThisAddIn.cs e adiciona o **preenchendo documentos a partir de um banco de dados** projeto **Gerenciador de soluções**.  
  
2.  Se seu projeto utiliza o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], adicione uma referência ao assembly Microsoft.Office.Tools.Word.v4.0.Utilities.dll. Essa referência é necessário adicionar programaticamente os controles de formulários do Windows para o documento mais tarde neste passo a passo.  
  
## <a name="creating-a-data-source"></a>Criar uma fonte de dados  
 Use o **fontes de dados** janela para adicionar um conjunto de dados tipado ao seu projeto.  
  
#### <a name="to-add-a-typed-dataset-to-the-project"></a>Para adicionar um conjunto de dados tipado ao projeto  
  
1.  Se o **fontes de dados** janela não estiver visível, exibir, na barra de menus, escolhendo **exibição**, **outras janelas**, **fontes de dados**.  
  
2.  Escolha **adicionar nova fonte de dados** para iniciar o **Assistente de configuração de fonte de dados**.  
  
3.  Clique em **banco de dados**e, em seguida, clique em **próximo**.  
  
4.  Se você tiver uma conexão existente para o `AdventureWorksLT` de banco de dados, escolha essa conexão e clique em **próximo**.  
  
     Caso contrário, clique em **nova Conexão**e usar o **Adicionar Conexão** caixa de diálogo para criar a nova conexão. Para obter mais informações, consulte [adicionar novas conexões](../data-tools/add-new-connections.md).  
  
5.  No **salvar a cadeia de Conexão no arquivo de configuração do aplicativo** , clique em **próximo**.  
  
6.  No **escolher seus objetos de banco de dados** página, expanda **tabelas** e selecione **cliente (SalesLT)**.  
  
7.  Clique em **Finalizar**.  
  
     O arquivo AdventureWorksLTDataSet.xsd é adicionado ao **Gerenciador de soluções**. Esse arquivo define os seguintes itens:  
  
    -   Um conjunto de dados tipado chamado `AdventureWorksLTDataSet`. Este conjunto de dados representa o conteúdo do **cliente (SalesLT)** tabela no banco de dados AdventureWorksLT.  
  
    -   Um TableAdapter chamado `CustomerTableAdapter`. Este TableAdapter pode ser usado para ler e gravar dados no `AdventureWorksLTDataSet`. Para obter mais informações, consulte [visão geral de TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview).  
  
     Você usará esses objetos posteriormente neste passo a passo.  
  
## <a name="creating-controls-and-binding-controls-to-data"></a>Criando controles e associando controles a dados  
 A interface para exibir os registros do banco de dados neste passo a passo é muito básica, e é criado dentro do documento. Um <xref:Microsoft.Office.Tools.Word.ContentControl> exibe um registro único banco de dados por vez e dois <xref:Microsoft.Office.Tools.Word.Controls.Button> controles permitem que você percorra os registros e para trás. O controle de conteúdo usa um <xref:System.Windows.Forms.BindingSource> para se conectar ao banco de dados.  
  
 Para obter mais informações sobre controles de associação de dados, consulte [ligar dados a controles em soluções do Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
#### <a name="to-create-the-interface-in-the-document"></a>Para criar a interface do documento  
  
1.  No `ThisAddIn` classe, declare os seguintes controles para exibir e percorrer o `Customer` tabela do `AdventureWorksLTDataSet` banco de dados.  
  
     [!code-vb[Trin_WordAddInDatabase#1](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#1)]
     [!code-csharp[Trin_WordAddInDatabase#1](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#1)]  
  
2.  No `ThisAddIn_Startup` método, adicione o seguinte código para inicializar o conjunto de dados, preencha o conjunto de dados com as informações a `AdventureWorksLTDataSet` banco de dados.  
  
     [!code-vb[Trin_WordAddInDatabase#2](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#2)]
     [!code-csharp[Trin_WordAddInDatabase#2](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#2)]  
  
3.  Adicione o seguinte código ao método de `ThisAddIn_Startup` . Isso gera um item de host que estende o documento. Para obter mais informações, consulte [Estendendo documentos do Word e pastas de trabalho do Excel no suplemento do VSTO em tempo de execução](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
     [!code-vb[Trin_WordAddInDatabase#3](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#3)]
     [!code-csharp[Trin_WordAddInDatabase#3](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#3)]  
  
4.  Defina vários intervalos no início do documento. Esses intervalos identificam onde inserir texto e coloque controles.  
  
     [!code-vb[Trin_WordAddInDatabase#4](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#4)]
     [!code-csharp[Trin_WordAddInDatabase#4](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#4)]  
  
5.  Adicione os controles da interface a intervalos definidos anteriormente.  
  
     [!code-vb[Trin_WordAddInDatabase#5](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#5)]
     [!code-csharp[Trin_WordAddInDatabase#5](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#5)]  
  
6.  Associar o controle de conteúdo para `AdventureWorksLTDataSet` usando o <xref:System.Windows.Forms.BindingSource>. Para desenvolvedores do c#, adicione dois manipuladores de eventos para o <xref:Microsoft.Office.Tools.Word.Controls.Button> controles.  
  
     [!code-vb[Trin_WordAddInDatabase#6](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#6)]
     [!code-csharp[Trin_WordAddInDatabase#6](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#6)]  
  
7.  Adicione o código a seguir para navegar entre os registros do banco de dados.  
  
     [!code-vb[Trin_WordAddInDatabase#7](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#7)]
     [!code-csharp[Trin_WordAddInDatabase#7](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#7)]  
  
## <a name="testing-the-add-in"></a>Testando o suplemento  
 Quando você abre o Word, o controle de conteúdo exibe dados do `AdventureWorksLTDataSet` conjunto de dados. Percorrer os registros do banco de dados clicando o **próximo** e **anterior** botões.  
  
#### <a name="to-test-the-vsto-add-in"></a>Para testar o suplemento do VSTO  
  
1.  Pressione **F5**.  
  
     Um controle de conteúdo chamado `customerContentControl` é criada e preenchida com dados. Ao mesmo tempo, um objeto de conjunto de dados chamado `adventureWorksLTDataSet` e um <xref:System.Windows.Forms.BindingSource> chamado `customerBindingSource` são adicionados ao projeto. O <xref:Microsoft.Office.Tools.Word.ContentControl> está associada ao <xref:System.Windows.Forms.BindingSource>, que por sua vez é associado ao objeto de conjunto de dados.  
  
2.  Clique o **próximo** e **anterior** botões para percorrer os registros do banco de dados.  
  
## <a name="see-also"></a>Consulte também  
 [Dados em soluções do Office](../vsto/data-in-office-solutions.md)   
 [Associando dados a controles em soluções do Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Como: preencher planilhas com dados de um banco de dados](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)   
 [Como: preencher documentos com dados de um banco de dados](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [Como: preencher documentos com dados de serviços](../vsto/how-to-populate-documents-with-data-from-services.md)   
 [Como: preencher documentos com dados de objetos](../vsto/how-to-populate-documents-with-data-from-objects.md)   
 [Como: percorrer registros do banco de dados em uma planilha](../vsto/how-to-scroll-through-database-records-in-a-worksheet.md)   
 [Como: atualizar uma fonte de dados com dados de um controle de Host](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [Passo a passo: Associação de dados simples em um projeto no nível de documento](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md)   
 [Passo a passo: Associação de dados complexos em um projeto no nível de documento](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md)   
 [Usando arquivos de banco de dados Local na visão geral das soluções do Office](../vsto/using-local-database-files-in-office-solutions-overview.md)   
 [Adicionar novas fontes de dados](/visualstudio/data-tools/add-new-data-sources)   
 [Associar controles do Windows Forms a dados no Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Como: preencher documentos com dados de objetos](../vsto/how-to-populate-documents-with-data-from-objects.md)   
 [Como: atualizar uma fonte de dados com dados de um controle de Host](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [Usando arquivos de banco de dados Local na visão geral das soluções do Office](../vsto/using-local-database-files-in-office-solutions-overview.md)   
 [Conectando a dados em aplicativos do Windows Forms](/visualstudio/data-tools/connecting-to-data-in-windows-forms-applications)   
 [Visão geral do componente BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-overview)  
  
  