---
title: 'CA2224: substituir igualdades em igualdades de operador de sobrecarga'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2224
- OverrideEqualsOnOverloadingOperatorEquals
- OverrideEqualsOnOverridingOperatorEquals
helpviewer_keywords:
- OverrideEqualsOnOverloadingOperatorEquals
- CA2224
ms.assetid: 7312afd9-84ba-417f-923e-7a159b53bf70
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f8836644e109e37855aa79dc67b461591b273786
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31921506"
---
# <a name="ca2224-override-equals-on-overloading-operator-equals"></a>CA2224: substituir igualdades em igualdades de operador de sobrecarga
|||
|-|-|
|NomeDoTipo|OverrideEqualsOnOverloadingOperatorEquals|
|CheckId|CA2224|
|Categoria|Microsoft.Usage|
|Alteração Significativa|Não separáveis|

## <a name="cause"></a>Causa
 Um tipo público implementa o operador de igualdade, mas não substitui <xref:System.Object.Equals%2A?displayProperty=fullName>.

## <a name="rule-description"></a>Descrição da Regra
 O operador de igualdade deve ser uma maneira conveniente sintaticamente para acessar a funcionalidade do <xref:System.Object.Equals%2A> método. Se você implementa o operador de igualdade, sua lógica deve ser idêntica de <xref:System.Object.Equals%2A>.

 O compilador c# emite um aviso se o seu código viola essa regra.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação desta regra, você deve remover a implementação do operador de igualdade ou substituir <xref:System.Object.Equals%2A> e ter os dois métodos retornam os mesmos valores. Se o operador de igualdade não apresentar um comportamento inconsistente, você poderá corrigir a violação, fornecendo uma implementação de <xref:System.Object.Equals%2A> que chama o <xref:System.Object.Equals%2A> método na classe base.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 É seguro suprimir um aviso de que essa regra se o operador de igualdade retorna o mesmo valor que a implementação herdada do <xref:System.Object.Equals%2A>. A seção de exemplo inclui um tipo de segurança pode suprimir um aviso dessa regra.

## <a name="examples-of-inconsistent-equality-definitions"></a>Exemplos de definições de igualdade inconsistente

### <a name="description"></a>Descrição
 O exemplo a seguir mostra um tipo com definições inconsistente de igualdade. `BadPoint` Altera o significado de igualdade, fornecendo uma implementação personalizada do operador de igualdade, mas não substitui <xref:System.Object.Equals%2A> para que ele se comporta de forma idêntica.

### <a name="code"></a>Código
 [!code-csharp[FxCop.Usage.OperatorEqualsRequiresEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_1.cs)]

## <a name="example"></a>Exemplo
 O código a seguir testa o comportamento de `BadPoint`.

 [!code-csharp[FxCop.Usage.TestOperatorEqualsRequiresEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_2.cs)]

 Este exemplo gerencia a seguinte saída.

 **a = (1,1 [0]) e b = (2,2 [1]) são iguais? Não**
**um = = b? Não**
**a1 e a são iguais? Sim**
**a1 = = um? Sim**
**b e bcopy são iguais? Não**
**b = = bcopy? Sim**
## <a name="example"></a>Exemplo
 O exemplo a seguir mostra um tipo que tecnicamente viola essa regra, mas não se comportar de forma inconsistente.

 [!code-csharp[FxCop.Usage.ValueTypeEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_3.cs)]

## <a name="example"></a>Exemplo
 O código a seguir testa o comportamento de `GoodPoint`.

 [!code-csharp[FxCop.Usage.TestValueTypeEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_4.cs)]

 Este exemplo gerencia a seguinte saída.

 **a = (1,1) e b = (2,2) são iguais? Não**
**um = = b? Não**
**a1 e a são iguais? Sim**
**a1 = = um? Sim**
**b e bcopy são iguais? Sim**
**b = = bcopy? Sim**
## <a name="class-example"></a>Exemplo de classe

### <a name="description"></a>Descrição
 O exemplo a seguir mostra uma classe (tipo de referência) que violam essa regra.

### <a name="code"></a>Código
 [!code-csharp[FxCop.Usage.OverrideEqualsClassViolation#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_5.cs)]

## <a name="example"></a>Exemplo
 O exemplo a seguir corrige a violação, substituindo <xref:System.Object.Equals%2A?displayProperty=fullName>.

 [!code-csharp[FxCop.Usage.OverrideEqualsClassFixed#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_6.cs)]

## <a name="structure-example"></a>Exemplo de estrutura

### <a name="description"></a>Descrição
 O exemplo a seguir mostra a estrutura (tipo de valor) que violam essa regra.

### <a name="code"></a>Código
 [!code-csharp[FxCop.Usage.OverrideEqualsStructViolation#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_7.cs)]

## <a name="example"></a>Exemplo
 O exemplo a seguir corrige a violação, substituindo <xref:System.ValueType.Equals%2A?displayProperty=fullName>.

 [!code-csharp[FxCop.Usage.OverrideEqualsStructFixed#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_8.cs)]

## <a name="related-rules"></a>Regras relacionadas
 [CA1046: não sobrecarregar operador Equals em tipos de referência](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

 [CA2225: as sobrecargas do operador têm alternativos nomeados](../code-quality/ca2225-operator-overloads-have-named-alternates.md)

 [CA2226: os operadores devem ter sobrecargas simétricas](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

 [CA2218: substituir GetHashCode em igualdades de substituição](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

 [CA2231: sobrecarregar operador Equals ao substituir ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)