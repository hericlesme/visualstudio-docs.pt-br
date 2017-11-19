---
title: "Métodos de ponto de interrupção | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], breakpoint methods
- breakpoints, methods
ms.assetid: a6f77bf0-bf81-443f-8683-5f12075bbe10
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d0d743c98fd9e311f7f118c152e579178b07513d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="breakpoint-related-methods"></a>Métodos de ponto de interrupção
Um mecanismo de depuração (DE) deve dar suporte a configuração de pontos de interrupção. Depuração do Visual Studio suporta os seguintes tipos de pontos de interrupção:  
  
-   Associado  
  
     Solicitado por meio da interface do usuário e associado com êxito para um local de código especificada  
  
-   Pendente  
  
     Solicitado por meio de interface do usuário, mas ainda não é vinculado a real de instruções  
  
## <a name="discussion"></a>Discussão  
 Por exemplo, um ponto de interrupção pendente ocorre quando as instruções ainda não foram carregadas. Quando o código é carregado, pendente tente pontos de interrupção para associar ao código no local indicado, ou seja, para inserir instruções de interrupção no código. Eventos são enviados para o Gerenciador de sessão de depuração (SDM) para indicar a associação com êxito, ou para notificar que houve erros de associação.  
  
 Um ponto de interrupção pendente também gerencia sua própria lista interna de pontos de interrupção associada correspondente. Um pendente de ponto de interrupção pode causar a inserção de muitos pontos de interrupção no código. A depuração da interface do usuário do Visual Studio mostra uma exibição de árvore de pendente pontos de interrupção e seus correspondente associadas a pontos de interrupção.  
  
 Criação e uso de pendente pontos de interrupção exigem a implementação do [IDebugEngine2::CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) método, bem como os seguintes métodos de [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) interfaces.  
  
|Método|Descrição|  
|------------|-----------------|  
|[CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)|Determina se um especificado pendente de ponto de interrupção pode ser associado a um local de código.|  
|[Ligação](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)|Associa um especificado pendente de ponto de interrupção em um ou mais locais de código.|  
|[GetState](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)|Obtém o estado de um ponto de interrupção pendente.|  
|[GetBreakpointRequest](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)|Obtém a solicitação de ponto de interrupção usada para criar um ponto de interrupção pendente.|  
|[Habilitar](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)|Alterna o estado ativado de um ponto de interrupção pendente.|  
|[EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)|Enumera todos os pontos de interrupção associados de um ponto de interrupção pendente.|  
|[EnumErrorBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)|Enumera todos os pontos de interrupção de erro resultantes de um ponto de interrupção pendente.|  
|[Excluir](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)|Exclui um ponto de interrupção pendente e todos os pontos de interrupção associados dele.|  
  
 Para enumerar os pontos de interrupção associados e os pontos de interrupção de erro, você deve implementar todos os métodos de [IEnumDebugBoundBreakpoints2](../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md) e [IEnumDebugErrorBreakpoints2](../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md).  
  
 Pendente pontos de interrupção que se vincular a um código local exigem implementação dos seguintes [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) métodos.  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)|Obtém o ponto de interrupção pendente que contém um ponto de interrupção.|  
|[GetState](../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)|Obtém o estado de um ponto de interrupção associado.|  
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)|Obtém a resolução de ponto de interrupção que descreve um ponto de interrupção.|  
|[Habilitar](../../extensibility/debugger/reference/idebugboundbreakpoint2-enable.md)|Habilita ou desabilita um ponto de interrupção.|  
|[Excluir](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)|Exclui um ponto de interrupção associado.|  
  
 Resolução e solicitação de informações exigem a implementação dos seguintes [IDebugBreakpointResolution2](../../extensibility/debugger/reference/idebugbreakpointresolution2.md) métodos.  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetBreakpointType](../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)|Obtém o tipo do ponto de interrupção representado por uma resolução.|  
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)|Obtém as informações de resolução do ponto de interrupção que descreve um ponto de interrupção.|  
  
 Requer a resolução de erros que podem ocorrer durante a associação de implementação dos seguintes [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) métodos.  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)|Obtém o ponto de interrupção pendente que contém um ponto de interrupção de erro.|  
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md)|Obtém a resolução de erro do ponto de interrupção que descreve um ponto de interrupção de erro.|  
  
 Resolução de erros que podem ocorrer durante a associação também requer os seguintes métodos de [IDebugErrorBreakpointResolution2](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md).  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetBreakpointType](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md)|Obtém o tipo de um ponto de interrupção.|  
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)|Obtém as informações de resolução de um ponto de interrupção.|  
  
 Exibindo o código-fonte em um ponto de interrupção exige que você implemente os métodos de [IDebugStackFrame2::GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) e/ou os métodos de [IDebugStackFrame2::GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md).  
  
## <a name="see-also"></a>Consulte também  
 [Controle de execução e avaliação de estado](../../extensibility/debugger/execution-control-and-state-evaluation.md)