---
title: FIELD_INFO_FIELDS | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- FIELD_INFO_FIELDS
helpviewer_keywords:
- FIELD_INFO_FIELDS enumeration
ms.assetid: a69487d2-e701-4165-804a-8a011df9a3bd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d74f39ce8e9e350c791371f20b7401d685fb1d18
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31102487"
---
# <a name="fieldinfofields"></a>FIELD_INFO_FIELDS
Especifica quais informações recuperar sobre um [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
enum enum_FIELD_INFO_FIELDS {   
   FIF_FULLNAME  = 0x0001,  
   FIF_NAME      = 0x0002,  
   FIF_TYPE      = 0x0004,  
   FIF_MODIFIERS = 0x0008,  
   FIF_ALL       = 0xffffffff,  
   FIF_NONE      = 0x0000  
};  
typedef DWORD FIELD_INFO_FIELDS;  
```  
  
```csharp  
public enum enum_FIELD_INFO_FIELDS {  
   FIF_FULLNAME  = 0x0001,  
   FIF_NAME      = 0x0002,  
   FIF_TYPE      = 0x0004,  
   FIF_MODIFIERS = 0x0008,  
   FIF_ALL       = 0xffffffff,  
   FIF_NONE      = 0x0000  
};  
```  
  
## <a name="members"></a>Membros  
 FIF_FULLNAME  
 Inicializar/usar o `bstrFullName` campo o [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) estrutura.  
  
 FIF_NAME  
 Inicializar/usar o `bstrName` campo o `FIELD_INFO` estrutura.  
  
 FIF_TYPE  
 Inicializar/usar o `bstrType` campo o `FIELD_INFO` estrutura.  
  
 FIF_MODIFIERS  
 Inicializar/usar o `bstrModifiers` campo o `FIELD_INFO` estrutura.  
  
## <a name="remarks"></a>Comentários  
 Esses valores também são passados como um argumento para o [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) método para especificar quais campos do [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) estrutura devem ser inicializado.  
  
 Esses valores também são usados no `dwFields` membro o `FIELD_INFO` estrutura para indicar quais campos são usados e válido.  
  
 Esses sinalizadores podem ser combinados com um bit a bit `OR`.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)