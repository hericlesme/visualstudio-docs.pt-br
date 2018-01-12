---
title: 'Como: programaticamente redefinir intervalos em Word documenta | Microsoft Docs'
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
- documents [Office development in Visual Studio], resetting ranges
- ranges, resetting in documents
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 08a2b57c9f30fab0b975ecf84ef8e0fb3127d346
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-reset-ranges-in-word-documents"></a>Como redefinir intervalos em documentos do Word programaticamente
  Use o <xref:Microsoft.Office.Interop.Word.Range.SetRange%2A> método para redimensionar um intervalo existente em um documento do Microsoft Office Word.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### <a name="to-reset-an-existing-range"></a>Para redefinir um intervalo existente  
  
1.  Defina um intervalo inicial, começando com os sete primeiros caracteres do documento.  
  
     O exemplo de código a seguir pode ser usado em uma personalização no nível do documento.  
  
     [!code-vb[Trin_VstcoreWordAutomation#43](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#43)]
     [!code-csharp[Trin_VstcoreWordAutomation#43](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#43)]  
  
     O exemplo de código a seguir pode ser usado em um suplemento do VSTO. Esse código usa o documento ativo.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#43](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#43)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#43](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#43)]  
  
2.  Use <xref:Microsoft.Office.Interop.Word.Range.SetRange%2A> para iniciar o intervalo em que a segunda frase e termina no final da frase quinto.  
  
     [!code-vb[Trin_VstcoreWordAutomation#44](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#44)]
     [!code-csharp[Trin_VstcoreWordAutomation#44](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#44)]  
  
## <a name="document-level-customization-example"></a>Exemplo de personalização de nível de documento  
  
#### <a name="to-reset-an-existing-range-in-a-document-level-customization"></a>Para redefinir um intervalo existente em uma personalização no nível do documento  
  
1.  O exemplo a seguir mostra o exemplo completo para uma personalização no nível do documento. Para usar esse código, executá-la na `ThisDocument` classe em seu projeto.  
  
     [!code-vb[Trin_VstcoreWordAutomation#42](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#42)]
     [!code-csharp[Trin_VstcoreWordAutomation#42](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#42)]  
  
## <a name="vsto-add-in-example"></a>Exemplo de suplemento do VSTO  
  
#### <a name="to-reset-an-existing-range-in-an-vsto-add-in"></a>Para redefinir um intervalo existente em um suplemento do VSTO  
  
1.  O exemplo a seguir mostra o exemplo completo de um suplemento do VSTO. Para usar esse código, executá-la na `ThisAddIn` classe em seu projeto.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#42](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#42)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#42](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#42)]  
  
## <a name="see-also"></a>Consulte também  
 [Como: estender a intervalos em documentos programaticamente](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [Como: definir programaticamente e selecionar intervalos em documentos](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Como: recuperar programaticamente caracteres iniciais e finais em intervalos](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)   
 [Como recolher intervalos ou seleções em documentos de forma programática](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)  
  
  