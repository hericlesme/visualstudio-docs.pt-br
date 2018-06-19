---
title: IDebugMethodField::EnumAllLocals | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugMethodField::EnumAllLocals
helpviewer_keywords:
- IDebugMethodField::EnumAllLocals method
ms.assetid: 0bc7cc13-2628-4bd8-8c06-4d2aa6755ea8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8c3c13f7252e6f3b662ded697ab267419fd66450
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31113599"
---
# <a name="idebugmethodfieldenumalllocals"></a>IDebugMethodField::EnumAllLocals
Cria um enumerador para todas as variáveis locais do método, incluindo aqueles gerados internamente por um compilador.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT EnumAllLocals(   
   IDebugAddress*     pAddress,  
   IEnumDebugFields** ppLocals  
);  
```  
  
```csharp  
int EnumAllLocals(  
   IDebugAddress        pAddress,   
   out IEnumDebugFields ppLocals  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pAddress`  
 [in] Um [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) que representa um endereço de depuração no método, apontando para um determinado escopo ou contexto de objeto.  
  
 `ppLocals`  
 [out] Retorna um [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) objeto que representa a lista de todos os locais no escopo especificado; caso contrário, retornará um valor nulo, que indica nenhuma locais.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, Retorna S_OK ou retornará S_FALSE se não houver nenhum locais. Caso contrário, retornará um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Somente as variáveis definidas dentro do bloco que contém o endereço de depuração determinado são enumeradas. Esse método inclui qualquer locais geradas pelo compilador. Se todos os dados necessários são locais explicitamente definidos na fonte, chamada de [EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) método.  
  
 Um método pode conter vários contextos ou blocos de escopo.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)