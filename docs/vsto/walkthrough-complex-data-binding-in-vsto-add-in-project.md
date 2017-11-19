---
title: "Passo a passo: Associação de dados complexos no VSTO suplemento projeto | Microsoft Docs"
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
- data binding [Office development in Visual Studio], Excel
- data [Office development in Visual Studio], binding data
- complex data [Office development in Visual Studio]
ms.assetid: ff52fb56-1f67-4ae2-a3d1-93038619d4e6
caps.latest.revision: "38"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9b106e9d1ef1fc10c5c0cd99ceaed76f87408713
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-complex-data-binding-in-vsto-add-in-project"></a>Passo a passo: Associando dados complexos no projeto de suplemento do VSTO
  Você pode associar dados a controles de host e controles de formulários do Windows em projetos de suplemento do VSTO. Este passo a passo demonstra como adicionar controles a uma planilha do Microsoft Office Excel e associar os controles de dados em tempo de execução.  
  
 [!INCLUDE[appliesto_xlallapp](../vsto/includes/appliesto-xlallapp-md.md)]  
  
 Esta explicação passo a passo ilustra as seguintes tarefas:  
  
-   Adicionando um <xref:Microsoft.Office.Tools.Excel.ListObject> controle em uma planilha em tempo de execução.  
  
-   Criando um <xref:System.Windows.Forms.BindingSource> que conecta o controle a uma instância de um conjunto de dados.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Você precisa dos seguintes componentes para concluir esta instrução passo a passo:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] ou [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
-   Acesso a uma instância em execução do SQL Server 2005 ou SQL Server 2005 Express que tem o `AdventureWorksLT` o banco de dados de exemplo está anexado a ele. Você pode baixar o `AdventureWorksLT` do banco de dados de [site da CodePlex](http://go.microsoft.com/fwlink/?LinkId=115611). Para obter mais informações sobre como anexar um banco de dados, consulte os tópicos a seguir:  
  
    -   Para anexar um banco de dados usando o SQL Server Management Studio ou o SQL Server Management Studio Express, consulte [como: anexar um banco de dados (SQL Server Management Studio)](http://msdn.microsoft.com/en-us/b4efb0ae-cfe6-4d81-a4b4-6e4916885caa).  
  
    -   Para anexar um banco de dados usando a linha de comando, consulte [como: anexar um arquivo de banco de dados SQL Server Express](http://msdn.microsoft.com/en-us/0f8e42b5-7a8c-4c30-8c98-7d2bdc8dcc68).  
  
## <a name="creating-a-new-project"></a>Criando um novo projeto  
 A primeira etapa é criar um projeto de suplemento do VSTO do Excel.  
  
#### <a name="to-create-a-new-project"></a>Para criar um novo projeto  
  
1.  Criar um projeto de suplemento do VSTO do Excel com o nome **preenchendo planilhas de um banco de dados**, usando o Visual Basic ou c#.  
  
     Para obter mais informações, consulte [como: criar projetos do Office no Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     O Visual Studio abrirá o `ThisAddIn.vb` ou `ThisAddIn.cs` de arquivos e adiciona o **preenchendo planilhas de um banco de dados** projeto **Gerenciador de soluções**.  
  
## <a name="creating-a-data-source"></a>Criar uma fonte de dados  
 Use o **fontes de dados** janela para adicionar um conjunto de dados tipado ao seu projeto.  
  
#### <a name="to-add-a-typed-dataset-to-the-project"></a>Para adicionar um conjunto de dados tipado ao projeto  
  
1.  Se o **fontes de dados** janela não estiver visível, exibir, na barra de menus, escolhendo **exibição**, **outras janelas**, **fontes de dados**.  
  
2.  Escolha **adicionar nova fonte de dados** para iniciar o **Assistente de configuração de fonte de dados**.  
  
3.  Clique em **banco de dados**e, em seguida, clique em **próximo**.  
  
4.  Se você tiver uma conexão existente para o `AdventureWorksLT` de banco de dados, escolha essa conexão e clique em **próximo**.  
  
     Caso contrário, clique em **nova Conexão**e usar o **Adicionar Conexão** caixa de diálogo para criar a nova conexão. Para obter mais informações, consulte [adicionar novas conexões](../data-tools/add-new-connections.md).  
  
5.  No **salvar a cadeia de Conexão no arquivo de configuração do aplicativo** , clique em **próximo**.  
  
6.  No **escolher seus objetos de banco de dados** página, expanda **tabelas** e selecione **endereço (SalesLT)**.  
  
7.  Clique em **Finalizar**.  
  
     O arquivo AdventureWorksLTDataSet.xsd é adicionado ao **Gerenciador de soluções**. Esse arquivo define os seguintes itens:  
  
    -   Um conjunto de dados tipado chamado `AdventureWorksLTDataSet`. Este conjunto de dados representa o conteúdo do **endereço (SalesLT)** tabela no banco de dados AdventureWorksLT.  
  
    -   Um TableAdapter chamado `AddressTableAdapter`. Este TableAdapter pode ser usado para ler e gravar dados no `AdventureWorksLTDataSet`. Para obter mais informações, consulte [visão geral de TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview).  
  
     Você usará esses objetos posteriormente neste passo a passo.  
  
## <a name="creating-controls-and-binding-controls-to-data"></a>Criando controles e associando controles a dados  
 Para este passo a passo, o <xref:Microsoft.Office.Tools.Excel.ListObject> controle exibe todos os dados na tabela selecionada como o usuário abre a pasta de trabalho. O objeto da lista usa uma <xref:System.Windows.Forms.BindingSource> para conectar-se o controle para o banco de dados.  
  
 Para obter mais informações sobre controles de associação de dados, consulte [ligar dados a controles em soluções do Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
#### <a name="to-add-the-list-object-dataset-and-table-adapter"></a>Para adicionar o objeto de lista, o conjunto de dados e o adaptador de tabela  
  
1.  No `ThisAddIn` classe, declare os seguintes controles para exibir o `Address` tabela da `AdventureWorksLTDataSet` conjunto de dados.  
  
     [!code-csharp[Trin_ExcelAddInDatabase#1](../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs#1)]
     [!code-vb[Trin_ExcelAddInDatabase#1](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb#1)]  
  
2.  No `ThisAddIn_Startup` método, adicione o seguinte código para inicializar o conjunto de dados e preencher o conjunto de dados com as informações a `AdventureWorksLTDataSet` conjunto de dados.  
  
     [!code-csharp[Trin_ExcelAddInDatabase#2](../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs#2)]
     [!code-vb[Trin_ExcelAddInDatabase#2](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb#2)]  
  
3.  Adicione o seguinte código ao método de `ThisAddIn_Startup` . Isso gera um item de host que estende a planilha. Para obter mais informações, consulte [Estendendo documentos do Word e pastas de trabalho do Excel no suplemento do VSTO em tempo de execução](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
     [!code-csharp[Trin_ExcelAddInDatabase#3](../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs#3)]
     [!code-vb[Trin_ExcelAddInDatabase#3](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb#3)]  
  
4.  Criar um intervalo e adicione o <xref:Microsoft.Office.Tools.Excel.ListObject> controle.  
  
     [!code-csharp[Trin_ExcelAddInDatabase#4](../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs#4)]
     [!code-vb[Trin_ExcelAddInDatabase#4](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb#4)]  
  
5.  Associar o objeto da lista para `AdventureWorksLTDataSet` usando o <xref:System.Windows.Forms.BindingSource>. Passar os nomes das colunas que você deseja vincular o objeto de lista.  
  
     [!code-csharp[Trin_ExcelAddInDatabase#5](../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs#5)]
     [!code-vb[Trin_ExcelAddInDatabase#5](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb#5)]  
  
## <a name="testing-the-add-in"></a>Testando o suplemento  
 Quando você abrir o Excel, o <xref:Microsoft.Office.Tools.Excel.ListObject> controle exibe os dados do `Address` tabela da `AdventureWorksLTDataSet` conjunto de dados.  
  
#### <a name="to-test-the-vsto-add-in"></a>Para testar o suplemento do VSTO  
  
-   Pressione **F5**.  
  
     Um <xref:Microsoft.Office.Tools.Excel.ListObject> controle chamado `addressListObject` é criado na planilha. Ao mesmo tempo, um objeto de conjunto de dados chamado `adventureWorksLTDataSet` e um <xref:System.Windows.Forms.BindingSource> chamado `addressBindingSource` são adicionados ao projeto. O <xref:Microsoft.Office.Tools.Excel.ListObject> está associada ao <xref:System.Windows.Forms.BindingSource>, que por sua vez é associado ao objeto de conjunto de dados.  
  
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
 [Usando arquivos de banco de dados Local na visão geral das soluções do Office](../vsto/using-local-database-files-in-office-solutions-overview.md)   
 [Conectando a dados em aplicativos do Windows Forms](/visualstudio/data-tools/connecting-to-data-in-windows-forms-applications)   
 [Visão geral do componente BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-overview)  
  
  