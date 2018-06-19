---
title: Sessão de depuração Manager | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- session debug manager, unifying session views
- session debug manager, broadcasting
- debugging [Debugging SDK], session debug manager
- session debug manager
- session debug manager, debug engine multiplexing
- session debug manager, delegating
ms.assetid: fbb1928d-dddc-43d1-98a4-e23b0ecbae09
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 001c0b954cd47b9825a6982f2474d6fd6d415e23
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31126221"
---
# <a name="session-debug-manager"></a>Gerenciador de sessão de depuração
O Gerenciador de sessão de depuração (SDM) gerencia qualquer número de mecanismos de depuração (DE) qualquer número de programas em vários processos em qualquer número de máquinas de depuração. Além de ser um mecanismo de depuração multiplexador, o SDM fornece uma exibição unificada da sessão de depuração para o IDE.  
  
## <a name="session-debug-manager-operation"></a>Operação do Gerenciador de depuração de sessão  
 O Gerenciador de sessão de depuração (SDM) gerencia DE. Pode haver mais de um mecanismo de depuração em execução em um computador ao mesmo tempo. Para multiplexar o DEs, o SDM envolve um número de interfaces do DEs e expõe o IDE como uma única interface.  
  
 Para aumentar o desempenho, algumas interfaces não são multiplexadas. Em vez disso, eles são usados diretamente a partir DE, e o SDM não vão chamadas a essas interfaces. Por exemplo, interfaces usadas com memória, código e contextos de documento não são multiplexadas, porque eles fazem referência a uma instrução específica, memória ou documento em um programa específico depurado por um específico DE. Não há outros ir deve ser envolvido no nível de comunicação.  
  
 Isso não é verdadeiro para todos os contextos. Chamadas para a interface de contexto de avaliação de expressão percorrer o SDM. Durante a avaliação da expressão, o SDM encapsula o [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interface que ele fornece ao IDE porque quando essa expressão é avaliada, pode envolver vários DEs que está depurando programas no mesmo processo que podem ser em execução no mesmo thread.  
  
 O SDM normalmente funciona como um mecanismo de delegação, mas ele pode atuar como um mecanismo de difusão. Por exemplo, durante a avaliação da expressão, o SDM funciona como um mecanismo de difusão para notificar todos os DEs que eles podem executar código em um thread especificado. Da mesma forma, quando o SDM recebe um evento de interrupção, ele transmite para todos os programas que devem interromper a execução. Quando uma etapa é chamada, o SDM transmite para todos os programas que eles podem continuar em execução. Pontos de interrupção também são transmitidos para cada DE.  
  
 O SDM não controla o programa atual, thread ou quadro de pilhas. O processo, programa e thread informações são enviadas para o SDM em conjunto com eventos de depuração específicos.  
  
## <a name="see-also"></a>Consulte também  
 [Mecanismo de depuração](../../extensibility/debugger/debug-engine.md)   
 [Componentes do depurador](../../extensibility/debugger/debugger-components.md)   
 [Contextos do depurador](../../extensibility/debugger/debugger-contexts.md)