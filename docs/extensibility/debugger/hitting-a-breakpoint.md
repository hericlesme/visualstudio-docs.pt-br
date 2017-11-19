---
title: "Alcançar um ponto de interrupção | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], hitting breakpoints
- breakpoints, hitting
ms.assetid: a77816e3-b15b-46a0-90cd-be7242e4d6c9
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 73cdce5415dd50059dcd443f67424203430aba87
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="hitting-a-breakpoint"></a>Alcançar um ponto de interrupção
O seguinte descreve o processo quando o mecanismo de depuração (DE) atinge um ponto de interrupção durante a execução passo a passo:  
  
## <a name="troubleshooting-a-hit-breakpoint"></a>Solucionando problemas de um ponto de interrupção de ocorrência  
  
1.  O envia DE um [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) interface como um **EVENT_SYNC_STOP**.  
  
2.  O Gerenciador de sessão de depuração (SDM) chama [IDebugBreakpointEvent2:::EnumBreakpoints](../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) para obter o ponto de interrupção foi atingido.  
  
## <a name="see-also"></a>Consulte também  
 [Chamar eventos do depurador](../../extensibility/debugger/calling-debugger-events.md)