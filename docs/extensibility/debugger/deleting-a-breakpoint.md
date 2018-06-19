---
title: Excluir um ponto de interrupção | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, deleting
- debugging [Debugging SDK], deleting breakpoints
ms.assetid: 75a046cc-d20a-4c79-ad2d-1f18426ac5d0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2bff63c243590db91ea97055943b89d73ea00308
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31104424"
---
# <a name="deleting-a-breakpoint"></a>Excluir um ponto de interrupção
O exemplo a seguir descreve o processo ao excluir um ponto de interrupção pendente:  
  
## <a name="deletion-process"></a>Processo de exclusão  
 O Gerenciador de sessão de depuração (SDM) chama o [IDebugPendingBreakpoint2::Delete](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md) método para remover o ponto de interrupção pendente e associados de todos os pontos de interrupção associado dele.  
  
> [!NOTE]
>  Também é possível excluir um único ponto de interrupção associado por uma chamada para [IDebugBoundBreakpoint2::Delete](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md).  
  
## <a name="see-also"></a>Consulte também  
 [Chamar eventos do depurador](../../extensibility/debugger/calling-debugger-events.md)