---
title: CONTEXT_INFO_FIELDS | Microsoft Docs
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
- CONTEXT_INFO_FIELDS
helpviewer_keywords:
- CONTEXT_INFO_FIELDS enumeration
ms.assetid: ef436bd3-738e-47e8-828c-8febce752439
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fd9d1ba718624e408c57c0bd68a3f5825068b9a6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47465384"
---
# <a name="contextinfofields"></a>CONTEXT_INFO_FIELDS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [CONTEXT_INFO_FIELDS](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/context-info-fields).  
  
Especifica quais informações devem ser recuperadas sobre um contexto de memória.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
enum enum_CONTEXT_INFO_FIELDS {   
   CIF_MODULEURL =       0x00000001,  
   CIF_FUNCTION =        0x00000002,  
   CIF_FUNCTIONOFFSET =  0x00000004,  
   CIF_ADDRESS =         0x00000008,  
   CIF_ADDRESSOFFSET =   0x00000010,  
   CIF_ADDRESSABSOLUTE = 0x00000020,  
   CIF_ALLFIELDS =       0x0000003f  
};  
typedef DWORD CONTEXT_INFO_FIELDS;  
```  
  
```csharp  
public enum enum_CONTEXT_INFO_FIELDS {  
   CIF_MODULEURL =       0x00000001,  
   CIF_FUNCTION =        0x00000002,  
   CIF_FUNCTIONOFFSET =  0x00000004,  
   CIF_ADDRESS =         0x00000008,  
   CIF_ADDRESSOFFSET =   0x00000010,  
   CIF_ADDRESSABSOLUTE = 0x00000020,  
   CIF_ALLFIELDS =       0x0000003f  
};  
```  
  
## <a name="members"></a>Membros  
 CIF_MODULEURL  
 Inicialização/usar o `bstrModuleUrl` campo do [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) estrutura.  
  
 CIF_FUNCTION  
 Inicialização/usar o `bstrFunction` campo do `CONTEXT_INFO` estrutura.  
  
 CIF_FUNCTIONOFFSET  
 Inicialização/usar o `posFunctionOffset` campo do `CONTEXT_INFO` estrutura.  
  
 CIF_ADDRESS  
 Inicialização/usar o `bstrAddress` campo do `CONTEXT_INFO` estrutura.  
  
 CIF_ADDRESSOFFSET  
 Inicialização/usar o `bstrAddressOffset` campo do `CONTEXT_INFO` estrutura.  
  
 CIF_ALLFIELDS  
 Inicialização/usar todos os campos do `CONTEXT_INFO` estrutura.  
  
## <a name="remarks"></a>Comentários  
 Esses valores são passados a um parâmetro para o [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md) método para indicar quais campos da [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) são de estrutura a ser inicializado.  
  
 Esses sinalizadores também são usados para indicar quais campos do `CONTEXT_INFO` estrutura são usados e válidos quando a estrutura é retornada.  
  
 Esses valores podem ser combinados com um OR bit a bit.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)

