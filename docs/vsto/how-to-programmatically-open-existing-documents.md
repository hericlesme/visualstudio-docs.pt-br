---
title: 'Como: abrir documentos existentes programaticamente | Microsoft Docs'
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
- documents [Office development in Visual Studio], opening
- Word [Office development in Visual Studio], opening documents
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 151571ace6790f05c067f8dff641988301bc1b0e
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
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
  
  