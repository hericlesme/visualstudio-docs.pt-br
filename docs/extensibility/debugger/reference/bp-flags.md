---
title: BP_FLAGS | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: BP_FLAGS
helpviewer_keywords: BP_FLAGS enumeration
ms.assetid: c45dfc74-5e7f-4f1e-a147-ab2a55dccbd0
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 3c4818cca16ffb23429006267829b076d52069c0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="bpflags"></a>BP_FLAGS
Fornece sinalizadores opcionais que podem ser usados para especificar informações adicionais ao definir um ponto de interrupção.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
enum enum_BP_FLAGS {   
   BP_FLAG_NONE            = 0x0000,  
   BP_FLAG_MAP_DOCPOSITION = 0x0001,  
   BP_FLAG_DONT_STOP       = 0x0002  
};  
typedef DWORD BP_FLAGS;  
```  
  
```csharp  
public enum enum_BP_FLAGS {   
   BP_FLAG_NONE            = 0x0000,  
   BP_FLAG_MAP_DOCPOSITION = 0x0001,  
   BP_FLAG_DONT_STOP       = 0x0002  
};  
```  
  
## <a name="members"></a>Membros  
 BP_FLAG_NONE  
 Não especifica que nenhum sinalizador de ponto de interrupção.  
  
 BP_FLAG_MAP_DOCPOSITION  
 Especifica que o mecanismo de depuração (DE) deve mapear o ponto de interrupção usando a posição do documento. Isso é aplicável somente a pontos de interrupção definidos nos arquivos de origem orientado por script, como páginas ASP (ASP).  
  
 BP_FLAG_DONT_STOP  
 Especifica que o ponto de interrupção deve ser processado pelo mecanismo de depuração, mas que o mecanismo de depuração, por fim, não deve parar existe (ou seja, um [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) não deve ser enviado um objeto de evento). Esse sinalizador é projetado para ser usado principalmente com pontos de rastreamento.  
  
## <a name="remarks"></a>Comentários  
 Usado para o `dwFlags` membro o [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) e [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) estruturas.  
  
 Esses valores podem ser combinados com um bit a bit `OR`.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)   
 [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)