---
title: 'Como: registrar para eventos de Buffer de texto com a API herdado | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - register for text buffer events
ms.assetid: 5fc00ced-882c-4b48-b46c-1fa5a2469f94
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b708507096e7035039e54af7505c8f5f939b5724
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31127225"
---
# <a name="how-to-register-for-text-buffer-events-with-the-legacy-api"></a>Como: registrar eventos de Buffer de texto com a API herdado de
Se você estiver acessando o buffer de texto usando a API herdada, você deve registrar para eventos de buffer de texto conforme mostrado no procedimento a seguir.  
  
### <a name="to-advise-text-buffer-events"></a>Para eventos de buffer de texto de aviso  
  
1.  De um ponteiro para uma das interfaces no <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>, chame `QueryInterface` para um ponteiro para <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>.  
  
2.  Chamar o <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer.FindConnectionPoint%2A> método e passar a ID de interface de eventos para o qual você deseja registrar.  
  
     Por exemplo, se você deseja registrar para <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents>, em seguida, passar uma ID de IID_IVsTextLinesEvents de interface.  
  
     O buffer de texto retorna um ponteiro para o <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> interface para o objeto de ponto de conexão apropriado.  
  
3.  Usando esse ponteiro, chame o <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A> método, passando um ponteiro para a implementação da interface de eventos para o qual você deseja registrar, por exemplo, o `IVsTextLinesEvents` interface.  
  
     O ambiente retorna um cookie que você pode usar para parar de escutar eventos chamando o <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Unadvise%2A> método.  
  
## <a name="see-also"></a>Consulte também  
 [Eventos de Buffer de texto na API herdado](../extensibility/text-buffer-events-in-the-legacy-api.md)