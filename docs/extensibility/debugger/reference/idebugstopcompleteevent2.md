---
title: IDebugStopCompleteEvent2 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IDebugStopCompleteEvent2 interface
ms.assetid: ff3e89f4-61bb-489d-901c-447260100218
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2e92138f969189a33e1a5aad5a083c8ac57852dc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugstopcompleteevent2"></a>IDebugStopCompleteEvent2
O mecanismo de depuração (DE) pode enviar esse evento opcional para o Gerenciador de sessão de depuração (SDM) quando um programa foi interrompido.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugStopCompleteEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 Isso é uma nova interface para [!INCLUDE[vsprvslong](../../../code-quality/includes/vsprvslong_md.md)]. Versões anteriores não oferecia suporte a interrupção assíncrona.  
  
 [Parar](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) é chamado pelo SDM em vários processos ou programas vários cenários. Quando um programa envia um evento de parada para o SDM, o SDM solicitações de outros programas, muito.  
  
 Ele é usado para informar assincronamente o SDM um programa foi interrompido. Isso é útil para um mecanismo de depuração de intérprete, às vezes, onde nenhum código é executado dentro do programa depurado, portanto [parar](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) não pode ser concluída de forma síncrona. Se um mecanismo de depuração deseja empregar essa notificação assíncrona, ela deve retornar `S_ASYNC_STOP` de [parar](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md).  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll