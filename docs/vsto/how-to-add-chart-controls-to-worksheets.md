---
title: 'Como: adicionar controles Chart a planilhas | Microsoft Docs'
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
- Chart control [Office development in Visual Studio], adding to worksheets
- controls [Office development in Visual Studio], adding to worksheets
ms.assetid: f02568e7-5caa-45b4-aa2a-4f73b0565d4e
caps.latest.revision: "44"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 53b30bb62e4c4f4146b1c43b6fe08f9683ba4867
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-chart-controls-to-worksheets"></a>Como adicionar controles Chart a planilhas
  Você pode adicionar <xref:Microsoft.Office.Tools.Excel.Chart> controles a uma planilha do Excel do Microsoft Office em tempo de design e em tempo de execução em personalizações no nível do documento. Você também pode adicionar <xref:Microsoft.Office.Tools.Excel.Chart> controles em tempo de execução em suplementos do VSTO.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Este tópico descreve as seguintes tarefas:  
  
-   [Adicionando controles de gráfico em tempo de design](#designtime)  
  
-   [Adicionando controles de gráfico em tempo de execução em um projeto no nível do documento](#runtimedoclevel)  
  
-   [Adicionando controles de gráfico em tempo de execução em um projeto de suplemento do VSTO](#runtimeaddin)  
  
 Para obter mais informações sobre <xref:Microsoft.Office.Tools.Excel.Chart> controles, consulte [controle de gráfico](../vsto/chart-control.md).  
  
##  <a name="designtime"></a>Adicionando controles de gráfico em tempo de Design  
 Você pode adicionar o <xref:Microsoft.Office.Tools.Excel.Chart> controle à sua planilha da mesma maneira que você adicionará um gráfico de dentro do aplicativo.  
  
> [!NOTE]  
>  O <xref:Microsoft.Office.Tools.Excel.Chart> controle não está disponível a **caixa de ferramentas** ou **fontes de dados** janela.  
  
#### <a name="to-add-a-chart-host-control-to-a-worksheet-in-excel"></a>Para adicionar um controle de host do gráfico para uma planilha do Excel  
  
1.  No **inserir** guia o **gráficos** de grupo, clique em **coluna**, clique em uma categoria de gráficos e, em seguida, clique no tipo de gráfico desejado.  
  
2.  No **Inserir gráfico** caixa de diálogo, clique em **Okey**.  
  
3.  No **Design** guia o **dados** de grupo, clique em **selecionar dados**.  
  
4.  No **Selecionar fonte de dados** clique na caixa de diálogo de **gráfico** **intervalo de dados** caixa e desmarque qualquer seleção padrão.  
  
5.  No **dados de gráfico** folha, selecione o intervalo de células que contém os dados para o gráfico (células **A5** por meio de **D8**).  
  
6.  No **Selecionar fonte de dados** caixa de diálogo, clique em **Okey**.  
  
##  <a name="runtimedoclevel"></a>Adicionando controles de gráfico em tempo de execução em um projeto no nível do documento  
 Você pode adicionar o <xref:Microsoft.Office.Tools.Excel.Chart> controle dinamicamente em tempo de execução. Criado dinamicamente gráficos não são mantidos no documento de forma que os controles de host quando o documento é fechado. Para obter mais informações, consulte [adicionando controles a documentos do Office em tempo de execução](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
#### <a name="to-add-a-chart-control-to-a-worksheet-programmatically"></a>Para adicionar um controle de gráfico em uma planilha programaticamente  
  
1.  No <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> manipulador de eventos do `Sheet1`, insira o código a seguir para adicionar o <xref:Microsoft.Office.Tools.Excel.Chart> controle.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#1](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#1)]
     [!code-vb[Trin_VstcoreHostControlsExcel#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#1)]  
  
##  <a name="runtimeaddin"></a>Adicionando controles de gráfico em tempo de execução em um projeto de suplemento do VSTO  
 Você pode adicionar um <xref:Microsoft.Office.Tools.Excel.Chart> controle programaticamente para qualquer planilha aberta em um projeto de suplemento do VSTO. Para obter mais informações, consulte [Estendendo documentos do Word e pastas de trabalho do Excel no suplemento do VSTO em tempo de execução](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
 Controles de gráfico criado dinamicamente não são mantidos na planilha de forma que os controles de host quando a planilha está fechada. Para obter mais informações, consulte [adicionando controles a documentos do Office em tempo de execução](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
#### <a name="to-add-a-chart-control-to-a-worksheet-programmatically"></a>Para adicionar um controle de gráfico em uma planilha programaticamente  
  
1.  O código a seguir gera um item de host de planilha com base na planilha aberta e, em seguida, adiciona um <xref:Microsoft.Office.Tools.Excel.Chart> controle.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#9](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#9)]
     [!code-vb[Trin_Excel_Dynamic_Controls#9](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#9)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo tem os seguintes requisitos:  
  
-   Dados armazenados no intervalo de A5 para D8 na planilha, no gráfico.  
  
## <a name="see-also"></a>Consulte também  
 [Estendendo documentos do Word e pastas de trabalho do Excel em suplementos do VSTO em tempo de execução](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Controles em documentos do Office](../vsto/controls-on-office-documents.md)   
 [Controle de gráfico](../vsto/chart-control.md)   
 [Automatizando o Excel usando objetos estendidos](../vsto/automating-excel-by-using-extended-objects.md)   
 [Itens de host e visão geral dos controles de Host](../vsto/host-items-and-host-controls-overview.md)   
 [Associando dados a controles em soluções do Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Limitações programáticas de itens de Host e Controles de Host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  