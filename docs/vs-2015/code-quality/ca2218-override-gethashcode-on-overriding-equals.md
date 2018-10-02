---
title: 'CA2218: Substituir GetHashCode em igualdades de substituição | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2218
- OverrideGetHashCodeOnOverridingEquals
helpviewer_keywords:
- OverrideGetHashCodeOnOverridingEquals
- CA2218
ms.assetid: 69b020cd-29e8-45a6-952e-32cf3ce2e21d
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: b952252b5b035242e69806e81b95884e05f862c5
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47587028"
---
# <a name="ca2218-override-gethashcode-on-overriding-equals"></a>CA2218: substituir GetHashCode em igualdades de substituição
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [CA2218: substituir GetHashCode em igualdades de substituição](https://docs.microsoft.com/visualstudio/code-quality/ca2218-override-gethashcode-on-overriding-equals).

|||
|-|-|
|NomeDoTipo|OverrideGetHashCodeOnOverridingEquals|
|CheckId|CA2218|
|Categoria|Microsoft.Usage|
|Alteração Significativa|Não separável|

## <a name="cause"></a>Causa
 Um tipo público substitui <xref:System.Object.Equals%2A?displayProperty=fullName> mas não substitui <xref:System.Object.GetHashCode%2A?displayProperty=fullName>.

## <a name="rule-description"></a>Descrição da Regra
 <xref:System.Object.GetHashCode%2A> Retorna um valor, com base na instância atual, que é adequada para algoritmos de hash e estruturas de dados como uma tabela de hash. Dois objetos que são do mesmo tipo e forem iguais devem retornar o mesmo código hash para garantir que instâncias dos tipos a seguir funcionem corretamente:

-   <xref:System.Collections.Hashtable?displayProperty=fullName>

-   <xref:System.Collections.SortedList?displayProperty=fullName>

-   <xref:System.Collections.Generic.Dictionary%602?displayProperty=fullName>

-   <xref:System.Collections.Generic.SortedDictionary%602?displayProperty=fullName>

-   <xref:System.Collections.Generic.SortedList%602?displayProperty=fullName>

-   <xref:System.Collections.Specialized.HybridDictionary?displayProperty=fullName>

-   <xref:System.Collections.Specialized.ListDictionary?displayProperty=fullName>

-   <xref:System.Collections.Specialized.OrderedDictionary?displayProperty=fullName>

-   Tipos que implementam <xref:System.Collections.Generic.IEqualityComparer%601?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, fornecer uma implementação de <xref:System.Object.GetHashCode%2A>. Para um par de objetos do mesmo tipo, você deve assegurar que a implementação retorna o mesmo valor se sua implementação de <xref:System.Object.Equals%2A> retorna `true` para o par.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra.

## <a name="class-example"></a>Exemplo de classe

### <a name="description"></a>Descrição
 O exemplo a seguir mostra uma classe (tipo de referência) que viola essa regra.

### <a name="code"></a>Código
 [!code-csharp[FxCop.Usage.GetHashCodeErrorClass#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.GetHashCodeErrorClass/cs/FxCop.Usage.GetHashCodeErrorClass.cs#1)]

### <a name="comments"></a>Comentários
 O exemplo a seguir corrige a violação, substituindo <xref:System.Object.GetHashCode>.

### <a name="code"></a>Código
 [!code-csharp[FxCop.Usage.GetHashCodeFixedClass#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.GetHashCodeFixedClass/cs/FxCop.Usage.GetHashCodeFixedClass.cs#1)]

## <a name="structure-example"></a>Exemplo de estrutura

### <a name="description"></a>Descrição
 O exemplo a seguir mostra uma estrutura (tipo de valor) que viola essa regra.

### <a name="code"></a>Código
 [!code-csharp[FxCop.Usage.GetHashCodeErrorStruct#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.GetHashCodeErrorStruct/cs/FxCop.Usage.GetHashCodeErrorStruct.cs#1)]

### <a name="comments"></a>Comentários
 O exemplo a seguir corrige a violação, substituindo <xref:System.Object.GetHashCode>.

### <a name="code"></a>Código
 [!code-csharp[FxCop.Usage.GetHashCodeFixedStruct#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.GetHashCodeFixedStruct/cs/FxCop.Usage.GetHashCodeFixedStruct.cs#1)]

## <a name="related-rules"></a>Regras relacionadas
 [CA1046: não sobrecarregar operador Equals em tipos de referência](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

 [CA2225: as sobrecargas do operador têm alternativos nomeados](../code-quality/ca2225-operator-overloads-have-named-alternates.md)

 [CA2226: os operadores devem ter sobrecargas simétricas](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

 [CA2224: substituir Equals ao sobrecarregar o operador Equals](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)

 [CA2231: sobrecarregar operador Equals ao substituir ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)

## <a name="see-also"></a>Consulte também

- <xref:System.Object.Equals%2A?displayProperty=fullName>
- <xref:System.Object.GetHashCode%2A?displayProperty=fullName>
- <xref:System.Collections.Hashtable?displayProperty=fullName>
- [Operadores de igualdade](http://msdn.microsoft.com/library/bc496a91-fefb-4ce0-ab4c-61f09964119a)