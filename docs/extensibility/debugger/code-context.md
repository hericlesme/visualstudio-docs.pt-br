---
title: Contexto de código | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 65e4d37a-086b-426e-9394-a3534967fd59
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9a84596246ae930cdffc0265f2f2e09652661819
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31097829"
---
# <a name="code-context"></a>Contexto de código
Em [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] depuração, um **contexto de código**:  
  
-   Fornece uma abstração de uma posição em código como conhecida para o mecanismo de depuração (DE). Para a maioria das arquiteturas de tempo de execução atualmente, um contexto de código pode ser pensado como um endereço no fluxo de instrução do programa. Para idiomas não tradicionais, em que o código não pode ser representado por instruções, um contexto de código pode ser representado por outros meios.  
  
-   Descreve a posição atual no fluxo de execução do programa que está sendo depurado.  
  
-   Existe somente quando um programa foi interrompido no ponto de interrupção.  
  
-   Tem um contexto de documento associado.  
  
-   É implementado por um [IDebugCodeContext2](../../extensibility/debugger/reference/idebugcodecontext2.md) interface.  
  
## <a name="see-also"></a>Consulte também  
 [Contexto de documento](../../extensibility/debugger/document-context.md)   
 [Contextos do depurador](../../extensibility/debugger/debugger-contexts.md)