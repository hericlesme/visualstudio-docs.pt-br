---
title: 'Como: adicionar controles NamedRange a planilhas | Microsoft Docs'
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
- ranges, adding to worksheets
- NamedRange control, adding to worksheets
- controls [Office development in Visual Studio], adding to worksheets
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: ef0ec1846a4ef75200fa6d37f137ca1ab1d70f48
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-add-namedrange-controls-to-worksheets"></a>Como adicionar controles NamedRange a planilhas
  Você pode adicionar <xref:Microsoft.Office.Tools.Excel.NamedRange> controles a uma planilha do Excel do Microsoft Office em tempo de design e em tempo de execução no nível de documento.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Você também pode adicionar <xref:Microsoft.Office.Tools.Excel.NamedRange> controles em tempo de execução em projetos de suplemento do VSTO.  
  
 Este tópico descreve as seguintes tarefas:  
  
-   [Adicionando controles NamedRange em tempo de design](#designtime)  
  
-   [Adicionando controles NamedRange em tempo de execução em um projeto no nível do documento](#runtimedoclevel)  
  
-   [Adicionando controles NamedRange em tempo de execução em um projeto de suplemento do VSTO](#runtimeaddin)  
  
 Para obter mais informações sobre <xref:Microsoft.Office.Tools.Excel.NamedRange> controles, consulte [controle NamedRange](../vsto/namedrange-control.md).  
  
##  <a name="designtime"></a>Adicionando controles NamedRange em tempo de Design  
 Há várias maneiras de adicionar <xref:Microsoft.Office.Tools.Excel.NamedRange> controles em uma planilha em um projeto no nível do documento em tempo de design: de dentro do Excel do Visual Studio **caixa de ferramentas**e o **fontes de dados** janela.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
#### <a name="to-add-a-namedrange-control-to-a-worksheet-using-the-name-box-in-excel"></a>Para adicionar um controle NamedRange a uma planilha usando a caixa de nome no Excel  
  
1.  Selecione uma ou mais células que você deseja incluir no intervalo nomeado.  
  
2.  No **caixa nome**, digite um nome para o intervalo e pressione ENTER.  
  
     O **caixa nome** está localizado ao lado da barra de fórmulas acima coluna **um** da planilha.  
  
#### <a name="to-add-a-namedrange-control-to-a-worksheet-using-the-toolbox"></a>Para adicionar um controle NamedRange a uma planilha usando a caixa de ferramentas  
  
1.  Abra o **caixa de ferramentas** e clique no **Excel controles** guia.  
  
2.  Clique em <xref:Microsoft.Office.Tools.Excel.NamedRange> e arraste-o para uma planilha.  
  
     O **adicionar nomeado intervalo** caixa de diálogo é exibida.  
  
3.  Selecione uma ou mais células que você deseja incluir no intervalo nomeado.  
  
4.  Clique em **OK**.  
  
     Se você não quiser que o nome padrão que é fornecido para o controle, você pode alterar o nome no **propriedades** janela.  
  
#### <a name="to-add-a-namedrange-control-to-a-worksheet-using-the-data-sources-window"></a>Para adicionar um controle NamedRange a uma planilha usando a janela fontes de dados  
  
1.  Abra o **fontes de dados** janela e criar uma fonte de dados para seu projeto. Para obter mais informações, consulte [adicionar novas conexões](../data-tools/add-new-connections.md).  
  
2.  Arraste um campo único do **fontes de dados** janela à sua planilha.  
  
     Uma associação de dados <xref:Microsoft.Office.Tools.Excel.NamedRange> controle é adicionado à planilha. Para obter mais informações, consulte [Vinculação de dados e Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms).  
  
##  <a name="runtimedoclevel"></a>Adicionando controles NamedRange em tempo de execução em um projeto no nível do documento  
 Você pode adicionar um <xref:Microsoft.Office.Tools.Excel.NamedRange> controle por meio de programação à sua planilha em tempo de execução. Isso permite que você crie os controles de host em resposta a eventos. Criado dinamicamente intervalos nomeados não são mantidos na planilha de forma que os controles de host quando a planilha está fechada. Para obter mais informações, consulte [adicionando controles a documentos do Office em tempo de execução](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
#### <a name="to-add-a-namedrange-control-to-a-worksheet-programmatically"></a>Para adicionar um controle NamedRange a uma planilha programaticamente  
  
1.  No <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> manipulador de eventos do `Sheet1`, insira o código a seguir para adicionar o <xref:Microsoft.Office.Tools.Excel.NamedRange> controle a célula **A1** e defina seu <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> propriedade`Hello world!`  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#3](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#3)]
     [!code-vb[Trin_VstcoreHostControlsExcel#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#3)]  
  
##  <a name="runtimeaddin"></a>Adicionando controles NamedRange em tempo de execução em um projeto de suplemento do VSTO  
 Você pode adicionar um <xref:Microsoft.Office.Tools.Excel.NamedRange> controle programaticamente para qualquer planilha aberta em um projeto de suplemento do VSTO. Criado dinamicamente intervalos nomeados não são mantidos na planilha de forma que os controles de host quando a planilha está fechada. Para obter mais informações, consulte [Estendendo documentos do Word e pastas de trabalho do Excel no suplemento do VSTO em tempo de execução](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
#### <a name="to-add-a-namedrange-control-to-a-worksheet-programmatically"></a>Para adicionar um controle NamedRange a uma planilha programaticamente  
  
1.  O código a seguir gera um item de host de planilha com base na planilha aberta e, em seguida, adiciona um <xref:Microsoft.Office.Tools.Excel.NamedRange> controle a célula **A1** e define seu <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> propriedade `Hello world`.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#7](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#7)]
     [!code-vb[Trin_Excel_Dynamic_Controls#7](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#7)]  
  
## <a name="see-also"></a>Consulte também  
 [Estendendo documentos do Word e pastas de trabalho do Excel em suplementos do VSTO em tempo de execução](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Controles em documentos do Office](../vsto/controls-on-office-documents.md)   
 [Controle NamedRange](../vsto/namedrange-control.md)   
 [Automatizando o Excel usando objetos estendidos](../vsto/automating-excel-by-using-extended-objects.md)   
 [Itens de host e visão geral dos controles de Host](../vsto/host-items-and-host-controls-overview.md)   
 [Como: redimensionar controles NamedRange](../vsto/how-to-resize-namedrange-controls.md)   
 [Limitações programáticas de itens de Host e Controles de Host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  