---
title: Usando o Windows Forms a controles em planilhas do Excel | Microsoft Docs
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
- Windows Forms controls [Office development in Visual Studio], Excel
- Excel [Office development in Visual Studio], Windows Forms controls
- controls [Office development in Visual Studio], Window Forms controls
ms.assetid: bbda7461-0d69-4b56-8ba3-418d63ba49db
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7bbd9c19698a9c81b5af29d27bba91b8aa36dcd2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="using-windows-forms-controls-on-excel-worksheets"></a>Usando controles dos Windows Forms em planilhas do Excel
  Você pode adicionar controles de formulários do Windows para suas pastas de trabalho do Microsoft Office Excel da mesma maneira que você adicione controles de formulários do Windows. Para obter informações gerais sobre como trabalhar com controles em documentos, consulte [controles dos Windows Forms na visão geral de documentos do Office](../vsto/windows-forms-controls-on-office-documents-overview.md).  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="control-considerations-for-excel"></a>Considerações sobre o controle para o Excel  
 Há algumas considerações que são específicas para o Excel.  
  
### <a name="matching-control-size-to-cell-size"></a>Tamanho do controle correspondente ao tamanho da célula  
 Você pode definir o controle a ser redimensionado automaticamente quando o tamanho da célula pai for alterado. Para obter mais informações, consulte [como: redimensionar controles em células da planilha](../vsto/how-to-resize-controls-within-worksheet-cells.md).  
  
### <a name="adding-components-that-are-shared-by-all-worksheets"></a>Adicionando componentes que são compartilhados por todas as planilhas  
 Você pode adicionar os componentes que você deseja compartilhar entre todas as planilhas, como um <xref:System.Data.DataSet>, para o Designer de pasta de trabalho em vez de para planilhas. O componente será exibido na bandeja do componente.  
  
### <a name="formula-for-embedding-controls"></a>Fórmula para inserção de controles  
 Quando você seleciona um controle no Excel, você verá **=EMBED("WinForms.Control.Host","")** no **barra de fórmulas**. Esse texto é necessário e não deve ser excluído.  
  
## <a name="see-also"></a>Consulte também  
 [Como: redimensionar controles dentro das células da planilha](../vsto/how-to-resize-controls-within-worksheet-cells.md)   
 [Como: ocultar controles em planilhas durante a impressão](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)   
 [Passo a passo: Alterando a formatação da planilha usando controles CheckBox](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md)   
 [Passo a passo: Exibindo texto em uma caixa de texto em uma planilha usando um botão](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md)   
 [Instruções passo a passo: atualizando um gráfico em uma planilha usando botões de opção](../vsto/walkthrough-updating-a-chart-in-a-worksheet-using-radio-buttons.md)  
  
  