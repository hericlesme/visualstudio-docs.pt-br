---
title: 'Como: preencher documentos com dados de um banco de dados | Microsoft Docs'
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
- documents, populating with data
- data, adding to documents
ms.assetid: 1eb5b13d-7359-407e-8be8-e42c1829f10c
caps.latest.revision: "48"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e528bb0ef732400639f8604cf471d7f54a89ae73
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-populate-documents-with-data-from-a-database"></a>Como preencher documentos com dados de um banco de dados
  Você pode acessar dados em nível de documento do Microsoft Office da mesma maneira que você acessar dados em projetos de formulários do Windows. Use as mesmas ferramentas e código para trazer os dados de um banco de dados para sua solução, e você pode usar controles de formulários do Windows para exibir os dados.  
  
 Além disso, você pode exibir dados usando controles de host. Controles de host são objetos nativo no Microsoft Office Word que foram aprimorados com eventos e a capacidade de associação de dados. Para obter mais informações, consulte [itens de Host e visão geral dos controles de Host](../vsto/host-items-and-host-controls-overview.md).  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 O exemplo a seguir mostra como adicionar controles associados a dados em projetos de nível de documento usando um designer. Para obter um exemplo de como adicionar controles associados a dados em projetos de suplemento do VSTO em tempo de execução, consulte [passo a passo: associação de dados simples no VSTO suplemento projeto](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md).  
  
 ![link para vídeo](../vsto/media/playvideo.gif "link para vídeo") para uma demonstração de vídeo relacionada, consulte [vinculação de dados para o Word 2007 conteúdo controles usando Visual Studio Tools para o Office System (3.0)](http://go.microsoft.com/fwlink/?LinkId=136785).  
  
## <a name="adding-a-control-to-a-document-at-design-time"></a>Adicionando um controle a um documento em tempo de Design  
  
#### <a name="to-populate-a-document-with-data-from-a-database"></a>Para popular um documento com dados de um banco de dados  
  
1.  Abrir um projeto de nível de documento do Word no [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], com o documento aberto no designer.  
  
2.  Abra o **fontes de dados** janela e criar uma fonte de dados de um banco de dados. Para obter mais informações, consulte [adicionar novas conexões](../data-tools/add-new-connections.md).  
  
3.  Arraste o campo desejado a **fontes de dados** janela para o documento.  
  
 Um controle de conteúdo é adicionado ao documento. O tipo de controle de conteúdo depende do tipo de dados do campo selecionado. Para obter mais informações, consulte [controles de conteúdo](../vsto/content-controls.md).  
  
 Você pode adicionar um controle diferente selecionando o campo de dados de **fontes de dados** janela e, em seguida, escolhendo um controle diferente na lista suspensa.  
  
## <a name="objects-in-the-project"></a>Objetos do projeto  
 Além de controle, os seguintes objetos de dados são automaticamente adicionados ao seu projeto:  
  
-   Um conjunto de dados tipado que encapsula as tabelas de dados que você se conectou no banco de dados. Para obter mais informações, consulte [ferramentas do conjunto de dados no Visual Studio](/visualstudio/data-tools/dataset-tools-in-visual-studio).  
  
-   Um <xref:System.Windows.Forms.BindingSource> que conecta o controle para o conjunto de dados tipado. Para obter mais informações, consulte [visão geral do componente BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-overview).  
  
-   Um TableAdapter que conecta o conjunto de dados tipado para o banco de dados. Para obter mais informações, consulte [criar e configurar TableAdapters](../data-tools/create-and-configure-tableadapters.md).  
  
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
 [Como: atualizar uma fonte de dados com dados de um controle de Host](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [Usando arquivos de banco de dados Local na visão geral das soluções do Office](../vsto/using-local-database-files-in-office-solutions-overview.md)   
 [Conectando a dados em aplicativos do Windows Forms](/visualstudio/data-tools/connecting-to-data-in-windows-forms-applications)   
 [Visão geral do componente BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-overview)  
  
  