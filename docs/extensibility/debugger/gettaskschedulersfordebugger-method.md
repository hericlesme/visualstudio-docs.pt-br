---
title: "Método GetTaskSchedulersForDebugger | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: GetTaskSchedulersForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 58aa236a-5ab8-4695-b303-89dffdbcd946
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 474d809f36d21b254dbb8bf302cd21bc83db88a9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="gettaskschedulersfordebugger-method"></a>Método GetTaskSchedulersForDebugger
Recupera uma matriz de todos os <xref:System.Threading.Tasks.TaskScheduler> objetos que estão ativos no momento.  
  
 **Namespace:**<xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** mscorlib (em mscorlib.dll)  
  
 Porque você não pode acessar esse membro interno do .NET Framework, a sintaxe a seguir é fornecida em comum Intermediate Language (CIL).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
.method assembly hidebysig static class System.Threading.Tasks.TaskScheduler[] GetTaskSchedulersForDebugger() cil managed  
```  
  
## <a name="return-value"></a>Valor de retorno  
 Uma matriz de todos os <xref:System.Threading.Tasks.TaskScheduler> objetos que estão ativos no momento neste <xref:System.AppDomain>.  
  
## <a name="remarks"></a>Comentários  
 Este método não é thread-safe e não deve ser usado simultaneamente com outras instâncias do <xref:System.Threading.Tasks.TaskScheduler>. Ele deve ser chamado de um depurador somente quando o depurador suspendeu a todos os outros threads.  
  
## <a name="see-also"></a>Consulte também  
 [Classe TaskScheduler](../../extensibility/debugger/taskscheduler-class-internal-members.md)