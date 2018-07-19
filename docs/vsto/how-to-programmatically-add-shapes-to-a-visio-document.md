---
title: 'Como: adicionar formas a um documento do Visio programaticamente'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visio [Office development in Visual Studio], adding Visio shapes
- shapes [Office development in Visual Studio], adding Visio shapes
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 32fc1b61505711cbcf353819372bcd1452bf3716
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/11/2018
ms.locfileid: "35256663"
---
# <a name="how-to-programmatically-add-shapes-to-a-visio-document"></a>Como: adicionar formas a um documento do Visio programaticamente
  Você pode adicionar formas a um documento do Microsoft Office Visio recuperando os mestres de um estêncil e descartando as formas na página ativa.  
  
 Para obter mais informações, consulte a documentação de referência do VBA para o [Microsoft.Office.Interop.Visio.Documents.Add](http://msdn.microsoft.com/library/office/ff766868.aspx) método [Microsoft.Office.Interop.Visio.Application.ActivePage](http://msdn.microsoft.com/library/office/ff765484.aspx) propriedade, e [Microsoft.Office.Interop.Visio.Page.Drop](http://msdn.microsoft.com/library/office/ff765054.aspx) método.  
  
## <a name="add-shapes-to-a-visio-document"></a>Adicionar formas a um documento do Visio  
  
### <a name="to-add-shapes-to-a-visio-document"></a>Para adicionar formas a um documento do Visio  
  
-   Com um documento ativo, recuperar os mestres da coleção Documents.Masters e solte as formas no documento ativo. Você pode recuperar um mestre, usando o índice ou nome do mestre.  
  
     O exemplo de código a seguir cria um documento do Visio em branco e, em seguida, abre-o com o **formas básicas** estêncil encaixado. O código, em seguida, recupera várias formas e os solta na página ativa.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#13](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#13)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#13](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#13)]  
  
## <a name="see-also"></a>Consulte também  
 [Soluções do Visio](../vsto/visio-solutions.md)   
 [Visão geral do modelo de objeto do Visio](../vsto/visio-object-model-overview.md)   
 [Trabalhar com formas do Visio](../vsto/working-with-visio-shapes.md)   
 [Como: copiar e colar formas em um documento do Visio de forma programática](../vsto/how-to-programmatically-copy-and-paste-shapes-in-a-visio-document.md)  
  
  