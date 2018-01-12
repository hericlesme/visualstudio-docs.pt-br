---
title: 'Como: salvar documentos do Visio programaticamente | Microsoft Docs'
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
- documents [Office development in Visual Studio], saving Visio documents
- Visio [Office development in Visual Studio], saving Visio documents
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: c255c481123ef4159d63ad87d9c8fa2ac97cbdae
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-save-visio-documents"></a>Como salvar documentos do Visio programaticamente
  Há várias maneiras de salvar documentos do Microsoft Office Visio:  
  
-   Salve alterações em um documento existente.  
  
-   Salvar um novo documento ou salvar um documento com um novo nome.  
  
-   Salve um documento com os argumentos especificados.  
  
 Para obter mais informações, consulte a documentação de referência do VBA para o [Microsoft.Office.Interop.Visio.Document.Save](https://msdn.microsoft.com/library/office/ff766478.aspx) método [Microsoft.Office.Interop.Visio.Document.SaveAs](https://msdn.microsoft.com/library/office/ff765824.aspx) método e [ Microsoft.Office.Interop.Visio.Document.SaveAsEx](https://msdn.microsoft.com/library/office/ff768149.aspx) método.  
  
## <a name="saving-an-existing-document"></a>Salvar um documento existente  
  
#### <a name="to-save-a-document"></a>Para salvar um documento  
  
-   Chame o método Microsoft.Office.Interop.Visio.Document.Save da classe Microsoft.Office.Tools.Visio.Document de um documento que foi salvo anteriormente.  
  
     Para usar este exemplo de código, executá-la na `ThisAddIn` classe em seu projeto.  
  
    > [!NOTE]  
    >  O método Microsoft.Office.Interop.Visio.Document.Save lança uma exceção se um novo documento do Visio ainda não foram salvas.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#11](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#11)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#11](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#11)]  
  
## <a name="saving-a-document-with-a-new-name"></a>Salvar um documento com um novo nome  
 Use o método Microsoft.Office.Interop.Visio.Document.SaveAs para salvar um novo documento ou um documento que tem um novo nome. Esse método requer que você especifique o novo nome de arquivo.  
  
#### <a name="to-save-the-active-visio-document-with-a-new-name"></a>Para salvar o documento do Visio ativo com um novo nome  
  
-   Chame o método Microsoft.Office.Interop.Visio.Document.SaveAs do Microsoft.Office.Tools.Visio.Document que você deseja salvar, usando um caminho totalmente qualificado, incluindo um nome de arquivo. Se um arquivo com esse nome já existe nessa pasta, ele será substituído silenciosamente.  
  
     Para usar este exemplo de código, executá-la na `ThisAddIn` classe em seu projeto.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#10](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#10)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#10](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#10)]  
  
## <a name="saving-a-document-with-a-new-name-and-specified-arguments"></a>Salvar um documento com um novo nome e argumentos especificados  
 Use o método Microsoft.Office.Interop.Visio.Document.SaveAsEx para salvar um documento com um novo nome e especifique quaisquer argumentos aplicável para aplicar ao documento.  
  
#### <a name="to-save-document-with-a-new-name-and-specified-arguments"></a>Para salvar o documento com um novo nome e argumentos especificados  
  
-   Chame o método Microsoft.Office.Interop.Visio.Document.SaveAsEx do Microsoft.Office.Tools.Visio.Document que você deseja salvar, usando um caminho totalmente qualificado, incluindo um nome de arquivo. Se um arquivo com esse nome já existe nessa pasta, uma exceção será lançada.  
  
     O exemplo de código a seguir salva o documento ativo com um novo nome, marca o documento como somente leitura e mostra o documento na lista de documentos usados recentemente. Para usar este exemplo de código, executá-la na `ThisAddIn` classe em seu projeto.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#12](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#12)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#12](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#12)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo de código requer o seguinte:  
  
-   Para salvar um documento que tem um novo nome, um diretório chamado `Test` devem estar localizados na pasta Meus documentos (para Windows XP e anterior) ou a pasta de documentos (para Windows Vista).  
  
## <a name="see-also"></a>Consulte também  
 [Soluções do Visio](../vsto/visio-solutions.md)   
 [Visão geral do modelo de objeto do Visio](../vsto/visio-object-model-overview.md)   
 [Como: criar novos documentos do Visio programaticamente](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [Como: abrir documentos do Visio programaticamente](../vsto/how-to-programmatically-open-visio-documents.md)   
 [Como: fechar documentos do Visio programaticamente](../vsto/how-to-programmatically-close-visio-documents.md)   
 [Como imprimir documentos do Visio de forma programática](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  