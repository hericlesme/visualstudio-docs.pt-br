---
title: BoundsRules restringir o local de forma e tamanho | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Domain-Specific Language, events
ms.assetid: 4d08e541-fc67-4e68-bf31-30d346aa2aa0
caps.latest.revision: "18"
author: alancameronwills
ms.author: awills
manager: douge
ms.workload: multiple
ms.openlocfilehash: 81c6ab1f043074b4da601dbfe2d3dc52243b00e5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="boundsrules-constrain-shape-location-and-size"></a>BoundsRules restringem o local e o tamanho de uma forma
Um *limites regra* é uma classe que define limites sobre o tamanho e o local de uma forma. Ele fornece um método que é chamado repetidamente enquanto um usuário está arrastando uma forma ou cantos ou lados de uma forma.  
  
 O exemplo a seguir restringe uma forma retangular para ser uma barra de tamanho fixo, horizontal ou vertical. Quando o usuário arrasta cantos ou lados, a estrutura de tópicos inverte entre as duas configurações permitidas de altura e largura.  
  
 Os limites de regra é uma classe derivada de <xref:Microsoft.VisualStudio.Modeling.Diagrams.BoundsRules>. Uma instância da regra é criada na forma:  
  
```  
using Microsoft.VisualStudio.Modeling.Diagrams; ...  
public partial class BarShape  
{  
  /// <summary>  
  /// Rule invoked when the user is resizing a shape.  
  /// </summary>  
  public override BoundsRules BoundsRules  
  { get { return new BarBoundsRule(); } }  
}  
/// <summary>  
/// Rule invoked when the user is changing a shape's outline.  
/// Provides real-time mouse rubber-band feedback, so must work fast.  
/// </summary>  
public class BarBoundsRule: BoundsRules  
{   
  public override RectangleD GetCompliantBounds   
     (ShapeElement shape, RectangleD proposedBounds)  
  {  
    double thickness = 0.1;  
    if (proposedBounds.Height > proposedBounds.Width)  
    {  
      // There is a minimum width for a shape; the width  
      // will actually be set to the lesser of   
      // thickness and that minimum.  
      return new RectangleD(proposedBounds.Location,   
            new SizeD(thickness, proposedBounds.Height));  
    }  
    else  
    {  
      // There is a minimum height for a shape; the   
      // height will actually be set to the lesser of   
      // thickness and that minimum.  
      return new RectangleD(proposedBounds.Location,   
         new SizeD(proposedBounds.Width, thickness));  
} } }  
```  
  
 Observe que o local e o tamanho podem ser restringidas se desejar.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.Modeling.Diagrams.BoundsRules>   
 [Respondendo a alterações e propagando-as](../modeling/responding-to-and-propagating-changes.md)