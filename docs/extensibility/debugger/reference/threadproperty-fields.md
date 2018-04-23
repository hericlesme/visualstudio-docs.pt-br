---
title: THREADPROPERTY_FIELDS | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- THREADPROPERTY_FIELDS
helpviewer_keywords:
- THREADPROPERTY_FIELDS enumeration
ms.assetid: 5b88acb9-03ea-4c29-a788-f0087dccbe23
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6c5733bfa889a38c1d143fdd3bfbd8f208fed13a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="threadpropertyfields"></a>THREADPROPERTY_FIELDS
Especifica quais informações sobre um segmento a ser recuperado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
enum enum_THREADPROPERTY_FIELDS {   
   TPF_ID           = 0x0001,  
   TPF_SUSPENDCOUNT = 0x0002,  
   TPF_STATE        = 0x0004,  
   TPF_PRIORITY     = 0x0008,  
   TPF_NAME         = 0x0010,  
   TPF_LOCATION     = 0x0020,  
   TPF_ALLFIELDS    = 0xffffffff  
};  
typedef DWORD THREADPROPERTY_FIELDS;  
```  
  
```csharp  
public enum enum_THREADPROPERTY_FIELDS {   
   TPF_ID           = 0x0001,  
   TPF_SUSPENDCOUNT = 0x0002,  
   TPF_STATE        = 0x0004,  
   TPF_PRIORITY     = 0x0008,  
   TPF_NAME         = 0x0010,  
   TPF_LOCATION     = 0x0020,  
   TPF_ALLFIELDS    = 0xffffffff  
};  
```  
  
## <a name="members"></a>Membros  
 TPF_ID  
 Inicializar/usar o `dwThreadId` campo o [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) estrutura.  
  
 TPF_SUSPENDCOUNT  
 Inicializar/usar o `dwSuspendCount` campo o `THREADPROPERTIE`estrutura.  
  
 TPF_STATE  
 Inicializar/usar o `dwThreadState` campo o `THREADPROPERTIE`estrutura.  
  
 TPF_PRIORITY  
 Inicializar/usar o `bstrPriority` campo o `THREADPROPERTIE`estrutura.  
  
 TPF_NAME  
 Inicializar/usar o `bstrName` campo o `THREADPROPERTIE`estrutura.  
  
 TPF_LOCATION  
 Inicializar/usar o `bstrLocation` campo o `THREADPROPERTIE`estrutura.  
  
 TPF_ALLFIELDS  
 Especifica todos os campos.  
  
## <a name="remarks"></a>Comentários  
 Esses valores são passados como um argumento para o [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) método para indicar quais campos do [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) estrutura devem ser inicializado.  
  
 Esses valores também são usados em `dwFields` membro o `THREADPROPERTIES` estrutura para indicar quais campos são usados e válido.  
  
 Esses sinalizadores podem ser combinados com um bit a bit `OR`.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)   
 [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)