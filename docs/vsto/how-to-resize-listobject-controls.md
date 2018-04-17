---
title: 'Como: redimensionar controles ListObject | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], resizing
- ListObject control, resizing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 12a81e6bb4a0484b79ad42b8fbab77db97ea82c0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-resize-listobject-controls"></a>Como redimensionar controles ListObject
  Definir o tamanho de um <xref:Microsoft.Office.Tools.Excel.ListObject> controle quando você adiciona uma pasta de trabalho do Microsoft Office Excel; no entanto, você pode redimensioná-la mais tarde. Por exemplo, você talvez queira alterar uma lista de colunas de duas a três colunas.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Você pode redimensionar <xref:Microsoft.Office.Tools.Excel.ListObject> controles em tempo de design ou em tempo de execução no nível de documento. Você pode redimensionar <xref:Microsoft.Office.Tools.Excel.ListObject> controles em tempo de execução em um projeto de suplemento do VSTO.  
  
 Este tópico descreve as seguintes tarefas:  
  
-   [Redimensionar controles ListObject em tempo de design](#designtime)  
  
-   [Redimensionar controles ListObject em tempo de execução em um projeto no nível de documento](#runtimedoclevel)  
  
-   [Redimensionar controles ListObject em tempo de execução em um projeto de suplemento do VSTO](#runtimeaddin)  
  
 Para obter mais informações sobre <xref:Microsoft.Office.Tools.Excel.ListObject> controles, consulte [controle ListObject](../vsto/listobject-control.md).  
  
 ![link para vídeo](../vsto/media/playvideo.gif "link para vídeo") para uma demonstração de vídeo relacionada, consulte [como fazer i: adicionar colunas a um objeto de lista de associação de dados em tempo de execução?](http://go.microsoft.com/fwlink/?LinkID=130318).  
  
##  <a name="designtime"></a> Redimensionar um controle ListObject em tempo de Design  
 Para redimensionar uma lista, clique e arraste uma das alças de dimensionamento, ou você pode redefinir seu tamanho no **redimensionar lista** caixa de diálogo.  
  
#### <a name="to-resize-a-list-by-using-the-resize-list-dialog-box"></a>Para redimensionar uma lista usando a caixa de diálogo redimensionar lista  
  
  
1.  Clique em qualquer lugar do <xref:Microsoft.Office.Tools.Excel.ListObject> tabela. O **ferramentas de tabela, Design** guia na faixa de opções é exibida.  
  
2.  Na seção de propriedades, clique em **redimensionar tabela**.  

    ![VSTO_ResizeTable](../vsto/media/vsto-resizetable.png)
  
3.  Selecione o novo intervalo de dados para sua tabela.  
  
4.  Clique em **OK**.  
  
##  <a name="runtimedoclevel"></a> Redimensionar um controle ListObject em tempo de execução em um projeto no nível de documento  
 Você pode redimensionar um <xref:Microsoft.Office.Tools.Excel.ListObject> controle em tempo de execução usando o <xref:Microsoft.Office.Tools.Excel.ListObject.Resize%2A> método. Você não pode usar esse método para mover o <xref:Microsoft.Office.Tools.Excel.ListObject> controle para um novo local na planilha. Os cabeçalhos devem permanecer na mesma linha e o redimensionado <xref:Microsoft.Office.Tools.Excel.ListObject> controle deve se sobrepor o objeto da lista original. O redimensionado <xref:Microsoft.Office.Tools.Excel.ListObject> controle deve conter uma linha de cabeçalho e pelo menos uma linha de dados.  
  
#### <a name="to-resize-a-list-object-programmatically"></a>Para redimensionar um objeto da lista de forma programática  
  
1.  Criar um <xref:Microsoft.Office.Tools.Excel.ListObject> controle que abrange a célula **A1** por meio de **B3** em `Sheet1`.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#6](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#6)]
     [!code-vb[Trin_VstcoreHostControlsExcel#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#6)]  
  
2.  Redimensionar a lista para incluir células **A1** por meio de **C5**.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#7](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#7)]
     [!code-vb[Trin_VstcoreHostControlsExcel#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#7)]  
  
##  <a name="runtimeaddin"></a> Redimensionando um ListObject em tempo de execução em um projeto de suplemento do VSTO  
 Você pode redimensionar um <xref:Microsoft.Office.Tools.Excel.ListObject> controle em qualquer planilha aberta em tempo de execução. Para obter mais informações sobre como adicionar um <xref:Microsoft.Office.Tools.Excel.ListObject> para uma planilha usando um suplemento do VSTO, consulte [como: adicionar controles ListObject a planilhas](../vsto/how-to-add-listobject-controls-to-worksheets.md).  
  
#### <a name="to-resize-a-list-object-programmatically"></a>Para redimensionar um objeto da lista de forma programática  
  
1.  Criar um <xref:Microsoft.Office.Tools.Excel.ListObject> controle que abrange a célula **A1** por meio de **B3** em `Sheet1`.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#12](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#12)]
     [!code-vb[Trin_Excel_Dynamic_Controls#12](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#12)]  
  
2.  Redimensionar a lista para incluir células **A1** por meio de **C5**.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#13](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#13)]
     [!code-vb[Trin_Excel_Dynamic_Controls#13](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#13)]  
  
## <a name="see-also"></a>Consulte também  
 [Estendendo documentos do Word e pastas de trabalho do Excel em suplementos do VSTO em tempo de execução](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Controles em documentos do Office](../vsto/controls-on-office-documents.md)   
 [Adicionando controles a documentos do Office em tempo de execução](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Itens de host e visão geral dos controles de Host](../vsto/host-items-and-host-controls-overview.md)   
 [Automatizando o Excel usando objetos estendidos](../vsto/automating-excel-by-using-extended-objects.md)   
 [Controle ListObject](../vsto/listobject-control.md)   
 [Como: adicionar controles ListObject a planilhas](../vsto/how-to-add-listobject-controls-to-worksheets.md)   
 [Como: redimensionar controles de indicador](../vsto/how-to-resize-bookmark-controls.md)   
 [Como redimensionar controles NamedRange](../vsto/how-to-resize-namedrange-controls.md)  
  
  