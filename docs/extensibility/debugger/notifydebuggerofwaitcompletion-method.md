---
title: "Método NotifyDebuggerOfWaitCompletion | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: NotifyDebuggerOfWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: 841c5908-4f3f-400b-a7b0-96a95f362817
caps.latest.revision: "5"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5bfd605665627bcc9269f9225acb7d2e12418ab4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="notifydebuggerofwaitcompletion-method"></a>Método NotifyDebuggerOfWaitCompletion
Método de espaço reservado usado como um destino de ponto de interrupção pelo depurador. Esse método não deve ser embutida ou otimizado.  
  
 **Namespace:**<xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** mscorlib (em mscorlib.dll)  
  
## <a name="syntax"></a>Sintaxe  
  
```vb  
private void NotifyDebuggerOfWaitCompletion()  
```  
  
## <a name="remarks"></a>Comentários  
 Todas as operações de junção com uma tarefa devem chamar esse método se o bit de notificação do depurador está definido.  
  
## <a name="requirements"></a>Requisitos  
  
## <a name="see-also"></a>Consulte também  
 [Classe de tarefa](../../extensibility/debugger/task-class-internal-members.md)