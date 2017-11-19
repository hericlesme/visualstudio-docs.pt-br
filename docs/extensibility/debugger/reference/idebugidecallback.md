---
title: IDebugIDECallback | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IDebugIDECallback interface
ms.assetid: 8d31adc0-1c44-4658-8d4f-f4b73e35f4a6
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d74c49a7de90e0c804cd4ec10a9201d3bff57866
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugidecallback"></a>IDebugIDECallback
> [!IMPORTANT]
>  No Visual Studio 2015, essa maneira de implementar avaliadores de expressão foi preterida. Para obter informações sobre como implementar avaliadores de expressão do CLR, consulte [avaliadores de expressão CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [amostra do avaliador de expressão gerenciado](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Permite que um avaliador de expressão (EE) exibir uma mensagem na janela de saída do depurador.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugIDECallback : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 Esse retorno de chamada é implementado pelo mecanismo de depuração gerenciada.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Ele pode ser consumido por um avaliador de expressão para enviar a saída para a janela de saída do depurador.  
  
## <a name="methods"></a>Métodos  
 Essa interface implementa o método a seguir:  
  
|Método|Descrição|  
|------------|-----------------|  
|[DisplayMessage](../../../extensibility/debugger/reference/idebugidecallback-displaymessage.md)|Envia a cadeia de caracteres de mensagem especificada para a janela de saída do depurador.|  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: Ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll