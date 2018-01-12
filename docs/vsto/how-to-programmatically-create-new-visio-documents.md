---
title: 'Como: criar novos documentos do Visio programaticamente | Microsoft Docs'
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
- Visio [Office development in Visual Studio], creating Visio documents
- documents [Office development in Visual Studio], creating Visio documents
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 072a279bd342f60f8ebfb307a880c39bdc8b2d51
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-create-new-visio-documents"></a>Como criar novos documentos do Visio programaticamente
  Quando você cria um novo Microsoft Office Visio documento de desenho, você pode adicioná-lo à coleção de Microsoft.Office.Interop.Visio.Documents abrir documentos do Visio. Consequentemente, o método Microsoft.Office.Interop.Visio.Documents.Add cria um novo documento de desenho do Visio. Para obter mais informações, consulte a documentação de referência do VBA para o [Microsoft.Office.Interop.Visio.Documents.Add](http://msdn.microsoft.com/library/office/ff766868.aspx) método.  
  
## <a name="creating-new-blank-documents"></a>Criando novos documentos em branco  
  
#### <a name="to-create-a-new-document"></a>Para criar um novo documento  
  
-   Use o método Microsoft.Office.Interop.Visio.Documents.Add para criar um novo documento em branco que não seja baseado em um modelo.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#1](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#1)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#1](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#1)]  
  
## <a name="creating-documents-copied-from-existing-documents"></a>Criando documentos copiados de documentos existentes  
 O método Microsoft.Office.Interop.Visio.Documents.Add pode criar um novo documento que é uma cópia de um documento do Visio existente. Você deve fornecer o nome de arquivo e o caminho totalmente qualificado do diagrama.  
  
#### <a name="to-create-a-new-document-that-is-copied-from-an-existing-document"></a>Para criar um novo documento que é copiado de um documento existente  
  
-   Chame o método Microsoft.Office.Interop.Visio.Documents.Add e especifique o caminho do diagrama do Visio.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#2](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#2)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#2](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#2)]  
  
## <a name="creating-stencils-copied-from-existing-stencils"></a>Criando estênceis copiados de estênceis existentes  
 O [Microsoft.Office.Interop.Visio.Documents.Add](http://msdn.microsoft.com/library/office/ff766868.aspx) método pode criar um novo estêncil que é uma cópia de um estêncil do Visio existente. Você deve fornecer o nome de arquivo e o caminho totalmente qualificado do estêncil.  
  
#### <a name="to-create-a-new-stencil-that-is-copied-from-an-existing-stencil"></a>Para criar um novo estêncil que é copiado de um estêncil existente  
  
-   Chame o método Microsoft.Office.Interop.Visio.Documents.Add e especifique o caminho do estêncil.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#3](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#3)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#3](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#3)]  
  
## <a name="creating-documents-based-on-existing-templates"></a>Criando documentos com base em modelos existentes  
 O método Microsoft.Office.Interop.Visio.Documents.Add pode criar um novo documento (um arquivo. vsd) com base em um modelo existente do Visio (um arquivo. vst). Esse método copia o estênceis, estilos e configurações que fazem parte do espaço de trabalho modelo. Você deve fornecer o nome de arquivo e o caminho totalmente qualificado do modelo.  
  
#### <a name="to-create-a-new-document-that-is-based-on-an-existing-template"></a>Para criar um novo documento com base em um modelo existente  
  
-   Chame o método Microsoft.Office.Interop.Visio.Documents.Add e especifique o caminho do modelo.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#4](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#4)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#4](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#4)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo de código requer o seguinte:  
  
-   Um documento do Visio chamado `myDrawing.vsd` devem estar localizados em um diretório chamado `Test` na pasta Meus documentos (para Windows XP e anterior) ou a pasta de documentos (para Windows Vista).  
  
-   Um documento do Visio chamado `myStencil.vss` devem estar localizados em um diretório chamado `Test` na pasta Meus documentos (para Windows XP e anterior) ou a pasta de documentos (para Windows Vista).  
  
-   Um documento do Visio chamado `myTemplate.vst` devem estar localizados em um diretório chamado `Test` na pasta Meus documentos (para Windows XP e anterior) ou a pasta de documentos (para Windows Vista).  
  
## <a name="see-also"></a>Consulte também  
 [Soluções do Visio](../vsto/visio-solutions.md)   
 [Visão geral do modelo de objeto do Visio](../vsto/visio-object-model-overview.md)   
 [Como: abrir documentos do Visio programaticamente](../vsto/how-to-programmatically-open-visio-documents.md)   
 [Como: fechar documentos do Visio programaticamente](../vsto/how-to-programmatically-close-visio-documents.md)   
 [Como: salvar documentos do Visio programaticamente](../vsto/how-to-programmatically-save-visio-documents.md)   
 [Como imprimir documentos do Visio de forma programática](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  