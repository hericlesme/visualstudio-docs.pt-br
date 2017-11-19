---
title: 'Como: disparar eventos quando o Editor perde o foco | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - fire events on losing focus
ms.assetid: 64d40695-6917-468a-8037-a253453ac159
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9a566d52dc1aabb9895e2f1f9751fdb37ae016d6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-fire-events-when-the-editor-loses-focus"></a>Como: disparar eventos quando o Editor perde o foco
Às vezes, é necessário saber quando um editor perde o foco no quadro da janela. Por exemplo, você precisará extrair o código de uma janela de código depois que o editor não está mais focalizado nele. O procedimento a seguir fornece as etapas a seguir para receber uma notificação do editor perdendo o foco.  
  
### <a name="to-fire-an-event-in-response-to-an-editor-losing-focus"></a>Para disparar um evento em resposta a um editor perdendo o foco  
  
1.  Monitorar eventos de seleção obtendo um <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> de objeto <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>.  
  
2.  Chamar <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.AdviseSelectionEvents%2A> e fornecê-la a <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents> objeto.  
  
3.  Em sua chamada a <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A>, procure `elementid==SEID_WindowFrame`.  
  
4.  Teste o `varValueNew` parâmetro para duas coisas:  
  
    1.  O quadro de janela que você está procurando.  
  
    2.  O ponto no qual seu programa perde a seleção do quadro de janela.