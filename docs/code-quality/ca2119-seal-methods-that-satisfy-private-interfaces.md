---
title: "CA2119: Métodos de lacre que satisfazem interfaces privadas | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SealMethodsThatSatisfyPrivateInterfaces
- CA2119
helpviewer_keywords:
- CA2119
- SealMethodsThatSatisfyPrivateInterfaces
ms.assetid: 483d02e1-cfaf-4754-a98f-4116df0f3509
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: b61a3e81ff7be1ff868f2dd9ce42dd5cb10522cb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ca2119-seal-methods-that-satisfy-private-interfaces"></a>CA2119: os métodos para lacrar que atendam a interfaces privadas
|||  
|-|-|  
|NomeDoTipo|SealMethodsThatSatisfyPrivateInterfaces|  
|CheckId|CA2119|  
|Categoria|Microsoft.Security|  
|Alteração Significativa|Quebra|  
  
## <a name="cause"></a>Causa  
 Um tipo público herdável fornece uma implementação de método substituível de um `internal` (`Friend` no Visual Basic) interface.  
  
## <a name="rule-description"></a>Descrição da Regra  
 Métodos de interface tem acessibilidade pública, que não pode ser alterada pelo tipo de implementação. Uma interface interna cria um contrato que não se destina a ser implementada fora do assembly que define a interface. Um tipo público que implementa um método de uma interface interna usando o `virtual` (`Overridable` no Visual Basic) modificador permite que o método a ser substituído por um tipo derivado que está fora do assembly. Se um segundo tipo de definição de assembly chama o método e espera um contrato somente interno, o comportamento pode ficar comprometido quando, em vez disso, o método substituído no assembly externo é executado. Isso cria uma vulnerabilidade de segurança.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Para corrigir uma violação desta regra, impedem que o método que está sendo substituído fora do assembly usando um dos seguintes:  
  
-   Verifique o tipo de declaração `sealed` (`NotInheritable` no Visual Basic).  
  
-   Altere a acessibilidade do tipo declarativo a `internal` (`Friend` no Visual Basic).  
  
-   Remova todos os construtores públicos do tipo de declaração.  
  
-   Implementar o método sem usar o `virtual` modificador.  
  
-   Implemente o método explicitamente.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 É seguro suprimir um aviso de que essa regra se, após uma análise cuidadosa, não existe nenhum problema de segurança que pode ser explorável se o método for substituído fora do assembly.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra um tipo, `BaseImplementation`, que viola essa regra.  
  
 [!code-cpp[FxCop.Security.SealMethods1#1](../code-quality/codesnippet/CPP/ca2119-seal-methods-that-satisfy-private-interfaces_1.cpp)]
 [!code-csharp[FxCop.Security.SealMethods1#1](../code-quality/codesnippet/CSharp/ca2119-seal-methods-that-satisfy-private-interfaces_1.cs)]
 [!code-vb[FxCop.Security.SealMethods1#1](../code-quality/codesnippet/VisualBasic/ca2119-seal-methods-that-satisfy-private-interfaces_1.vb)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir explora a implementação do método virtual do exemplo anterior.  
  
 [!code-cpp[FxCop.Security.SealMethods2#1](../code-quality/codesnippet/CPP/ca2119-seal-methods-that-satisfy-private-interfaces_2.cpp)]
 [!code-csharp[FxCop.Security.SealMethods2#1](../code-quality/codesnippet/CSharp/ca2119-seal-methods-that-satisfy-private-interfaces_2.cs)]
 [!code-vb[FxCop.Security.SealMethods2#1](../code-quality/codesnippet/VisualBasic/ca2119-seal-methods-that-satisfy-private-interfaces_2.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces](/dotnet/csharp/programming-guide/interfaces/index)   
 [Interfaces](/dotnet/visual-basic/programming-guide/language-features/interfaces/index)