---
title: Contexto de código | Microsoft Docs
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
- debugging [Debugging SDK], contexts
ms.assetid: 65e4d37a-086b-426e-9394-a3534967fd59
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4e9ff125a75731de5ca312e5417996f9c6dda764
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47468379"
---
# <a name="code-context"></a>Contexto de código
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [contexto de código](https://docs.microsoft.com/visualstudio/extensibility/debugger/code-context).  
  
Na [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] depuração, um **contexto de código**:  
  
-   Fornece uma abstração de uma posição no código como conhecidos para o mecanismo de depuração (DES). Para a maioria das arquiteturas de tempo de execução atualmente, um contexto de código pode ser pensado como um endereço no fluxo de instruções de um programa. Para idiomas não tradicionais, onde o código não pode ser representado por instruções, um contexto de código pode ser representado por outros meios.  
  
-   Descreve a posição atual no fluxo de execução do programa que está sendo depurado.  
  
-   Existe apenas quando um programa foi interrompido no ponto de interrupção.  
  
-   Tem um contexto de documento associado.  
  
-   É implementado por uma [IDebugCodeContext2](../../extensibility/debugger/reference/idebugcodecontext2.md) interface.  
  
## <a name="see-also"></a>Consulte também  
 [Contexto de documento](../../extensibility/debugger/document-context.md)   
 [Contextos do depurador](../../extensibility/debugger/debugger-contexts.md)

