---
title: Visão geral do modelo de objeto do Excel | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Worksheet object
- Range object
- object models [Office development in Visual Studio], Excel
- object models [Office development in Visual Studio], Office
- Workbook class
- objects [Office development in Visual Studio], Office object models
- Excel object model
- Office object models
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6b700d3834cf432ff9af2ec17e1daa3011763cac
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="excel-object-model-overview"></a>Visão geral do modelo de objeto do Excel
  Para desenvolver soluções que usam o Microsoft Office Excel, você pode interagir com os objetos fornecidos pelo modelo de objeto do Excel. Este tópico apresenta os objetos mais importantes:  
  
-   <xref:Microsoft.Office.Interop.Excel.Application>  
  
-   <xref:Microsoft.Office.Interop.Excel.Workbook>  
  
-   <xref:Microsoft.Office.Interop.Excel.Worksheet>  
  
-   <xref:Microsoft.Office.Interop.Excel.Range>  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 O modelo de objeto segue rigorosamente a interface do usuário. O <xref:Microsoft.Office.Interop.Excel.Application> objeto representa o aplicativo inteiro e cada <xref:Microsoft.Office.Interop.Excel.Workbook> objeto contém uma coleção de `Worksheet` objetos. A partir daí, é a abstração principal que representa as células de <xref:Microsoft.Office.Interop.Excel.Range> objeto, que permite que você trabalhe com células individuais ou grupos de células.  
  
 Além do modelo de objeto do Excel, os projetos do Office no Visual Studio fornecem *itens de host* e *hospedar controles* que estende alguns objetos no modelo de objeto do Excel. Itens de host e controles de host se comportam como os objetos do Excel, eles estendem, mas eles também têm funcionalidade adicional, como recursos de associação de dados e eventos extras. Para obter mais informações, consulte [automatizando o Excel usando objetos estendidos](../vsto/automating-excel-by-using-extended-objects.md) e [itens de Host e visão geral dos controles de Host](../vsto/host-items-and-host-controls-overview.md).  
  
 Este tópico fornece uma visão geral sobre o modelo de objeto do Excel. Para obter recursos onde você pode aprender mais sobre todo o modelo de objeto do Excel, consulte [usando a documentação do modelo de objeto do Excel](#ExcelOMDocumentation).  
  
 ![link para vídeo](../vsto/media/playvideo.gif "link para vídeo") para uma demonstração de vídeo relacionada, consulte [como fazer i: usar manipuladores de eventos em um Excel 2007 suplemento?](http://go.microsoft.com/fwlink/?LinkID=130291), e [como fazer i: Use formas para criar um gráfico de bolhas no Excel? ](http://go.microsoft.com/fwlink/?LinkID=130313).  
  
## <a name="accessing-objects-in-an-excel-project"></a>Acessando objetos em um projeto do Excel  
 Quando você cria um novo projeto de suplemento do VSTO para Excel, o Visual Studio cria automaticamente um arquivo de código ThisAddIn ou ThisAddIn.cs. Você pode acessar o objeto do aplicativo usando `Me.Application` ou `this.Application`.  
  
 Quando você cria um novo projeto de nível de documento para Excel, você tem a opção de criar um novo projeto de modelo do Excel ou de pasta de trabalho do Excel. Visual Studio cria automaticamente os arquivos de código a seguir no seu novo projeto do Excel para projetos da pasta de trabalho e o modelo.  
  
|Visual Basic|C#|  
|------------------|---------|  
|ThisWorkbook|ThisWorkbook.cs|  
|Sheet1.vb|Sheet1.cs|  
|Sheet2.vb|Sheet2.cs|  
|Sheet3.vb|Sheet3.cs|  
  
 Você pode usar o `Globals` classe em seu projeto para acessar `ThisWorkbook`, `Sheet1`, `Sheet2`, ou `Sheet3` de fora da respectiva classe. Para obter mais informações, consulte [acesso Global a objetos em projetos do Office](../vsto/global-access-to-objects-in-office-projects.md). A exemplo a seguir chama o <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A> método `Sheet1` independentemente se o código é colocado em um do `Sheet` *n* classes ou `ThisWorkbook` classe.  
  
 [!code-csharp[Trin_VstcoreExcelAutomation#82](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#82)]
 [!code-vb[Trin_VstcoreExcelAutomation#82](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#82)]  
  
 Como os dados em um documento do Excel estiverem altamente estruturados, o modelo de objeto é hierárquica e direto. O Excel fornece centenas de objetos com o qual deseja interagir, mas você pode obter um bom começo no modelo de objeto, concentrando-se em um subconjunto muito pequeno de objetos disponíveis. Esses objetos incluem os seguintes quatro:  
  
-   Aplicativo  
  
-   Pastas de trabalho  
  
-   Planilha  
  
-   Intervalo  
  
 A maioria do trabalho feito com o Excel gira em torno de quatro esses objetos e seus membros.  
  
### <a name="application-object"></a>Objeto de aplicativo  
 O Excel <xref:Microsoft.Office.Interop.Excel.Application> objeto representa o aplicativo do Excel. O <xref:Microsoft.Office.Interop.Excel.Application> objeto expõe uma grande quantidade de informações sobre o aplicativo em execução, as opções aplicadas a essa instância, e os objetos do usuário atual abra dentro da instância.  
  
> [!NOTE]  
>  Você não deve definir o <xref:Microsoft.Office.Interop.Excel.ApplicationClass.EnableEvents%2A> propriedade o <xref:Microsoft.Office.Interop.Excel.Application> objeto no Excel para **false**. Definir essa propriedade como false impede que o Excel gerar todos os eventos, incluindo eventos de controles de host.  
  
### <a name="workbook-object"></a>Objeto de pasta de trabalho  
 O <xref:Microsoft.Office.Interop.Excel.Workbook> objeto representa uma única pasta de trabalho dentro do aplicativo Excel.  
  
 As ferramentas de desenvolvimento do Office no Visual Studio estende o <xref:Microsoft.Office.Interop.Excel.Workbook> objeto fornecendo o <xref:Microsoft.Office.Tools.Excel.Workbook> tipo. Esse tipo oferece acesso a todos os recursos de um <xref:Microsoft.Office.Interop.Excel.Workbook> objeto. Para obter mais informações, consulte [Item de Host de pasta de trabalho](../vsto/workbook-host-item.md).  
  
### <a name="worksheet-object"></a>Objeto de planilha  
 O <xref:Microsoft.Office.Interop.Excel.Worksheet> objeto é um membro do <xref:Microsoft.Office.Interop.Excel.Worksheets> coleção. Muitas das propriedades, métodos e eventos do <xref:Microsoft.Office.Interop.Excel.Worksheet> são idênticos ou semelhantes aos membros fornecidos pelo <xref:Microsoft.Office.Interop.Excel.Application> ou <xref:Microsoft.Office.Interop.Excel.Workbook> objetos.  
  
 O Excel fornece um <xref:Microsoft.Office.Interop.Excel.Sheets> coleção como uma propriedade de um <xref:Microsoft.Office.Interop.Excel.Workbook> objeto. Cada membro do <xref:Microsoft.Office.Interop.Excel.Sheets> coleção é um <xref:Microsoft.Office.Interop.Excel.Worksheet> ou um <xref:Microsoft.Office.Interop.Excel.Chart> objeto.  
  
 As ferramentas de desenvolvimento do Office no Visual Studio estendem o <xref:Microsoft.Office.Interop.Excel.Worksheet> objeto fornecendo o <xref:Microsoft.Office.Tools.Excel.Worksheet> tipo. Esse tipo oferece acesso a todos os recursos de um <xref:Microsoft.Office.Interop.Excel.Worksheet> objeto, bem como novos recursos, como a capacidade de hospedar controles gerenciados e tratar eventos de novo. Para obter mais informações, consulte [Item de Host de planilha](../vsto/worksheet-host-item.md).  
  
### <a name="range-object"></a>Objeto de intervalo  
 O <xref:Microsoft.Office.Interop.Excel.Range> é o objeto que você usará mais em seus aplicativos do Excel. Antes de você pode manipular qualquer região dentro do Excel, você deve express-lo como um <xref:Microsoft.Office.Interop.Excel.Range> do objeto e trabalhar com métodos e propriedades do intervalo. Um <xref:Microsoft.Office.Interop.Excel.Range> objeto representa uma célula, uma linha, uma coluna, uma seleção de células que contém um ou mais blocos de células, o que podem pode não ser contíguas ou até mesmo um grupo de células em várias planilhas.  
  
 O Visual Studio estende o <xref:Microsoft.Office.Interop.Excel.Range> objeto fornecendo o <xref:Microsoft.Office.Tools.Excel.NamedRange> e <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> tipos. Esses tipos tem a maioria dos mesmos recursos que um <xref:Microsoft.Office.Interop.Excel.Range> objeto, bem como novos recursos, como a capacidade de associação de dados e os novos eventos. Para obter mais informações, consulte [controle NamedRange](../vsto/namedrange-control.md) e [controle XmlMappedRange](../vsto/xmlmappedrange-control.md).  
  
##  <a name="ExcelOMDocumentation"></a> Usando a documentação do modelo de objeto do Excel  
 Para obter informações completas sobre o modelo de objeto do Excel, você pode consultar para a referência de assembly de interoperabilidade primária (PIA) do Excel e a referência de modelo de objeto VBA.  
  
### <a name="primary-interop-assembly-reference"></a>Referência de Assembly de interoperabilidade primária  
 A documentação de referência do Excel PIA descreve os tipos no assembly de interoperabilidade primário para o Excel. Esta documentação está disponível no seguinte local: [referência de Assembly de interoperabilidade do Excel 2010 primário](http://go.microsoft.com/fwlink/?LinkId=189585).  
  
 Para obter mais informações sobre o design de PIA do Excel, como as diferenças entre classes e interfaces no PIA e como os eventos em que o PIA são implementados, consulte [visão geral de Classes e Interfaces de Assemblies de interoperabilidade primários do Office](http://go.microsoft.com/fwlink/?LinkId=189592).  
  
### <a name="vba-object-model-reference"></a>Referência de modelo de objeto do VBA  
 A referência de modelo de objeto VBA documenta o modelo de objeto do Excel como ele é exposto para o Visual Basic para código Applications (VBA). Para obter mais informações, consulte [referência de modelo de objeto do Excel 2010](http://go.microsoft.com/fwlink/?LinkId=199768).  
  
 Todos os objetos e membros na referência de modelo de objeto do VBA correspondem aos tipos e membros no Excel PIA. Por exemplo, o objeto de planilha na referência de modelo de objeto do VBA corresponde do <xref:Microsoft.Office.Interop.Excel.Worksheet> objeto no Excel PIA. Embora a referência de modelo de objeto VBA fornece exemplos de código para a maioria das propriedades, métodos e eventos, você deve converter o código VBA essa referência ao Visual Basic ou Visual c#, se você quiser usá-los em um projeto do Excel que você cria usando o Visual Studio.  
  
### <a name="related-topics"></a>Tópicos relacionados  
  
|Título|Descrição|  
|-----------|-----------------|  
|[Soluções do Excel](../vsto/excel-solutions.md)|Explica como você pode criar personalizações no nível do documento e suplementos do VSTO para o Microsoft Office Excel.|  
|[Trabalhando com intervalos](../vsto/working-with-ranges.md)|Fornece exemplos que mostram como executar tarefas comuns com intervalos.|  
|[Trabalhando com planilhas](../vsto/working-with-worksheets.md)|Fornece exemplos que mostram como executar tarefas comuns com planilhas.|  
|[Trabalhando com pastas de trabalho](../vsto/working-with-workbooks.md)|Fornece exemplos que mostram como executar tarefas comuns com pastas de trabalho.|  
  
  