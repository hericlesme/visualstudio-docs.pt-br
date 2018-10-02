---
title: IDebugProgramDestroyEventFlags2 | Microsoft Docs
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
- IDebugProgramDestroyEventFlags2 interface
ms.assetid: d384ff71-dc71-40b9-a871-801f8b6a3418
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 86d3a6ba48107753e5403f39d5b982b4dc88ffdd
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47475362"
---
# <a name="idebugprogramdestroyeventflags2"></a>IDebugProgramDestroyEventFlags2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [IDebugProgramDestroyEventFlags2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugprogramdestroyeventflags2).  
  
Permite que um mecanismo de depuração substituir o comportamento padrão do [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] interface do usuário quando você encerrar uma sessão de depuração.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugProgramDestroyEventFlags2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 Essa interface é implementada pelos mecanismos de depuração. É útil para hosts que podem criar e destruir vários programas durante a vida útil de um processo.  
  
## <a name="methods"></a>Métodos  
 A tabela a seguir mostra os métodos de `IDebugProgramDestroyEventFlags2`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetFlags](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2-getflags.md)|Recupera o programa destruir sinalizadores.|  
  
## <a name="remarks"></a>Comentários  
 O comportamento padrão do [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] interface do usuário é retornar ao modo de design depois que todos os programas tem enviado um programa destruir o evento. Essa interface permite que um mecanismo de depuração alterar esse comportamento.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

