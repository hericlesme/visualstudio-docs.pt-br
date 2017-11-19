---
title: 'Como: abrir documentos do Visio programaticamente | Microsoft Docs'
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
- documents [Office development in Visual Studio], opening Visio documents
- Visio [Office development in Visual Studio], opening Visio documents
ms.assetid: bddb820c-bde7-4d21-a0b3-6d1968baccab
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4aa949d1ff2a8d9954c29314a85363d04d09b1a8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-open-visio-documents"></a>Como abrir documentos do Visio programaticamente
  Há dois métodos para abrir documentos existentes do Microsoft Office Visio: OpenEx e abrir. O método OpenEx é idêntico para o método Open, exceto que ele fornece argumentos em que o chamador pode especificar como o documento é aberto.  
  
 Para obter detalhes sobre o modelo de objeto, consulte a documentação de referência do VBA para o [Microsoft.Office.Interop.Visio.Documents.Open](https://msdn.microsoft.com/library/office/ff765240.aspx) método e [Microsoft.Office.Interop.Visio.Documents.OpenEx](https://msdn.microsoft.com/library/office/ff767229.aspx) método.  
  
## <a name="opening-a-visio-document"></a>Abrir um documento do Visio  
  
#### <a name="to-open-a-visio-document"></a>Para abrir um documento do Visio  
  
-   Chame o método Microsoft.Office.Interop.Visio.Documents.Open e fornecer o caminho totalmente qualificado do documento do Visio.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#5](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#5)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#5](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#5)]  
  
## <a name="opening-a-visio-document-with-specified-arguments"></a>Abrir um documento do Visio com os argumentos especificados  
  
#### <a name="to-open-a-visio-document-as-read-only-and-docked"></a>Para abrir um documento do Visio como somente leitura e encaixada  
  
-   Chame o método Microsoft.Office.Interop.Visio.Documents.OpenEx, forneça o caminho totalmente qualificado do documento do Visio e incluir os argumentos que você deseja usar — nesse caso, encaixado e somente leitura.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#6](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#6)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#6](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#6)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo de código requer o seguinte:  
  
-   Um documento do Visio chamado `myDrawing.vsd` devem estar localizados em um diretório chamado `Test` na pasta Meus documentos (para Windows XP e anterior) ou a pasta de documentos (para Windows Vista).  
  
## <a name="see-also"></a>Consulte também  
 [Soluções do Visio](../vsto/visio-solutions.md)   
 [Visão geral do modelo de objeto do Visio](../vsto/visio-object-model-overview.md)   
 [Como: criar novos documentos do Visio programaticamente](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [Como: fechar documentos do Visio programaticamente](../vsto/how-to-programmatically-close-visio-documents.md)   
 [Como: salvar documentos do Visio programaticamente](../vsto/how-to-programmatically-save-visio-documents.md)   
 [Como imprimir documentos do Visio de forma programática](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  