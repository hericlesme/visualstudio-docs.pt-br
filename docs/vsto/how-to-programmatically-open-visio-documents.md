---
title: 'Como: abrir documentos do Visio de forma programática'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], opening Visio documents
- Visio [Office development in Visual Studio], opening Visio documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a3a7d2a9855abef0415661798c8a213eb748e22f
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/11/2018
ms.locfileid: "35257846"
---
# <a name="how-to-programmatically-open-visio-documents"></a>Como: abrir documentos do Visio de forma programática
  Há dois métodos para abrir documentos existentes do Microsoft Office Visio: Open e OpenEx. O método OpenEx é idêntico ao método Open, exceto que ele forneça argumentos em que o chamador pode especificar como o documento é aberto.  
  
 Para obter detalhes sobre o modelo de objeto, consulte a documentação de referência do VBA para o [Microsoft.Office.Interop.Visio.Documents.Open](https://msdn.microsoft.com/library/office/ff765240.aspx) método e [Microsoft.Office.Interop.Visio.Documents.OpenEx](https://msdn.microsoft.com/library/office/ff767229.aspx) método.  
  
## <a name="open-a-visio-document"></a>Abra um documento do Visio  
  
### <a name="to-open-a-visio-document"></a>Para abrir um documento do Visio  
  
-   Chamar o `Microsoft.Office.Interop.Visio.Documents.Open` método e fornecer o caminho totalmente qualificado do documento do Visio.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#5](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#5)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#5](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#5)]  
  
## <a name="open-a-visio-document-with-specified-arguments"></a>Abra um documento do Visio com argumentos especificados  
  
### <a name="to-open-a-visio-document-as-read-only-and-docked"></a>Para abrir um documento do Visio como somente leitura e encaixados  
  
-   Chamar o `Microsoft.Office.Interop.Visio.Documents.OpenEx` método, forneça o caminho totalmente qualificado do documento do Visio e incluir os argumentos que você deseja usar — nesse caso, encaixado e somente leitura.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#6](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#6)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#6](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#6)]  
  
## <a name="compile-the-code"></a>Compilar o código  
 Este exemplo de código requer o seguinte:  
  
-   Um documento do Visio chamado `myDrawing.vsd` devem estar localizados em um diretório chamado `Test` na *Meus documentos* pasta (para o Windows XP e versões anteriores) ou o *documentos* pasta (para Windows Vista).  
  
## <a name="see-also"></a>Consulte também  
 [Soluções do Visio](../vsto/visio-solutions.md)   
 [Visão geral do modelo de objeto do Visio](../vsto/visio-object-model-overview.md)   
 [Como: criar novos documentos do Visio programaticamente](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [Como: fechar documentos do Visio programaticamente](../vsto/how-to-programmatically-close-visio-documents.md)   
 [Como: salvar documentos do Visio programaticamente](../vsto/how-to-programmatically-save-visio-documents.md)   
 [Como: imprimir documentos do Visio de forma programática](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  