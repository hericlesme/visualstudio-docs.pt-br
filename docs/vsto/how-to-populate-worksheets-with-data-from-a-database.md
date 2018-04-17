---
title: 'Como: preencher planilhas com dados de um banco de dados | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets [Office development in Visual Studio], populating
- databases [Office development in Visual Studio], populating worksheets
- data [Office development in Visual Studio], adding to worksheets
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 31f0bd40b38ed85631874556908a41e21b860ecd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-populate-worksheets-with-data-from-a-database"></a>Como preencher planilhas com dados de um banco de dados
  Você pode acessar dados em projetos do Office em nível de documento da mesma maneira que você acessar dados em projetos de formulários do Windows. Usar as mesmas ferramentas e código para trazer os dados para sua solução, e você pode até usar controles de formulários do Windows para exibir os dados. Além disso, você pode tirar proveito dos controles chamados controles de host, que são objetos nativo no Microsoft Office Excel que foram aprimorados com eventos e a capacidade de associação de dados. Para obter mais informações, consulte [itens de Host e visão geral dos controles de Host](../vsto/host-items-and-host-controls-overview.md).  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 O exemplo a seguir mostra como adicionar controles associados a dados em projetos de nível de documento usando um designer. Para obter um exemplo de como adicionar controles associados a dados em projetos no nível de aplicativo em tempo de execução, consulte [passo a passo: associação de dados complexos no VSTO suplemento projeto](../vsto/walkthrough-complex-data-binding-in-vsto-add-in-project.md).  
  
 ![link para vídeo](../vsto/media/playvideo.gif "link para vídeo") para uma demonstração de vídeo relacionada, consulte [como fazer i: transferir dados em uma planilha do Excel?](http://go.microsoft.com/fwlink/?LinkID=130277), e [como fazer i: consumir banco de dados no Excel?](http://go.microsoft.com/fwlink/?LinkID=130287).  
  
## <a name="adding-a-data-bound-control-to-a-worksheet-at-design-time"></a>Adicionando um controle associado a dados a uma planilha em tempo de Design  
  
#### <a name="to-populate-a-worksheet-with-data-from-a-database"></a>Para preencher uma planilha com os dados de um banco de dados  
  
1.  Abra um projeto de nível de documento do Excel no Visual Studio, com a planilha aberta no designer.  
  
2.  Abra o **fontes de dados** janela e criar uma fonte de dados para seu projeto. Para obter mais informações, consulte [adicionar novas conexões](../data-tools/add-new-connections.md).  
  
3.  Arraste o campo ou a tabela que você quer o **fontes de dados** janela à sua planilha.  
  
 Um dos seguintes controles é criado na planilha:  
  
-   Se você arrastar um campo, um <xref:Microsoft.Office.Tools.Excel.NamedRange> controle é criado na planilha. Para obter mais informações, consulte [controle NamedRange](../vsto/namedrange-control.md).  
  
-   Se você arrastar uma tabela, um <xref:Microsoft.Office.Tools.Excel.ListObject> controle é criado na planilha. Para obter mais informações, consulte [controle ListObject](../vsto/listobject-control.md).  
  
 Você pode adicionar um controle diferente, selecionando a tabela ou campo no **fontes de dados** janela e, em seguida, escolhendo um controle diferente na lista suspensa.  
  
## <a name="objects-in-the-project"></a>Objetos do projeto  
 Além de controle, os seguintes objetos de dados são automaticamente adicionados ao seu projeto:  
  
-   Um conjunto de dados tipado que encapsula as tabelas de dados que você se conectou no banco de dados. Para obter mais informações, consulte [ferramentas do conjunto de dados no Visual Studio](/visualstudio/data-tools/dataset-tools-in-visual-studio).  
  
-   Um <xref:System.Windows.Forms.BindingSource> que conecta o controle para o conjunto de dados tipado. Para obter mais informações, consulte [visão geral do componente BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-overview).  
  
-   Um TableAdapter que conecta o conjunto de dados tipado para o banco de dados. Para obter mais informações, consulte [visão geral de TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview).  
  
-   TableAdapterManager, que é usado para coordenar os adaptadores de tabelas do conjunto de dados para habilitar atualizações hierárquicas. Para obter mais informações, consulte [atualização hierárquica](../data-tools/hierarchical-update.md) e [TableAdapterManager Reference](../data-tools/fill-datasets-by-using-tableadapters.md#tableadaptermanager-reference).  
  
 Quando você executar o projeto, o controle exibe o primeiro registro na fonte de dados. Você pode usar o <xref:System.Windows.Forms.BindingSource> para permitir que os usuários percorrer os registros.  
  
#### <a name="to-scroll-through-the-records"></a>Para percorrer os registros  
  
-   Use <xref:System.Windows.Forms.BindingSource> métodos como <xref:System.Windows.Forms.BindingSource.MoveNext%2A> e <xref:System.Windows.Forms.BindingSource.MovePrevious%2A>.  
  
 Para obter informações sobre como enviar atualizações para o conjunto de dados tipado e o banco de dados, consulte [como: atualizar uma fonte de dados com dados de um controle de Host](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md).  
  
## <a name="see-also"></a>Consulte também  
 [Associando dados a controles em soluções do Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Adicionar novas fontes de dados](/visualstudio/data-tools/add-new-data-sources)   
 [Associar controles do Windows Forms a dados no Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Como: preencher documentos com dados de objetos](../vsto/how-to-populate-documents-with-data-from-objects.md)   
 [Como: preencher documentos com dados de um banco de dados](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [Como: preencher documentos com dados de serviços](../vsto/how-to-populate-documents-with-data-from-services.md)   
 [Como: atualizar uma fonte de dados com dados de um controle de Host](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [Como os i: transferir dados em uma planilha do Excel](http://go.microsoft.com/fwlink/?LinkID=130277)   
 [Como usar consumir os dados do banco de dados no Excel?](http://go.microsoft.com/fwlink/?LinkID=130287)  
  
  