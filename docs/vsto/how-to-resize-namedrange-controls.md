---
title: 'Como: redimensionar controles NamedRange | Microsoft Docs'
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
- controls [Office development in Visual Studio], resizing
- NamedRange control, resizing
- ranges, resizing in Excel
ms.assetid: 7d6f0b2f-be46-49b7-9f38-b4c8849683f7
caps.latest.revision: "48"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 344abe2cd271504f476b0464bb8d7b3065716b1d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-resize-namedrange-controls"></a>Como redimensionar controles NamedRange
  Você pode definir o tamanho de um <xref:Microsoft.Office.Tools.Excel.NamedRange> controle quando você adiciona a um documento do Microsoft Office Excel; no entanto, você pode redimensioná-la mais tarde.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Você pode redimensionar um intervalo nomeado em tempo de design ou em tempo de execução no nível de documento. Você também pode redimensionar intervalos nomeados em tempo de execução no nível do aplicativo suplementos do VSTO.  
  
 Este tópico descreve as seguintes tarefas:  
  
-   [Redimensionar controles NamedRange em tempo de design](#designtime)  
  
-   [Redimensionar controles NamedRange em tempo de execução em um projeto no nível de documento](#runtimedoclevel)  
  
-   [Redimensionar controles NamedRange em tempo de execução em um projeto de suplemento do VSTO](#runtimeaddin)  
  
##  <a name="designtime"></a>Redimensionar controles NamedRange em tempo de Design  
 Você pode redimensionar um intervalo nomeado redefinindo seu tamanho no **definir nome** caixa de diálogo.  
  
#### <a name="to-resize-a-named-range-by-using-the-define-name-dialog-box"></a>Para redimensionar um intervalo nomeado usando a caixa de diálogo Definir nome  
  
1.  Clique um <xref:Microsoft.Office.Tools.Excel.NamedRange> controle.  
  
2.  Clique em **gerenciar os intervalos nomeados** no menu de atalho.  
  
     O **definir nome** caixa de diálogo é exibida.  
  
3.  Selecione o intervalo nomeado que você deseja redimensionar.  
  
4.  Limpar o **refere-se ao** caixa.  
  
5.  Selecione as células que você deseja usar para definir o tamanho do intervalo nomeado.  
  
6.  Clique em **OK**.  
  
##  <a name="runtimedoclevel"></a>Redimensionar controles NamedRange em tempo de execução em um projeto no nível de documento  
 Você pode redimensionar um intervalo nomeado programaticamente usando o <xref:Microsoft.Office.Tools.Excel.NamedRange.RefersTo%2A> propriedade.  
  
> [!NOTE]  
>  No **propriedades** janela, o <xref:Microsoft.Office.Tools.Excel.NamedRange.RefersTo%2A> propriedade está marcada como somente leitura.  
  
#### <a name="to-resize-a-named-range-programmatically"></a>Para redimensionar um intervalo nomeado programaticamente  
  
1.  Criar um <xref:Microsoft.Office.Tools.Excel.NamedRange> controle na célula **A1** de `Sheet1`.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#4](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#4)]
     [!code-vb[Trin_VstcoreHostControlsExcel#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#4)]  
  
2.  Redimensionar o intervalo nomeado para incluir a célula **B1**.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#5)]
     [!code-vb[Trin_VstcoreHostControlsExcel#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#5)]  
  
##  <a name="runtimeaddin"></a>Redimensionar controles NamedRange em tempo de execução em um projeto de suplemento do VSTO  
 Você pode redimensionar um <xref:Microsoft.Office.Tools.Excel.NamedRange> controle em qualquer planilha aberta em tempo de execução. Para obter mais informações sobre como adicionar um <xref:Microsoft.Office.Tools.Excel.NamedRange> para uma planilha usando um suplemento do VSTO, consulte [como: adicionar controles NamedRange a planilhas](../vsto/how-to-add-namedrange-controls-to-worksheets.md).  
  
#### <a name="to-resize-a-named-range-programmatically"></a>Para redimensionar um intervalo nomeado programaticamente  
  
1.  Criar um <xref:Microsoft.Office.Tools.Excel.NamedRange> controle na célula **A1** de `Sheet1`.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#10](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#10)]
     [!code-vb[Trin_Excel_Dynamic_Controls#10](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#10)]  
  
2.  Redimensionar o intervalo nomeado para incluir a célula **B1**.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#11](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#11)]
     [!code-vb[Trin_Excel_Dynamic_Controls#11](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#11)]  
  
## <a name="see-also"></a>Consulte também  
 [Estendendo documentos do Word e pastas de trabalho do Excel em suplementos do VSTO em tempo de execução](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Adicionando controles a documentos do Office em tempo de execução](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Controles em documentos do Office](../vsto/controls-on-office-documents.md)   
 [Itens de host e visão geral dos controles de Host](../vsto/host-items-and-host-controls-overview.md)   
 [Automatizando o Excel usando objetos estendidos](../vsto/automating-excel-by-using-extended-objects.md)   
 [Controle NamedRange](../vsto/namedrange-control.md)   
 [Como: adicionar controles NamedRange a planilhas](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Como: redimensionar controles de indicador](../vsto/how-to-resize-bookmark-controls.md)   
 [Como redimensionar controles ListObject](../vsto/how-to-resize-listobject-controls.md)  
  
  