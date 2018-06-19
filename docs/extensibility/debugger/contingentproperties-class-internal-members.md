---
title: Classe ContingentProperties - membros internos | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- ContingentProperties class [.NET Framework debug engines]
- debug engines, ContingentProperties class [.NET Framework]
ms.assetid: c49d1362-ab1c-4b6d-9950-fcae40e0e66b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b44bec34394df6f976416a827d7eb5d67cb99f6a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31097842"
---
# <a name="contingentproperties-class---internal-members"></a>Classe ContingentProperties - membros internos
Contém propriedades adicionais para um <xref:System.Threading.Tasks.Task> objeto.  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** mscorlib (em mscorlib.dll)  
  
 Porque você não pode acessar esses membros internos do .NET Framework, a sintaxe a seguir é fornecida em comum Intermediate Language (CIL).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
.class auto ansi nested assembly beforefieldinit ContingentProperties  
       extends System.Object  
```  
  
## <a name="members"></a>Membros  
  
### <a name="fields"></a>Campos  
  
|Nome|Descrição|  
|----------|-----------------|  
|[m_children](../../extensibility/debugger/m-children-field.md)|A lista de tarefas filho que estão registrados com essa tarefa.|  
  
## <a name="remarks"></a>Comentários  
 O .NET Framework inicializa os campos dessa classe somente quando eles são necessários.  
  
## <a name="see-also"></a>Consulte também  
 [Elementos internos de extensões paralelas para o .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)