---
title: 'CA1816: Chamar GC. SuppressFinalize corretamente | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1816
- DisposeMethodsShouldCallSuppressFinalize
helpviewer_keywords:
- DisposeMethodsShouldCallSuppressFinalize
- CA1816
ms.assetid: 47915fbb-103f-4333-b157-1da16bf49660
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5e99f722d211b2e1bd548f1bf22c995246f3e0b4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="ca1816-call-gcsuppressfinalize-correctly"></a>CA1816: chamar GC.SuppressFinalize corretamente
|||  
|-|-|  
|NomeDoTipo|CallGCSuppressFinalizeCorrectly|  
|CheckId|CA1816|  
|Categoria|Microsoft. Uso|  
|Alteração Significativa|Não separáveis|  
  
## <a name="cause"></a>Causa  
  
-   Um método que é uma implementação de <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> não chama <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.  
  
-   Um método que não é uma implementação de <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> chamadas <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.  
  
-   Chama um método <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> e passa algo diferente desse (Me no Visual Basic).  
  
## <a name="rule-description"></a>Descrição da Regra  
 O <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> método permite que os usuários liberar os recursos a qualquer momento antes do objeto se torna disponível para coleta de lixo. Se o <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> método é chamado, ele libera os recursos do objeto. Isso torna a finalização desnecessária. <xref:System.IDisposable.Dispose%2A?displayProperty=fullName>deve chamar <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> para o coletor de lixo não chamar o finalizador do objeto.  
  
 Para impedir que os tipos derivados com finalizadores precisar reimplementar <xref:System.IDisposable> e para chamá-lo, sem lacre tipos sem os finalizadores devem chamar ainda <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Para corrigir uma violação desta regra:  
  
 Se o método é uma implementação de <xref:System.IDisposable.Dispose%2A>, adicione uma chamada para <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.  
  
 Se o método não é uma implementação de <xref:System.IDisposable.Dispose%2A>, remova a chamada para <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> ou movê-lo para o tipo <xref:System.IDisposable.Dispose%2A> implementação.  
  
 Alterar todas as chamadas para <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> para passar esse (Me no Visual Basic).  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 Somente suprimir um aviso dessa regra, se você estiver deliberating usando <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> para controlar o tempo de vida de outros objetos. Não suprimir um aviso de que essa regra se uma implementação de <xref:System.IDisposable.Dispose%2A> não chama <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>. Nessa situação, falhando suprimir a finalização degrada o desempenho e não fornecer nenhum benefícios.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra um método que incorretamente chamadas <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.  
  
 [!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../code-quality/codesnippet/VisualBasic/ca1816-call-gc-suppressfinalize-correctly_1.vb)]
 [!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../code-quality/codesnippet/CSharp/ca1816-call-gc-suppressfinalize-correctly_1.cs)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra um método que corretamente chamadas <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.  
  
 [!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../code-quality/codesnippet/VisualBasic/ca1816-call-gc-suppressfinalize-correctly_2.vb)]
 [!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../code-quality/codesnippet/CSharp/ca1816-call-gc-suppressfinalize-correctly_2.cs)]  
  
## <a name="related-rules"></a>Regras relacionadas  
 [CA2215: métodos Dispose devem chamar o descarte da classe base](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)  
  
 [CA2216: os tipos descartáveis devem declarar o finalizador](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)  
  
## <a name="see-also"></a>Consulte também  
 [Padrão de Dispose](/dotnet/standard/design-guidelines/dispose-pattern)