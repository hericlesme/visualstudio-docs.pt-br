---
title: ATTACH_REASON | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ATTACH_REASON
helpviewer_keywords: ATTACH_REASON enumeration
ms.assetid: 159fb70b-a344-4ba6-9115-b7eaa16e228f
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 527e7a445356a46abdd6f2edb0555b7c5c9c7de8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="attachreason"></a>ATTACH_REASON
Especifica o motivo para o mecanismo de depuração (DE) para anexar a um nó de programa.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
enum enum_ATTACH_REASON {   
   ATTACH_REASON_LAUNCH = 0x0001,  
   ATTACH_REASON_USER   = 0x0002,  
   ATTACH_REASON_AUTO   = 0x0003  
};  
typedef DWORD ATTACH_REASON;  
```  
  
```csharp  
public enum enum_ATTACH_REASON {   
   ATTACH_REASON_LAUNCH = 0x0001,  
   ATTACH_REASON_USER   = 0x0002,  
   ATTACH_REASON_AUTO   = 0x0003  
};  
```  
  
## <a name="members"></a>Membros  
 ATTACH_REASON_AUTO  
 Anexe porque o processo está em modo de depuração.  
  
 ATTACH_REASON_LAUNCH  
 Anexe porque o processo foi iniciado.  
  
 ATTACH_REASON_USER  
 Anexe devido a uma solicitação de usuário.  
  
## <a name="remarks"></a>Comentários  
 Esses valores são usados como um parâmetro para o [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) e [Attach](../../../extensibility/debugger/reference/idebugprogramex2-attach.md) métodos.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Anexar](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [Anexar](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)