---
title: Roteiro para estender o depurador | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], roadmap
- Debugging SDK, roadmap
ms.assetid: 1f4096a8-f7aa-4dfa-84e1-6d59263e70bb
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: af86f2b8daeffeb700b619c4ba0d9cbb00700dd8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="roadmap-for-extending-the-debugger"></a>Roteiro para estender o depurador
Esta documentação fornece informações de referência e a guia para estender o [!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)] depurador com o [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)].  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]depuração documentação inclui exemplos, uma referência abrangente e vários cenários de amostra que demonstram as maneiras comuns de personalizar o depurador.  
  
 O compilador e sua saída determinam o que você precisa fazer para implementar a depuração no seu produto. Se seu compilador:  
  
-   Tem como alvo o sistema operacional nativo do Windows e grava um. O arquivo PDB, você pode depurar programas com o mecanismo de depuração de código nativo (DE), que é integrado ao [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Você não precisa implementar um avaliador de expressão ou DE. O avaliador de expressão é gravado para a sintaxe da linguagem de programação C++.  
  
-   Produz Microsoft intermediate language (MSIL) de saída, você pode depurar programas com o mecanismo de depuração de código gerenciado DE, que também está integrado a [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Portanto, você precisa implementar apenas um avaliador de expressão. Um avaliador de expressão de exemplo é fornecido para você. Para mais informações, consulte os seguintes tópicos:  
  
     [Avaliação de expressão](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)  
  
     [Avaliar expressões](../../extensibility/debugger/evaluating-expressions.md)  
  
     [Contexto da avaliação de expressão](../../extensibility/debugger/expression-evaluation-context.md)  
  
     [Avaliação de expressão no modo de interrupção](../../extensibility/debugger/expression-evaluation-in-break-mode.md)  
  
     [Escrever um avaliador de expressão do Common Language Runtime](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)  
  
-   Destinos de uma propriedade de sistema operacional ou outro ambiente de tempo de execução, você precisa escrever sua próprias DE. Um tutorial que cria uma DE simples usando COM ATL é fornecido. Para mais informações, consulte os seguintes tópicos:  
  
     [Criar um mecanismo de depuração personalizado](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
  
     [Tutorial: Criando um mecanismo de depuração usando COM ATL](http://msdn.microsoft.com/en-us/9097b71e-1fe7-48f7-bc00-009e25940c24)  
  
     [Implementar um fornecedor de porta](../../extensibility/debugger/implementing-a-port-supplier.md)  
  
     [Amostras](../../extensibility/debugger/visual-studio-debugging-samples.md)  
  
## <a name="see-also"></a>Consulte também  
 [Introdução](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)