---
title: "Entrando no modo de interrupção | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- break mode, stepping
- stepping, in break mode
- debugging [Debugging SDK], stepping in break mode
ms.assetid: b08dc8ee-6c63-4462-a097-6f525cfbb35a
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 011de9ce3e4e1445354f907dcf56a0f4ecbef6bc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="stepping-in-break-mode"></a>Entrando no modo de interrupção
O exemplo a seguir descreve o processo que ocorre quando o depurador está no modo de interrupção e deve percorrer o código:  
  
## <a name="stepping-process"></a>Processo de revisão  
  
1.  Chamar [IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md) com [STEPKIND](../../extensibility/debugger/reference/stepkind.md) e [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) argumentos para executar uma etapa.  
  
2.  Quando a etapa for concluída, enviar um [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) como um evento de parada.  
  
## <a name="see-also"></a>Consulte também  
 [Chamar eventos do depurador](../../extensibility/debugger/calling-debugger-events.md)