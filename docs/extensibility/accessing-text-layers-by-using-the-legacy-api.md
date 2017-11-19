---
title: Acessando as camadas de texto usando a API herdado | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - text layers
ms.assetid: 2258fcdd-38d1-479d-b8f8-1d4e6525f72c
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 54a981a57605ccb93062ac0678b1e8b5673c6d1a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="accessing-text-layers-by-using-the-legacy-api"></a>Acessando as camadas de texto usando a API herdado
Normalmente, uma camada de texto encapsula alguns aspectos do layout de texto. Por exemplo, uma camada de "uma função no tempo" oculta o texto antes e depois de uma função que contém o cursor (ponto de inserção de texto).  
  
 Uma camada de texto reside entre um buffer e um modo de exibição e modifica o modo que de exibição vê o conteúdo do buffer.  
  
## <a name="text-layer-information"></a>Informações da camada de texto  
 A lista a seguir descreve como as camadas de texto funcionam [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]:  
  
-   O texto em uma camada de texto pode ser adornado com marcadores e cores de sintaxe.  
  
-   No momento, você não pode implementar seus próprio camadas.  
  
-   Expõe uma camada <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>, que é derivada de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>. O buffer de texto em si também é implementado como uma camada, o que permite que uma exibição polimorficamente lidar com camadas subjacentes.  
  
-   Qualquer número de camadas pode estar entre o modo de exibição e o buffer. Cada camada lida apenas com a camada abaixo dela, e o modo de exibição lida principalmente com a camada superior. (O modo de exibição tem algumas informações sobre o buffer).  
  
-   Uma camada pode afetar apenas as camadas que estão abaixo dele. Ele não afeta as camadas acima dele além da origem de eventos padrão.  
  
-   No editor de texto oculto, texto sintético e quebra automática de linha são implementados como camadas. Você pode implementar o texto oculto e sintético sem interagir diretamente com as camadas. Para obter mais informações, consulte [de estrutura de tópicos em um serviço de linguagem herdado](../extensibility/internals/outlining-in-a-legacy-language-service.md) e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSyntheticTextSession>.  
  
-   Cada camada de texto tem seu próprio sistema de coordenadas de local que é exposto por meio de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer> interface. A camada de quebra automática de linha, por exemplo, pode conter duas linhas enquanto o buffer de texto subjacente pode conter apenas uma linha.  
  
-   O modo de exibição se comunica com camadas por meio de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView> interface. Use esta interface para reconciliar as coordenadas de exibição com as coordenadas de buffer.  
  
-   Qualquer camada, como a camada de texto sintéticos que se origina o texto deve fornecer uma implementação de local de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CreateTrackingPoint%2A>.  
  
-   Além disso <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>, uma camada de texto deve implementar <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> e acionar eventos no <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents> interface.  
  
## <a name="see-also"></a>Consulte também  
 [Cores de sintaxe no editores personalizados](../extensibility/syntax-coloring-in-custom-editors.md)   
 [Usar marcadores de texto com a API herdado](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Personalizando Menus e controles do Editor usando a API herdado](../extensibility/customizing-editor-controls-and-menus-by-using-the-legacy-api.md)