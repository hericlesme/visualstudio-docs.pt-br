---
title: IDebugProgramNodeAttach2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProgramNodeAttach2
helpviewer_keywords:
- IDebugProgramNodeAttach2 interface
ms.assetid: 46b37ac9-a026-4ad3-997b-f19e2f8deb73
caps.latest.revision: 3
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 1ff6b3aa49030ed49a05cb81e0a949c7bc55806c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprogramnodeattach2"></a>IDebugProgramNodeAttach2
Permite que um nó de programa ser notificado de uma tentativa de anexar ao programa associado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugProgramNodeAttach2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 Essa interface é implementada na mesma classe que implementa o [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) interface para receber a notificação de uma operação de anexação e dar a oportunidade de cancelar a operação de anexação.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Obter essa interface chamando o `QueryInterface` método em um [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) objeto. O [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) método deve ser chamado antes do [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) método para fornecer o nó de programa a oportunidade de interromper o processo de conexão.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem Vtable  
 Essa interface implementa o método a seguir:  
  
|Método|Descrição|  
|------------|-----------------|  
|[OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)|Anexa ao programa associado ou adia o processo de conexão para o [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) método.|  
  
## <a name="remarks"></a>Comentários  
 Esta interface é a opção preferencial ao preterido [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md) método. Todos os mecanismos de depuração são sempre carregados com o `CoCreateInstance` funcionar, ou seja, eles são instanciados fora do espaço de endereço do programa que está sendo depurado.  
  
 Se uma implementação anterior do `IDebugProgramNode2::Attach_V7` método simplesmente foi definindo o `GUID` do programa que está sendo depurado, em seguida, somente o [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) método precisa ser implementado.  
  
 Se uma implementação anterior do `IDebugProgramNode2::Attach_V7` método usado a interface de retorno de chamada que foi fornecida, em seguida, essa funcionalidade precisa ser movido para uma implementação do [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) método e o `IDebugProgramNodeAttach2` interface não precisa ser implementado.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [Anexar](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)