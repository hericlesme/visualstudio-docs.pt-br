---
title: Itens de host e visão geral dos controles de host
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- host controls [Office development in Visual Studio], adding
- Office documents [Office development in Visual Studio, host controls
- host items [Office development in Visual Studio]
- application development [Office development in Visual Studio], host items
- Office applications [Office development in Visual Studio], host items
- host controls [Office development in Visual Studio], listed
- Excel [Office development in Visual Studio], host items
- host controls [Office Development in Visual Stuio], naming
- host controls [Office development in Visual Studio]
- host controls [Office development in Visual Studio], about host controls
- document-level customizations [Office development in Visual Studio], host controls
- Office applications [Office development in Visual Studio], host controls
- documents [Office development in Visual Studio], host controls
- controls [Office development in Visual Studio], host controls
- application development [Office development in Visual Studio], host controls
- Excel [Office development in Visual Studio], host controls
- host items [Office development in Visual Studio], about host items
- host items [Office development in Visual Studio], listed
- documents [Office development in Visual Studio], host items
- data binding [Office development in Visual Studio], host controls
- Office documents [Office development in Visual Studio, host items
- Word [Office development in Visual Studio], host items
- document-level customizations [Office development in Visual Studio], host items
- Word [Office development in Visual Studio], host controls
- host controls [Office development in Visual Studio], deleting
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: afc067e46f3cad5baa46bb5fef2381e82791dc76
ms.sourcegitcommit: 697162f54d3c4e30df702fd0289e447e211e3a85
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/25/2018
---
# <a name="host-items-and-host-controls-overview"></a>Itens de host e visão geral dos controles de host
  Itens de host e controles de host são tipos que ajudam a fornecer o modelo de programação para soluções do Office que são criadas usando as ferramentas de desenvolvimento do Office no Visual Studio. Itens de host e controles de host tornam interagir com os modelos de objeto do Microsoft Office Word e Microsoft Office Excel, que são baseados em COM, mais como interagir com os objetos gerenciados, como controles de formulários do Windows.  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
## <a name="host-items"></a>Itens de host  
 Itens de host são os tipos que estão na parte superior de hierarquias de modelos de objeto em projetos do Office. O [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] define os seguintes itens de host para soluções do Word e Excel:  
  
-   <xref:Microsoft.Office.Tools.Word.Document>  
  
-   <xref:Microsoft.Office.Tools.Excel.Workbook>  
  
-   <xref:Microsoft.Office.Tools.Excel.Worksheet>  
  
-   <xref:Microsoft.Office.Tools.Excel.ChartSheet>  
  
 Cada um desses tipos estende um objeto que existe nativamente no modelo de objeto do Word ou Excel, chamado um *objeto Office nativo*. Por exemplo, o <xref:Microsoft.Office.Tools.Word.Document> estende o item de host do <xref:Microsoft.Office.Interop.Word.Document> objeto, que é definido no assembly de interoperabilidade primário para o Word.  
  
 Itens de host geralmente têm a mesma funcionalidade de base como os objetos correspondentes do Office, mas são aprimorados com os seguintes recursos:  
  
-   A capacidade de hospedar controles gerenciados, incluindo controles de host e controles de formulários do Windows.  
  
-   Modelos de evento mais ricas. Alguns eventos de documento, a pasta de trabalho e a planilha em que os modelos de objeto do Word e Excel nativo são gerados somente no nível do aplicativo. Itens de host fornecem esses eventos no nível do documento, para que seja mais fácil manipular os eventos para um documento específico.  
  
### <a name="understand-host-items-in-document-level-projects"></a>Entender os itens de host no nível de documento  
 Em projetos de nível de documento, itens de host fornecem um ponto de entrada para o seu código e têm designers que o ajudam a desenvolver sua solução.  
  
 O <xref:Microsoft.Office.Tools.Word.Document> e <xref:Microsoft.Office.Tools.Excel.Worksheet> itens de host associou designers são a representação visual do documento ou planilha, como um designer de formulários do Windows. Você pode usar esse designer para modificar o conteúdo do documento ou planilha diretamente no Word ou Excel e arraste os controles na superfície de design. Para obter mais informações, consulte [item de host do documento](../vsto/document-host-item.md) e [item de host de planilha](../vsto/worksheet-host-item.md).  
  
 O <xref:Microsoft.Office.Tools.Excel.Workbook> item de host não agir como um contêiner para controles que têm uma interface do usuário. Em vez disso, o designer para este item de host funciona como uma bandeja de componente, que permite que você arrasta um componente, como um <xref:System.Data.DataSet>, para sua superfície de design. Para obter mais informações, consulte [item de host de pasta de trabalho](../vsto/workbook-host-item.md).  
  
 Itens de host não podem ser criados programaticamente projetos no nível de documento. Em vez disso, use o `ThisDocument`, `ThisWorkbook`, ou `Sheet` *n* classes que gera automaticamente em seu projeto do Visual Studio em tempo de design. Essas classes geradas derivam de itens de host, e eles fornecem um ponto de entrada para seu código. Para obter mais informações, consulte [limitações programáticas de itens de host e controles de host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).  
  
### <a name="understand-host-items-in-vsto-add-in-projects"></a>Entender os itens de host em projetos de suplemento do VSTO  
 Quando você criar um suplemento do VSTO, você não tem acesso a qualquer item de host por padrão. No entanto, você pode gerar <xref:Microsoft.Office.Tools.Word.Document>, <xref:Microsoft.Office.Tools.Excel.Workbook>, e <xref:Microsoft.Office.Tools.Excel.Worksheet> hospedar itens no Word e Excel VSTO Add-ins em tempo de execução.  
  
 Depois de gerar um item de host, você pode executar tarefas como adicionar controles a documentos. Para obter mais informações, consulte [documentos de estender o Word e pastas de trabalho do Excel no suplemento do VSTO em tempo de execução](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
## <a name="host-controls"></a>Controles de host  
 Controles de host estendem vários objetos de interface de usuário em modelos de objeto do Word e Excel, como `Microsoft.Office.Interop.Word.ContentControl` e <xref:Microsoft.Office.Interop.Excel.Range> objetos.  
  
 Os seguintes controles de host estão disponíveis para projetos do Excel:  
  
-   [Controle de gráfico](../vsto/chart-control.md)  
  
-   [Controle ListObject](../vsto/listobject-control.md)  
  
-   [Controle NamedRange](../vsto/namedrange-control.md)  
  
-   [Controle XmlMappedRange](../vsto/xmlmappedrange-control.md)  
  
 Os seguintes controles de host estão disponíveis para projetos do Word:  
  
-   [Controle indicador](../vsto/bookmark-control.md)  
  
-   [Controles de conteúdo](../vsto/content-controls.md)  
  
-   [Controle XMLNode](../vsto/xmlnode-control.md)  
  
-   [Controle XMLNodes](../vsto/xmlnodes-control.md)  
  
 Controles de host que são adicionados a documentos do Office se comportam como os objetos do Office nativo; No entanto, controles de host tem funcionalidade adicional, incluindo recursos de associação de dados e eventos. Por exemplo, quando quiser capturar os eventos de um nativo <xref:Microsoft.Office.Interop.Excel.Range> do objeto no Excel, primeiro você deve tratar o evento de alteração da planilha. Em seguida, você deve determinar se a alteração ocorreu dentro de <xref:Microsoft.Office.Interop.Excel.Range>. Em contraste, o <xref:Microsoft.Office.Tools.Excel.NamedRange> controle de host tem um <xref:Microsoft.Office.Tools.Excel.NamedRange.Change> eventos que você pode manipular diretamente.  
  
 A relação entre um item de host e controles de host é muito semelhante para a relação entre um controles de formulário do Windows e Windows Forms. Assim como você colocaria um controle de caixa de texto em um formulário do Windows, você coloca um <xref:Microsoft.Office.Tools.Excel.NamedRange> control em um <xref:Microsoft.Office.Tools.Excel.Worksheet> item de host. A ilustração a seguir mostra a relação entre itens de host e controles de host.  
  
 ![Relação entre itens de host e controles de host](../vsto/media/hostitemscontrols.png "relação entre itens de host e controles de host")  
  
 Você também pode usar controles de formulários do Windows em suas soluções do Office ao adicioná-los diretamente para a superfície de documento do Word e Excel. Para obter mais informações, consulte [controles do Windows Forms em Visão geral de documentos do Office](../vsto/windows-forms-controls-on-office-documents-overview.md).  
  
> [!NOTE]  
>  Não há suporte para a adição de controles de host ou controles de formulários do Windows de um subdocumento do Word.  
  
### <a name="add-host-controls-to-your-documents"></a>Adicionar controles de host para seus documentos  
 Em projetos de nível de documento, você pode adicionar controles de host para o documento do Word ou planilhas do Excel em tempo de design das seguintes maneiras:  
  
-   Adicionar controles de host para o documento em tempo de design da mesma maneira, você adicionaria um objeto nativo.  
  
-   Arraste os controles de host do **caixa de ferramentas** em seus documentos e planilhas. Controles de host do Excel estão disponíveis no **Excel controles** projetos do Excel e o host do Word controles estão disponíveis na guia o **controles do Word** guia em projetos do Word.  
  
-   Arraste os controles de host do **fontes de dados** window em seus documentos e planilhas. Isso permite que você adicione controles que já estão associados a dados. Para obter mais informações, consulte [ligar dados a controles em soluções do Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
 No nível de documento e projetos de suplemento do VSTO, você também pode adicionar alguns controles de host para documentos em tempo de execução. Para obter mais informações, consulte [adicionar controles a documentos do Office em tempo de execução](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 Para obter mais informações sobre como adicionar controles de host a documentos, consulte os tópicos a seguir:  
  
-   [Como: adicionar controles Chart a planilhas](../vsto/how-to-add-chart-controls-to-worksheets.md)  
  
-   [Como: adicionar controles ListObject a planilhas](../vsto/how-to-add-listobject-controls-to-worksheets.md)  
  
-   [Como: adicionar controles NamedRange a planilhas](../vsto/how-to-add-namedrange-controls-to-worksheets.md)  
  
-   [Como: adicionar controles XMLMappedRange a planilhas](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)  
  
-   [Como: adicionar controles de indicador a documentos do Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)  
  
-   [Como: adicionar conteúdo controles a documentos do Word](../vsto/how-to-add-content-controls-to-word-documents.md)  
  
-   [Como: adicionar controles XMLNode a documentos do Word](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)  
  
-   [Como: adicionar controles XMLNodes a documentos do Word](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)  
  
### <a name="name-host-controls"></a>Controles de host de nome  
 Quando você arrasta um controle de host do **caixa de ferramentas** ao documento, o controle é automaticamente nomeado usando o tipo de controle com um número incremental no final. Por exemplo, os indicadores são nomeados **bookmark1**, **bookmark2**, e assim por diante. Se você usar a funcionalidade nativa do Word ou Excel para adicionar o controle, você pode atribuir um nome específico no momento em que você criá-lo. Você também pode renomear os controles, alterando o valor da **nome** propriedade o **propriedades** janela.  
  
> [!NOTE]  
>  Você não pode usar palavras reservadas para controles de host do nome. Por exemplo, se você adicionar um <xref:Microsoft.Office.Tools.Excel.NamedRange> controlar para uma planilha e altere o nome para **sistema**, erros ocorrem quando você compilar o projeto.  
  
### <a name="delete-host-controls"></a>Excluir controles de host  
 Em projetos de nível de documento, você pode excluir hospedar controles em tempo de design selecionando o controle na planilha do Excel ou do documento do Word e pressionando o **excluir** chave. No entanto, você deve usar o **definir nome** caixa de diálogo no Excel para excluir <xref:Microsoft.Office.Tools.Excel.NamedRange> controles.  
  
 Se você adicionar um controle de host para um documento em tempo de design, não remova-o por meio de programação em tempo de execução porque na próxima vez que você tentar usar o controle de código, uma exceção será lançada. O `Delete` método de um controle de host remove somente os controles de host que serão adicionados ao documento em tempo de execução. Se você chamar o `Delete` método de um controle de host que foi criado no tempo de design, uma exceção será lançada.  
  
 Por exemplo, o <xref:Microsoft.Office.Tools.Excel.NamedRange.Delete%2A> método de um <xref:Microsoft.Office.Tools.Excel.NamedRange> exclui somente com êxito o <xref:Microsoft.Office.Tools.Excel.NamedRange> se ele foi adicionado programaticamente a planilha, que é conhecido como criar controles de host dinamicamente. Controles de host criado dinamicamente também podem ser removidos, passando o nome do controle para o `Remove` método o <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A> ou <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> propriedade. Para obter mais informações, consulte [adicionar controles a documentos do Office em tempo de execução](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 Se os usuários finais excluir um controle de host do documento em tempo de execução, a solução pode falhar de maneiras inesperadas. Você pode usar os recursos de proteção de documento do Word e Excel para proteger os controles de host que está sendo excluído. Para obter mais informações, consulte [amostras de desenvolvimento do Office e explicações passo a passo](../vsto/office-development-samples-and-walkthroughs.md).  
  
> [!NOTE]  
>  Não remover programaticamente controles durante o `Shutdown` manipulador de eventos do documento ou planilha. Os elementos de interface do usuário não estão mais disponíveis quando o `Shutdown` evento ocorre. Se você quiser remover controles antes do aplicativo for fechado, adicione seu código para outro manipulador de eventos, como `BeforeClose` ou `BeforeSave`.  
  
### <a name="program-against-host-control-events"></a>Programe em eventos de controle de host  
 É uma maneira que os controles de host estendem objetos do Office adicionando eventos. Por exemplo, o <xref:Microsoft.Office.Interop.Excel.Range> objeto no Excel e <xref:Microsoft.Office.Interop.Word.Bookmark> objeto no Word não tem eventos, mas o [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] estende esses objetos, adicionando eventos programáveis. Você pode acessar e código em relação a esses eventos a mesma forma que você acessar eventos de controles de formulários do Windows: através da lista suspensa de evento em Visual Basic e a página de propriedades de evento em c#. Para obter mais informações, consulte [passo a passo: Programe em eventos de um controle NamedRange](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md).  
  
> [!NOTE]  
>  Você não deve definir o <xref:Microsoft.Office.Interop.Excel._Application.EnableEvents%2A> propriedade o <xref:Microsoft.Office.Interop.Excel.Application> objeto no Excel para **false**. Definir essa propriedade como **false** impede que o Excel gerar todos os eventos, incluindo eventos de controles de host.  
  
## <a name="see-also"></a>Consulte também  
 [Limitações programáticas de itens de host e controles de host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Programa de suplementos do VSTO](../vsto/programming-vsto-add-ins.md)   
 [Programa personalizações no nível do documento](../vsto/programming-document-level-customizations.md)   
 [Automatizar o Word usando objetos estendidos](../vsto/automating-word-by-using-extended-objects.md)   
 [Automatizar o Excel usando objetos estendidos](../vsto/automating-excel-by-using-extended-objects.md)   
 [Controles em documentos do Office](../vsto/controls-on-office-documents.md)   
 [Associar dados a controles em soluções do Office](../vsto/binding-data-to-controls-in-office-solutions.md)  
  