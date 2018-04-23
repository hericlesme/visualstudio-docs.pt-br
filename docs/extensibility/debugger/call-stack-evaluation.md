---
title: Avaliação de pilha de chamadas | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], call stack evaluation
- call stacks, evaluation
ms.assetid: 373d6b49-0459-4cce-816e-05745a44fe49
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bcfc2f2afa622534772390df59597f6972463de8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="call-stack-evaluation"></a>Avaliação de pilha de chamada
Para exibir os quadros de pilha da pilha de chamadas durante o modo de interrupção, você deve implementar o [EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) método.  
  
## <a name="methods-for-evaluation"></a>Métodos para avaliação  
 Para um mecanismo de depuração simples (DE), pode haver apenas um quadro de pilha. Para examinar o quadro de pilha durante o modo de interrupção, você deve implementar os seguintes métodos de [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md).  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)|Obtém o contexto de código para um quadro de pilha. O contexto de código representa o ponteiro de instrução atual em um quadro de pilha.|  
|[GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|Obtém o contexto de documento para um quadro de pilha. O contexto de documento representa o local atual no código-fonte para um quadro de pilha. Necessário para exibir o código-fonte, quando você for interrompido em um programa.|  
  
 Esses métodos exigem a implementação de várias interfaces de contexto e métodos. Portanto, você deve implementar o [GetDocumentContext](../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md) método e os seguintes métodos de [IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md).  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetStatementRange](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)|Obtém o intervalo de instrução de arquivo de um contexto de documento.|  
  
 Para enumerar os contextos de código, você deve implementar todos os métodos de [IEnumDebugCodeContexts2](../../extensibility/debugger/reference/ienumdebugcodecontexts2.md).  
  
## <a name="see-also"></a>Consulte também  
 [Controle de execução e avaliação de estado](../../extensibility/debugger/execution-control-and-state-evaluation.md)