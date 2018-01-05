---
title: "CA1052: Os tipos de suporte estático devem ser lacrados | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- StaticHolderTypesShouldBeSealed
- CA1052
helpviewer_keywords:
- CA1052
- StaticHolderTypesShouldBeSealed
ms.assetid: 51a3165d-781e-4a55-aa0d-ea25fee7d4f2
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: d9ce807aca8b28a279a3a423802196e710f63dea
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ca1052-static-holder-types-should-be-sealed"></a>CA1052: os tipos de suporte estático devem ser lacrados
|||  
|-|-|  
|NomeDoTipo|StaticHolderTypesShouldBeSealed|  
|CheckId|CA1052|  
|Categoria|Microsoft.Design|  
|Alteração Significativa|Quebra|  
  
## <a name="cause"></a>Causa  
 Um tipo público ou protegido contém apenas membros estáticos e não é declarado com o [lacrado](/dotnet/csharp/language-reference/keywords/sealed) ([NotInheritable](/dotnet/visual-basic/language-reference/modifiers/notinheritable)) modificador.  
  
## <a name="rule-description"></a>Descrição da Regra  
 Essa regra pressupõe que um tipo que contém somente membros estáticos não foi projetado para ser herdadas, pois o tipo não fornece nenhuma funcionalidade que pode ser substituída em um tipo derivado. Um tipo que não pode ser herdada deve ser marcado com o `sealed` modificador para impedir seu uso como um tipo base.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Para corrigir uma violação desta regra, marque o tipo como `sealed`. Se estiver direcionando [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 2.0 ou posterior, uma abordagem melhor é marcar o tipo como `static`. Dessa forma, você não precisa declarar um construtor particular para impedir que a classe que está sendo criado.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 Suprima um aviso dessa regra somente se o tipo deve ser herdada. A ausência de `sealed` modificador sugere que o tipo é útil como um tipo base.  
  
## <a name="example-of-a-violation"></a>Exemplo de uma violação  
  
### <a name="description"></a>Descrição  
 O exemplo a seguir mostra um tipo que viola a regra.  
  
### <a name="code"></a>Código  
 [!code-csharp[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/CSharp/ca1052-static-holder-types-should-be-sealed_1.cs)]
 [!code-vb[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/VisualBasic/ca1052-static-holder-types-should-be-sealed_1.vb)]
 [!code-cpp[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/CPP/ca1052-static-holder-types-should-be-sealed_1.cpp)]  
  
## <a name="fix-with-the-static-modifier"></a>Corrigir com o modificador estático  
  
### <a name="description"></a>Descrição  
 O exemplo a seguir mostra como corrigir uma violação desta regra ao marcar o tipo com o `static` modificador.  
  
### <a name="code"></a>Código  
 [!code-csharp[FxCop.Design.StaticMembersFixed#1](../code-quality/codesnippet/CSharp/ca1052-static-holder-types-should-be-sealed_2.cs)]  
  
## <a name="related-rules"></a>Regras relacionadas  
 [CA1053: os tipos de suporte estático não devem ter construtores](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md)
