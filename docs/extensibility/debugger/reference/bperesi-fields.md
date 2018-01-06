---
title: BPERESI_FIELDS | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: BPERESI_FIELDS
helpviewer_keywords: BPERESI_FIELDS enumeration
ms.assetid: dd7dd89c-1043-46a1-a929-099cc039c344
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 36ac591940acaed2ac8b8f92c701580d9d45f94a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="bperesifields"></a>BPERESI_FIELDS
Especifica as informações a serem recuperados sobre uma falha na resolução de um ponto de interrupção.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
enum enum_BPERESI_FIELDS {   
   PERESI_BPRESLOCATION = 0x0001,  
   BPERESI_PROGRAM      = 0x0002,  
   BPERESI_THREAD       = 0x0004,  
   BPERESI_MESSAGE      = 0x0008,  
   BPERESI_TYPE         = 0x0010,  
   BPERESI_ALLFIELDS    = 0xffffffff  
};  
typedef DWORD BPERESI_FIELDS;  
```  
  
```csharp  
public enum enum_BPERESI_FIELDS {   
   PERESI_BPRESLOCATION = 0x0001,  
   BPERESI_PROGRAM      = 0x0002,  
   BPERESI_THREAD       = 0x0004,  
   BPERESI_MESSAGE      = 0x0008,  
   BPERESI_TYPE         = 0x0010,  
   BPERESI_ALLFIELDS    = 0xffffffff  
};  
```  
  
## <a name="members"></a>Membros  
 PERESI_BPRESLOCATION  
 Inicializar/usar o `bpResLocation` campo (localização de resolução do ponto de interrupção) do [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) estrutura.  
  
 BPERESI_PROGRAM  
 Inicializar/usar o `pProgram` campo o `BP_ERROR_RESOLUTION_INFO` estrutura.  
  
 BPERESI_THREAD  
 Inicializar/usar o `pThread` campo o `BP_ERROR_RESOLUTION_INFO` estrutura.  
  
 BPERESI_MESSAGE  
 Inicializar/usar o `bstrMessage` campo o `BP_ERROR_RESOLUTION_INFO` estrutura.  
  
 BPERESI_TYPE  
 Inicializar/usar o `dwType` campo (tipo de ponto de interrupção) da `BP_ERROR_RESOLUTION_INFO` estrutura.  
  
 BPERESI_ALLFIELDS  
 Todos os campos de inicialização/usar o `BP_ERROR_RESOLUTION_INFO` estrutura.  
  
## <a name="remarks"></a>Comentários  
 Passado como um parâmetro para o [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md) método para indicar quais campos do [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) estrutura devem ser inicializado.  
  
 Esses valores também são usados para indicar quais campos o `BP_ERROR_RESOLUTION_INFO` estrutura são válidos e usadas quando essa estrutura é retornada.  
  
 Esses valores podem ser combinados com um bit a bit `OR`.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)   
 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)