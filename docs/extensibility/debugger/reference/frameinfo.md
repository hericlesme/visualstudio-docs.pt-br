---
title: FRAMEINFO | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- FRAMEINFO
helpviewer_keywords:
- FRAMEINFO structure
ms.assetid: 95001b89-dddb-45bb-889d-8327994e38a5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4080a0d868f154136b11058abdf29948a353b0ba
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31104196"
---
# <a name="frameinfo"></a>FRAMEINFO
Descreve um quadro de pilha.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
typedef struct tagFRAMEINFO {   
   FRAMEINFO_FLAGS    m_dwValidFields;  
   BSTR               m_bstrFuncName;  
   BSTR               m_bstrReturnType;  
   BSTR               m_bstrArgs;  
   BSTR               m_bstrLanguage;  
   BSTR               m_bstrModule;  
   UINT64             m_addrMin;  
   UINT64             m_addrMax;  
   IDebugStackFrame2* m_pFrame;  
   IDebugModule2*     m_pModule;  
   BOOL               m_fHasDebugInfo;  
   BOOL               m_fStaleCode;  
   BOOL               m_fAnnotatedFrame;  
} FRAMEINFO;  
```  
  
```csharp  
public struct FRAMEINFO {   
   public uint              m_dwValidFields;  
   public string            m_bstrFuncName;  
   public string            m_bstrReturnType;  
   public string            m_bstrArgs;  
   public string            m_bstrLanguage;  
   public string            m_bstrModule;  
   public ulong             m_addrMin;  
   public ulong             m_addrMax;  
   public IDebugStackFrame2 m_pFrame;  
   public IDebugModule2     m_pModule;  
   public int               m_fHasDebugInfo;  
   public int               m_fStaleCode;  
   public int               m_fAnnotatedFrame;  
} FRAMEINFO;  
```  
  
## <a name="members"></a>Membros  
 m_dwValidFields  
 Uma combinação de sinalizadores do [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md) enumeração que especifica quais campos são preenchidos.  
  
 m_bstrFuncName  
 O nome da função associado ao quadro de pilha.  
  
 m_bstrReturnType  
 O tipo de retorno associado com o quadro de pilha.  
  
 m_bstrArgs  
 Os argumentos para a função associada ao quadro de pilha.  
  
 m_bstrLanguage  
 O idioma no qual a função é implementada.  
  
 m_bstrModule  
 O nome do módulo associado ao quadro de pilha.  
  
 m_addrMin  
 O endereço de pilha física mínimo.  
  
 m_addrMAX  
 O endereço físico máximo da pilha.  
  
 m_pFrame  
 O [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) objeto que representa deste quadro de pilhas.  
  
 m_pFrame  
 O [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) objeto que representa o módulo que contém este quadro de pilha.  
  
 m_fHasDebugInfo  
 Diferente de zero (`TRUE`) se houver informações de depuração no quadro especificado.  
  
 m_fHasDebugInfo  
 Diferente de zero (`TRUE`) se o quadro de pilhas é associado com o código que não é mais válido.  
  
 m_fHasDebugInfo  
 Diferente de zero (`TRUE`) se o quadro de pilhas é anotado, o Gerenciador de sessão de depuração (SDM).  
  
## <a name="remarks"></a>Comentários  
 Essa estrutura é passada para o [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md) método a ser preenchido. Essa estrutura também está contida em uma lista que está contida no [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) interface que, por sua vez, é retornado de uma chamada para o [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) método.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Estruturas e uniões](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)   
 [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)   
 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)