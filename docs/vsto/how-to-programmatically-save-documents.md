---
title: 'Como: salvar documentos programaticamente | Microsoft Docs'
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
- documents [Office development in Visual Studio], saving
- Word [Office development in Visual Studio], saving documents
ms.assetid: a6225ae9-94f5-421a-9860-5299002d543d
caps.latest.revision: "44"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 251522a745ee7b8dc9894a403f09d1a6d3f32793
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-save-documents"></a>Como salvar documentos programaticamente
  Há várias maneiras de salvar documentos do Microsoft Office Word. Você pode salvar um documento sem alterar o nome do documento, ou você pode salvar um documento com um novo nome.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="saving-a-document-without-changing-the-name"></a>Salvar um documento sem alterar o nome  
  
#### <a name="to-save-the-document-associated-with-a-document-level-customization"></a>Para salvar o documento associado a uma personalização no nível do documento  
  
1.  Chamar o <xref:Microsoft.Office.Tools.Word.Document.Save%2A> método o <xref:Microsoft.Office.Tools.Word.Document> classe. Para usar este exemplo de código, executá-la na `ThisDocument` classe em seu projeto.  
  
     [!code-vb[Trin_VstcoreWordAutomation#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#7)]
     [!code-csharp[Trin_VstcoreWordAutomation#7](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#7)]  
  
#### <a name="to-save-the-active-document"></a>Para salvar o documento ativo  
  
1.  Chamar o <xref:Microsoft.Office.Interop.Word._Document.Save%2A> método para o documento ativo. Para usar este exemplo de código, executá-la na `ThisDocument` ou `ThisAddIn` classe em seu projeto.  
  
     [!code-vb[Trin_VstcoreWordAutomation#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#8)]
     [!code-csharp[Trin_VstcoreWordAutomation#8](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#8)]  
  
 Se você não tiver certeza se o documento que você deseja salvar é o documento ativo, você pode consultar a ele por seu nome.  
  
#### <a name="to-save-a-document-specified-by-name"></a>Para salvar um documento especificado por nome  
  
1.  Use o nome do documento como um argumento para o <xref:Microsoft.Office.Interop.Word.Documents> coleção. Para usar este exemplo de código, executá-la na `ThisDocument` ou `ThisAddIn` classe em seu projeto.  
  
     [!code-vb[Trin_VstcoreWordAutomation#9](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#9)]
     [!code-csharp[Trin_VstcoreWordAutomation#9](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#9)]  
  
## <a name="saving-a-document-with-a-new-name"></a>Salvar um documento com um novo nome  
 Use o método SaveAs para salvar um documento com um novo nome. Você pode usar esse método do <xref:Microsoft.Office.Tools.Word.Document> item de host em um projeto de nível de documento do Word ou de um nativo <xref:Microsoft.Office.Interop.Word.Document> objeto em qualquer projeto do Word. Esse método requer que você especifique o novo nome de arquivo, mas outros argumentos são opcionais.  
  
> [!NOTE]  
>  Se você mostrar o **SaveAs** caixa de diálogo dentro do <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> manipulador de eventos do `ThisDocument` e defina o *Cancelar* parâmetro **false**, talvez o aplicativo feche inesperadamente. Se você definir o *Cancelar* parâmetro **true**, uma mensagem de erro será exibida indicando que o salvamento automático foi desabilitado.  
  
#### <a name="to-save-the-document-associated-with-a-document-level-customization-with-a-new-name"></a>Para salvar o documento associado a uma personalização no nível do documento com um novo nome  
  
1.  Chamar o <xref:Microsoft.Office.Tools.Word.Document.SaveAs%2A> método o `ThisDocument` classe em seu projeto, usando um nome de arquivo e caminho totalmente qualificado. Se um arquivo com esse nome já existe nessa pasta, ele será substituído silenciosamente. Para usar este exemplo de código, executá-la na `ThisDocument` classe.  
  
    > [!NOTE]  
    >  O <xref:Microsoft.Office.Tools.Word.Document.SaveAs%2A> método lançará uma exceção se um diretório de destino não existir ou se não houver outros problemas ao salvar um arquivo. É uma prática recomendada usar um **try... catch** bloquear em torno de <xref:Microsoft.Office.Tools.Word.Document.SaveAs%2A> método ou dentro de um método de chamada.  
  
     [!code-vb[Trin_VstcoreWordAutomation#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#10)]
     [!code-csharp[Trin_VstcoreWordAutomation#10](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#10)]  
  
#### <a name="to-save-a-native-document-with-a-new-name"></a>Para salvar um documento nativo com um novo nome  
  
1.  Chamar o <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> método o <xref:Microsoft.Office.Interop.Word.Document> que você deseja salvar, usando um nome de arquivo e caminho totalmente qualificado. Se um arquivo com esse nome já existe nessa pasta, ele será substituído silenciosamente.  
  
     O exemplo de código a seguir salva o documento ativo com um novo nome. Para usar este exemplo de código, executá-la na `ThisDocument` ou `ThisAddIn` classe em seu projeto.  
  
    > [!NOTE]  
    >  O <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> método lançará uma exceção se um diretório de destino não existir ou se não houver outros problemas ao salvar um arquivo. É uma prática recomendada usar um **try... catch** bloquear em torno de <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> método ou dentro de um método de chamada.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#10)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#10](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#10)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo de código requer o seguinte:  
  
-   Para salvar um documento por nome, um documento chamado NewDocument.doc deve existir em um diretório chamado teste na unidade C.  
  
-   Para salvar um documento com um novo nome, um diretório chamado teste deve existir na unidade C.  
  
## <a name="see-also"></a>Consulte também  
 [Como: fechar documentos programaticamente](../vsto/how-to-programmatically-close-documents.md)   
 [Como: abrir documentos existentes programaticamente](../vsto/how-to-programmatically-open-existing-documents.md)   
 [Item de Host do documento](../vsto/document-host-item.md)   
 [Parâmetros opcionais em soluções do Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  