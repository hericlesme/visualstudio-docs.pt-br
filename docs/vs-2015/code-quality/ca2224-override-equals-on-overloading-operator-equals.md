---
title: 'CA2224: Substituir equals ao sobrecarregar operador equals | Microsoft Docs'
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
- CA2224
- OverrideEqualsOnOverloadingOperatorEquals
- OverrideEqualsOnOverridingOperatorEquals
helpviewer_keywords:
- OverrideEqualsOnOverloadingOperatorEquals
- CA2224
ms.assetid: 7312afd9-84ba-417f-923e-7a159b53bf70
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: cd7acd4b99d3278d75aa3721137511857e04fe7c
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47587039"
---
# <a name="ca2224-override-equals-on-overloading-operator-equals"></a>CA2224: substituir igualdades em igualdades de operador de sobrecarga
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [CA2224: substituir equals ao sobrecarregar operador equals](https://docs.microsoft.com/visualstudio/code-quality/ca2224-override-equals-on-overloading-operator-equals).

|||
|-|-|
|NomeDoTipo|OverrideEqualsOnOverloadingOperatorEquals|
|CheckId|CA2224|
|Categoria|Microsoft.Usage|
|Alteração Significativa|Não separável|

## <a name="cause"></a>Causa
 Um tipo público implementa o operador de igualdade, mas não substitui <xref:System.Object.Equals%2A?displayProperty=fullName>.

## <a name="rule-description"></a>Descrição da Regra
 O operador de igualdade se destina a ser uma forma conveniente sintaticamente para acessar a funcionalidade do <xref:System.Object.Equals%2A> método. Se você implementar o operador de igualdade, sua lógica deve ser idêntica de <xref:System.Object.Equals%2A>.

 O compilador c# emite um aviso se seu código viola essa regra.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, você deve remover a implementação do operador de igualdade ou substituir <xref:System.Object.Equals%2A> e ter os dois métodos retornam os mesmos valores. Se o operador de igualdade não introduz um comportamento inconsistente, você poderá corrigir a violação, fornecendo uma implementação de <xref:System.Object.Equals%2A> que chama o <xref:System.Object.Equals%2A> método na classe base.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 É seguro suprimir um aviso nessa regra, se o operador de igualdade retorna o mesmo valor que a implementação herdada de <xref:System.Object.Equals%2A>. A seção de exemplo inclui um tipo que com segurança possível suprimir um aviso nessa regra.

## <a name="examples-of-inconsistent-equality-definitions"></a>Exemplos de definições de igualdade inconsistente

### <a name="description"></a>Descrição
 O exemplo a seguir mostra um tipo com definições inconsistentes de igualdade. `BadPoint` Altera o significado de igualdade, fornecendo uma implementação personalizada do operador de igualdade, mas não substitui <xref:System.Object.Equals%2A> , de modo que ele se comporta de forma idêntica.

### <a name="code"></a>Código
 [!code-csharp[FxCop.Usage.OperatorEqualsRequiresEquals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperatorEqualsRequiresEquals/cs/FxCop.Usage.OperatorEqualsRequiresEquals.cs#1)]

## <a name="example"></a>Exemplo
 O código a seguir testa o comportamento de `BadPoint`.

 [!code-csharp[FxCop.Usage.TestOperatorEqualsRequiresEquals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.TestOperatorEqualsRequiresEquals/cs/FxCop.Usage.TestOperatorEqualsRequiresEquals.cs#1)]

 Este exemplo gerencia a seguinte saída.

 **a = (1,1 [0]) e b = (2,2 [1]) são iguais? Não**
**um = = b? Não**
**a1 e a são iguais? Sim**
**a1 = = um? Sim**
**b e bcopy são iguais? Não**
**b = = bcopy? Sim**
## <a name="example"></a>Exemplo
 O exemplo a seguir mostra um tipo que tecnicamente viola essa regra, mas não se comportar de maneira inconsistente.

 [!code-csharp[FxCop.Usage.ValueTypeEquals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ValueTypeEquals/cs/FxCop.Usage.ValueTypeEquals.cs#1)]

## <a name="example"></a>Exemplo
 O código a seguir testa o comportamento de `GoodPoint`.

 [!code-csharp[FxCop.Usage.TestValueTypeEquals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.TestValueTypeEquals/cs/FxCop.Usage.TestValueTypeEquals.cs#1)]

 Este exemplo gerencia a seguinte saída.

 **a = (1,1) e b = (2,2) são iguais? Não**
**um = = b? Não**
**a1 e a são iguais? Sim**
**a1 = = um? Sim**
**b e bcopy são iguais? Sim**
**b = = bcopy? Sim**
## <a name="class-example"></a>Exemplo de classe

### <a name="description"></a>Descrição
 O exemplo a seguir mostra uma classe (tipo de referência) que viola essa regra.

### <a name="code"></a>Código
 [!code-csharp[FxCop.Usage.OverrideEqualsClassViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OverrideEqualsClassViolation/cs/FxCop.Usage.OverrideEqualsClassViolation.cs#1)]

## <a name="example"></a>Exemplo
 O exemplo a seguir corrige a violação, substituindo <xref:System.Object.Equals%2A?displayProperty=fullName>.

 [!code-csharp[FxCop.Usage.OverrideEqualsClassFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OverrideEqualsClassFixed/cs/FxCop.Usage.OverrideEqualsClassFixed.cs#1)]

## <a name="structure-example"></a>Exemplo de estrutura

### <a name="description"></a>Descrição
 O exemplo a seguir mostra uma estrutura (tipo de valor) que viola essa regra.

### <a name="code"></a>Código
 [!code-csharp[FxCop.Usage.OverrideEqualsStructViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OverrideEqualsStructViolation/cs/FxCop.Usage.OverrideEqualsStructViolation.cs#1)]

## <a name="example"></a>Exemplo
 O exemplo a seguir corrige a violação, substituindo <xref:System.ValueType.Equals%2A?displayProperty=fullName>.

 [!code-csharp[FxCop.Usage.OverrideEqualsStructFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OverrideEqualsStructFixed/cs/FxCop.Usage.OverrideEqualsStructFixed.cs#1)]

## <a name="related-rules"></a>Regras relacionadas
 [CA1046: não sobrecarregar operador Equals em tipos de referência](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

 [CA2225: as sobrecargas do operador têm alternativos nomeados](../code-quality/ca2225-operator-overloads-have-named-alternates.md)

 [CA2226: os operadores devem ter sobrecargas simétricas](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

 [CA2218: substituir GetHashCode em igualdades de substituição](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

 [CA2231: sobrecarregar operador Equals ao substituir ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)



