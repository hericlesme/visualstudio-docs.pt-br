---
title: 'Como: Cache programaticamente uma fonte de dados em um documento do Office | Microsoft Docs'
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
- Office applications [Office development in Visual Studio], data
- datasets [Office development in Visual Studio], caching
- StartCaching method
- data caching [Office development in Visual Studio], programmatically
- data [Office development in Visual Studio], caching
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 09d4b46aaa68a92ffb9ddfe70f329e97a1b7526d
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-cache-a-data-source-in-an-office-document"></a>Como armazenar em cache de forma programática uma fonte de dados em um documento do Office
  Você pode adicionar programaticamente um objeto de dados para o cache de dados em um documento chamando o `StartCaching` método de um host de item, como um <xref:Microsoft.Office.Tools.Word.Document>, <xref:Microsoft.Office.Tools.Excel.Workbook>, ou <xref:Microsoft.Office.Tools.Excel.Worksheet>. Remove um objeto de dados do cache de dados, chamando o `StopCaching` método de um item de host.  
  
 O `StartCaching` método e o `StopCaching` método são ambos particular, mas eles aparecem no IntelliSense.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Quando você usa o `StartCaching` método para adicionar um objeto de dados para o cache de dados, o objeto de dados não precisa ser declarada com o <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> atributo. No entanto, o objeto de dados deve atender a certos requisitos a serem adicionadas ao cache de dados. Para obter mais informações, consulte [Caching Data](../vsto/caching-data.md).  
  
### <a name="to-programmatically-cache-a-data-object"></a>Para armazenar em cache programaticamente um objeto de dados  
  
1.  Declare o objeto de dados no nível de classe, não dentro de um método. Este exemplo presume que você está declarando um <xref:System.Data.DataSet> chamado `dataSet1` que você deseja armazenar em cache programaticamente.  
  
     [!code-csharp[Trin_VstcoreDataExcel#12](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#12)]
     [!code-vb[Trin_VstcoreDataExcel#12](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#12)]  
  
2.  Instanciar o objeto de dados e, em seguida, chamar o `StartCaching` método da instância de documento ou planilha e passe no nome do objeto de dados.  
  
     [!code-csharp[Trin_VstcoreDataExcel#13](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#13)]
     [!code-vb[Trin_VstcoreDataExcel#13](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#13)]  
  
### <a name="to-stop-caching-a-data-object"></a>Para interromper o caching de um objeto de dados  
  
1.  Chamar o `StopCaching` método da instância de documento ou planilha e passe no nome do objeto de dados. Este exemplo pressupõe que você tenha um <xref:System.Data.DataSet> chamado `dataSet1` que você deseja interromper o caching.  
  
     [!code-csharp[Trin_VstcoreDataExcel#14](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#14)]
     [!code-vb[Trin_VstcoreDataExcel#14](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#14)]  
  
    > [!NOTE]  
    >  Não chame `StopCaching` o manipulador de eventos para o `Shutdown` eventos de um documento ou planilha. No momento o `Shutdown` evento é gerado, é muito tarde para modificar o cache de dados. Para obter mais informações sobre o `Shutdown` evento, consulte [eventos em projetos do Office](../vsto/events-in-office-projects.md).  
  
## <a name="see-also"></a>Consulte também  
 [Cache de dados](../vsto/caching-data.md)   
 [Como: dados armazenados em Cache para uso Offline ou em um servidor](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)   
 [Como: armazenar em Cache dados em um documento protegido por senha](../vsto/how-to-cache-data-in-a-password-protected-document.md)   
 [Acessando dados em documentos no servidor](../vsto/accessing-data-in-documents-on-the-server.md)   
 [Salvando dados](/visualstudio/data-tools/saving-data)  
  
  