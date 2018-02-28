---
title: "Contexto de avaliação de expressão | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- expression evaluation, context
ms.assetid: a2fd3758-09bd-45ae-8ecc-2d276c0036ba
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: ab4e57f500c2dfbfe673713c784cbc93ff52a73d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="expression-evaluation-context"></a>Contexto de avaliação de expressão
Em [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] depuração, uma **contexto de avaliação de expressão**:  
  
-   Representa um contexto de avaliação da expressão. Geralmente, um contexto de avaliação corresponde ao escopo léxico no qual avaliar variáveis, parâmetros, funções e métodos. Por exemplo, um contexto de avaliação de expressão associado a um quadro de pilha fornecem o contexto para avaliar as variáveis locais, parâmetros de método e membros de classe (se aplicável).  
  
-   Ocorre quando um programa foi interrompido no ponto de interrupção. A expressão em si é uma estrutura de dados que representa uma expressão analisada está pronta para associação e avaliar dentro do contexto especificado.  
  
     Mais especificamente, as expressões são criadas usando o [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) método. Quando uma expressão é avaliada, ele gera uma cadeia de caracteres imprimível, que contém o nome e tipo de variável ou argumento e seu valor. Essa cadeia de caracteres é exibida na janela Inspeção ou na janela locais do IDE.  
  
     Dado um `BSTR` e um [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) interface, um mecanismo de depuração (DE) pode criar um [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interface analisando uma expressão. Dado um `IDebugExpression2` interface, o DE pode obter um valor por meio da avaliação de expressão síncronas ou assíncronas. Esse valor, junto com o nome e o tipo da variável ou argumento, é enviado para o IDE para exibição.  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de avaliação de expressão](../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [Contextos do depurador](../../extensibility/debugger/debugger-contexts.md)