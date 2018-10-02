---
title: THREADPROPERTY_FIELDS | Microsoft Docs
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
- THREADPROPERTY_FIELDS
helpviewer_keywords:
- THREADPROPERTY_FIELDS enumeration
ms.assetid: 5b88acb9-03ea-4c29-a788-f0087dccbe23
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 861a7d51b69f72938750a3210c29b8ac560af016
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47462847"
---
# <a name="threadpropertyfields"></a>THREADPROPERTY_FIELDS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [THREADPROPERTY_FIELDS](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/threadproperty-fields).  
  
Especifica quais informações sobre um thread deve ser recuperado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
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
 Inicialização/usar o `dwThreadId` campo do [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) estrutura.  
  
 TPF_SUSPENDCOUNT  
 Inicialização/usar o `dwSuspendCount` campo do `THREADPROPERTIE`estrutura.  
  
 TPF_STATE  
 Inicialização/usar o `dwThreadState` campo do `THREADPROPERTIE`estrutura.  
  
 TPF_PRIORITY  
 Inicialização/usar o `bstrPriority` campo do `THREADPROPERTIE`estrutura.  
  
 TPF_NAME  
 Inicialização/usar o `bstrName` campo do `THREADPROPERTIE`estrutura.  
  
 TPF_LOCATION  
 Inicialização/usar o `bstrLocation` campo do `THREADPROPERTIE`estrutura.  
  
 TPF_ALLFIELDS  
 Especifica todos os campos.  
  
## <a name="remarks"></a>Comentários  
 Esses valores são passados como um argumento para o [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) método para indicar quais campos da [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) são de estrutura a ser inicializado.  
  
 Esses valores também são usados no `dwFields` membro o `THREADPROPERTIES` estrutura para indicar quais campos são usados e válido.  
  
 Esses sinalizadores podem ser combinados com um bit a bit `OR`.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)   
 [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)

