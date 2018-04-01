---
title: PROVIDER_PROCESS_DATA | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- PROVIDER_PROCESS_DATA
helpviewer_keywords:
- PROVIDER_PROCESS_DATA structure
ms.assetid: ec2362ed-4a0c-4a09-9d66-8ff04e4f41ee
caps.latest.revision: 9
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 57b4b23f9bc723ee1ce7a10d12eb9fee0355d8ef
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="providerprocessdata"></a>PROVIDER_PROCESS_DATA
Essa estrutura fornece informações sobre os processos em execução em um computador.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
typedef struct tagPROVIDER_PROCESS_DATA {  
   PROVIDER_FIELDS    Fields;  
   PROGRAM_NODE_ARRAY ProgramNodes;  
   BOOL               fIsDebuggerPresent;  
} PROVIDER_PROCESS_DATA;  
```  
  
```csharp  
public struct PROVIDER_PROCESS_DATA {  
   public uint               Fields;  
   public PROGRAM_NODE_ARRAY ProgramNodes;  
   public int                fIsDebuggerPresent;  
}  
```  
  
## <a name="members"></a>Membros  
 Campos  
 Uma combinação de sinalizadores do [PROVIDER_FIELDS](../../../extensibility/debugger/reference/provider-fields.md) enumeração, que indica quais campos são preenchidos.  
  
 ProgramNodes  
 Um [PROGRAM_NODE_ARRAY](../../../extensibility/debugger/reference/program-node-array.md) estrutura que contém uma matriz de nós de programa.  
  
 fIsDebuggerPresent  
 Diferente de zero (`TRUE`) se o [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] depurador está em execução, zero (`FALSE`) se não for.  
  
## <a name="remarks"></a>Comentários  
 Essa estrutura é passada para o [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) método em que ele é preenchido.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Estruturas e uniões](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [PROVIDER_FIELDS](../../../extensibility/debugger/reference/provider-fields.md)   
 [PROGRAM_NODE_ARRAY](../../../extensibility/debugger/reference/program-node-array.md)   
 [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)