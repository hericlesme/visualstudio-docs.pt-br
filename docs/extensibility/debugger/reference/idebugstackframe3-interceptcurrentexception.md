---
title: IDebugStackFrame3::InterceptCurrentException | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugStackFrame3::InterceptCurrentException
helpviewer_keywords: IDebugStackFrame3::InterceptCurrentException
ms.assetid: 116c7324-7645-4c15-b484-7a5cdd065ef5
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9631f2206705ef6daf36b355aa6cb1d5be6458d4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugstackframe3interceptcurrentexception"></a>IDebugStackFrame3::InterceptCurrentException
Chamado pelo depurador no quadro de pilhas atual quando quer interceptar a exceção atual.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT InterceptCurrentException(  
   INTERCEPT_EXCEPTION_ACTION dwFlags,  
   UINT64*                    pqwCookie  
);  
```  
  
```csharp  
int InterceptCurrentException(  
   uint dwFlags,   
   out  ulong pqwCookie  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dwFlags`  
 [in] Especifica as ações diferentes. Atualmente, apenas o [INTERCEPT_EXCEPTION_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md) valor `IEA_INTERCEPT` é suportado e deve ser especificado.  
  
 `pqwCookie`  
 [out] Valor exclusivo que identifica uma exceção específica.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará S_OK; Caso contrário, retorna um código de erro.  
  
 A seguir estão os retornos de erro mais comuns.  
  
|Erro|Descrição|  
|-----------|-----------------|  
|`E_EXCEPTION_CANNOT_BE_INTERCEPTED`|A exceção atual não pode ser interceptada.|  
|`E_EXCEPTION_CANNOT_UNWIND_ABOVE_CALLBACK`|O quadro atual da execução ainda não foi pesquisado para um manipulador.|  
|`E_INTERCEPT_CURRENT_EXCEPTION_NOT_SUPPORTED`|Esse método não tem suporte para este quadro.|  
  
## <a name="remarks"></a>Comentários  
 Quando uma exceção for lançada, o depurador assumir o controle de tempo de execução nos pontos-chave durante o processo de manipulação de exceções. Durante esses momentos chave, o depurador pode solicitar que o quadro de pilhas atual se o quadro deseja interceptar a exceção. Dessa forma, uma exceção interceptada é essencialmente um manipulador de exceção durante a execução de um quadro de pilha, mesmo se esse quadro de pilha não tiver um manipulador de exceção (por exemplo, um bloco try/catch no código de programa).  
  
 Quando o depurador deseja saber se a exceção deve ser interceptada, ele chama esse método no objeto de quadro de pilha atual. Esse método é responsável pelo tratamento todos os detalhes da exceção. Se o [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md) interface não foi implementada ou a `InterceptStackException` método retorna qualquer erro, então o depurador continua a processar a exceção normalmente.  
  
> [!NOTE]
>  Exceções podem ser interceptadas apenas em código gerenciado, ou seja, quando o programa que está sendo depurado está em execução em tempo de execução .NET. Naturalmente, os implementadores de linguagem de terceiros podem implementar `InterceptStackException` em seus próprios mecanismos de depuração se eles assim escolhem.  
  
 Depois que a interceptação for concluída, um [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md) é sinalizado.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)   
 [INTERCEPT_EXCEPTION_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md)   
 [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)