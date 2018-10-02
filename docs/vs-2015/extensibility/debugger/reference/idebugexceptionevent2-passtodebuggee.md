---
title: IDebugExceptionEvent2::PassToDebuggee | Microsoft Docs
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
- IDebugExceptionEvent2::PassToDebuggee
helpviewer_keywords:
- IDebugExceptionEvent2::PassToDebuggee
ms.assetid: a20d0f0b-2ca0-4437-bd22-9213c81d2738
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9243bc7c9532e740bca6fd0faed44463a9dd9381
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47476339"
---
# <a name="idebugexceptionevent2passtodebuggee"></a>IDebugExceptionEvent2::PassToDebuggee
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [IDebugExceptionEvent2::PassToDebuggee](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee).  
  
Especifica se a exceção deve ser passada para o programa que está sendo depurado quando a execução é retomada, ou se a exceção deve ser descartada.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT PassToDebuggee(  
   BOOL fPass  
);  
```  
  
```csharp  
int PassToDebuggee(  
   int fPass  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `fPass`  
 [in] Diferente de zero (`TRUE`) se a exceção deve ser passada para o programa que está sendo depurado quando a execução é retomada, ou zero (`FALSE`) se a exceção deve ser descartada.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Chamar esse método não provoca nenhum código ser executado no programa que está sendo depurado. A chamada é simplesmente definir o estado para a próxima execução do código. Por exemplo, chamadas para o [CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) método pode retornar `S_OK` com o [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md).`dwState` campo definido como `EXCEPTION_STOP_SECOND_CHANCE`.  
  
 O IDE pode receber o [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) evento e a chamada a [continuar](../../../extensibility/debugger/reference/idebugprogram2-continue.md) método. O mecanismo de depuração (DES) deve ter um comportamento padrão para manipular o caso se o `PassToDebuggee` método não é chamado.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)   
 [CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)   
 [Continue](../../../extensibility/debugger/reference/idebugprogram2-continue.md)

