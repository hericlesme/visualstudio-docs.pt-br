---
title: 'Como: disparar eventos quando o Editor perde o foco | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - fire events on losing focus
ms.assetid: 64d40695-6917-468a-8037-a253453ac159
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bbdcf30443bc548fd8d182db301cbc7119d8ceae
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
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