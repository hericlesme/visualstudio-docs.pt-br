---
title: IDebugEngine2::CreatePendingBreakpoint | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugEngine2::CreatePendingBreakpoint
helpviewer_keywords:
- IDebugEngine2::CreatePendingBreakpoint
ms.assetid: 92e85b90-a931-48d9-89a7-a6edcb83ae5a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6a0813e077d8bdc2ba024dc932a6cb571b1b2fed
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="idebugengine2creatependingbreakpoint"></a>IDebugEngine2::CreatePendingBreakpoint
Cria um ponto de interrupção pendente no mecanismo de depuração (DE).  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT CreatePendingBreakpoint(   
   IDebugBreakpointRequest2*  pBPRequest,  
   IDebugPendingBreakpoint2** ppPendingBP  
);  
```  
  
```csharp  
int CreatePendingBreakpoint(   
   IDebugBreakpointRequest2     pBPRequest,  
   out IDebugPendingBreakpoint2 ppPendingBP  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pBPRequest`  
 [in] Um [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) objeto que descreve o ponto de interrupção pendente para criar.  
  
 `ppPendingBP`  
 [out] Retorna um [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) objeto que representa o ponto de interrupção pendente.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro. Normalmente retorna `E_FAIL` se o `pBPRequest` parâmetro não corresponde a qualquer linguagem com suporte DE se o `pBPRequest` parâmetro é inválido ou incompleto.  
  
## <a name="remarks"></a>Comentários  
 Um ponto de interrupção pendente é essencialmente uma coleção de todas as informações necessárias para associar um ponto de interrupção no código. O ponto de interrupção pendente retornado deste método não está associado ao código até que o [associar](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) método é chamado.  
  
 Para cada pendente de ponto de interrupção conjuntos de dados do usuário, o Gerenciador de sessão de depuração (SDM) chama esse método em cada DE anexado. Cabe DE verificar se o ponto de interrupção é válido para programas em execução em que DE.  
  
 Quando o usuário define um ponto de interrupção em uma linha de código, o DE está livre para associar o ponto de interrupção para a linha mais próxima do documento que corresponde a esse código. Isso possibilita que o usuário definir um ponto de interrupção na primeira linha de uma instrução de várias linha, mas associá-lo na última linha (em que todo o código é atribuído nas informações de depuração).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como implementar esse método para um simples `CProgram` objeto. Implementação do `IDebugEngine2::CreatePendingBreakpoint` , em seguida, pode encaminhar todas as chamadas a esta implementação do método de cada programa.  
  
```  
HRESULT CProgram::CreatePendingBreakpoint(IDebugBreakpointRequest2* pBPRequest, IDebugPendingBreakpoint2** ppPendingBP)     
{    
  
   // Create and initialize the CPendingBreakpoint object.  
   CComObject<CPendingBreakpoint> *pPending;    
   CComObject<CPendingBreakpoint>::CreateInstance(&pPending);    
   pPending->Initialize(pBPRequest, m_pInterp, m_pCallback, m_pEngine);    
   return pPending->QueryInterface(ppPendingBP);    
}    
```  
  
## <a name="see-also"></a>Consulte também  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [Ligação](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)   
 [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)   
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)