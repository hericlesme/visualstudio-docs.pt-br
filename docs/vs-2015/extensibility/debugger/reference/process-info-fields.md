---
title: PROCESS_INFO_FIELDS | Microsoft Docs
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
- PROCESS_INFO_FIELDS
helpviewer_keywords:
- PROCESS_INFO_FIELDS enumeration
ms.assetid: 0d9cc345-3d3a-44d8-ae15-a67acb97a828
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8b272fba2e05c25e60b2db1f11be16b97d261101
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47472671"
---
# <a name="processinfofields"></a>PROCESS_INFO_FIELDS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [PROCESS_INFO_FIELDS](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/process-info-fields).  
  
Especificado que tipo de informações para recuperar para um processo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
enum enum_PROCESS_INFO_FIELDS {   
   PIF_FILE_NAME             = 0x00000001,  
   PIF_BASE_NAME             = 0x00000002,  
   PIF_TITLE                 = 0x00000004,  
   PIF_PROCESS_ID            = 0x00000008,  
   PIF_SESSION_ID            = 0x00000010,  
   PIF_ATTACHED_SESSION_NAME = 0x00000020,  
   PIF_CREATION_TIME         = 0x00000040,  
   PIF_FLAGS                 = 0x00000080,  
   PIF_ALL                   = 0x000000ff  
};  
typedef DWORD PROCESS_INFO_FIELDS;  
```  
  
```csharp  
public enum enum_PROCESS_INFO_FIELDS {   
   PIF_FILE_NAME             = 0x00000001,  
   PIF_BASE_NAME             = 0x00000002,  
   PIF_TITLE                 = 0x00000004,  
   PIF_PROCESS_ID            = 0x00000008,  
   PIF_SESSION_ID            = 0x00000010,  
   PIF_ATTACHED_SESSION_NAME = 0x00000020,  
   PIF_CREATION_TIME         = 0x00000040,  
   PIF_FLAGS                 = 0x00000080,  
   PIF_ALL                   = 0x000000ff  
};  
```  
  
## <a name="members"></a>Membros  
 PIF_FILE_NAME  
 Inicialização/usar o `bstrFileName` campo do [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) estrutura.  
  
 PIF_BASE_NAME  
 Inicialização/usar o `bstrBaseName` campo do `PROCESS_INFO` estrutura.  
  
 PIF_TITLE  
 Inicialização/usar o `bstrTitle` campo do `PROCESS_INFO` estrutura.  
  
 PIF_PROCESS_ID  
 Inicialização/usar o `ProcessId` campo do `PROCESS_INFO` estrutura.  
  
 PIF_SESSION_ID  
 Inicialização/usar o `dwSessionId` campo do `PROCESS_INFO` estrutura.  
  
 PIF_ATTACHED_SESSION_NAME  
 Inicialização/usar o `bstrAttachedSessionName` campo do `PROCESS_INFO` estrutura.  
  
 PIF_CREATION_TIME  
 Inicialização/usar o `CreationTime` campo do `PROCESS_INFO` estrutura.  
  
 PIF_FLAGS  
 Inicialização/usar o `Flags` campo do `PROCESS_INFO` estrutura.  
  
 PIF_ALL  
 Preenche todos os campos.  
  
## <a name="remarks"></a>Comentários  
 Passado para o [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md) método para indicar quais campos da [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) são de estrutura a ser inicializado.  
  
 Também é usado na `Fields` campo do `PROCESS_INFO` estrutura para indicar quais campos são usados e válido.  
  
 Esses sinalizadores podem ser combinados com um bit a bit `OR`.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)

