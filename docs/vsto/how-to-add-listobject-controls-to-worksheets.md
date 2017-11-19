---
title: 'Como: adicionar controles ListObject a planilhas | Microsoft Docs'
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
- ListObject control, adding to worksheets
- controls [Office development in Visual Studio], adding to worksheets
ms.assetid: 40788ecb-937f-4d2a-90ba-9c938e495b74
caps.latest.revision: "44"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8c22c8aa98ab2b1522b2cd9094738dd251708aee
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-add-listobject-controls-to-worksheets"></a>Como adicionar controles ListObject a planilhas
  Você pode adicionar <xref:Microsoft.Office.Tools.Excel.ListObject> controles a uma planilha do Excel do Microsoft Office em tempo de design e em tempo de execução no nível de documento.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Você também pode adicionar <xref:Microsoft.Office.Tools.Excel.ListObject> controles em tempo de execução em projetos de suplemento do VSTO.  
  
 Este tópico descreve as seguintes tarefas:  
  
-   [Adicionando controles ListObject em tempo de design](#designtime)  
  
-   [Adicionando controles ListObject em tempo de execução em um projeto no nível do documento](#runtimedoclevel)  
  
-   [Adicionando controles ListObject em tempo de execução em um projeto de suplemento do VSTO](#runtimeaddin)  
  
 Para obter mais informações sobre <xref:Microsoft.Office.Tools.Excel.ListObject> controles, consulte [controle ListObject](../vsto/listobject-control.md).  
  
##  <a name="designtime"></a>Adicionando controles ListObject em tempo de Design  
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
  
     Uma associação de dados <xref:Microsoft.Office.Tools.Excel.ListObject> controle é adicionado à planilha. Para obter mais informações, consulte [Vinculação de dados e Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms).  
  
##  <a name="runtimedoclevel"></a>Adicionando controles ListObject em tempo de execução em um projeto no nível do documento  
 Você pode adicionar o <xref:Microsoft.Office.Tools.Excel.ListObject> controle dinamicamente em tempo de execução. Isso permite que você crie os controles de host em resposta a eventos. Objetos de lista criados dinamicamente não são mantidos na planilha como hospedar controles quando a planilha está fechada. Para obter mais informações, consulte [adicionando controles a documentos do Office em tempo de execução](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
#### <a name="to-add-a-listobject-control-to-a-worksheet-programmatically"></a>Para adicionar um controle ListObject a uma planilha programaticamente  
  
1.  No <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> manipulador de eventos do `Sheet1`, insira o código a seguir para adicionar um <xref:Microsoft.Office.Tools.Excel.ListObject> controle células **A1** por meio de **A4**.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#2)]
     [!code-vb[Trin_VstcoreHostControlsExcel#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#2)]  
  
##  <a name="runtimeaddin"></a>Adicionando controles ListObject em tempo de execução em um projeto de suplemento do VSTO  
 Você pode adicionar um <xref:Microsoft.Office.Tools.Excel.ListObject> controle programaticamente para qualquer planilha aberta em um projeto de suplemento do VSTO. Objetos de lista criados dinamicamente não são mantidos na planilha como hospedar controles quando a planilha é salvo e fechada. Para obter mais informações, consulte [Estendendo documentos do Word e pastas de trabalho do Excel no suplemento do VSTO em tempo de execução](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
#### <a name="to-add-a-listobject-control-to-a-worksheet-programmatically"></a>Para adicionar um controle ListObject a uma planilha programaticamente  
  
1.  O código a seguir gera um item de host de planilha com base na planilha aberta e, em seguida, adiciona um <xref:Microsoft.Office.Tools.Excel.ListObject> controle células **A1** por meio de **A4**.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#8](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#8)]
     [!code-vb[Trin_Excel_Dynamic_Controls#8](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#8)]  
  
## <a name="see-also"></a>Consulte também  
 [Estendendo documentos do Word e pastas de trabalho do Excel em suplementos do VSTO em tempo de execução](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Controles em documentos do Office](../vsto/controls-on-office-documents.md)   
 [Controle ListObject](../vsto/listobject-control.md)   
 [Automatizando o Excel usando objetos estendidos](../vsto/automating-excel-by-using-extended-objects.md)   
 [Itens de host e visão geral dos controles de Host](../vsto/host-items-and-host-controls-overview.md)   
 [Como: redimensionar controles ListObject](../vsto/how-to-resize-listobject-controls.md)   
 [Associando dados a controles em soluções do Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Limitações programáticas de itens de Host e Controles de Host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  