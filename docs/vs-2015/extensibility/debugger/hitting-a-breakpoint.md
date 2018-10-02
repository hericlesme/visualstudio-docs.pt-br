---
title: Atingindo um ponto de interrupção | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], hitting breakpoints
- breakpoints, hitting
ms.assetid: a77816e3-b15b-46a0-90cd-be7242e4d6c9
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 394ff3ba3826240df43faea4acd4aee107de1969
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47472846"
---
# <a name="hitting-a-breakpoint"></a>Atingindo um ponto de interrupção
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [atingir um ponto de interrupção](https://docs.microsoft.com/visualstudio/extensibility/debugger/hitting-a-breakpoint).  
  
O exemplo a seguir descreve o processo quando o mecanismo de depuração (DES) atinge um ponto de interrupção durante a execução ou passo a passo:  
  
## <a name="troubleshooting-a-hit-breakpoint"></a>Solução de problemas de um ponto de interrupção de ocorrência  
  
1.  O envia DE um [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) interface como um **EVENT_SYNC_STOP**.  
  
2.  O Gerenciador de sessão de depuração (SDM) chama [IDebugBreakpointEvent2:::EnumBreakpoints](../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) para obter o ponto de interrupção foi atingido.  
  
## <a name="see-also"></a>Consulte também  
 [Chamar eventos do depurador](../../extensibility/debugger/calling-debugger-events.md)

