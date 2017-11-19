---
title: PROCESS_INFO_FLAGS | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: PROCESS_INFO_FLAGS
helpviewer_keywords: PROCESS_INFO_FLAGS enumeration
ms.assetid: 696951ce-701a-40c2-ac8c-b897f3aae6e2
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 228b2d3286ad0b69a2eb813e18b8837ec038f28f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="processinfoflags"></a>PROCESS_INFO_FLAGS
Descreve ou especifica as propriedades de um processo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
enum enum_PROCESS_INFO_FLAGS {   
   PIFLAG_SYSTEM_PROCESS    = 0x00000001,  
   PIFLAG_DEBUGGER_ATTACHED = 0x00000002,  
   PIFLAG_PROCESS_STOPPED   = 0x00000004,  
   PIFLAG_PROCESS_RUNNING   = 0x00000008,  
};  
typedef DWORD PROCESS_INFO_FLAGS;  
```  
  
```csharp  
enum enum_PROCESS_INFO_FLAGS {   
   PIFLAG_SYSTEM_PROCESS    = 0x00000001,  
   PIFLAG_DEBUGGER_ATTACHED = 0x00000002,  
   PIFLAG_PROCESS_STOPPED   = 0x00000004,  
   PIFLAG_PROCESS_RUNNING   = 0x00000008,  
};  
```  
  
## <a name="members"></a>Membros  
 PIFLAG_SYSTEM_PROCESS  
 Indica que o processo é um processo do sistema.  
  
 PIFLAG_DEBUGGER_ATTACHED  
 Indica que o processo está sendo depurado por um depurador. Pode ser um [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] depurador, ou pode ser algum outro depurador, por exemplo, WinDbg.  
  
 PIFLAG_PROCESS_STOPPED  
 Indica que o processo será interrompido. Válido somente se `PIFLAG_DEBUGGER_ATTACHED` também for especificado. Disponível em [!INCLUDE[vsprvslong](../../../code-quality/includes/vsprvslong_md.md)] e posterior.  
  
 PIFLAG_PROCESS_RUNNING  
 Indica que o processo está sendo executado. Válido somente se `PIFLAG_DEBUGGER_ATTACHED` também for especificado. Disponível em [!INCLUDE[vsprvslong](../../../code-quality/includes/vsprvslong_md.md)] e posterior.  
  
## <a name="remarks"></a>Comentários  
 Usado para o `Flags` membro o [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) estrutura.  
  
 Esses sinalizadores podem ser combinados com um bit a bit `OR`.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)