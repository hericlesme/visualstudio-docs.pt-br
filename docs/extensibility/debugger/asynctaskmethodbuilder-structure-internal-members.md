---
title: Estrutura AsyncTaskMethodBuilder - membros internos | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debug engines, AsyncTaskMethodBuilder structure [.NET Framework]
- AsyncTaskMethodBuilder structure [.NET Framework debug engines]
ms.assetid: f32f5857-7ef8-45fd-8b5a-7f644eb98b11
caps.latest.revision: "5"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 763f06d03eff79d82096bc2b5eb3046fe05f7aca
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="asynctaskmethodbuilder-structure---internal-members"></a>Estrutura AsyncTaskMethodBuilder - membros internos
Este tópico descreve os membros internos do <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> classe. Para obter informações gerais sobre esta classe, consulte o <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> tópico de referência.  
  
 **Namespace:**<xref:System.Runtime.CompilerServices?displayProperty=fullName>  
  
 **Assembly:** mscorlib (em mscorlib.dll)  
  
 Porque você não pode acessar esses membros internos do .NET Framework, a sintaxe a seguir é fornecida em comum Intermediate Language (CIL).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncTaskMethodBuilder  
       extends System.ValueType  
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder  
```  
  
## <a name="internal-members"></a>Membros internos  
  
|Nome|Descrição|  
|----------|-----------------|  
|[Propriedade ObjectIdForDebugger](../../extensibility/debugger/asynctaskmethodbuilder-objectidfordebugger-property.md)|Obtém um objeto que pode ser usado para identificar com exclusividade este construtor para o depurador.|  
|[campo m_builder](../../extensibility/debugger/asynctaskmethodbuilder-m-builder-field.md)|Representa o objeto de construtor genérico para o qual essa instância não genérico delega.|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder>   
 [Elementos internos de extensões paralelas para o .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)