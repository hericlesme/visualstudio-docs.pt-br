---
title: 'Como: abrir documentos existentes programaticamente | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], opening
- Word [Office development in Visual Studio], opening documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0c7542b2222839afc75b3b5b1b84fc5afe56f523
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-open-existing-documents"></a>Como abrir documentos existentes programaticamente
  O <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> método abre o documento do Microsoft Office Word existente especificado por um nome de arquivo e caminho totalmente qualificado. Este método retorna um <xref:Microsoft.Office.Interop.Word.Document> que representa o documento aberto.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### <a name="to-open-a-document"></a>Para abrir um documento  
  
-   Chamar o <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> método o <xref:Microsoft.Office.Interop.Word.Documents> coleta e fornecer um caminho para o documento.  
  
     [!code-vb[Trin_VstcoreWordAutomation#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#5)]
     [!code-csharp[Trin_VstcoreWordAutomation#5](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#5)]  
  
### <a name="to-open-a-document-as-read-only"></a>Para abrir um documento como somente leitura  
  
-   Chamar o <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> método, fornecer um caminho para o documento e definir o *ReadOnly* argumento **True** na chamada do método.  
  
     [!code-vb[Trin_VstcoreWordAutomation#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#6)]
     [!code-csharp[Trin_VstcoreWordAutomation#6](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#6)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo de código requer o seguinte:  
  
-   Um documento chamado NewDocument.doc deve existir em um diretório chamado teste na unidade C.  
  
## <a name="see-also"></a>Consulte também  
 [Como: criar novos documentos programaticamente](../vsto/how-to-programmatically-create-new-documents.md)   
 [Como: fechar documentos programaticamente](../vsto/how-to-programmatically-close-documents.md)   
 [Parâmetros opcionais em soluções do Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  