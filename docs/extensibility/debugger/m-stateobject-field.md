---
title: m_stateObject campo | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- m_stateObject field, Task class [.NET Framework debug engines]
ms.assetid: 68c54b22-3e1c-4031-b9c7-b972c519d8a0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 79313460d380b2b505f6fa75f35351811ddaa470
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31097453"
---
# <a name="mstateobject-field"></a>m_stateObject campo
Um objeto que representa os dados que deseja usar a ação.  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** mscorlib (em mscorlib.dll)  
  
 Porque você não pode acessar esse membro interno do .NET Framework, a sintaxe a seguir é fornecida em comum Intermediate Language (CIL).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
.field assembly object m_stateObject  
```  
  
## <a name="remarks"></a>Comentários  
 Este é o `state` parâmetro o <xref:System.Threading.Tasks.Task.%23ctor%2A> construtor. Também é o campo de backup para o <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=fullName> propriedade.  
  
## <a name="see-also"></a>Consulte também  
 [Classe de tarefa](../../extensibility/debugger/task-class-internal-members.md)