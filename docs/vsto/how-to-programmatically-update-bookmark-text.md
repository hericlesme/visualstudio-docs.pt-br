---
title: 'Como: atualizar programaticamente o texto do indicador | Microsoft Docs'
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
- bookmarks, updating text
- text [Office development in Visual Studio], updating in bookmarks
- Bookmark control, updating contents
ms.assetid: 2324164d-2538-4695-9aaf-7285ce403be3
caps.latest.revision: "46"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 6c9db34e05c964b95a41593b194c4941293c7efb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-update-bookmark-text"></a>Como atualizar indicador de texto programaticamente
  Você pode inserir texto em um indicador de espaço reservado em um documento do Word do Microsoft Office para que você possa recuperar o texto em um momento posterior, ou substituir texto em um indicador. Se você estiver desenvolvendo uma personalização no nível do documento, você também pode atualizar o texto em uma <xref:Microsoft.Office.Tools.Word.Bookmark> controle associado a dados. Para obter mais informações, consulte [vinculação de dados a controles em soluções do Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 O objeto de indicador pode ser um destes dois tipos:  
  
-   Um <xref:Microsoft.Office.Tools.Word.Bookmark> controle de host.  
  
     <xref:Microsoft.Office.Tools.Word.Bookmark>controles de estendem nativo <xref:Microsoft.Office.Interop.Word.Bookmark> objetos, permitindo que a associação de dados e a exposição de eventos. Para obter mais informações sobre controles de host, consulte [itens de Host e visão geral dos controles de Host](../vsto/host-items-and-host-controls-overview.md).  
  
-   Um nativo <xref:Microsoft.Office.Interop.Word.Bookmark> objeto.  
  
     <xref:Microsoft.Office.Interop.Word.Bookmark>objetos não têm recursos de ligação de eventos ou dados.  
  
 Quando você atribui o texto para um indicador, o comportamento difere entre um <xref:Microsoft.Office.Interop.Word.Bookmark> e um <xref:Microsoft.Office.Tools.Word.Bookmark>. Para obter mais informações, consulte [indicador controle](../vsto/bookmark-control.md).  
  
## <a name="using-host-controls"></a>Usando controles de Host  
  
#### <a name="to-update-bookmark-contents-using-a-bookmark-control"></a>Para atualizar o conteúdo de indicador usando um controle de indicador  
  
1.  Criar um procedimento que usa um `bookmark` argumento para o nome do indicador e um `newText` argumento de cadeia de caracteres atribuir ao <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> propriedade.  
  
    > [!NOTE]  
    >  Atribuição de texto para o <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> ou <xref:Microsoft.Office.Tools.Word.Bookmark.FormattedText%2A> propriedade de um <xref:Microsoft.Office.Tools.Word.Bookmark> controle não faz com que o indicador a ser excluído.  
  
     [!code-vb[Trin_VstcoreWordAutomation#63](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#63)]
     [!code-csharp[Trin_VstcoreWordAutomation#63](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#63)]  
  
2.  Atribuir o *TextoNovo* de cadeia de caracteres para o <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> propriedade o <xref:Microsoft.Office.Tools.Word.Bookmark>.  
  
     [!code-vb[Trin_VstcoreWordAutomation#64](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#64)]
     [!code-csharp[Trin_VstcoreWordAutomation#64](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#64)]  
  
## <a name="using-word-objects"></a>Usando objetos do Word  
  
#### <a name="to-update-bookmark-contents-using-a-word-bookmark-object"></a>Para atualizar o conteúdo de indicador usando um objeto do indicador do Word  
  
1.  Criar um procedimento que tem um `bookmark` argumento para o nome do <xref:Microsoft.Office.Interop.Word.Bookmark>e um `newText` argumento de cadeia de caracteres atribuir ao <xref:Microsoft.Office.Interop.Word.Range.Text%2A> propriedade do indicador.  
  
    > [!NOTE]  
    >  Atribuição de texto a uma palavra nativo <xref:Microsoft.Office.Interop.Word.Bookmark> objeto faz com que o indicador a ser excluído.  
  
     [!code-vb[Trin_VstcoreWordAutomation#65](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#65)]
     [!code-csharp[Trin_VstcoreWordAutomation#65](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#65)]  
  
2.  Atribuir o *TextoNovo* de cadeia de caracteres para o <xref:Microsoft.Office.Interop.Word.Range.Text%2A> propriedade do indicador, que exclui automaticamente o indicador. Em seguida, adicione novamente o indicador para o <xref:Microsoft.Office.Interop.Word.Bookmarks> coleção.  
  
     O exemplo de código a seguir pode ser usado em uma personalização no nível do documento.  
  
     [!code-vb[Trin_VstcoreWordAutomation#66](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#66)]
     [!code-csharp[Trin_VstcoreWordAutomation#66](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#66)]  
  
     O exemplo de código a seguir pode ser usado em um suplemento do VSTO. Este exemplo usa o documento ativo.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#66](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#66)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#66](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#66)]  
  
## <a name="see-also"></a>Consulte também  
 [Como: programaticamente inserir texto em documentos do Word](../vsto/how-to-programmatically-insert-text-into-word-documents.md)   
 [Visão geral do modelo de objeto do Word](../vsto/word-object-model-overview.md)   
 [Controle do Indicador](../vsto/bookmark-control.md)  
  
  