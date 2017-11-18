---
title: "CA1011: Considere passar tipos base como parâmetros | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ConsiderPassingBaseTypesAsParameters
- CA1011
helpviewer_keywords:
- CA1011
- ConsiderPassingBaseTypesAsParameters
ms.assetid: ce1e1241-dcf4-419b-9363-1d5bc4989279
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ae6923e369d0f4245759bff2c66dc931dc51baf8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="ca1011-consider-passing-base-types-as-parameters"></a>CA1011: considere a passagem dos tipos base como parâmetros
|||  
|-|-|  
|NomeDoTipo|ConsiderPassingBaseTypesAsParameters|  
|CheckId|CA1011|  
|Categoria|Microsoft.Design|  
|Alteração Significativa|Quebra|  
  
## <a name="cause"></a>Causa  
 Uma declaração de método inclui um parâmetro formal que é um tipo derivado, e o método chama somente os membros do tipo base do parâmetro.  
  
## <a name="rule-description"></a>Descrição da Regra  
 Quando um tipo de base é especificado como um parâmetro em uma declaração de método, qualquer tipo derivado do tipo de base pode ser passado como o argumento correspondente ao método. Quando o argumento é usado dentro do corpo de método, o método específico que é executado depende do tipo do argumento. Se a funcionalidade adicional que é fornecida pelo tipo derivado não for necessária, use o tipo de base permite o uso mais amplo do método.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Para corrigir uma violação desta regra, altere o tipo do parâmetro ao seu tipo base.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 É seguro suprimir um aviso da regra  
  
-   Se o método requer que a funcionalidade específica que é fornecida pelo tipo derivado  
  
     \- ou -  
  
-   para impor que apenas o tipo derivado, ou um tipo mais derivado, é passada para o método.  
  
 Nesses casos, o código será mais robusto devido o forte verificação de tipo que é fornecido pelo compilador e tempo de execução.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra um método `ManipulateFileStream`, que pode ser usado somente com um <xref:System.IO.FileStream> objeto, o que viola essa regra. Um segundo método, `ManipulateAnyStream`, atenda a regra, substituindo o <xref:System.IO.FileStream> parâmetro usando um <xref:System.IO.Stream>.  
  
 [!code-csharp[FxCop.Design.ConsiderPassingBaseTypes#1](../code-quality/codesnippet/CSharp/ca1011-consider-passing-base-types-as-parameters_1.cs)]
 [!code-cpp[FxCop.Design.ConsiderPassingBaseTypes#1](../code-quality/codesnippet/CPP/ca1011-consider-passing-base-types-as-parameters_1.cpp)]
 [!code-vb[FxCop.Design.ConsiderPassingBaseTypes#1](../code-quality/codesnippet/VisualBasic/ca1011-consider-passing-base-types-as-parameters_1.vb)]  
  
## <a name="related-rules"></a>Regras relacionadas  
 [CA1059: os membros não devem expor determinados tipos concretos](../code-quality/ca1059-members-should-not-expose-certain-concrete-types.md)