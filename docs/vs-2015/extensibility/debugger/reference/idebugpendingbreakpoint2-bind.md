---
title: IDebugPendingBreakpoint2::Bind | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugPendingBreakpoint2::Bind
helpviewer_keywords:
- Bind method
- IDebugPendingBreakpoint2::Bind method
ms.assetid: 46e3f307-219d-40cd-a929-d41399c60ecf
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cd8ab4846796e872cc7de97e82efa719405d99c4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47468297"
---
# <a name="idebugpendingbreakpoint2bind"></a>IDebugPendingBreakpoint2::Bind
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [IDebugPendingBreakpoint2::Bind](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugpendingbreakpoint2-bind).  
  
Associa a esse ponto de interrupção pendente para um ou mais locais de código.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT Bind(   
   void   
);  
```  
  
```csharp  
int Bind();  
```  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro. Retorna `E_BP_DELETED` se o ponto de interrupção tiver sido excluído.  
  
## <a name="remarks"></a>Comentários  
 Quando este método é chamado, um mecanismo de depuração (DES) deve tentar associar este ponto de interrupção pendente para todos os locais de código que correspondem.  
  
 Depois que esse método retorna, o chamador precisa aguardar por eventos que indica que o ponto de interrupção pendente tiver associado ou é um erro antes de assumir que as chamadas para o [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md) ou [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)métodos vai enumerar todos os limite ou erro de pontos de interrupção, respectivamente.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)   
 [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)   
 [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)   
 [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)

