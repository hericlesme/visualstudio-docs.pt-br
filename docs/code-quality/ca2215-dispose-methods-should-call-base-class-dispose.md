---
title: "CA2215: Métodos Dispose devem chamar dispose da classe base | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2215
- DisposeMethodsShouldCallBaseClassDispose
- Dispose methods should call base class dispose
helpviewer_keywords:
- DisposeMethodsShouldCallBaseClassDispose
- CA2215
ms.assetid: c772e7a6-a87e-425c-a70e-912664ae9042
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0659b9ec82353e3c658f1ba89f07fad197dd8670
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="ca2215-dispose-methods-should-call-base-class-dispose"></a>CA2215: os métodos de descarte devem chamar o descarte da classe base
|||  
|-|-|  
|NomeDoTipo|DisposeMethodsShouldCallBaseClassDispose|  
|CheckId|CA2215|  
|Categoria|Microsoft.Usage|  
|Alteração Significativa|Não separáveis|  
  
## <a name="cause"></a>Causa  
 Um tipo que implementa <xref:System.IDisposable?displayProperty=fullName> herda de um tipo que implementa também <xref:System.IDisposable>. O <xref:System.IDisposable.Dispose%2A> não chama o método do tipo herdo o <xref:System.IDisposable.Dispose%2A> método do tipo pai.  
  
## <a name="rule-description"></a>Descrição da Regra  
 Se um tipo herda de um tipo descartável, ele deverá chamar o <xref:System.IDisposable.Dispose%2A> método do tipo de base em seu próprio <xref:System.IDisposable.Dispose%2A> método. Chamar o método do tipo base Dispose garante que todos os recursos criados pelo tipo de base são lançados.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Para corrigir uma violação desta regra, chame `base`.<xref:System.IDisposable.Dispose%2A> no seu <xref:System.IDisposable.Dispose%2A> método.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 É seguro suprimir um aviso de que essa regra se a chamada para `base`.<xref:System.IDisposable.Dispose%2A> ocorre em um nível mais profundo de chamada que as verificações de regra.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra um tipo `TypeA` que implementa <xref:System.IDisposable>.  
  
 [!code-csharp[FxCop.Usage.IDisposablePattern#1](../code-quality/codesnippet/CSharp/ca2215-dispose-methods-should-call-base-class-dispose_1.cs)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra um tipo `TypeB` que herda do tipo `TypeA` e chama corretamente seu <xref:System.IDisposable.Dispose%2A> método.  
  
 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../code-quality/codesnippet/VisualBasic/ca2215-dispose-methods-should-call-base-class-dispose_2.vb)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.IDisposable?displayProperty=fullName>   
 [Padrão de Dispose](/dotnet/standard/design-guidelines/dispose-pattern)