---
title: Envio de eventos | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], sending events
ms.assetid: 064231e7-59b5-4437-8240-a23c0a7ec2a9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9bbe7946b866cd751be1f0dac2dba5b8dea57e04
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="sending-events"></a>Envio de eventos
O mecanismo para comunicação entre o depurador e o mecanismo de depuração (DE) é um modelo de evento com base em DCOM. Os eventos são enviados como objetos COM, e cada evento tem parâmetros que especificam o seguinte:  
  
-   O DE que o evento de chamada.  
  
-   Uma descrição do que aconteceu.  
  
-   O processo, programa e informações de thread que identifica o contexto do qual o evento ocorreu. O processo não é enviado para eventos enviados a partir DE.  
  
-   O tipo de evento que indica se o evento é síncrona ou assíncrona.  
  
 Todos os eventos de depuração são enviados usando o método [IDebugEventCallback2::Event](../../extensibility/debugger/reference/idebugeventcallback2-event.md).  
  
## <a name="in-this-section"></a>Nesta seção  
 [Fontes de evento](../../extensibility/debugger/event-sources-visual-studio-sdk.md)  
 Explica as duas origens de eventos: o mecanismo de depuração (DE) e a sessão de depuração do Gerenciador (SDM).  
  
 [Tipos de eventos com suporte](../../extensibility/debugger/supported-event-types.md)  
 Aborda os tipos com suporte no momento do evento: síncrono e assíncrono.  
  
 [Descrição do evento](../../extensibility/debugger/event-descriptions.md)  
 Define os eventos e os motivos para seu uso.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Criar um mecanismo de depuração personalizado](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 Descreve como a DE funciona com o sistema operacional ou interpretador para fornecer serviços de depuração.