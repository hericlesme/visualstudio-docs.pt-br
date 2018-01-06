---
title: Estrutura AsyncVoidMethodBuilder - membros internos | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debug engines, AsyncVoidMethodBuilder structure [.NET Framework]
- AsyncVoidMethodBuilder structure [.NET Framework debug engines]
ms.assetid: fe2970ab-d4c5-4355-a8e4-772ee0a57178
caps.latest.revision: "4"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 2debb60ed63a68f3925ed91ee6b8d374b84ce392
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="asyncvoidmethodbuilder-structure---internal-members"></a>Estrutura AsyncVoidMethodBuilder - membros internos
Este tópico descreve os membros internos do <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> classe. Para obter informações gerais sobre esta classe, consulte o <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> tópico de referência.  
  
 **Namespace:**<xref:System.Runtime.CompilerServices?displayProperty=fullName>  
  
 **Assembly:** mscorlib (em mscorlib.dll)  
  
 Porque você não pode acessar esses membros internos do .NET Framework, a sintaxe a seguir é fornecida em comum Intermediate Language (CIL).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncVoidMethodBuilder  
       extends System.ValueType  
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder  
```  
  
## <a name="internal-members"></a>Membros internos  
  
|Nome|Descrição|  
|----------|-----------------|  
|[Propriedade ObjectIdForDebugger](../../extensibility/debugger/asyncvoidmethodbuilder-objectidfordebugger-property.md)|Obtém um objeto que pode ser usado para identificar com exclusividade este construtor para o depurador.|  
|[campo m_objectIdForDebugger](../../extensibility/debugger/asyncvoidmethodbuilder-m-objectidfordebugger-field.md)|Representa o objeto inicializado lentamente usado pelo depurador para identificar exclusivamente este construtor.|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder>   
 [Elementos internos de extensões paralelas para o .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)