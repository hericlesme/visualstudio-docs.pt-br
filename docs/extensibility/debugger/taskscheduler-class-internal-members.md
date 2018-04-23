---
title: Classe TaskScheduler - membros internos | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- TaskScheduler class [.NET Framework debug engines]
- debug engines, TaskScheduler class [.NET Framework]
ms.assetid: 87f1c969-0217-4464-8907-7609c1bf61d3
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 18cd3ec809df921d6baefbf8018fefc77db238d3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="taskscheduler-class---internal-members"></a>Classe TaskScheduler - membros internos
Este tópico descreve os membros internos do <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName> classe ajudá-lo a implementar um depurador personalizado. Para obter informações gerais sobre esta classe, consulte o <xref:System.Threading.Tasks.TaskScheduler> tópico de referência.  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** mscorlib (em mscorlib.dll)  
  
 Porque você não pode acessar esses membros internos do .NET Framework, a sintaxe a seguir é fornecida em comum Intermediate Language (CIL).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
.class public abstract auto ansi beforefieldinit System.Threading.Tasks.TaskScheduler  
       extends System.Object  
```  
  
## <a name="members"></a>Membros  
  
### <a name="methods"></a>Métodos  
  
|Nome|Descrição|  
|----------|-----------------|  
|[GetScheduledTasksForDebugger](../../extensibility/debugger/getscheduledtasksfordebugger-method.md)|Recupera uma matriz de todas as tarefas agendadas.|  
|[GetTaskSchedulersForDebugger](../../extensibility/debugger/gettaskschedulersfordebugger-method.md)|Recupera uma matriz de todos os <xref:System.Threading.Tasks.TaskScheduler> objetos que estão ativos no momento.|  
  
## <a name="remarks"></a>Comentários  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>   
 [Elementos internos de extensões paralelas para o .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)