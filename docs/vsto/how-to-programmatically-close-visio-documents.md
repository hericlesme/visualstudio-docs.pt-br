---
title: 'Como: fechar documentos do Visio programaticamente | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], closing Visio documents
- Visio [Office development in Visual Studio], closing Visio documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 314d8e5bfd40e1e45d4795a6e4523db19124741a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-close-visio-documents"></a>Como fechar documentos do Visio programaticamente
  Você pode fechar o documento ativo do Microsoft Office Visio usando o método Microsoft.Office.Interop.Visio.Document.Close.  
  
 Para obter detalhes sobre esse método, consulte a documentação de referência do VBA para o [Microsoft.Office.Interop.Visio.Document.Close](http://msdn.microsoft.com/library/office/ff767415.aspx) método.  
  
## <a name="closing-the-active-document"></a>Fechar o documento ativo  
  
#### <a name="to-close-the-active-document"></a>Para fechar o documento ativo  
  
-   Chame o método Microsoft.Office.Interop.Visio.Document.Close para fechar o documento ativo.  
  
     Para usar o exemplo de código a seguir, executá-lo no `ThisAddIn` classe em um projeto de suplemento do VSTO para Visio.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#7](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#7)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#7](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#7)]  
  
## <a name="see-also"></a>Consulte também  
 [Soluções do Visio](../vsto/visio-solutions.md)   
 [Visão geral do modelo de objeto do Visio](../vsto/visio-object-model-overview.md)   
 [Como: criar novos documentos do Visio programaticamente](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [Como: abrir documentos do Visio programaticamente](../vsto/how-to-programmatically-open-visio-documents.md)   
 [Como: salvar documentos do Visio programaticamente](../vsto/how-to-programmatically-save-visio-documents.md)   
 [Como imprimir documentos do Visio de forma programática](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  