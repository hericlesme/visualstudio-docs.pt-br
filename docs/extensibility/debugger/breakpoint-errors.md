---
title: "Erros de ponto de interrupção | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- breakpoints, errors
- debugging [Debugging SDK], breakpoint errors
- errors [Debugging SDK]
ms.assetid: 79221c6b-a924-4c8e-a778-e312e4e0c0c8
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 9cd9347290199ce695f7b2f42733ad8e5d108ac0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="breakpoint-errors"></a>Erros de ponto de interrupção
O seguinte descreve o processo quando um ponto de interrupção tenta associar ao código, mas falha:  
  
## <a name="troubleshooting-a-breakpoint-error"></a>Solucionando problemas de um erro de ponto de interrupção  
  
1.  O mecanismo de depuração (DE) envia um [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) para o Gerenciador de sessão de depuração (SDM).  
  
2.  As chamadas SDM [IDebugBreakpointErrorEvent2::GetErrorBreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md) (IDebugErrorBreakpoint2 * * `ppErrorBP`) para obter o ponto de interrupção de erro.  
  
3.  As chamadas SDM [IDebugErrorBreakpoint2::GetPendingBreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md) para obter o ponto de interrupção pendente do qual o ponto de interrupção de erro foi originado.  
  
4.  As chamadas SDM [IDebugErrorBreakpoint2::GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) para obter a razão por que o ponto de interrupção de erro Falha ao associar.  
  
## <a name="see-also"></a>Consulte também  
 [Chamar eventos do depurador](../../extensibility/debugger/calling-debugger-events.md)