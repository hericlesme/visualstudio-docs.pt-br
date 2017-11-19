---
title: 'Como: criar novos documentos programaticamente | Microsoft Docs'
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
- templates [Office development in Visual Studio], custom document
- Word [Office development in Visual Studio], creating documents
- documents [Office development in Visual Studio], creating
ms.assetid: c24bb8a3-1303-438e-9b33-ba8b00b29c3b
caps.latest.revision: "49"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b1935b7657e7aad612b855ecd4e9c1c8e222c952
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-create-new-documents"></a>Como criar novos documentos programaticamente
  Quando você cria um documento programaticamente, o novo documento é um nativo <xref:Microsoft.Office.Interop.Word.Document> objeto. Este objeto não tem eventos adicionais e recursos de associação de dados de um <xref:Microsoft.Office.Tools.Word.Document> item de host. Para obter mais informações, consulte [limitações programáticas de itens de Host e controles de Host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Quando você desenvolve um projeto no nível do documento, você não pode adicionar programaticamente <xref:Microsoft.Office.Tools.Word.Document> hospedar itens ao seu projeto. Em um projeto de suplemento do VSTO, você pode converter qualquer <xref:Microsoft.Office.Interop.Word.Document> o objeto para um <xref:Microsoft.Office.Tools.Word.Document> item de host em tempo de execução. Para obter mais informações, consulte [Estendendo documentos do Word e pastas de trabalho do Excel no suplemento do VSTO em tempo de execução](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
### <a name="to-create-a-new-document-based-on-the-normal-template"></a>Para criar um novo documento baseado no modelo Normal  
  
-   Use o <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> método o <xref:Microsoft.Office.Interop.Word.Documents> coleção para criar um novo documento com base no modelo Normal. Para usar este exemplo de código, executá-la na `ThisDocument` ou `ThisAddIn` classe em seu projeto.  
  
     [!code-vb[Trin_VstcoreWordAutomation#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#1)]
     [!code-csharp[Trin_VstcoreWordAutomation#1](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#1)]  
  
## <a name="using-custom-templates"></a>Usando modelos personalizados  
 O <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> método tem um *modelo* argumento para criar um novo documento com base em um modelo diferente de modelo Normal. Você deve fornecer o nome de arquivo e o caminho totalmente qualificado do modelo.  
  
#### <a name="to-create-a-new-document-based-on-a-custom-template"></a>Para criar um novo documento com base em um modelo personalizado  
  
-   Chamar o <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> método o <xref:Microsoft.Office.Interop.Word.Documents> coleção e especifique o caminho para o modelo. Para usar este exemplo de código, executá-la na `ThisDocument` ou `ThisAddIn` classe em seu projeto.  
  
     [!code-vb[Trin_VstcoreWordAutomation#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#2)]
     [!code-csharp[Trin_VstcoreWordAutomation#2](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#2)]  
  
## <a name="see-also"></a>Consulte também  
 [Como: abrir documentos existentes programaticamente](../vsto/how-to-programmatically-open-existing-documents.md)   
 [Itens de host e visão geral dos controles de Host](../vsto/host-items-and-host-controls-overview.md)   
 [Limitações programáticas de itens de Host e controles de Host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Parâmetros opcionais em soluções do Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  