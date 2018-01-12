---
title: 'Como: programaticamente proteger documentos e partes de documentos | Microsoft Docs'
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
- document protection
- documents [Office development in Visual Studio], document protection
- Word documents, protection
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 8655a03659bd3b69e23fd155620d42df6d52386c
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-protect-documents-and-parts-of-documents"></a>Como proteger documentos e partes de documentos programaticamente
  Você pode adicionar proteção de documentos do Microsoft Office Word para impedir que os usuários façam qualquer edição do documento.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Você também pode marcar determinadas áreas do documento como exceções para que os usuários especificados podem editar apenas as áreas do documento. Por exemplo, você talvez queira proteger um documento inteiro, exceto um indicador específico. Opcionalmente, você pode adicionar uma senha para que os usuários não é possível remover a proteção de documento, a menos que eles conhecem a senha.  
  
> [!NOTE]  
>  O exemplo a seguir não usa proteção por senha; No entanto, convém considerar o uso de uma senha ao adicionar proteção de documento. Para obter mais informações, consulte o exemplo de protetor de documento em [amostras de desenvolvimento do Office e explicações passo a passo](../vsto/office-development-samples-and-walkthroughs.md).  
  
 Você também pode usar controles de conteúdo para proteger partes de documentos. Para obter mais informações, consulte [como: proteger partes de documentos por controles de conteúdo usando](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md).  
  
## <a name="protecting-a-document-that-is-part-of-a-document-level-customization"></a>Proteger um documento que faz parte de uma personalização no nível do documento  
  
#### <a name="to-protect-a-document-that-is-part-of-a-document-level-customization"></a>Para proteger um documento que faz parte de uma personalização no nível do documento  
  
1.  Chamar o <xref:Microsoft.Office.Tools.Word.Document.Protect%2A> método o `ThisDocument` classe em seu projeto.  
  
     [!code-vb[Trin_VstcoreWordAutomation#111](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#111)]
     [!code-csharp[Trin_VstcoreWordAutomation#111](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#111)]  
  
#### <a name="to-exclude-a-bookmark-control-from-document-protection"></a>Para excluir um controle de indicador da proteção de documento  
  
1.  Proteger o documento inteiro usando o <xref:Microsoft.Office.Tools.Word.Document.Protect%2A> método.  
  
     [!code-vb[Trin_VstcoreWordAutomation#111](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#111)]
     [!code-csharp[Trin_VstcoreWordAutomation#111](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#111)]  
  
2.  Excluir `Bookmark1` da proteção de documento.  
  
     [!code-vb[Trin_VstcoreWordAutomation#112](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#112)]
     [!code-csharp[Trin_VstcoreWordAutomation#112](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#112)]  
  
### <a name="compiling-the-code"></a>Compilando o código  
 Para usar esses exemplos de código, executá-los da `ThisDocument` classe em seu projeto. Esses exemplos de código, suponha que você tiver uma <xref:Microsoft.Office.Tools.Word.Bookmark> controle chamado `Bookmark1` no documento no qual esse código é exibido.  
  
## <a name="protecting-a-document-by-using-an-vsto-add-in"></a>Proteger um documento usando um suplemento do VSTO  
  
#### <a name="to-protect-a-document-by-using-an-application-level-vsto-add-in"></a>Para proteger um documento usando um suplemento do VSTO do nível do aplicativo  
  
1.  Chamar o <xref:Microsoft.Office.Interop.Word._Document.Protect%2A> método o <xref:Microsoft.Office.Interop.Word.Document> que você deseja proteger.  
  
     O exemplo de código a seguir protege o documento ativo. Para usar este exemplo de código, executá-la na `ThisAddIn` classe em seu projeto.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#111](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#111)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#111](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#111)]  
  
## <a name="see-also"></a>Consulte também  
 [Proteção de documento em soluções de nível de documento](../vsto/document-protection-in-document-level-solutions.md)   
 [Proteção por senha em documentos do Office](../vsto/password-protection-on-office-documents.md)   
 [Como: permitir que o código em execução atrás de documentos com permissões restritas](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)   
 [Como: adicionar controles de indicador a documentos do Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)   
 [Projetando e criando soluções do Office](../vsto/designing-and-creating-office-solutions.md)  
  
  