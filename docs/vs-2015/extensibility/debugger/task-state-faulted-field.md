---
title: Campo TASK_STATE_FAULTED | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- TASK_STATE_FAULTED field, Task class [.NET Framework debug engines]
ms.assetid: ced826ae-09a9-4acf-af00-a2343d396bb8
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 59b5a798efc108324012bcd0b2c38183c3eb09d8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47475831"
---
# <a name="taskstatefaulted-field"></a>Campo TASK_STATE_FAULTED
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [campo TASK_STATE_FAULTED](https://docs.microsoft.com/visualstudio/extensibility/debugger/task-state-faulted-field).  
  
A tarefa foi concluída devido a uma exceção sem tratamento.  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** mscorlib (em mscorlib. dll)  
  
 Porque você não pode acessar esse membro interno do .NET Framework, a sintaxe a seguir é fornecida em comum Intermediate Language (CIL).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
.field static assembly literal int32 TASK_STATE_FAULTED = int32(0x00400000)  
```  
  
## <a name="remarks"></a>Comentários  
 Se o [m_stateFlags](../../extensibility/debugger/m-stateflags-field.md) campo contém esse valor, o <xref:System.Threading.Tasks.Task.Status%2A> propriedade retorna <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName>.  
  
## <a name="see-also"></a>Consulte também  
 [Classe de tarefa](../../extensibility/debugger/task-class-internal-members.md)

