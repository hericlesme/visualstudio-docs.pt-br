---
title: Entrar no modo de quebra | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- break mode
- debugging [Debugging SDK], entering break mode
ms.assetid: e9a8a241-cd21-4d4e-999a-283554c288b1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bb601ca4cf00ca2cc811f75ec27ad12bc6be32db
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="entering-break-mode"></a>Entrar no modo de interrupção
O exemplo a seguir descreve o processo que ocorre quando um ponto de interrupção é encontrado após entrar em uma função, executando para a linha do código-fonte que contém o cursor ou para um ponto de interrupção.  
  
## <a name="break-mode-process"></a>Processo do modo de interrupção  
  
1.  O mecanismo de depuração (DE) envia [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md), [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md), ou qualquer outro evento de interrupção para fazer com que o IDE entrar no modo de interrupção.  
  
2.  O SDM obtém as informações de pilha de chamada do thread, da seguinte maneira:  
  
    -   [IDebugThread2::EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)  
  
    -   [IEnumDebugFrameInfo2::GetCount](../../extensibility/debugger/reference/ienumdebugframeinfo2-getcount.md)  
  
    -   [IEnumDebugFrameInfo2::Next](../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md)  
  
    -   [IDebugStackFrame2::GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) para obter as informações de código fonte  
  
    -   [IDebugDocumentContext2::GetName](../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md) para obter o nome do arquivo  
  
    -   [IDebugDocumentContext2::GetStatementRange](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md) para obter o intervalo de instrução  
  
    -   [IDebugStackFrame2::GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md) para obter informações de memória  
  
## <a name="see-also"></a>Consulte também  
 [Chamar eventos do depurador](../../extensibility/debugger/calling-debugger-events.md)