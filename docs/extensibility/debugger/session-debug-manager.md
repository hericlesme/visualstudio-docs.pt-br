---
title: "Sessão de depuração Manager | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- session debug manager, unifying session views
- session debug manager, broadcasting
- debugging [Debugging SDK], session debug manager
- session debug manager
- session debug manager, debug engine multiplexing
- session debug manager, delegating
ms.assetid: fbb1928d-dddc-43d1-98a4-e23b0ecbae09
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 7d7acd147fd8d2b73b2172900baf7e1f49808e9a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
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