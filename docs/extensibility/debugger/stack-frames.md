---
title: Quadros de pilha | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- stack frames, debugging
- debugging [Debugging SDK], stack frames
- stack frames
ms.assetid: b5e439d4-1e9d-4e13-9cad-bb8b136d4ca8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: feb2bc9d87486b6f83cf4b19ecec24c8c03edee5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31127993"
---
# <a name="stack-frames"></a>Quadros de pilhas
Em termos de arquitetura do depurador, um **quadro de pilha**:  
  
-   É uma abstração de uma pilha que fornece o contexto de execução de um thread. Um thread sempre é executado dentro de uma função. Um quadro de pilha contém as variáveis locais da função e os argumentos para ele. Para depurar com o Visual Studio, o idioma ou o ambiente que está sendo depurado deve oferecer suporte a quadros de pilhas.  
  
-   Pode ambos identificar e descrever a mesmo e pode retornar o thread associado. Um quadro de pilha também pode retornar o contexto do código que representa o ponteiro de instrução atual, bem como a documentação associada e contextos de avaliação de expressão.  
  
-   Tem propriedades que descrevem o nome, tipo e valor dos argumentos e variáveis locais e que aparecem em várias janelas de depuração do IDE.  
  
-   É representado por um [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) interface, normalmente criado por um mecanismo de depuração (DE) ou a máquina virtual como consequência de execução de um thread.  
  
## <a name="see-also"></a>Consulte também  
 [Contextos de depurador](../../extensibility/debugger/debugger-contexts.md)   
 [Conceitos do depurador](../../extensibility/debugger/debugger-concepts.md)   
 [Mecanismo de depuração](../../extensibility/debugger/debug-engine.md)   
 [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)