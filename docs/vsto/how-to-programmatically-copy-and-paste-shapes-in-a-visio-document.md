---
title: 'Como: programaticamente copiar e colar formas em um documento do Visio | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- shapes [Office development in Visual Studio], copying and pasting Visio shapes
- Visio [Office development in Visual Studio], copying and pasting Visio shapes
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 488cda5519a211754498b50a88995de64a8ed366
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-copy-and-paste-shapes-in-a-visio-document"></a>Como copiar e colar formas em um documento do Visio programaticamente
  Programaticamente, você pode copiar formas em uma página de um documento e colá-los em uma nova página no mesmo documento. Você pode optar por colá-los para o local padrão (o centro da janela ativa) ou para as mesmas localizações de coordenadas que tinham na página original.  
  
## <a name="copying-and-pasting-shapes"></a>Copiando e colando formas  
 Para obter detalhes sobre o modelo de objeto, consulte a documentação de referência do VBA para o [Microsoft.Office.Interop.Visio.Shape.DrawRectangle](https://msdn.microsoft.com/library/office/ff765757.aspx), [Microsoft.Office.Interop.Visio.Shape.DrawOval](https://msdn.microsoft.com/library/office/ff767121.aspx), [ Microsoft.Office.Interop.Visio.Shape.Copy](https://msdn.microsoft.com/library/office/ff765638.aspx), e [Microsoft.Office.Interop.Visio.Shape.Paste](https://msdn.microsoft.com/library/office/ff768361.aspx) métodos e [ Microsoft.Office.Interop.Visio.VisCutCopyPasteCodes.visCopyPasteNormal](https://msdn.microsoft.com/library/office/ff765187.aspx) sinalizador.  
  
#### <a name="to-copy-shapes-to-the-center-of-another-page"></a>Para copiar as formas no centro da outra página  
  
-   O exemplo a seguir demonstra como copiar as formas da primeira página e colá-los no centro da segunda página.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#14](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#14)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#14](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#14)]  
  
## <a name="copying-and-pasting-shapes-with-the-same-positions"></a>Copiando e colando formas com as mesmas posições  
 Para obter detalhes sobre o modelo de objeto, consulte a documentação de referência do VBA para o [Microsoft.Office.Interop.Visio.Shape.DrawRectangle](https://msdn.microsoft.com/library/office/ff765757.aspx), [Microsoft.Office.Interop.Visio.Shape.DrawOval](https://msdn.microsoft.com/library/office/ff767121.aspx), [ Microsoft.Office.Interop.Visio.Shape.Copy](https://msdn.microsoft.com/library/office/ff765638.aspx), e [Microsoft.Office.Interop.Visio.Shape.Paste](https://msdn.microsoft.com/library/office/ff768361.aspx) métodos e [ Microsoft.Office.Interop.Visio.VisCutCopyPasteCodes.visCopyPasteNoTranslate](https://msdn.microsoft.com/library/office/ff765187.aspx) sinalizador.  
  
 Se você precisar controlar o formato das informações coladas e (opcionalmente) estabelecer um link para um arquivo de origem (por exemplo, um documento do Word do Microsoft Office), use o método PasteSpecial.  
  
#### <a name="to-copy-shapes-and-shape-locations-to-another-page"></a>Para copiar formas e locais de forma para outra página  
  
-   O exemplo a seguir demonstra como copiar as formas da primeira página e colá-las na segunda página com seus locais originais de coordenada.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#15](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#15)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#15](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#15)]  
  
## <a name="see-also"></a>Consulte também  
 [Soluções do Visio](../vsto/visio-solutions.md)   
 [Visão geral do modelo de objeto do Visio](../vsto/visio-object-model-overview.md)   
 [Trabalhando com formas do Visio](../vsto/working-with-visio-shapes.md)   
 [Como adicionar formas a um documento do Visio de forma programática](../vsto/how-to-programmatically-add-shapes-to-a-visio-document.md)  
  
  