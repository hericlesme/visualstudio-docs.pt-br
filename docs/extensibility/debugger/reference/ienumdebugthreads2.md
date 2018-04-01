---
title: IEnumDebugThreads2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IEnumDebugThreads2
helpviewer_keywords:
- IEnumDebugThreads2
ms.assetid: 1854f078-3b49-42c2-b65b-33e3b506fd63
caps.latest.revision: 11
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: b03d9adbec92986ea8a1cf0f589bd451107a611f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ienumdebugthreads2"></a>IEnumDebugThreads2
Esta interface do enumera os threads em execução na sessão de depuração atual.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IEnumDebugThreads2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 O mecanismo de depuração (DE) implementa essa interface para representar uma lista de segmentos em um programa.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Chamar [EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md) para obter essa interface que representa uma lista de todos os threads em todos os programas em execução em um processo. Chamar [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) para obter essa interface que representa uma lista de segmentos em execução em um programa.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem Vtable  
 A tabela a seguir mostra os métodos de `IEnumDebugThreads2`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[Avançar](../../../extensibility/debugger/reference/ienumdebugthreads2-next.md)|Recupera um número especificado de threads na sequência de enumeração.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugthreads2-skip.md)|Ignora um número especificado de threads em uma sequência de enumeração.|  
|[Redefinir](../../../extensibility/debugger/reference/ienumdebugthreads2-reset.md)|Redefine uma sequência de enumeração para o início.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugthreads2-clone.md)|Cria um enumerador que contém o mesmo estado de enumeração do ano atual.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugthreads2-getcount.md)|Obtém o número de threads em um enumerador.|  
  
## <a name="remarks"></a>Comentários  
 O Visual Studio normalmente obtém essa interface para atualizar o **Threads** janela, bem como para obter o primeiro thread da lista, para chamar [Execute](../../../extensibility/debugger/reference/idebugprocess3-execute.md), [continuar](../../../extensibility/debugger/reference/idebugprocess3-continue.md), e [Etapa](../../../extensibility/debugger/reference/idebugprocess3-step.md).  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)   
 [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)   
 [Etapa](../../../extensibility/debugger/reference/idebugprocess3-step.md)   
 [Continuar](../../../extensibility/debugger/reference/idebugprocess3-continue.md)   
 [Executar](../../../extensibility/debugger/reference/idebugprocess3-execute.md)