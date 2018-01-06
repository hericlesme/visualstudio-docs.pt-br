---
title: Classe ContingentProperties - membros internos | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ContingentProperties class [.NET Framework debug engines]
- debug engines, ContingentProperties class [.NET Framework]
ms.assetid: c49d1362-ab1c-4b6d-9950-fcae40e0e66b
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: e1bd9c94b99b4881167d7ae434691ffd08666ced
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="contingentproperties-class---internal-members"></a>Classe ContingentProperties - membros internos
Contém propriedades adicionais para um <xref:System.Threading.Tasks.Task> objeto.  
  
 **Namespace:**<xref:System.Threading.Tasks?displayProperty=fullName>  
  
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