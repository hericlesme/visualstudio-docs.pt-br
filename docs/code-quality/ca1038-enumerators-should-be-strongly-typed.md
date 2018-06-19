---
title: 'CA1038: os enumeradores devem ser fortemente tipados'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- EnumeratorsShouldBeStronglyTyped
- CA1038
helpviewer_keywords:
- EnumeratorsShouldBeStronglyTyped
- CA1038
ms.assetid: 8919f526-d487-42a4-87dc-2b2ee25260c4
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b15295b0af35c927e56c37f56a48c86ac4c705af
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31898844"
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
 <xref:System.Collections.IEnumerator?displayProperty=fullName> <xref:System.Collections.CollectionBase?displayProperty=fullName> <xref:System.Collections.DictionaryBase?displayProperty=fullName> <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>