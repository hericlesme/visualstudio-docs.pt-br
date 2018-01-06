---
title: 'Como: armazenar em Cache dados em um documento protegido por senha | Microsoft Docs'
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
- data caching [Office development in Visual Studio], protected documents
- datasets [Office development in Visual Studio], caching
- data [Office development in Visual Studio], caching
ms.assetid: 91b865fc-bd01-438f-ac63-2fe3175bc2e8
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: ecc4913d9d508d95347945b8f4aaa816bc3d510c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-cache-data-in-a-password-protected-document"></a>Como armazenar dados em cache em um documento protegido por senha
  Se você adicionar dados para o cache de dados em um documento ou a pasta de trabalho que esteja protegida com uma senha, as alterações nos dados armazenados em cache não são salvas automaticamente. Você pode salvar as alterações aos dados armazenados em cache, substituindo os dois métodos em seu projeto.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="caching-in-word-documents"></a>Armazenamento em cache em documentos do Word  
  
#### <a name="to-cache-data-in-a-word-document-that-is-protected-with-a-password"></a>Os dados em cache em um documento do Word que esteja protegido com uma senha  
  
1.  No `ThisDocument` classe, marcar um campo ou propriedade pública a ser armazenado em cache. Para obter mais informações, consulte [Caching Data](../vsto/caching-data.md).  
  
2.  Substituir o <xref:Microsoft.Office.Tools.Word.DocumentBase.UnprotectDocument%2A> método o `ThisDocument` classe e remover a proteção do documento.  
  
     Quando o documento é salvo, o [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] chama esse método para que você tenha a oportunidade para desproteger o documento. Isso permite que as alterações feitas nos dados armazenados em cache sejam salvas.  
  
3.  Substituir o <xref:Microsoft.Office.Tools.Word.DocumentBase.ProtectDocument%2A> método o `ThisDocument` classe e reaplique a proteção para o documento.  
  
     Depois que o documento é salvo, o [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] chama esse método para que você tenha a oportunidade para reaplicar a proteção para o documento.  
  
### <a name="example"></a>Exemplo  
 O exemplo de código a seguir demonstra como armazenar em cache os dados em um documento do Word que esteja protegido com uma senha. Antes do código remove a proteção contra o <xref:Microsoft.Office.Tools.Word.DocumentBase.UnprotectDocument%2A> método, ele salva atual <xref:Microsoft.Office.Tools.Word.Document.ProtectionType%2A> valor, para que o mesmo tipo de proteção pode ser reaplicado no <xref:Microsoft.Office.Tools.Word.DocumentBase.ProtectDocument%2A> método.  
  
 [!code-csharp[Trin_CachedDataProtectedDocument#1](../vsto/codesnippet/CSharp/Trin_CachedDataProtectedDocument/ThisDocument.cs#1)]
 [!code-vb[Trin_CachedDataProtectedDocument#1](../vsto/codesnippet/VisualBasic/Trin_CachedDataProtectedDocument/ThisDocument.vb#1)]  
  
### <a name="compiling-the-code"></a>Compilando o código  
 Adicione este código para o `ThisDocument` classe em seu projeto. Esse código supõe que a senha é armazenada em um campo chamado `securelyStoredPassword`.  
  
## <a name="caching-in-excel-workbooks"></a>Cache em pastas de trabalho do Excel  
 Em projetos do Excel, esse procedimento é necessário somente quando você proteger toda a pasta de trabalho com uma senha usando o <xref:Microsoft.Office.Tools.Excel.Workbook.Protect%2A> método. Esse procedimento não será necessário se você proteger apenas uma planilha específica com uma senha usando o <xref:Microsoft.Office.Tools.Excel.Worksheet.Protect%2A> método.  
  
#### <a name="to-cache-data-in-an-excel-workbook-that-is-protected-with-a-password"></a>Os dados em cache em uma pasta de trabalho do Excel que é protegido por senha  
  
1.  No `ThisWorkbook` classe ou uma da `Sheet`  *n*  classes, marcar um campo ou propriedade pública a ser armazenado em cache. Para obter mais informações, consulte [Caching Data](../vsto/caching-data.md).  
  
2.  Substituir o <xref:Microsoft.Office.Tools.Excel.WorkbookBase.UnprotectDocument%2A> método o `ThisWorkbook` classe e remover a proteção da pasta de trabalho.  
  
     Quando a pasta de trabalho é salvo, o [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] chama esse método para que você tenha a oportunidade para desproteger a pasta de trabalho. Isso permite que as alterações feitas nos dados armazenados em cache sejam salvas.  
  
3.  Substituir o <xref:Microsoft.Office.Tools.Excel.WorkbookBase.ProtectDocument%2A> método o `ThisWorkbook` classe e reaplique a proteção para o documento.  
  
     Depois que a pasta de trabalho é salvo, o [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] chama esse método para que você tenha a oportunidade para reaplicar a proteção para a pasta de trabalho.  
  
### <a name="example"></a>Exemplo  
 O exemplo de código a seguir demonstra como armazenar em cache os dados em uma pasta de trabalho do Excel que é protegida com uma senha. Antes do código remove a proteção contra o <xref:Microsoft.Office.Tools.Excel.WorkbookBase.UnprotectDocument%2A> método, ele salva atual <xref:Microsoft.Office.Tools.Excel.Workbook.ProtectStructure%2A> e <xref:Microsoft.Office.Tools.Excel.Workbook.ProtectWindows%2A> valores, para que o mesmo tipo de proteção pode ser reaplicado no <xref:Microsoft.Office.Tools.Excel.WorkbookBase.ProtectDocument%2A> método.  
  
 [!code-vb[Trin_CachedDataProtectedWorkbook#1](../vsto/codesnippet/VisualBasic/Trin_CachedDataProtectedWorkbook/ThisWorkbook.vb#1)]
 [!code-csharp[Trin_CachedDataProtectedWorkbook#1](../vsto/codesnippet/CSharp/Trin_CachedDataProtectedWorkbook/ThisWorkbook.cs#1)]  
  
### <a name="compiling-the-code"></a>Compilando o código  
 Adicione este código para o `ThisWorkbook` classe em seu projeto. Esse código supõe que a senha é armazenada em um campo chamado `securelyStoredPassword`.  
  
## <a name="see-also"></a>Consulte também  
 [Cache de dados](../vsto/caching-data.md)   
 [Como: dados armazenados em Cache para uso Offline ou em um servidor](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)   
 [Como armazenar em cache de forma programática uma fonte de dados em um documento do Office](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)  
  
  