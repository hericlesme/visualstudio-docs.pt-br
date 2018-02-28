---
title: Contextos de depurador | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 79808036-b680-4e4c-9c61-4ed43aa11323
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: f36df39cf29ff298a327ec6e6d4bb02ff53485a0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="debugger-contexts"></a>Contextos de depurador
Em [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] de depuração, o mecanismo de depuração (DE) opera simultaneamente em vários contextos diferentes, da seguinte maneira:  
  
-   O contexto de código, que descreve o local atual no fluxo de execução do programa.  
  
-   O contexto da documentação ou posição, que descreve a posição atual dentro de um documento de origem.  
  
-   O contexto de avaliação de expressão, que descreve o contexto no qual expressão avaliação ocorrerá.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Contexto do código](../../extensibility/debugger/code-context.md)  
 Discute o contexto de código como um endereço no fluxo de instrução do programa em arquiteturas de tempo de execução de hoje versus idiomas não tradicionais, onde código não pode ser representado por instruções, mas outros meios.  
  
 [Posição do documento](../../extensibility/debugger/document-position.md)  
 Define a posição do documento na depuração no Visual Studio por meio de uma abstração de uma posição em um arquivo de origem conhecida para o IDE.  
  
 [Contexto do documento](../../extensibility/debugger/document-context.md)  
 Discute representa o contexto de documento na depuração do Visual Studio em relação a um arquivo de origem. Também descreve como o manipulador de símbolo mapeia um contexto de código para o contexto da documentação.  
  
 [Contexto da avaliação de expressão](../../extensibility/debugger/expression-evaluation-context.md)  
 Fornece informações sobre um contexto de avaliação de expressão no Visual Studio. Por exemplo, um contexto de avaliação de expressão associado a um quadro de pilha fornece o contexto para avaliar as variáveis locais, parâmetros de método e membros de classe.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Conceitos de depuração](../../extensibility/debugger/debugger-concepts.md)  
 Descreve os principais conceitos de arquitetura de depuração.  
  
 [Componentes de depuração](../../extensibility/debugger/debugger-components.md)  
 Fornece uma visão geral dos componentes de depuração Visual Studio, que incluem o mecanismo de depuração (DE), o avaliador de expressão (EE) e o manipulador de símbolo (SH).  
  
 [Tarefas de depuração](../../extensibility/debugger/debugging-tasks.md)  
 Contém links para várias tarefas de depuração, como iniciar um programa e avaliar expressões.