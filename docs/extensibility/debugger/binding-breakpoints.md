---
title: "Associação de pontos de interrupção | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: breakpoints, binding
ms.assetid: 70737387-c52f-4dae-8865-77d4b203bf25
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 55416d6b156055d967424476f5add3b4ed75d18d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="binding-breakpoints"></a>Associação de pontos de interrupção
Se o usuário define um ponto de interrupção, talvez, pressionando F9, o IDE Formula a solicitação e solicita que a sessão de depuração para criar o ponto de interrupção.  
  
## <a name="setting-a-breakpoint"></a>Definindo um ponto de interrupção  
 Definindo um ponto de interrupção é um processo de duas etapas, porque o código ou com o ponto de interrupção de dados talvez ainda não estejam disponíveis. Primeiro, o ponto de interrupção deve ser descrito e, em seguida, como códigos ou dados se torna disponíveis, ele deve ser associado a esse código ou dados, da seguinte maneira:  
  
1.  O ponto de interrupção é solicitado dos mecanismos de depuração relevantes (DEs) e, em seguida, o ponto de interrupção está associado ao código ou dados assim que possível.  
  
2.  A solicitação de ponto de interrupção é enviada para a sessão de depuração, que envia para todos os DEs relevantes. Qualquer ir escolhido para lidar com o ponto de interrupção cria correspondente pendente de ponto de interrupção.  
  
3.  A sessão de depuração coleta os pontos de interrupção pendentes e envia-os de volta para o pacote de depuração (o componente de depuração do Visual Studio).  
  
4.  O pacote de depuração solicita que a sessão de depuração para associar o ponto de interrupção pendente no código ou dados. A sessão de depuração envia essa solicitação para todos os DEs relevantes.  
  
5.  Se o DE é capaz de associar o ponto de interrupção, ele enviará que um ponto de interrupção associado o evento para a sessão de depuração. Caso contrário, ele envia um evento de erro do ponto de interrupção em vez disso.  
  
## <a name="pending-breakpoints"></a>Pontos de interrupção pendentes  
 Um ponto de interrupção pendente pode vincular a vários locais de código. Por exemplo, uma linha do código-fonte para um modelo de C++ pode associar a cada sequência de código gerada a partir do modelo. A sessão de depuração pode usar um evento associado do ponto de interrupção para enumerar os contextos de código associados a um ponto de interrupção no momento em que o evento foi enviado. Contextos de código mais podem ser vinculados posteriormente, para que o DE pode enviar que várias ponto de interrupção associado eventos para cada solicitação de associação. No entanto, um DE deve enviar somente um evento de erro de ponto de interrupção por solicitação de associação.  
  
## <a name="implementation"></a>Implementação  
 Programaticamente, o pacote de depuração chama a depuração de sessão Gerenciador (SDM) e concede a ele um [IDebugBreakpointRequest2](../../extensibility/debugger/reference/idebugbreakpointrequest2.md) interface que encapsula uma [BP_REQUEST_INFO](../../extensibility/debugger/reference/bp-request-info.md) estrutura que descreve o ponto de interrupção a ser definido. Embora os pontos de interrupção podem ser de várias formas, eles apontam para um contexto de códigos ou dados.  
  
 O SDM passa essa chamada para cada relevantes DE chamando seu [CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) método. Se escolher o DE lidar com o ponto de interrupção, ele cria e retorna um [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) interface. O SDM coleta essas interfaces e os passa para o pacote de depuração como um único `IDebugPendingBreakpoint2` interface.  
  
 Até o momento, nenhum evento foi gerado.  
  
 O pacote de depuração, em seguida, tenta associar o ponto de interrupção pendente para códigos ou dados chamando [associar](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md), que é implementado por DE.  
  
 Se o ponto de interrupção está associado, envia o DE um [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) interface de eventos para o pacote de depuração. Os usos do pacote de depuração essa interface para enumerar todos os contextos de código (ou o contexto de dados único) associado ao ponto de interrupção chamando [EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md), que retorna um ou mais [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) interfaces. O [GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md) interface retorna um [IDebugBreakpointResolution2](../../extensibility/debugger/reference/idebugbreakpointresolution2.md) interface, e [GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) retorna um [BP_ RESOLUTION_INFO](../../extensibility/debugger/reference/bp-resolution-info.md) union contendo o contexto de códigos ou dados.  
  
 Se o DE não é possível associar o ponto de interrupção, ele enviará um único [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) interface de eventos para o pacote de depuração. O pacote de depuração recupera o tipo de erro (erro ou aviso) e a mensagem informativa chamando [GetErrorBreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md), seguido por [GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) e [ GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md). Isso retorna um [BP_ERROR_RESOLUTION_INFO](../../extensibility/debugger/reference/bp-error-resolution-info.md) estrutura que contém o tipo de erro e a mensagem.  
  
 Se um DE trata de um ponto de interrupção, mas não é possível vinculá-lo, ele retornará um erro de tipo `BPET_TYPE_ERROR`. O pacote de depuração responde exibindo uma caixa de diálogo de erro e o IDE coloca um glifo de exclamação dentro de glifo de ponto de interrupção à esquerda da linha do código-fonte.  
  
 Se um DE trata de um ponto de interrupção, não é possível associar a ele, mas algum outro ir pode associá-lo, ele retorna um aviso. O IDE responde colocando um glifo de ponto dentro de glifo de ponto de interrupção à esquerda da linha do código-fonte.  
  
## <a name="see-also"></a>Consulte também  
 [Tarefas de depuração](../../extensibility/debugger/debugging-tasks.md)