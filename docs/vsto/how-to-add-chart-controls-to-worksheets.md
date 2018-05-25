---
title: 'Como: adicionar controles Chart a planilhas'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Chart control [Office development in Visual Studio], adding to worksheets
- controls [Office development in Visual Studio], adding to worksheets
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 05fc2cafda3ed4aa0ff7756062c1cec0429ebc96
ms.sourcegitcommit: 697162f54d3c4e30df702fd0289e447e211e3a85
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/25/2018
---
# <a name="how-to-add-chart-controls-to-worksheets"></a>Como: adicionar controles Chart a planilhas
  Você pode adicionar <xref:Microsoft.Office.Tools.Excel.Chart> controles a uma planilha do Excel do Microsoft Office em tempo de design e em tempo de execução em personalizações no nível do documento. Você também pode adicionar <xref:Microsoft.Office.Tools.Excel.Chart> controles em tempo de execução em suplementos do VSTO.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Este tópico descreve as seguintes tarefas:  
  
-   [Adicionar controles de gráfico em tempo de design](#designtime)  
  
-   [Adicionar controles de gráfico em tempo de execução em um projeto no nível de documento](#runtimedoclevel)  
  
-   [Adicionar controles de gráfico em tempo de execução em um projeto de suplemento do VSTO](#runtimeaddin)  
  
 Para obter mais informações sobre <xref:Microsoft.Office.Tools.Excel.Chart> controles, consulte [controle gráfico](../vsto/chart-control.md).  
  
##  <a name="designtime"></a> Adicionar controles de gráfico em tempo de design  
 Você pode adicionar o <xref:Microsoft.Office.Tools.Excel.Chart> controle à sua planilha da mesma maneira que você adicionará um gráfico de dentro do aplicativo.  
  
> [!NOTE]  
>  O <xref:Microsoft.Office.Tools.Excel.Chart> controle não está disponível a **caixa de ferramentas** ou **fontes de dados** janela.  
  
### <a name="to-add-a-chart-host-control-to-a-worksheet-in-excel"></a>Para adicionar um controle de host do gráfico para uma planilha do Excel  
  
1.  No **inserir** guia o **gráficos** de grupo, clique em **coluna**, clique em uma categoria de gráficos e, em seguida, clique no tipo de gráfico desejado.  
  
2.  No **Inserir gráfico** caixa de diálogo, clique em **Okey**.  
  
3.  No **Design** guia o **dados** de grupo, clique em **selecionar dados**.  
  
4.  No **Selecionar fonte de dados** clique na caixa de diálogo de **gráfico** **intervalo de dados** caixa e desmarque qualquer seleção padrão.  
  
5.  No **dados de gráfico** folha, selecione o intervalo de células que contém os dados para o gráfico (células **A5** por meio de **D8**).  
  
6.  No **Selecionar fonte de dados** caixa de diálogo, clique em **Okey**.  
  
##  <a name="runtimedoclevel"></a> Adicionar controles de gráfico em tempo de execução em um projeto no nível de documento  
 Você pode adicionar o <xref:Microsoft.Office.Tools.Excel.Chart> controle dinamicamente em tempo de execução. Criado dinamicamente gráficos não são mantidos no documento de forma que os controles de host quando o documento é fechado. Para obter mais informações, consulte [adicionar controles a documentos do Office em tempo de execução](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
#### <a name="to-add-a-chart-control-to-a-worksheet-programmatically"></a>Para adicionar um controle de gráfico em uma planilha programaticamente  
  
1.  No <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> manipulador de eventos do `Sheet1`, insira o código a seguir para adicionar o <xref:Microsoft.Office.Tools.Excel.Chart> controle.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#1](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#1)]
     [!code-vb[Trin_VstcoreHostControlsExcel#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#1)]  
  
##  <a name="runtimeaddin"></a> Adicionar controles de gráfico em tempo de execução em um projeto de suplemento do VSTO  
 Você pode adicionar um <xref:Microsoft.Office.Tools.Excel.Chart> controle programaticamente para qualquer planilha aberta em um projeto de suplemento do VSTO. Para obter mais informações, consulte [documentos de estender o Word e pastas de trabalho do Excel no suplemento do VSTO em tempo de execução](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
 Controles de gráfico criado dinamicamente não são mantidos na planilha de forma que os controles de host quando a planilha está fechada. Para obter mais informações, consulte [adicionar controles ao Office documentos em tempo de execução](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
#### <a name="to-add-a-chart-control-to-a-worksheet-programmatically"></a>Para adicionar um controle de gráfico em uma planilha programaticamente  
  
1.  O código a seguir gera um item de host de planilha com base na planilha aberta e, em seguida, adiciona um <xref:Microsoft.Office.Tools.Excel.Chart> controle.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#9](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#9)]
     [!code-vb[Trin_Excel_Dynamic_Controls#9](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#9)]  
  
## <a name="compile-the-code"></a>Compile o código  
 Este exemplo tem os seguintes requisitos:  
  
-   Dados armazenados no intervalo de A5 para D8 na planilha, no gráfico.  
  
## <a name="see-also"></a>Consulte também  
 [Estender a documentos do Word e pastas de trabalho do Excel no suplemento do VSTO em tempo de execução](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Controles em documentos do Office](../vsto/controls-on-office-documents.md)   
 [Controle de gráfico](../vsto/chart-control.md)   
 [Automatizar o Excel usando objetos estendidos](../vsto/automating-excel-by-using-extended-objects.md)   
 [Itens de host e visão geral dos controles de host](../vsto/host-items-and-host-controls-overview.md)   
 [Associar dados a controles em soluções do Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Limitações programáticas de itens de host e controles de host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  