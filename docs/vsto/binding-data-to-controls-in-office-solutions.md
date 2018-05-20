---
title: Associar dados a controles em soluções do Office
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office documents [Office development in Visual Studio], connecting to data
- data, data binding
- data binding
- data binding, Office solutions
- data binding, controls
- Office applications [Office development in Visual Studio], data binding
- controls, data binding
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 540dc1f05ee54bc0a9cb0a9f4965c297aa42e33d
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
---
# <a name="bind-data-to-controls-in-office-solutions"></a>Associar dados a controles em soluções do Office
  Você pode associar controles de formulários do Windows e *hospedar controles* em um documento do Microsoft Office Word ou planilha do Microsoft Office Excel para uma fonte de dados para os controles de exibem automaticamente os dados. Você pode associar dados a controles em projetos do nível do aplicativo e o nível do documento.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Controles de host estendem os objetos que estão nos modelos de objeto Word e Excel, como controles de conteúdo do Word e intervalos nomeados em Excel. Para obter mais informações, consulte [itens de Host e visão geral dos controles de host](../vsto/host-items-and-host-controls-overview.md).  
  
 Windows Forms e controles de host usam o modelo de associação de dados de formulários do Windows, que dá suporte a ambos *associação de dados simples* e *associação de dados complexos* para fontes de dados como conjuntos de dados e tabelas de dados. Para obter informações completas sobre o modelo de associação de dados em formulários do Windows, consulte [ligação de dados e o Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms).  
  
 ![link para vídeo](../vsto/media/playvideo.gif "link para vídeo") para uma demonstração de vídeo relacionada, consulte [How do i: consumir dados de banco de dados no Excel?](http://go.microsoft.com/fwlink/?LinkID=130287).  
  
## <a name="simple-data-binding"></a>Vinculação de dados simples  
 Associação de dados simples existe quando uma propriedade do controle está associada a um elemento de dados simples, como um valor em uma tabela de dados. Por exemplo, o <xref:Microsoft.Office.Tools.Excel.NamedRange> controle tem um <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> propriedade que pode ser associada a um campo em um conjunto de dados. Quando o campo no conjunto de dados é alterado, o valor do intervalo nomeado também será alterado. Todos os hospedam controles, exceto para o <xref:Microsoft.Office.Tools.Word.XMLNodes> controlar, oferecem suporte à associação de dados simples. O <xref:Microsoft.Office.Tools.Word.XMLNodes> controle é uma coleção e, portanto, não dá suporte a associação de dados.  
  
 Para executar associação de dados simples para um controle de host, adicione um <xref:System.Windows.Forms.Binding> para o `DataBindings` propriedade do controle. Um <xref:System.Windows.Forms.Binding> objeto representa a simple associação entre um valor de propriedade do controle e o valor de um elemento de dados.  
  
 O exemplo a seguir demonstra como associar o <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> propriedade para um elemento de dados em um projeto no nível do documento.  
  
 [!code-vb[Trin_BindableComponent#4](../vsto/codesnippet/VisualBasic/Trin_BindableComponent/Sheet1.vb#4)]
 [!code-csharp[Trin_BindableComponent#4](../vsto/codesnippet/CSharp/Trin_BindableComponent/Sheet1.cs#4)]  
  
 Para instruções passo a passo que demonstra a associação de dados simples, consulte [passo a passo: associação de dados simples em um projeto no nível do documento](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md) para um projeto de nível de documento e [passo a passo: associação de dados simples no projeto de suplemento do VSTO ](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md) para um projeto de suplemento do VSTO.  
  
## <a name="complex-data-binding"></a>Vinculação de dados complexos  
 Associação de dados complexos existe quando uma propriedade do controle está associada a mais de um elemento de dados, como várias colunas em uma tabela de dados. O <xref:Microsoft.Office.Tools.Excel.ListObject> controlar para Excel é o único controle de host que oferece suporte à associação de dados complexos. Também há muitos controles de formulários do Windows que oferecem suporte à associação de dados complexos, como o <xref:System.Windows.Forms.DataGridView> controle.  
  
 Para executar associação de dados complexos, defina o `DataSource` propriedade do controle para um objeto de fonte de dados com suporte para associação de dados complexos. Por exemplo, o <xref:Microsoft.Office.Tools.Excel.ListObject.DataSource%2A> propriedade o <xref:Microsoft.Office.Tools.Excel.ListObject> controle pode ser associado a várias colunas em uma tabela de dados. Todos os dados na tabela de dados aparece no <xref:Microsoft.Office.Tools.Excel.ListObject> controle e como os dados nas alterações de dados de tabela, o <xref:Microsoft.Office.Tools.Excel.ListObject> também será alterado. Para obter uma lista das fontes de dados que você pode usar para associação de dados complexos, consulte [fontes de dados com suporte no Windows Forms](/dotnet/framework/winforms/data-sources-supported-by-windows-forms).  
  
 O exemplo de código a seguir cria um <xref:System.Data.DataSet> com dois <xref:System.Data.DataTable> objetos e preenche uma das tabelas com dados. O código, em seguida, associa a <xref:Microsoft.Office.Tools.Excel.ListObject> para a tabela que contém dados. Este exemplo é para um projeto de nível de documento do Excel.  
  
 [!code-csharp[Trin_ExcelListObject#18](../vsto/codesnippet/CSharp/Trin_ExcelListObject/Trin_ExcelListObject.cs#18)]
 [!code-vb[Trin_ExcelListObject#18](../vsto/codesnippet/VisualBasic/Trin_ExcelListObject/Sheet1.vb#18)]  
  
 Para instruções passo a passo que demonstre a associação de dados complexos, consulte [passo a passo: associação de dados complexos em um projeto no nível de documento](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md) para um projeto de nível de documento e [passo a passo: associação de dados complexos em projeto de suplemento do VSTO ](../vsto/walkthrough-complex-data-binding-in-vsto-add-in-project.md) para um projeto de suplemento do VSTO.  
  
## <a name="display-data-in-documents-and-workbooks"></a>Exibir dados em documentos e pastas de trabalho  
 Em projetos de nível de documento, você pode usar o **fontes de dados** janela para adicionar controles associados a dados para seus documentos ou pastas de trabalho facilmente, da mesma forma que você pode usá-lo para formulários do Windows. Para obter mais informações sobre como usar o **fontes de dados** janela, consulte [controla associar Windows Forms a dados no Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md) e [adicionar novas fontes de dados](../data-tools/add-new-data-sources.md).  
  
### <a name="drag-controls-from-the-data-sources-window"></a>Arraste os controles da janela fontes de dados  
 Um controle é criado no documento, quando você arrasta um objeto do **fontes de dados** janela. O tipo de controle que é criado depende se você está associando uma única coluna de dados ou de várias colunas de dados.  
  
 Para o Excel, um <xref:Microsoft.Office.Tools.Excel.NamedRange> controle é criado na planilha para cada campo individual e um <xref:Microsoft.Office.Tools.Excel.ListObject> controle é criado para cada intervalo de dados que inclui várias linhas e colunas. Você pode alterar esse padrão selecionando a tabela ou campo no **fontes de dados** janela e, em seguida, escolhendo um controle diferente na lista suspensa.  
  
 Um <xref:Microsoft.Office.Tools.Word.ContentControl> controle é adicionado a documentos. O tipo de controle de conteúdo depende do tipo de dados do campo que você selecionou.  
  
### <a name="bind-data-in-document-level-projects-at-design-time"></a>Associar dados no nível de documento em tempo de design  
 Os tópicos a seguir mostram exemplos de associação de dados em tempo de design:  
  
-   [Como: preencher planilhas com dados de um banco de dados](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)  
  
-   [Como: preencher documentos com dados de um banco de dados](../vsto/how-to-populate-documents-with-data-from-a-database.md)  
  
-   [Como: preencher documentos com dados de objetos](../vsto/how-to-populate-documents-with-data-from-objects.md)  
  
-   [Como: preencher documentos com dados de serviços](../vsto/how-to-populate-documents-with-data-from-services.md)  
  
-   [Como: percorrer registros do banco de dados em uma planilha](../vsto/how-to-scroll-through-database-records-in-a-worksheet.md)  
  
### <a name="bind-data-in-vsto-add-in-projects"></a>Associar dados em projetos de suplemento do VSTO  
 Em projetos de suplemento do VSTO, é possível adicionar controles apenas em tempo de execução. Os tópicos a seguir mostram exemplos de associação de dados em tempo de execução:  
  
-   [Passo a passo: Associação de dados simples no projeto de suplemento do VSTO](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md)  
  
-   [Passo a passo: Associação de dados complexos em projeto de suplemento do VSTO](../vsto/walkthrough-complex-data-binding-in-vsto-add-in-project.md)  
  
## <a name="update-data-that-is-bound-to-host-controls"></a>Atualizar os dados associados a controles de host  
 Associação de dados entre uma fonte de dados e um controle de host envolve uma atualização de dados bidirecional. Na associação de dados simples, as alterações na fonte de dados são refletidas automaticamente no controle de host, mas as alterações no controle de host requerem uma chamada explícita para atualizar a fonte de dados. O motivo é que em alguns casos, as alterações em um campo de dados associados não são aceitas, a menos que eles são acompanhados por alterações em outro campo de associação de dados. Por exemplo, você pode ter dois campos, um para idade e outro para anos de experiência. Experiência não pode exceder a idade. Um usuário não é possível atualizar a idade de 50 para 25 e, em seguida, a experiência de 30 para 10, a menos que ele faz as alterações ao mesmo tempo. Para resolver esse problema, os campos com associação de dados simples não são atualizados até que as atualizações são explicitamente enviadas pelo código.  
  
 Para atualizar uma fonte de dados de controles de host que permitem a associação de dados simples, você deve enviar atualizações para a fonte de dados na memória (como um <xref:System.Data.DataSet> ou <xref:System.Data.DataTable>) e o banco de dados back-end, se sua solução usar um.  
  
 Você não precisa atualizar explicitamente a fonte de dados na memória quando você executa a associação de dados complexos usando o <xref:Microsoft.Office.Tools.Excel.ListObject> controle. Nesse caso, as alterações são enviadas automaticamente à fonte de dados na memória sem código adicional.  
  
 Para obter mais informações, consulte [como: atualizar uma fonte de dados com dados de um controle de host](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md).  
  
## <a name="see-also"></a>Consulte também  
 [Como fazer i: consumir dados de banco de dados no Excel?](http://go.microsoft.com/fwlink/?LinkID=130287)   
 [Associação de dados e o Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms)   
 [Como: criar um controle associado simples em um Windows Form](/dotnet/framework/winforms/how-to-create-a-simple-bound-control-on-a-windows-form)   
 [Associar controles do Windows Forms a dados no Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Salvar dados no banco de dados](../data-tools/save-data-back-to-the-database.md)    
 [Atualizar dados usando um TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md)    
 [Dados de cache](../vsto/caching-data.md)   
 [Dados em soluções do Office](../vsto/data-in-office-solutions.md)  
  
  