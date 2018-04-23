---
title: FIELD_INFO | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- FIELD_INFO
helpviewer_keywords:
- FIELD_INFO structure
ms.assetid: bfafef6d-0c83-43d7-a779-1f0d24b166a1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 180a968f642b8a4bf26e2e69d1d3ddff45dc1f25
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="fieldinfo"></a>FIELD_INFO
Essa estrutura descreve uma variável local, parâmetro ou outro campo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
typedef struct _tagFieldInfo {   
   FIELD_INFO_FIELDS dwFields;  
   BSTR              bstrFullName;  
   BSTR              bstrName;  
   BSTR              bstrType;  
   FIELD_MODIFIERS   dwModifiers;  
} FIELD_INFO;  
```  
  
```csharp  
public struct FIELD_INFO {  
   public uint   dwFields;  
   public string bstrFullName;  
   public string bstrName;  
   public string bstrType;  
   public uint   dwModifiers;  
};  
```  
  
## <a name="members"></a>Membros  
 dwFields  
 Uma combinação de sinalizadores do [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md) enumeração que especifica quais membros são preenchidos.  
  
 bstrFullName  
 O nome completo do campo.  
  
 bstrName  
 O nome curto do campo.  
  
 bstrType  
 O tipo do campo.  
  
 dwModifiers  
 Uma combinação de sinalizadores do [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md) enumeração que descreve o campo.  
  
## <a name="remarks"></a>Comentários  
 Essa estrutura é passada para o [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) método em que ele é preenchido.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Estruturas e uniões](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md)   
 [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)