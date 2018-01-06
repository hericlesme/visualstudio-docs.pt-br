---
title: 'Como: atualizar uma fonte de dados com dados de um controle de Host | Microsoft Docs'
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
- documents [Office development in Visual Studio], data source updates
- data [Office development in Visual Studio], updating a data source from a document
- host controls [Office development in Visual Studio], data source updates
- Office documents [Office development in Visual Studio, data sources
ms.assetid: b91025af-1eaa-44ee-88f2-71ecaa7a0440
caps.latest.revision: "53"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: eff45d9b2c8dbac0aade12a003008dd9b2c29fb2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-update-a-data-source-with-data-from-a-host-control"></a>Como atualizar uma fonte de dados com dados de um controle de host
  Você pode associar um controle de host a uma fonte de dados e atualizar a fonte de dados com as alterações feitas aos dados no controle. Há duas etapas principais neste processo:  
  
1.  Atualize a fonte de dados na memória com os dados modificados no controle. Normalmente, a fonte de dados na memória é um <xref:System.Data.DataSet>, um <xref:System.Data.DataTable>, ou algum outro objeto de dados.  
  
2.  Atualize o banco de dados com os dados alterados na fonte de dados na memória. Isso é aplicável somente se a fonte de dados está conectada a um banco de dados de back-end, como um banco de dados do SQL Server ou Microsoft Office Access.  
  
 Para obter mais informações sobre associação de dados e controles de host, consulte [itens de Host e visão geral dos controles de Host](../vsto/host-items-and-host-controls-overview.md) e [ligar dados a controles em soluções do Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
## <a name="updating-the-in-memory-data-source"></a>Atualizando a fonte de dados na memória  
 Por padrão, os controles de host que permitem a associação de dados simples (como controles de conteúdo em um documento do Word ou um controle de intervalo nomeado em uma planilha do Excel) não salvar as alterações de dados à fonte de dados na memória. Ou seja, quando um usuário final altera os valores em um controle de host e, em seguida, navega para fora do controle, o novo valor no controle não é salva automaticamente para a fonte de dados.  
  
 Para salvar os dados para a fonte de dados, você pode escrever código que atualiza a fonte de dados em resposta a um evento específico no tempo de execução, ou você pode configurar o controle para atualizar automaticamente a fonte de dados quando o valor no controle é alterado.  
  
 Você não precisa salvar <xref:Microsoft.Office.Tools.Excel.ListObject> muda para a fonte de dados na memória. Quando você associa um <xref:Microsoft.Office.Tools.Excel.ListObject> controle aos dados, o <xref:Microsoft.Office.Tools.Excel.ListObject> controle salva automaticamente as alterações para a fonte de dados na memória sem a necessidade de código adicional.  
  
#### <a name="to-update-the-in-memory-data-source-at-run-time"></a>Para atualizar a fonte de dados na memória em tempo de execução  
  
-   Chamar o <xref:System.Windows.Forms.Binding.WriteValue%2A> método o <xref:System.Windows.Forms.Binding> objeto que associa o controle à fonte de dados.  
  
     O exemplo a seguir salva as alterações feitas em um <xref:Microsoft.Office.Tools.Excel.NamedRange> controle em uma planilha do Excel para a fonte de dados. Este exemplo pressupõe que você tenha um <xref:Microsoft.Office.Tools.Excel.NamedRange> controle chamado `namedRange1` com seus <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> propriedade associada a um campo em uma fonte de dados.  
  
     [!code-csharp[Trin_VstcoreDataExcel#1](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#1)]
     [!code-vb[Trin_VstcoreDataExcel#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#1)]  
  
### <a name="automatically-updating-the-in-memory-data-source"></a>Atualizar automaticamente a fonte de dados na memória  
 Você também pode configurar um controle para que ele atualiza automaticamente a fonte de dados na memória. Em um projeto de nível de documento, você pode fazer isso usando o código ou o designer. Em um projeto de suplemento do VSTO, você deve usar o código.  
  
##### <a name="to-set-a-control-to-automatically-update-the-in-memory-data-source-by-using-code"></a>Para definir um controle para atualizar automaticamente a fonte de dados na memória usando código  
  
1.  Use o modo de System.Windows.Forms.DataSourceUpdateMode.OnPropertyChanged do <xref:System.Windows.Forms.Binding> objeto que associa o controle à fonte de dados. Há duas opções para atualizar a fonte de dados:  
  
    -   Para atualizar a fonte de dados quando o controle é validado, defina essa propriedade como System.Windows.Forms.DataSourceUpdateMode.OnValidation.  
  
    -   Para atualizar a fonte de dados quando o valor da propriedade de associação de dados do controle de alterações, defina essa propriedade como System.Windows.Forms.DataSourceUpdateMode.OnPropertyChanged.  
  
        > [!NOTE]  
        >  A opção System.Windows.Forms.DataSourceUpdateMode.OnPropertyChanged não se aplica a controles de host do Word, como o Word não notificações não oferta documento de alteração ou controle de alterações. No entanto, essa opção pode ser usada para controles de Windows Forms em documentos do Word.  
  
     O exemplo a seguir configura um <xref:Microsoft.Office.Tools.Excel.NamedRange> controle para atualizar a fonte de dados automaticamente quando o valor no controle é alterado. Este exemplo pressupõe que você tenha um <xref:Microsoft.Office.Tools.Excel.NamedRange> controle chamado `namedRange1` com seus <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> propriedade associada a um campo em uma fonte de dados.  
  
     [!code-csharp[Trin_VstcoreDataExcel#19](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#19)]
     [!code-vb[Trin_VstcoreDataExcel#19](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#19)]  
  
##### <a name="to-set-a-control-to-automatically-update-the-in-memory-data-source-by-using-the-designer"></a>Para definir um controle para atualizar automaticamente a fonte de dados na memória usando o designer  
  
1.  No Visual Studio, abra o documento do Word ou pasta de trabalho do Excel no designer.  
  
2.  Clique no controle que você deseja atualizar automaticamente a fonte de dados.  
  
3.  No **propriedades** janela, expanda o **(DataBindings)** propriedade.  
  
4.  Ao lado de **(Avançado)** propriedade, clique no botão de reticências (![de tela de VisualStudioEllipsesButton](../vsto/media/vbellipsesbutton.png "de tela de VisualStudioEllipsesButton")).  
  
5.  No **formatação e associação avançada** caixa de diálogo, clique o **modo de atualização de fonte de dados** lista suspensa e selecione um dos seguintes valores:  
  
    -   Para atualizar a fonte de dados quando o controle é validado, selecione **OnValidation**.  
  
    -   Para atualizar a fonte de dados quando o valor da propriedade de associação de dados do controle é alterado, selecione **OnPropertyChanged**.  
  
        > [!NOTE]  
        >  O **OnPropertyChanged** opção não se aplica a controles de host do Word, como o Word não notificações não oferta documento de alteração ou controle de alterações. No entanto, essa opção pode ser usada para controles de Windows Forms em documentos do Word.  
  
6.  Fechar o **formatação e associação avançada** caixa de diálogo.  
  
## <a name="updating-the-database"></a>Atualizando o banco de dados  
 Se a fonte de dados na memória estiver associada um banco de dados, você deve atualizar o banco de dados com as alterações para a fonte de dados. Para obter mais informações sobre como atualizar um banco de dados, consulte [salvar dados no banco de dados](../data-tools/save-data-back-to-the-database.md) e [atualizar dados usando um TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md) .  
  
#### <a name="to-update-the-database"></a>Para atualizar o banco de dados  
  
1.  Chamar o <xref:System.Windows.Forms.BindingSource.EndEdit%2A> método o <xref:System.Windows.Forms.BindingSource> para o controle.  
  
     O <xref:System.Windows.Forms.BindingSource> é gerado automaticamente quando você adicionar um controle associado a dados para um documento ou a pasta de trabalho em tempo de design. O <xref:System.Windows.Forms.BindingSource> conecta-se o controle para o conjunto de dados tipado em seu projeto. Para obter mais informações, consulte [visão geral do componente BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-overview).  
  
     O exemplo de código a seguir pressupõe que seu projeto contém um <xref:System.Windows.Forms.BindingSource> chamado `customersBindingSource`.  
  
     [!code-csharp[Trin_VstcoreDataExcel#20](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#20)]
     [!code-vb[Trin_VstcoreDataExcel#20](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#20)]  
  
2.  Chamar o `Update` método do TableAdapter gerado no seu projeto.  
  
     O TableAdapter é gerado automaticamente quando você adicionar um controle associado a dados para um documento ou a pasta de trabalho em tempo de design. O TableAdapter conecta-se o conjunto de dados tipado em seu projeto para o banco de dados. Para obter mais informações, consulte [visão geral de TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview).  
  
     O exemplo de código a seguir pressupõe que você tenha uma conexão para a tabela Customers no banco de dados Northwind, e que o seu projeto contém um TableAdapter chamado `customersTableAdapter` e um conjunto de dados tipado chamado `northwindDataSet`.  
  
     [!code-csharp[Trin_VstcoreDataExcel#21](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#21)]
     [!code-vb[Trin_VstcoreDataExcel#21](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#21)]  
  
## <a name="see-also"></a>Consulte também  
 [Associando dados a controles em soluções do Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Salvar dados no banco de dados](../data-tools/save-data-back-to-the-database.md)    
 [Atualizar dados usando um TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md)    
 [Como: percorrer registros do banco de dados em uma planilha](../vsto/how-to-scroll-through-database-records-in-a-worksheet.md)   
 [Como: preencher planilhas com dados de um banco de dados](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)   
 [Como: preencher documentos com dados de objetos](../vsto/how-to-populate-documents-with-data-from-objects.md)   
 [Como: preencher documentos com dados de um banco de dados](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [Como preencher documentos usando dados de serviços](../vsto/how-to-populate-documents-with-data-from-services.md)  
  
  