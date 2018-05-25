---
title: 'Como: adicionar controles de indicador a documentos do Word'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VST.Bookmark.Dialog
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Bookmark control, adding to documents
- Create Bookmark Control dialog box
- controls [Office development in Visual Studio], adding to documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c2814847270df70126cb8f286acdc152ddbed046
ms.sourcegitcommit: 697162f54d3c4e30df702fd0289e447e211e3a85
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/25/2018
---
# <a name="how-to-add-bookmark-controls-to-word-documents"></a>Como: adicionar controles de indicador a documentos do Word
  Em projetos de nível de documento, você pode adicionar <xref:Microsoft.Office.Tools.Word.Bookmark> controles para o documento em seu projeto em tempo de design ou em tempo de execução. Em projetos de suplemento do VSTO, você pode adicionar <xref:Microsoft.Office.Tools.Word.Bookmark> controles para qualquer documento aberto em tempo de execução.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Este tópico descreve as seguintes tarefas:  
  
-   [Adicionar controles de indicador em tempo de design](#designtime)  
  
-   [Adicionar controles de indicador em tempo de execução em um projeto no nível de documento](#runtimedoclevel)  
  
-   [Adicionar controles de indicador em tempo de execução em um projeto de suplemento do VSTO](#runtimeaddin)  
  
 Para obter mais informações sobre <xref:Microsoft.Office.Tools.Word.Bookmark> controles, consulte [controle indicador](../vsto/bookmark-control.md).  
  
##  <a name="designtime"></a> Adicionar controles de indicador em tempo de Design  
 Há várias maneiras de adicionar <xref:Microsoft.Office.Tools.Word.Bookmark> controles para o documento em um projeto no nível do documento em tempo de design:  
  
-   No Visual Studio **caixa de ferramentas**.  
  
     Você pode arrastar o <xref:Microsoft.Office.Tools.Word.Bookmark> controlar do **caixa de ferramentas** ao documento. Convém escolher dessa forma, se você já estiver usando o **caixa de ferramentas** para adicionar controles de formulários do Windows para o documento.  
  
-   De dentro do Word.  
  
     Você pode adicionar o <xref:Microsoft.Office.Tools.Word.Bookmark> controle ao documento da mesma maneira, você adicionaria o indicador nativo. A vantagem de adicioná-lo dessa maneira é que você pode nomear seu controle no momento que você criá-lo.  
  
-   Do **fontes de dados** janela.  
  
     Você pode arrastar o <xref:Microsoft.Office.Tools.Word.Bookmark> controle para o documento a partir de **fontes de dados** janela. Isso é útil quando você deseja associar o controle de dados ao mesmo tempo. Você pode adicionar o controle de host da mesma maneira que você adicionaria um controle de formulário do Windows do **fontes de dados** janela. Para obter mais informações, consulte [associação de dados e o Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms).  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
#### <a name="to-add-a-bookmark-control-to-a-document-from-the-toolbox"></a>Para adicionar um controle de indicador a um documento da caixa de ferramentas  
  
1.  Abra o **caixa de ferramentas** e clique no **controles Word** guia.  
  
2.  Arraste um <xref:Microsoft.Office.Tools.Word.Bookmark> controle o documento.  
  
     O **Adicionar indicador** caixa de diálogo é exibida.  
  
3.  Selecione o texto ou outros itens que você deseja incluir no indicador.  
  
4.  Clique em **OK**.  
  
     Se você não deseja manter o nome do indicador padrão, você pode alterar o nome no **propriedades** janela.  
  
#### <a name="to-add-a-bookmark-control-to-a-document-in-word"></a>Para adicionar um controle de indicador a um documento do Word  
  
1.  O documento que está hospedada no [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] designer, coloque o cursor onde você deseja adicionar o indicador ou selecione o texto que você deseja colocar o indicador.  
  
2.  No **inserir** guia da faixa de opções, no **Links** de grupo, clique no **indicador** botão.  
  
3.  No **indicador** caixa de diálogo, digite o nome do novo indicador e clique em **adicionar**.  
  
##  <a name="runtimedoclevel"></a> Adicionar controles de indicador em tempo de execução em um projeto no nível de documento  
 Você pode adicionar <xref:Microsoft.Office.Tools.Word.Bookmark> controles programaticamente para o documento em tempo de execução usando métodos do <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> propriedade o `ThisDocument` classe em seu projeto. Há duas sobrecargas do método que você pode usar para adicionar um <xref:Microsoft.Office.Tools.Word.Bookmark> controle das seguintes maneiras:  
  
-   Adicionar um <xref:Microsoft.Office.Tools.Word.Bookmark> em um intervalo especificado.  
  
-   Adicionar um <xref:Microsoft.Office.Tools.Word.Bookmark> que se baseia em um indicador nativo do documento (ou seja, um <xref:Microsoft.Office.Interop.Word.Bookmark>).  
  
 Criado dinamicamente <xref:Microsoft.Office.Tools.Word.Bookmark> controles não são mantidos no documento quando o documento é fechado. No entanto, um nativo <xref:Microsoft.Office.Interop.Word.Bookmark> permanecerá no documento. Você pode recriar um <xref:Microsoft.Office.Tools.Word.Bookmark> que se baseia em um indicador nativo na próxima vez em que o documento for aberto. Para obter mais informações, consulte [adicionar controles a documentos do Office em tempo de execução](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
#### <a name="to-add-a-bookmark-control-to-a-document-programmatically"></a>Para adicionar um controle de indicador a um documento programaticamente  
  
1.  No `ThisDocument_Startup` manipulador de eventos em seu projeto, insira o código a seguir para adicionar o <xref:Microsoft.Office.Tools.Word.Bookmark> controle ao primeiro parágrafo no documento.  
  
     [!code-csharp[Trin_VstcoreHostControlsWord#1](../vsto/codesnippet/CSharp/trin_vstcorehostcontrolsword/ThisDocument.cs#1)]
     [!code-vb[Trin_VstcoreHostControlsWord#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsWordVB/ThisDocument.vb#1)]  
  
    > [!NOTE]  
    >  Se você desejar criar um <xref:Microsoft.Office.Tools.Word.Bookmark> controle de uma já existente <xref:Microsoft.Office.Interop.Word.Bookmark>, use o <xref:Microsoft.Office.Tools.Word.ControlCollection.AddBookmark%2A> método e passe existentes no <xref:Microsoft.Office.Interop.Word.Bookmark>.  
  
##  <a name="runtimeaddin"></a> Adicionar controles de indicador em tempo de execução em um projeto de suplemento do VSTO  
 Você pode adicionar <xref:Microsoft.Office.Tools.Word.Bookmark> controles programaticamente para qualquer documento aberto em tempo de execução usando um suplemento do VSTO. Para fazer isso, gerar um <xref:Microsoft.Office.Tools.Word.Document> hospedar o item com base em um documento aberto e usar os métodos do <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> propriedade deste item de host. Há duas sobrecargas do método que você pode usar para adicionar um <xref:Microsoft.Office.Tools.Word.Bookmark> controle das seguintes maneiras:  
  
-   Adicionar um <xref:Microsoft.Office.Tools.Word.Bookmark> em um intervalo especificado.  
  
-   Adicionar um <xref:Microsoft.Office.Tools.Word.Bookmark> que se baseia em um indicador nativo do documento (ou seja, um <xref:Microsoft.Office.Interop.Word.Bookmark>).  
  
 Criado dinamicamente <xref:Microsoft.Office.Tools.Word.Bookmark> controles não são mantidos no documento quando o documento é fechado. No entanto, um nativo <xref:Microsoft.Office.Interop.Word.Bookmark> permanecerá no documento. Você pode recriar um <xref:Microsoft.Office.Tools.Word.Bookmark> que se baseia em um indicador nativo na próxima vez em que o documento for aberto. Para obter mais informações, consulte [manter controles dinâmicos em documentos do Office](../vsto/persisting-dynamic-controls-in-office-documents.md).  
  
 Para obter mais informações sobre como gerar itens de host em projetos de suplemento do VSTO, consulte [documentos de estender o Word e pastas de trabalho do Excel no suplemento do VSTO em tempo de execução](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
#### <a name="to-add-a-bookmark-control-at-a-specified-range"></a>Para adicionar um controle de indicador em um intervalo especificado  
  
1.  Use o <xref:Microsoft.Office.Tools.Word.ControlCollection.AddBookmark%2A> método e passar o <xref:Microsoft.Office.Interop.Word.Range> onde você deseja adicionar o <xref:Microsoft.Office.Tools.Word.Bookmark>.  
  
     O exemplo de código a seguir adiciona um novo <xref:Microsoft.Office.Tools.Word.Bookmark> para o início do documento ativo. Para usar este exemplo, execute o código do `ThisAddIn_Startup` manipulador de eventos em um projeto de suplemento do VSTO do Word.  
  
     [!code-vb[Trin_WordAddInDynamicControls#4](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#4)]
     [!code-csharp[Trin_WordAddInDynamicControls#4](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#4)]  
  
#### <a name="to-add-a-bookmark-control-that-is-based-on-a-native-bookmark-control"></a>Para adicionar um controle de indicador se baseia em um controle de indicador nativo  
  
1.  Use o <xref:Microsoft.Office.Tools.Word.ControlCollection.AddBookmark%2A> método e passar existente <xref:Microsoft.Office.Interop.Word.Bookmark> que você deseja usar como base para o novo <xref:Microsoft.Office.Tools.Word.Bookmark>.  
  
     O exemplo de código a seguir cria um novo <xref:Microsoft.Office.Tools.Word.Bookmark> que é baseado no primeiro <xref:Microsoft.Office.Interop.Word.Bookmark> no documento ativo. Para usar este exemplo, execute o código do `ThisAddIn_Startup` manipulador de eventos em um projeto de suplemento do VSTO do Word.  
  
     [!code-vb[Trin_WordAddInDynamicControls#5](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#5)]
     [!code-csharp[Trin_WordAddInDynamicControls#5](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#5)]  
  
## <a name="see-also"></a>Consulte também  
 [Automatizar o Word usando objetos estendidos](../vsto/automating-word-by-using-extended-objects.md)   
 [Itens de host e visão geral dos controles de host](../vsto/host-items-and-host-controls-overview.md)   
 [Adicionar controles a documentos do Office em tempo de execução](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Limitações programáticas de itens de host e controles de host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Programa de suplementos do VSTO](../vsto/programming-vsto-add-ins.md)   
 [Programa personalizações no nível do documento](../vsto/programming-document-level-customizations.md)   
 [Como: redimensionar controles de indicador](../vsto/how-to-resize-bookmark-controls.md)  
  
  