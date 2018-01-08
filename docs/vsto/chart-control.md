---
title: "Controle de gráfico | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VST.ProjectItem.ExcelChart
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Chart control [Office development in Visual Studio], events
- Chart control [Office development in Visual Studio]
- Chart control [Office development in Visual Studio], data binding
ms.assetid: 64f1a7cc-cc66-47da-aaeb-44a62ae53909
caps.latest.revision: "51"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: fc5dfd4916383af8b69c14a87805e965ea855d23
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="chart-control"></a>Controle Chart
  O <xref:Microsoft.Office.Tools.Excel.Chart> controle é um objeto de gráfico que expõe eventos. Quando você adiciona um gráfico em uma planilha, o Visual Studio cria um <xref:Microsoft.Office.Tools.Excel.Chart> do objeto que você pode programar diretamente sem a necessidade de desviar o modelo de objeto do Microsoft Office Excel.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="creating-the-control"></a>Criando o controle  
 Você pode adicionar <xref:Microsoft.Office.Tools.Excel.Chart> controles a uma planilha do Excel do Microsoft Office em tempo de design ou em tempo de execução em um projeto no nível do documento.  
  
 Você pode adicionar <xref:Microsoft.Office.Tools.Excel.Chart> controles a uma planilha em tempo de execução em um suplemento do VSTO. Para obter mais informações, consulte [como: adicionar controles de gráfico para planilhas](../vsto/how-to-add-chart-controls-to-worksheets.md).  
  
> [!NOTE]  
>  Objetos de gráfico criado dinamicamente não são mantidos na planilha como hospedar controles quando a planilha está fechada. Para obter mais informações, consulte [adicionando controles a documentos do Office em tempo de execução](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
## <a name="formatting"></a>Formatação  
 Toda a formatação que pode ser aplicado a um <xref:Microsoft.Office.Interop.Excel.Chart> também podem ser aplicadas a um <xref:Microsoft.Office.Tools.Excel.Chart> controle. Isso inclui as bordas, fontes, tipo de gráfico, as linhas de grade, legenda e rótulos de dados.  
  
## <a name="events"></a>Eventos  
 Os seguintes eventos estão disponíveis para o <xref:Microsoft.Office.Tools.Excel.Chart> controle:  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.ActivateEvent>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.BeforeDoubleClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.BeforeRightClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.BindingContextChanged>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.Calculate>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.Deactivate>  
  
-   <xref:System.ComponentModel.Component.Disposed>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.DragOver>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.DragPlot>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.MouseDown>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.MouseMove>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.MouseUp>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.Resize>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.SelectEvent>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.SeriesChange>  
  
## <a name="see-also"></a>Consulte também  
 [Explicações passo a passo e exemplos de desenvolvimento do office](../vsto/office-development-samples-and-walkthroughs.md)   
 [Estendendo documentos do Word e pastas de trabalho do Excel em suplementos do VSTO em tempo de execução](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Controles em documentos do Office](../vsto/controls-on-office-documents.md)   
 [Adicionando controles a documentos do Office em tempo de execução](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Automatizando o Excel usando objetos estendidos](../vsto/automating-excel-by-using-extended-objects.md)   
 [Como: adicionar controles Chart a planilhas](../vsto/how-to-add-chart-controls-to-worksheets.md)   
 [Associando dados a controles em soluções do Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Limitações programáticas de itens de Host e Controles de Host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  