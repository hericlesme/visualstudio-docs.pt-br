---
title: "Guia de Introdução ao depurador extensibilidade | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- getting started, Debugging SDK
- debugging [Debugging SDK], getting started
- Debugging SDK, getting started
ms.assetid: d6ce6f43-1409-4bf7-93cd-f3464ca23504
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1419f4e45aefed59aa36b249568a53a47ad3c459
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="getting-started-with-debugger-extensibility"></a>Guia de Introdução ao depurador de extensibilidade
O [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] fornece as informações que você deve ter para criar e personalizar os componentes do depurador usados para depurar programas de dentro do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]depuração adicionou melhorias derivadas a usabilidade ampla teste executado no anterior [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] depuradores. Você pode usar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] depuração para percorrer um aplicativo de vários idioma, ou você pode implementar durante a execução de edição de variáveis durante a depuração de aplicativos e soluções de vários idiomas.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]depuração é executada fora do processo com o programa que está sendo depurado e, portanto, menos intrusiva no espaço de processo do aplicativo. Portanto, é mais fácil de escrever componentes que interagem com o depurador sem afetar seu programa de depuração.  
  
 Usar melhor o [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], você deve estar familiarizado com o seguinte:  
  
-   O [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente de desenvolvimento integrado (IDE)  
  
-   A linguagem de programação C++  
  
-   COM DA ATL  
  
## <a name="in-this-section"></a>Nesta seção  
 [Roteiro para estender o depurador](../../extensibility/debugger/roadmap-for-extending-the-debugger.md)  
 Descreve o processo de implementação de depuração no seu produto, dependendo de seu compilador e sua saída.  
  
 [Componentes do depurador](../../extensibility/debugger/debugger-components.md)  
 Fornece uma visão geral de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] depuração componentes, que incluem o mecanismo de depuração (DE), o avaliador de expressão (EE) e o manipulador de símbolo (SH).  
  
 [Conceitos do depurador](../../extensibility/debugger/debugger-concepts.md)  
 Descreve os principais conceitos de arquitetura de depuração.  
  
 [Contextos do depurador](../../extensibility/debugger/debugger-contexts.md)  
 Explica como o mecanismo de depuração (DE) simultaneamente opera no código, documentação e contextos de avaliação de expressão. Descreve, para cada um dos três contextos, local, posição ou avaliação relevante a ele.  
  
 [Tarefas de depuração](../../extensibility/debugger/debugging-tasks.md)  
 Contém links para várias tarefas de depuração, como iniciar um programa e avaliar expressões.