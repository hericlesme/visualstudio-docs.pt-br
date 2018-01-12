---
title: 'Como: mapear colunas ListObject para dados | Microsoft Docs'
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
- data [Office development in Visual Studio], mapping to ListObject column
- ListObject control, mapping data
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: c8def85e851ac6a51eef59e3f0538025f0e7ce6c
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-map-listobject-columns-to-data"></a>Como mapear colunas ListObject para dados
  Quando você associa um <xref:Microsoft.Office.Tools.Excel.ListObject> o controle para um <xref:System.Data.DataTable>, você não deseja exibir todas as colunas em uma lista ou você pode ter algumas colunas que não estão associadas a dados. Você pode mapear as colunas que você deseja que apareça no <xref:Microsoft.Office.Tools.Excel.ListObject> quando você chama o <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> método.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 ![link para vídeo](../vsto/media/playvideo.gif "link para vídeo") para uma demonstração de vídeo relacionada, consulte [como criar uma lista do Excel que está conectado a uma lista do SharePoint?](http://go.microsoft.com/fwlink/?LinkID=130263).  
  
## <a name="mapping-columns"></a>Mapeamento de colunas  
  
#### <a name="to-map-a-data-table-to-columns-in-a-list"></a>Para mapear uma tabela de dados para colunas em uma lista  
  
1.  Criar o <xref:System.Data.DataTable> no nível de classe.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#16](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs#16)]
     [!code-vb[Trin_VstcoreHostControlsExcel#16](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb#16)]  
  
2.  Adicionar colunas de exemplo e os dados no `Startup` manipulador de eventos do `Sheet1` classe (em um projeto no nível de documento) ou `ThisAddIn` classe (em um projeto de suplemento do VSTO).  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#17](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs#17)]
     [!code-vb[Trin_VstcoreHostControlsExcel#17](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb#17)]  
  
3.  Chamar o <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> método e passar os nomes de coluna na ordem em que elas devem aparecer. O objeto da lista será associado a recém-criado <xref:System.Data.DataTable>, mas a ordem das colunas no objeto de lista será diferente da ordem em que aparecem no <xref:System.Data.DataTable>.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#18](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs#18)]
     [!code-vb[Trin_VstcoreHostControlsExcel#18](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb#18)]  
  
## <a name="specifying-unmapped-columns"></a>Especificando colunas não mapeadas  
 Quando você mapear as colunas para um <xref:System.Data.DataTable>, você também pode especificar que determinadas colunas não devem ser associadas a dados, passando uma cadeia de caracteres vazia. Uma nova coluna que não está associada aos dados é adicionada para o <xref:Microsoft.Office.Tools.Excel.ListObject> controle.  
  
#### <a name="to-specify-an-unmapped-column-when-mapping-listobject-columns"></a>Para especificar uma coluna não mapeada no mapeamento de colunas ListObject  
  
1.  Chamar o <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> método e passar os nomes de coluna na ordem em que elas devem aparecer. Use uma cadeia de caracteres vazia para indicar onde é adicionada uma coluna não mapeada; Nesse caso, entre a coluna de título e a última coluna de nome.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#19](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs#19)]
     [!code-vb[Trin_VstcoreHostControlsExcel#19](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb#19)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo de código pressupõe que você tiver uma <xref:Microsoft.Office.Tools.Excel.ListObject> chamado `list1` na planilha em que esse código é exibido.  
  
## <a name="see-also"></a>Consulte também  
 [Estendendo documentos do Word e pastas de trabalho do Excel em suplementos do VSTO em tempo de execução](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Controles em documentos do Office](../vsto/controls-on-office-documents.md)   
 [Adicionando controles a documentos do Office em tempo de execução](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Como: Preencher controles ListObject com dados](../vsto/how-to-fill-listobject-controls-with-data.md)   
 [Automatizando o Excel usando objetos estendidos](../vsto/automating-excel-by-using-extended-objects.md)   
 [Controle ListObject](../vsto/listobject-control.md)  
  
  