---
title: CONTEXT_INFO | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- CONTEXT_INFO
helpviewer_keywords:
- CONTEXT_INFO structure
ms.assetid: 6b513f4e-e7b0-4969-adf0-2205ccc1e09b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fb634f59a3a7eb3b37e70dd87f48b22a07251d0e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31100426"
---
# <a name="contextinfo"></a>CONTEXT_INFO
Essa estrutura descreve um contexto de memória ou o contexto de código.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
typedef struct _tagCONTEXT_INFO {   
   CONTEXT_INFO_FIELDS dwFields;  
   BSTR                bstrModuleUrl;  
   BSTR                bstrFunction;  
   TEXT_POSITION       posFunctionOffset;  
   BSTR                bstrAddress;  
   BSTR                bstrAddressOffset;  
   BSTR                bstrAddressAbsolute;  
} CONTEXT_INFO;  
```  
  
```csharp  
public struct CONTEXT_INFO {  
   public uint          dwFields;  
   public string        bstrModuleUrl;  
   public string        bstrFunction;  
   public TEXT_POSITION posFunctionOffset;  
   public string        bstrAddress;  
   public string        bstrAddressOffset;  
   public string        bstrAddressAbsolute;  
};  
```  
  
## <a name="members"></a>Membros  
 dwFields  
 Uma combinação de sinalizadores de ele [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md) enumeração que especifica quais campos são preenchidos **.**  
  
 bstrModuleUrl  
 O nome do módulo onde se encontra o contexto.  
  
 bstrFunction  
 O nome da função onde se encontra o contexto.  
  
 posFunctionOffset  
 Um [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) estrutura que identifica o deslocamento de linha e coluna da função associada ao contexto de código.  
  
 bstrAddress  
 O endereço no código onde se encontra o contexto determinado.  
  
 bstrAddressOffset  
 O deslocamento do endereço no código onde se encontra o contexto determinado.  
  
 bstrAddressAbsolute  
 O endereço absoluto na memória onde se encontra o contexto determinado.  
  
## <a name="remarks"></a>Comentários  
 Essa estrutura é retornada de uma chamada para o [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md) método.  
  
 Um uso típico para esta estrutura é suportados um **memória** janela de depuração.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Estruturas e uniões](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)   
 [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)