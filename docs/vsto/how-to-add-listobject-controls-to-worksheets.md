---
title: 'Como: adicionar controles ListObject a planilhas'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ListObject control, adding to worksheets
- controls [Office development in Visual Studio], adding to worksheets
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 3ab95f3929b556f6ece0d3b44ee12bad6f21a361
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
---
# <a name="how-to-add-listobject-controls-to-worksheets"></a>Como: adicionar controles ListObject a planilhas
  Você pode adicionar <xref:Microsoft.Office.Tools.Excel.ListObject> controles a uma planilha do Excel do Microsoft Office em tempo de design e em tempo de execução no nível de documento.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Você também pode adicionar <xref:Microsoft.Office.Tools.Excel.ListObject> controles em tempo de execução em projetos de suplemento do VSTO.  
  
 Este tópico descreve as seguintes tarefas:  
  
-   [Adicionar controles ListObject em tempo de design](#designtime)  
  
-   [Adicionar controles ListObject em tempo de execução em um projeto no nível de documento](#runtimedoclevel)  
  
-   [Adicionar controles ListObject em tempo de execução em um projeto de suplemento do VSTO](#runtimeaddin)  
  
 Para obter mais informações sobre <xref:Microsoft.Office.Tools.Excel.ListObject> controles, consulte [controle ListObject](../vsto/listobject-control.md).  
  
##  <a name="designtime"></a> Adicionar controles ListObject em tempo de design  
 Há várias maneiras de adicionar <xref:Microsoft.Office.Tools.Excel.ListObject> controles em uma planilha em um projeto no nível do documento em tempo de design: de dentro do Excel do Visual Studio **caixa de ferramentas**e o **fontes de dados** janela.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
#### <a name="to-use-the-ribbon-in-excel"></a>Para usar a faixa de opções no Excel  
  
1.  No **inserir** guia o **tabelas** de grupo, clique em **tabela**.  
  
2.  Selecione as células que você deseja incluir na lista e clique em **Okey**.  
  
#### <a name="to-use-the-toolbox"></a>Para usar a caixa de ferramentas  
  
1.  Do **Excel controles** guia do **caixa de ferramentas**, arraste um <xref:Microsoft.Office.Tools.Excel.ListObject> à planilha.  
  
     O **adicionar ListObject controle** caixa de diálogo é exibida.  
  
2.  Selecione as células que você deseja incluir na lista e clique em **Okey**.  
  
     Se você não deseja manter o nome padrão, você pode alterar o nome no **propriedades** janela.  
  
#### <a name="to-use-the-data-sources-window"></a>Para usar a janela fontes de dados  
  
1.  Abra o **fontes de dados** janela e criar uma fonte de dados para seu projeto. Para obter mais informações, consulte [adicionar novas conexões](../data-tools/add-new-connections.md).  
  
2.  Arraste uma tabela a partir de **fontes de dados** janela à sua planilha.  
  
     Uma associação de dados <xref:Microsoft.Office.Tools.Excel.ListObject> controle é adicionado à planilha. Para obter mais informações, consulte [associação de dados e o Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms).  
  
##  <a name="runtimedoclevel"></a> Adicionar controles ListObject em tempo de execução em um projeto no nível de documento  
 Você pode adicionar o <xref:Microsoft.Office.Tools.Excel.ListObject> controle dinamicamente em tempo de execução. Isso permite que você crie os controles de host em resposta a eventos. Objetos de lista criados dinamicamente não são mantidos na planilha como hospedar controles quando a planilha está fechada. Para obter mais informações, consulte [adicionar controles a documentos do Office em tempo de execução](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
#### <a name="to-add-a-listobject-control-to-a-worksheet-programmatically"></a>Para adicionar um controle ListObject a uma planilha programaticamente  
  
1.  No <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> manipulador de eventos do `Sheet1`, insira o código a seguir para adicionar um <xref:Microsoft.Office.Tools.Excel.ListObject> controle células **A1** por meio de **A4**.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#2)]
     [!code-vb[Trin_VstcoreHostControlsExcel#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#2)]  
  
##  <a name="runtimeaddin"></a> Adicionar controles ListObject em tempo de execução em um projeto de suplemento do VSTO  
 Você pode adicionar um <xref:Microsoft.Office.Tools.Excel.ListObject> controle programaticamente para qualquer planilha aberta em um projeto de suplemento do VSTO. Objetos de lista criados dinamicamente não são mantidos na planilha como hospedar controles quando a planilha é salvo e fechada. Para obter mais informações, consulte [documentos de estender o Word e pastas de trabalho do Excel no suplemento do VSTO em tempo de execução](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
#### <a name="to-add-a-listobject-control-to-a-worksheet-programmatically"></a>Para adicionar um controle ListObject a uma planilha programaticamente  
  
1.  O código a seguir gera um item de host de planilha com base na planilha aberta e, em seguida, adiciona um <xref:Microsoft.Office.Tools.Excel.ListObject> controle células **A1** por meio de **A4**.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#8](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#8)]
     [!code-vb[Trin_Excel_Dynamic_Controls#8](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#8)]  
  
## <a name="see-also"></a>Consulte também  
 [Estender a documentos do Word e pastas de trabalho do Excel no suplemento do VSTO em tempo de execução](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Controles em documentos do Office](../vsto/controls-on-office-documents.md)   
 [Controle ListObject](../vsto/listobject-control.md)   
 [Automatizar o Excel usando objetos estendidos](../vsto/automating-excel-by-using-extended-objects.md)   
 [Itens de host e visão geral dos controles de host](../vsto/host-items-and-host-controls-overview.md)   
 [Como: redimensionar controles ListObject](../vsto/how-to-resize-listobject-controls.md)   
 [Associar dados a controles em soluções do Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Limitações programáticas de itens de host e controles de host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  