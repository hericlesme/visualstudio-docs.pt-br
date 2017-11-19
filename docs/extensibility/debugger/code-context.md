---
title: "Contexto de código | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugging [Debugging SDK], contexts
ms.assetid: 65e4d37a-086b-426e-9394-a3534967fd59
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 92d6ed317bcf6ceead42db850ee61969409eb136
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
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