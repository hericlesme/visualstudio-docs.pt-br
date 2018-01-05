---
title: 'CA1038: Enumeradores devem ser fortemente tipados | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- EnumeratorsShouldBeStronglyTyped
- CA1038
helpviewer_keywords:
- EnumeratorsShouldBeStronglyTyped
- CA1038
ms.assetid: 8919f526-d487-42a4-87dc-2b2ee25260c4
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 84ddea0bebd5c3811da84abadd207b839ec8be48
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ca1038-enumerators-should-be-strongly-typed"></a>CA1038: os enumeradores devem ser fortemente tipados
|||  
|-|-|  
|NomeDoTipo|EnumeratorsShouldBeStronglyTyped|  
|CheckId|CA1038|  
|Categoria|Microsoft.Design|  
|Alteração Significativa|Quebra|  
  
## <a name="cause"></a>Causa  
 Implementa um tipo público ou protegido <xref:System.Collections.IEnumerator?displayProperty=fullName> , mas não fornece uma versão fortemente tipada de <xref:System.Collections.IEnumerator.Current%2A?displayProperty=fullName> propriedade. Tipos derivados dos seguintes tipos são isentos dessa regra:  
  
-   <xref:System.Collections.CollectionBase?displayProperty=fullName>  
  
-   <xref:System.Collections.DictionaryBase?displayProperty=fullName>  
  
-   <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>  
  
## <a name="rule-description"></a>Descrição da Regra  
 Essa regra requer <xref:System.Collections.IEnumerator> implementações também fornecer uma versão fortemente tipada do <xref:System.Collections.IEnumerator.Current%2A> propriedade para que os usuários não precisarão converter o valor de retorno para o tipo forte quando eles usam a funcionalidade fornecida pela interface. Essa regra pressupõe que o tipo que implementa <xref:System.Collections.IEnumerator> contém uma coleção de instâncias de um tipo que é mais forte que <xref:System.Object>.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Para corrigir uma violação desta regra, implemente a propriedade de interface explicitamente (declare-o como `IEnumerator.Current`). Adicionar versão fortemente tipada da propriedade, declarada como pública `Current`, e retornar um objeto fortemente tipado.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 Suprima um aviso dessa regra ao implementar um enumerador baseada em objeto para uso com uma coleção com base em objeto, como uma árvore binária. Tipos que estendem a nova coleção vai definir o enumerador fortemente tipado e expor a propriedade fortemente tipada.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra a maneira correta de implementar um fortemente tipada <xref:System.Collections.IEnumerator> tipo.  
  
 [!code-csharp[FxCop.Design.IEnumeratorStrongTypes#1](../code-quality/codesnippet/CSharp/ca1038-enumerators-should-be-strongly-typed_1.cs)]  
  
## <a name="related-rules"></a>Regras relacionadas  
 [CA1035: as implementações de ICollection têm membros fortemente tipados](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)  
  
 [CA1039: as listas são fortemente tipadas](../code-quality/ca1039-lists-are-strongly-typed.md)  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Collections.IEnumerator?displayProperty=fullName>   
 <xref:System.Collections.CollectionBase?displayProperty=fullName>   
 <xref:System.Collections.DictionaryBase?displayProperty=fullName>   
 <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>