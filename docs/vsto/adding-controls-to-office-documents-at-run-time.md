---
title: Adicionar controles a documentos do Office em tempo de execução
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office documents [Office development in Visual Studio, Windows Forms controls
- host controls [Office development in Visual Studio], adding
- Windows Forms controls [Office development in Visual Studio], adding
- Office documents [Office development in Visual Studio, host controls
- user controls [Office development in Visual Studio], adding at runtime
- documents [Office development in Visual Studio], Windows Forms controls
- document-level customizations [Office development in Visual Studio], host controls
- documents [Office development in Visual Studio], host controls
- document-level customizations [Office development in Visual Studio], Windows Forms controls
- controls [Office development in Visual Studio], adding at runtime
- helper methods [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: af280d407a8453b66658ee5395a88d2b91b991b7
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
---
# <a name="add-controls-to-office-documents-at-runtime"></a>Adicionar controles a documentos do Office em tempo de execução
  Você pode adicionar controles a um documento do Microsoft Office Word e do Microsoft Office Excel em tempo de execução. Você também pode removê-los em tempo de execução. Controles que você adicionar ou remover em tempo de execução são chamados *controles dinâmicos*.  

 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  

 Este tópico descreve o seguinte:  

-   [Gerenciar controles em tempo de execução usando coleções de controle](#ControlsCollection).  

-   [Adicionar controles de host para documentos](#HostControls).  

-   [Adicionar controles de Windows Forms a documentos](#WindowsForms).  

 ![link para vídeo](../vsto/media/playvideo.gif "link para vídeo") para uma demonstração de vídeo relacionada, consulte [como i: adicionar controles a um documento se superfície em tempo de execução?](http://go.microsoft.com/fwlink/?LinkId=132782).  

##  <a name="ControlsCollection"></a> Gerenciar controles em tempo de execução usando coleções de controle  
 Para adicionar, obter ou remova os controles em tempo de execução, use métodos auxiliares de <xref:Microsoft.Office.Tools.Excel.ControlCollection> e <xref:Microsoft.Office.Tools.Word.ControlCollection> objetos.  

 A maneira que você acessar esses objetos depende do tipo de projeto que você está desenvolvendo:  

-   Em um projeto de nível de documento para Excel, use o <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A> propriedade o `Sheet1`, `Sheet2`, e `Sheet3` classes. Para obter mais informações sobre essas classes, consulte [item de host de planilha](../vsto/worksheet-host-item.md).  

-   Em um projeto de nível de documento para Word, use o <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> propriedade o `ThisDocument` classe. Para obter mais informações sobre essa classe, consulte [item de host do documento](../vsto/document-host-item.md).  

-   Em um projeto do suplemento do VSTO para Excel ou Word, use o `Controls` propriedade de um <xref:Microsoft.Office.Tools.Excel.Worksheet> ou <xref:Microsoft.Office.Tools.Word.Document> que geram em tempo de execução. Para obter mais informações sobre como gerar esses objetos em tempo de execução, consulte [documentos de estender o Word e pastas de trabalho do Excel no suplemento do VSTO em tempo de execução](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  

### <a name="add-controls"></a>Adicionar controles  
 O <xref:Microsoft.Office.Tools.Excel.ControlCollection> e <xref:Microsoft.Office.Tools.Word.ControlCollection> tipos incluem métodos auxiliares que você pode usar para adicionar controles de host e controles comuns do Windows Forms a documentos e planilhas. Cada nome de método tem o formato `Add` *classe de controle*, onde *classe de controle* é o nome da classe do controle que você deseja adicionar. Por exemplo, para adicionar um <xref:Microsoft.Office.Tools.Excel.NamedRange> controle ao documento, use o <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddNamedRange%2A> método.  

 O exemplo de código a seguir adiciona uma <xref:Microsoft.Office.Tools.Excel.NamedRange> para `Sheet1` em um projeto de nível de documento para Excel.  

 [!code-vb[Trin_ExcelWorkbookDynamicControls#3](../vsto/codesnippet/VisualBasic/trin_excelworkbookdynamiccontrols4/ThisWorkbook.vb#3)]
 [!code-csharp[Trin_ExcelWorkbookDynamicControls#3](../vsto/codesnippet/CSharp/trin_excelworkbookdynamiccontrols4/ThisWorkbook.cs#3)]  

### <a name="access-and-delete-controls"></a>Controles de acesso e delete  
 Você pode usar o `Controls` propriedade de um <xref:Microsoft.Office.Tools.Excel.Worksheet> ou <xref:Microsoft.Office.Tools.Word.Document> para iterar por todos os controles no documento, incluindo controles adicionados em tempo de design. Também são chamados de controles que você adicionar em tempo de design *controles estáticos*.  

 Você pode remover controles dinâmicos, chamando o `Delete` método do controle, ou chamando o `Remove` método de cada coleção de controles. O seguinte exemplo de código usa o <xref:Microsoft.Office.Tools.Excel.ControlCollection.Remove%2A> método para remover um <xref:Microsoft.Office.Tools.Excel.NamedRange> de `Sheet1` em um projeto de nível de documento para Excel.  

 [!code-vb[Trin_ExcelWorkbookDynamicControls#4](../vsto/codesnippet/VisualBasic/trin_excelworkbookdynamiccontrols4/ThisWorkbook.vb#4)]
 [!code-csharp[Trin_ExcelWorkbookDynamicControls#4](../vsto/codesnippet/CSharp/trin_excelworkbookdynamiccontrols4/ThisWorkbook.cs#4)]  

 Não é possível remover controles estáticos em tempo de execução. Se você tentar usar o `Delete` ou `Remove` método para remover um controle estático, um <xref:Microsoft.Office.Tools.CannotRemoveControlException> será lançada.  

> [!NOTE]  
>  Não remover programaticamente os controles no `Shutdown` manipulador de eventos do documento. Os elementos de interface do usuário do documento não estão mais disponíveis quando o `Shutdown` é gerado. Se você quiser remover controles antes de fecha o documento, adicione seu código para o manipulador de eventos para um outro evento, como <xref:Microsoft.Office.Tools.Word.Document.BeforeClose> ou <xref:Microsoft.Office.Tools.Word.Document.BeforeSave> para Word, ou <xref:Microsoft.Office.Tools.Excel.Workbook.BeforeClose>, ou <xref:Microsoft.Office.Tools.Excel.Workbook.BeforeSave> para Excel.  

##  <a name="HostControls"></a> Adicionar controles de host a documentos  
 Quando você adicionar controles de host a documentos programaticamente, você deve fornecer um nome que identifica exclusivamente o controle, e você deve especificar onde adicionar o controle no documento. Para obter instruções específicas, consulte os tópicos a seguir:  

-   [Como: adicionar controles ListObject a planilhas](../vsto/how-to-add-listobject-controls-to-worksheets.md)  

-   [Como: adicionar controles NamedRange a planilhas](../vsto/how-to-add-namedrange-controls-to-worksheets.md)  

-   [Como: adicionar controles Chart a planilhas](../vsto/how-to-add-chart-controls-to-worksheets.md)  

-   [Como: adicionar conteúdo controles a documentos do Word](../vsto/how-to-add-content-controls-to-word-documents.md)  

-   [Como: adicionar controles de indicador a documentos do Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)  

 Para obter mais informações sobre controles de host, consulte [itens de Host e visão geral dos controles de host](../vsto/host-items-and-host-controls-overview.md).  

 Quando um documento é salvo e, em seguida, fechado, todos os controles de host criado dinamicamente forem desconectados de seus eventos e percam sua funcionalidade de associação de dados. Você pode adicionar código à sua solução para recriar os controles de host quando o documento for aberto novamente. Para obter mais informações, consulte [manter controles dinâmicos em documentos do Office](../vsto/persisting-dynamic-controls-in-office-documents.md).  

> [!NOTE]  
>  Métodos auxiliares não são fornecidos para o seguinte host controles, porque esses controles não podem ser adicionados por meio de programação para documentos: <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>, <xref:Microsoft.Office.Tools.Word.XMLNode>, e <xref:Microsoft.Office.Tools.Word.XMLNodes>.  

##  <a name="WindowsForms"></a> Adicionar controles de Windows Forms a documentos  
 Quando você adiciona um controle Windows Forms a um documento programaticamente, você deve fornecer o local do controle e um nome que identifica exclusivamente o controle. O [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] fornece métodos auxiliares para cada controle. Esses métodos estão sobrecarregados para que você pode passar um intervalo ou coordenadas específicas para o local do controle.  

 Quando um documento é salvo e, em seguida, fechado, todos os controles de formulários do Windows criados dinamicamente são removidos do documento. Você pode adicionar código à sua solução para recriar os controles quando o documento for aberto novamente. Se você criar controles de formulários do Windows dinâmicos usando um suplemento do VSTO, os wrappers de ActiveX para os controles são deixados no documento. Para obter mais informações, consulte [manter controles dinâmicos em documentos do Office](../vsto/persisting-dynamic-controls-in-office-documents.md).  

> [!NOTE]  
>  Controles de formulários do Windows não podem ser adicionados por meio de programação para documentos protegidos. Se você programaticamente desproteger um documento do Word ou planilha do Excel para adicionar um controle, você deve escrever código adicional para remover o wrapper do ActiveX do controle quando o documento é fechado. Wrapper do ActiveX do controle não é excluído automaticamente de documentos protegidos.  

### <a name="add-custom-controls"></a>Adicionar controles personalizados  
 Se você deseja adicionar um <xref:System.Windows.Forms.Control> que não é suportada pelos métodos auxiliares disponíveis, como um controle de usuário personalizada, use os seguintes métodos:  

-   Para o Excel, use um do <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddControl%2A> métodos de um <xref:Microsoft.Office.Tools.Excel.ControlCollection> objeto.  

-   Para o Word, use um do <xref:Microsoft.Office.Tools.Word.ControlCollection.AddControl%2A> métodos de um <xref:Microsoft.Office.Tools.Word.ControlCollection> objeto.  

 Para adicionar o controle, passar o <xref:System.Windows.Forms.Control>, um local para o controle e um nome que identifica exclusivamente o controle para o `AddControl` método. O `AddControl` método retorna um objeto que define como o controle interage com a planilha ou o documento. O `AddControl` método retorna um <xref:Microsoft.Office.Tools.Excel.ControlSite> (para Excel) ou um <xref:Microsoft.Office.Tools.Word.ControlSite> objeto (para o Word).  

 O exemplo de código a seguir demonstra como usar o <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddControl%2A> método adicionar dinamicamente um controle de usuário personalizada para uma planilha em um projeto do nível de documento do Excel. Neste exemplo, o controle de usuário é chamado `UserControl1`e o <xref:Microsoft.Office.Interop.Excel.Range> chamado `range1`. Para usar este exemplo, execute-o de um `Sheet` *n* classe no projeto.  

 [!code-vb[Trin_VstcoreProgrammingControlsExcel#2](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#2)]
 [!code-csharp[Trin_VstcoreProgrammingControlsExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#2)]  

### <a name="use-members-of-custom-controls"></a>Use os membros de controles personalizados  
 Depois de usar uma da `AddControl` métodos para adicionar um controle a uma planilha ou um documento, você agora tem dois objetos de controle diferentes:  

-   O <xref:System.Windows.Forms.Control> que representa o controle personalizado.  

-   O `ControlSite`, `OLEObject`, ou `OLEControl` objeto que representa o controle depois que ele foi adicionado para a planilha ou o documento.  

 Muitas propriedades e métodos são compartilhados entre esses controles. É importante que você acesse esses membros por meio do controle apropriado:  

-   Para acessar os membros que pertencem somente para o controle personalizado, use o <xref:System.Windows.Forms.Control>.  

-   Para acessar os membros que são compartilhados pelos controles, use o `ControlSite`, `OLEObject`, ou `OLEControl` objeto.  

 Se você acessar um membro compartilhado o <xref:System.Windows.Forms.Control>, pode falhar sem aviso ou de notificação ou ele pode produzir resultados inválidos. Sempre use métodos ou propriedades do `ControlSite`, `OLEObject`, ou `OLEControl` objeto, a menos que o método ou propriedade necessária não está disponível; só então deve você referência a <xref:System.Windows.Forms.Control>.  

 Por exemplo, o <xref:Microsoft.Office.Tools.Excel.ControlSite> classe e o <xref:System.Windows.Forms.Control> classe tiver um `Top` propriedade. Para obter ou definir a distância entre a parte superior do controle e o início do documento, use o <xref:Microsoft.Office.Tools.Excel.ControlSite.Top%2A> propriedade o <xref:Microsoft.Office.Tools.Excel.ControlSite>, não o <xref:System.Windows.Forms.Control.Top%2A> propriedade do <xref:System.Windows.Forms.Control>.  

 [!code-vb[Trin_VstcoreProgrammingControlsExcel#3](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#3)]
 [!code-csharp[Trin_VstcoreProgrammingControlsExcel#3](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#3)]  

## <a name="see-also"></a>Consulte também  
 [Controles em documentos do Office](../vsto/controls-on-office-documents.md)   
 [Manter controles dinâmicos em documentos do Office](../vsto/persisting-dynamic-controls-in-office-documents.md)   
 [Como: adicionar controles ListObject a planilhas](../vsto/how-to-add-listobject-controls-to-worksheets.md)   
 [Como: adicionar controles NamedRange a planilhas](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Como: adicionar controles Chart a planilhas](../vsto/how-to-add-chart-controls-to-worksheets.md)   
 [Como: adicionar controles content a documentos do Word](../vsto/how-to-add-content-controls-to-word-documents.md)   
 [Como: adicionar controles de indicador a documentos do Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)   
 [Controles de formulários do Windows na visão geral de documentos do Office](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Como: adicionar controles de Windows Forms a documentos do Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
