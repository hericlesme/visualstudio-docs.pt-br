---
title: 'Como: fechar documentos do Visio programaticamente'
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
ms.openlocfilehash: e27b0a19005b7076629f2848f95c8cb5749c096f
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "35670217"
---
# <a name="how-to-programmatically-close-visio-documents"></a>Como: fechar documentos do Visio programaticamente
  Você pode fechar o documento ativo do Microsoft Office Visio usando a `Microsoft.Office.Interop.Visio.Document.Close` método.  
  
 Para obter detalhes sobre esse método, consulte a documentação de referência do VBA para o [Microsoft.Office.Interop.Visio.Document.Close](http://msdn.microsoft.com/library/office/ff767415.aspx) método.  
  
## <a name="close-the-active-document"></a>Fechar o documento ativo  
  
### <a name="to-close-the-active-document"></a>Para fechar o documento ativo  
  
-   Chamar o `Microsoft.Office.Interop.Visio.Document.Close` método para fechar o documento ativo.  
  
     Para usar o exemplo de código a seguir, execute-o `ThisAddIn` classe em um projeto de suplemento do VSTO para Visio.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#7](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#7)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#7](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#7)]  
  
## <a name="see-also"></a>Consulte também  
 [Soluções do Visio](../vsto/visio-solutions.md)   
 [Visão geral do modelo de objeto do Visio](../vsto/visio-object-model-overview.md)   
 [Como: criar novos documentos do Visio programaticamente](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [Como: abrir documentos do Visio de forma programática](../vsto/how-to-programmatically-open-visio-documents.md)   
 [Como: salvar documentos do Visio programaticamente](../vsto/how-to-programmatically-save-visio-documents.md)   
 [Como: imprimir documentos do Visio de forma programática](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  