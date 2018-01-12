---
title: "Como: usar programaticamente as caixas de diálogo do Word no modo oculto | Microsoft Docs"
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
- hidden dialog boxes
- Word [Office development in Visual Studio], dialog boxes
- dialog boxes, hidden mode in Word
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 08427d6310421135032bb3517cda1eefc1122358
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-use-word-dialog-boxes-in-hidden-mode"></a>Como usar caixas de diálogo do Word no modo Oculto programaticamente
  Você pode executar operações complexas com chamada de um método invocando caixas de diálogo internas no Microsoft Office Word sem exibi-los para o usuário. Você pode fazer isso usando o <xref:Microsoft.Office.Interop.Word.Dialog.Execute%2A> método o <xref:Microsoft.Office.Interop.Word.Dialog> objeto sem chamar o <xref:Microsoft.Office.Interop.Word.Dialog.Display%2A> método.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="examples"></a>Exemplos  
 Os exemplos de código a seguir demonstram como usar o **Configurar página** caixa de diálogo no modo oculto para definir propriedades de instalação de várias página com nenhuma entrada do usuário. Os exemplos usam um <xref:Microsoft.Office.Interop.Word.Dialog> objeto para definir um tamanho de página personalizado. As configurações específicas de configuração de página, como a margem superior, margem inferior e assim por diante, estão disponíveis como propriedades de associação tardia do <xref:Microsoft.Office.Interop.Word.Dialog> objeto. Essas propriedades são criadas dinamicamente por palavra em tempo de execução.  
  
 O exemplo a seguir demonstra como executar essa tarefa em projetos do Visual Basic onde **Option Strict** é desativado e em projetos do Visual c# que visam o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. Nesses projetos, você pode usar os recursos de associação tardia nos compiladores do Visual Basic e Visual c#. Para usar este exemplo, executá-la na `ThisDocument` ou `ThisAddIn` classe em seu projeto.  
  
 [!code-vb[Trin_VstcoreWordAutomation#123](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#123)]
 [!code-csharp[Trin_VstcoreWordAutomation#123](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#123)]  
  
 O exemplo a seguir demonstra como executar essa tarefa em projetos do Visual Basic onde **Option Strict** está em. Nesses projetos, você deve usar reflexão para acessar as propriedades de associação tardia. Para usar este exemplo, executá-la na `ThisDocument` ou `ThisAddIn` classe em seu projeto.  
  
 [!code-vb[Trin_VstcoreWordAutomation#104](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#104)]  
  
## <a name="see-also"></a>Consulte também  
 [Como: programaticamente, Use as caixas de diálogo integradas no Word](../vsto/how-to-programmatically-use-built-in-dialog-boxes-in-word.md)   
 [Visão geral do modelo de objeto do Word](../vsto/word-object-model-overview.md)   
 [Associação tardia em soluções do Office](../vsto/late-binding-in-office-solutions.md)   
 [Reflexão (C#)](/dotnet/csharp/programming-guide/concepts/reflection)  
 [Reflexão (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)  
  
  