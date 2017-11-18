---
title: 'CA2200: Rethrow para preservar detalhes da pilha | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- RethrowToPreserveStackDetails
- CA2200
helpviewer_keywords:
- CA2200
- RethrowToPreserveStackDetails
ms.assetid: 046e1b98-c4dc-4515-874f-9c0de2285621
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ca2e6e61b88d4d8aaccd4784e1b521e0cbb48bd4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="ca2200-rethrow-to-preserve-stack-details"></a>CA2200: relançar para preservar detalhes da pilha
|||  
|-|-|  
|NomeDoTipo|RethrowToPreserveStackDetails|  
|CheckId|CA2200|  
|Categoria|Microsoft.Usage|  
|Alteração Significativa|Não separáveis|  
  
## <a name="cause"></a>Causa  
 Uma exceção é lançada novamente e a exceção é especificada explicitamente no `throw` instrução.  
  
## <a name="rule-description"></a>Descrição da Regra  
 Depois que uma exceção será lançada, parte das informações que ele executa é o rastreamento de pilha. O rastreamento de pilha é uma lista de hierarquia de chamada de método que inicia com o método que gerou a exceção e termina com o método que captura a exceção. Se uma exceção é gerada novamente com a especificação de exceção de `throw` instrução, o rastreamento de pilha for reiniciado, o método atual e a lista de chamadas de método entre o método original que gerou a exceção e o método atual for perdida. Para manter as informações de rastreamento de pilha original com a exceção, use o `throw` instrução sem especificar a exceção.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Para corrigir uma violação desta regra, gera novamente a exceção sem especificar a exceção explicitamente.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 Não suprima um aviso nessa regra.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra um método `CatchAndRethrowExplicitly`, que viola a regra e um método `CatchAndRethrowImplicitly`, que atende a regra.  
  
 [!code-csharp[FxCop.Usage.Rethrow#1](../code-quality/codesnippet/CSharp/ca2200-rethrow-to-preserve-stack-details_1.cs)]
 [!code-vb[FxCop.Usage.Rethrow#1](../code-quality/codesnippet/VisualBasic/ca2200-rethrow-to-preserve-stack-details_1.vb)]