---
title: Excluindo um ponto de interrupção | Microsoft Docs
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
- breakpoints, deleting
- debugging [Debugging SDK], deleting breakpoints
ms.assetid: 75a046cc-d20a-4c79-ad2d-1f18426ac5d0
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 18b88cc55a4c641e56c062356a9f74c2224835a8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47467594"
---
# <a name="deleting-a-breakpoint"></a>Excluindo um ponto de interrupção
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [excluindo um ponto de interrupção](https://docs.microsoft.com/visualstudio/extensibility/debugger/deleting-a-breakpoint).  
  
O exemplo a seguir descreve o processo ao excluir um ponto de interrupção pendente:  
  
## <a name="deletion-process"></a>Processo de exclusão  
 O Gerenciador de sessão de depuração (SDM) chama o [IDebugPendingBreakpoint2::Delete](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md) método para remover o ponto de interrupção pendente e acoplados todos os pontos de interrupção associado dele.  
  
> [!NOTE]
>  Também é possível excluir um único ponto de interrupção associado por uma chamada para [IDebugBoundBreakpoint2::Delete](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md).  
  
## <a name="see-also"></a>Consulte também  
 [Chamar eventos do depurador](../../extensibility/debugger/calling-debugger-events.md)

