---
title: CANSTOP_REASON | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CANSTOP_REASON
helpviewer_keywords: CANSTOP_REASON enumeration
ms.assetid: 6da944eb-36cd-4a8c-8d71-544c775cfcc1
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4446921759c1b72dd75c31b52bab35d02b219942
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="canstopreason"></a>CANSTOP_REASON
Usado para determinar se um programa pode interromper a execução depois de atingir um ponto específico na execução.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
enum enum_CANSTOP_REASON {   
   CANSTOP_ENTRYPOINT = 0x0000,  
   CANSTOP_STEPIN     = 0x0001  
};  
typedef DWORD CANSTOP_REASON;  
```  
  
```csharp  
public enum enum_CANSTOP_REASON {   
   CANSTOP_ENTRYPOINT = 0x0000,  
   CANSTOP_STEPIN     = 0x0001  
};  
```  
  
## <a name="members"></a>Membros  
 CANSTOP_ENTRYPOINT  
 Especifica o ponto de entrada do programa especificado.  
  
 CANSTOP_STEPIN  
 Especifica a entrar em uma função.  
  
## <a name="remarks"></a>Comentários  
 Passado como um argumento para o [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md) método para confirmar com a sessão de depuração Manager (SDM) se for okey parar depois de atingir o ponto de entrada do programa, ou depois de passo a passo em uma função ou método.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)