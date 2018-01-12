---
title: 'Como: criar programaticamente tabelas do Word | Microsoft Docs'
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
- documents [Office development in Visual Studio], adding tables
- tables [Office development in Visual Studio], adding to documents
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: cdec862635ff011049f48176b28b31835ca33139
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-create-word-tables"></a>Como criar tabelas do Word programaticamente
  O <xref:Microsoft.Office.Interop.Word.Tables> coleção é um membro do <xref:Microsoft.Office.Interop.Word.Document>, <xref:Microsoft.Office.Tools.Word.Document>, <xref:Microsoft.Office.Interop.Word.Selection>, e <xref:Microsoft.Office.Interop.Word.Range> classes, o que significa que você pode criar uma tabela em qualquer um nesses contextos. Você usa o <xref:Microsoft.Office.Interop.Word.Tables.Add%2A> método o <xref:Microsoft.Office.Interop.Word.Tables> coleção para adicionar uma tabela no intervalo especificado.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="creating-tables-in-document-level-customizations"></a>Criando tabelas em personalizações no nível do documento  
  
#### <a name="to-add-a-simple-table-to-a-document"></a>Para adicionar uma tabela simple para um documento  
  
-   Use o <xref:Microsoft.Office.Interop.Word.Tables.Add%2A> método para adicionar uma tabela consiste em três linhas e quatro colunas no início do documento.  
  
     Para usar o exemplo de código a seguir, executá-la na `ThisDocument` classe em seu projeto.  
  
     [!code-vb[Trin_VstcoreWordAutomation#86](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#86)]
     [!code-csharp[Trin_VstcoreWordAutomation#86](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#86)]  
  
 Quando você cria uma tabela, ele é adicionado automaticamente para o <xref:Microsoft.Office.Interop.Word.Tables> coleção do <xref:Microsoft.Office.Tools.Word.Document> item de host. Você pode referir-se à tabela por seu número de item usando o <xref:Microsoft.Office.Interop.Word.Tables.Item%2A> propriedade, conforme mostrado no código a seguir.  
  
#### <a name="to-refer-to-a-table-by-item-number"></a>Para fazer referência a uma tabela por número de item  
  
1.  Use o <xref:Microsoft.Office.Interop.Word.Tables.Item%2A> propriedade e fornecer o número de item da tabela que você deseja consultar.  
  
     Para usar o exemplo de código a seguir, executá-la na `ThisDocument` classe em seu projeto.  
  
     [!code-vb[Trin_VstcoreWordAutomation#87](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#87)]
     [!code-csharp[Trin_VstcoreWordAutomation#87](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#87)]  
  
 Cada <xref:Microsoft.Office.Interop.Word.Table> objeto também tem um <xref:Microsoft.Office.Interop.Word.Table.Range%2A> atributos de propriedade que permite que você defina a formatação.  
  
#### <a name="to-apply-a-style-to-a-table"></a>Para aplicar um estilo a uma tabela  
  
1.  Use o <xref:Microsoft.Office.Interop.Word.Table.Style%2A> propriedade para aplicar um dos estilos internos de palavras em uma tabela.  
  
     Para usar o exemplo de código a seguir, executá-la na `ThisDocument` classe em seu projeto.  
  
     [!code-vb[Trin_VstcoreWordAutomation#88](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#88)]
     [!code-csharp[Trin_VstcoreWordAutomation#88](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#88)]  
  
## <a name="creating-tables-in-vsto-add-ins"></a>Criando tabelas em suplementos do VSTO  
  
#### <a name="to-add-a-simple-table-to-a-document"></a>Para adicionar uma tabela simple para um documento  
  
-   Use o <xref:Microsoft.Office.Interop.Word.Tables.Add%2A> método para adicionar uma tabela consiste em três linhas e quatro colunas no início do documento.  
  
     O exemplo de código a seguir adiciona uma tabela para o documento ativo. Para usar este exemplo, executá-la na `ThisAddIn` classe em seu projeto.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#86](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#86)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#86](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#86)]  
  
 Quando você cria uma tabela, ele é adicionado automaticamente para o <xref:Microsoft.Office.Interop.Word.Tables> coleção do <xref:Microsoft.Office.Interop.Word.Document>. Você pode referir-se à tabela por seu número de item usando o <xref:Microsoft.Office.Interop.Word.Tables.Item%2A> propriedade, conforme mostrado no código a seguir.  
  
#### <a name="to-refer-to-a-table-by-item-number"></a>Para fazer referência a uma tabela por número de item  
  
1.  Use o <xref:Microsoft.Office.Interop.Word.Tables.Item%2A> propriedade e fornecer o número de item da tabela que você deseja consultar.  
  
     O exemplo de código a seguir usa o documento ativo. Para usar este exemplo, executá-la na `ThisAddIn` classe em seu projeto.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#87](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#87)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#87](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#87)]  
  
 Cada <xref:Microsoft.Office.Interop.Word.Table> objeto também tem um <xref:Microsoft.Office.Interop.Word.Table.Range%2A> atributos de propriedade que permite que você defina a formatação.  
  
#### <a name="to-apply-a-style-to-a-table"></a>Para aplicar um estilo a uma tabela  
  
1.  Use o <xref:Microsoft.Office.Interop.Word.Table.Style%2A> propriedade para aplicar um dos estilos internos de palavras em uma tabela.  
  
     O exemplo de código a seguir usa o documento ativo. Para usar este exemplo, executá-la na `ThisAddIn` classe em seu projeto.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#88](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#88)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#88](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#88)]  
  
## <a name="see-also"></a>Consulte também  
 [Como: adicionar texto e formatação a células em tabelas do Word programaticamente](../vsto/how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables.md)   
 [Como: adicionar programaticamente as linhas e colunas a tabelas do Word](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md)   
 [Como: programaticamente preencher tabelas do Word com propriedades de documento](../vsto/how-to-programmatically-populate-word-tables-with-document-properties.md)   
 [Parâmetros opcionais em soluções do Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  