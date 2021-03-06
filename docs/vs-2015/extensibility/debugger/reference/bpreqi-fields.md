---
title: BPREQI_FIELDS | Microsoft Docs
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
- BPREQI_FIELDS
helpviewer_keywords:
- BPREQI_FIELDS enumeration
ms.assetid: 679e771e-4a79-484e-af37-f962ef4aa245
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4be4e49b79c2b2dc62843e785d1fb38b517f34b1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47476000"
---
# <a name="bpreqifields"></a>BPREQI_FIELDS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [BPREQI_FIELDS](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/bpreqi-fields).  
  
Especifica as informações a serem recuperados sobre uma solicitação de ponto de interrupção.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
enum enum_BPREQI_FIELDS {   
   BPREQI_BPLOCATION   = 0x0001,  
   BPREQI_LANGUAGE     = 0x0002,  
   BPREQI_PROGRAM      = 0x0004,  
   BPREQI_PROGRAMNAME  = 0x0008,  
   BPREQI_THREAD       = 0x0010,  
   BPREQI_THREADNAME   = 0x0020,  
   BPREQI_PASSCOUNT    = 0x0040,  
   BPREQI_CONDITION    = 0x0080,  
   BPREQI_FLAGS        = 0x0100,  
   BPREQI_ALLOLDFIELDS = 0x01ff  
   BPREQI_VENDOR       = 0x0200,   // BP_REQUEST_INFO2 only  
   BPREQI_CONSTRAINT   = 0x0400,   // BP_REQUEST_INFO2 only  
   BPREQI_TRACEPOINT   = 0x0800,   // BP_REQUEST_INFO2 only  
   BPREQI_ALLFIELDS    = 0x0fff    // BP_REQUEST_INFO2 only  
};  
typedef DWORD BPREQI_FIELDS;  
```  
  
```csharp  
public enum enum_BPREQI_FIELDS {   
   BPREQI_BPLOCATION   = 0x0001,  
   BPREQI_LANGUAGE     = 0x0002,  
   BPREQI_PROGRAM      = 0x0004,  
   BPREQI_PROGRAMNAME  = 0x0008,  
   BPREQI_THREAD       = 0x0010,  
   BPREQI_THREADNAME   = 0x0020,  
   BPREQI_PASSCOUNT    = 0x0040,  
   BPREQI_CONDITION    = 0x0080,  
   BPREQI_FLAGS        = 0x0100,  
   BPREQI_ALLOLDFIELDS = 0x01ff  
   BPREQI_VENDOR       = 0x0200,   // BP_REQUEST_INFO2 only  
   BPREQI_CONSTRAINT   = 0x0400,   // BP_REQUEST_INFO2 only  
   BPREQI_TRACEPOINT   = 0x0800,   // BP_REQUEST_INFO2 only  
   BPREQI_ALLFIELDS    = 0x0fff    // BP_REQUEST_INFO2 only  
};  
```  
  
## <a name="members"></a>Membros  
 BPREQI_BPLOCATION  
 Inicialização/usar o `bpLocation` campo (localização do ponto de interrupção) a [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) ou [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) estrutura.  
  
 BPREQI_LANGUAGE  
 Inicialização/usar o `guidLanguage` campo do `BP_REQUEST_INFO` ou `BP_REQUEST_INFO2` estrutura.  
  
 BPREQI_PROGRAM  
 Inicialização/usar o `pProgram` campo do `BP_REQUEST_INFO` ou `BP_REQUEST_INFO2` estrutura.  
  
 BPREQI_PROGRAMNAME  
 Inicialização/usar o `bstrProgramName` campo do `BP_REQUEST_INFO` ou `BP_REQUEST_INFO2` estrutura.  
  
 BPREQI_THREAD  
 Inicialização/usar o `pThread` campo do `BP_REQUEST_INFO` ou `BP_REQUEST_INFO2` estrutura.  
  
 BPREQI_THREADNAME  
 Inicialização/usar o `bstrThreadName` campo do `BP_REQUEST_INFO` ou `BP_REQUEST_INFO2` estrutura.  
  
 BPREQI_PASSCOUNT  
 Inicialização/usar o `bpPassCount` campo do `BP_REQUEST_INFO` ou `BP_REQUEST_INFO2` estrutura.  
  
 BPREQI_CONDITION  
 Inicialização/usar o `bpCondition` campo (condição de ponto de interrupção) da `BP_REQUEST_INFO` ou `BP_REQUEST_INFO2` estrutura.  
  
 BPREQI_FLAGS  
 Inicialização/usar o `dwFlags` campo do `BP_REQUEST_INFO` ou `BP_REQUEST_INFO2` estrutura.  
  
 BPREQI_ALLOLDFIELDS  
 Inicialização/usar todos os campos para o do `BP_REQUEST_INFO` estrutura.  
  
 BPREQI_VENDOR  
 Inicialização/usar o `guidVendor` campo de `BP_REQUEST_INFO2` estrutura.  
  
 BPREQI_CONSTRAINT  
 Inicialização/usar o `bstrConstraint` campo de `BP_REQUEST_INFO2` estrutura.  
  
 BPREQI_TRACEPOINT  
 Inicialização/usar o `bstrTracepoint` campo de `BP_REQUEST_INFO2` estrutura.  
  
 BPREQI_ALLFIELDS  
 Especifica todos os campos para o `BP_REQUEST_INFO2` estrutura.  
  
## <a name="remarks"></a>Comentários  
 Passado como um argumento para o [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md) e [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) métodos para especificar quais campos dos [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) e [BP_REQUEST_INFO2 ](../../../extensibility/debugger/reference/bp-request-info2.md) estruturas são a ser inicializado.  
  
 Esses sinalizadores também são usados para indicar quais campos do `BP_REQUEST_INFO` e `BP_REQUEST_INFO2` estruturas são usadas e é válido quando cada estrutura é retornada.  
  
 Esses valores podem ser combinados com um bit a bit `OR`.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)   
 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)

