---
title: 'CA1815: substituir igualdades e igualdades de operador em tipos de valor'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1815
- OverrideEqualsAndOperatorEqualsOnValueTypes
helpviewer_keywords:
- OverrideEqualsAndOperatorEqualsOnValueTypes
- CA1815
ms.assetid: 0a8ab3a3-ee8e-46f7-985d-dcf00c89363b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4d3fbe44347e1d0c453c2db9de1f5deac84ab771
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31914800"
---
# <a name="ca1815-override-equals-and-operator-equals-on-value-types"></a>CA1815: substituir igualdades e igualdades de operador em tipos de valor
|||
|-|-|
|NomeDoTipo|OverrideEqualsAndOperatorEqualsOnValueTypes|
|CheckId|CA1815|
|Categoria|Microsoft.Performance|
|Alteração Significativa|Não recentes|

## <a name="cause"></a>Causa
 Um tipo de valor público não substituir <xref:System.Object.Equals%2A?displayProperty=fullName>, ou não implementa o operador de igualdade (= =). Esta regra não verifica as enumerações.

## <a name="rule-description"></a>Descrição da Regra
 Para tipos de valor, a implementação herdada do <xref:System.Object.Equals%2A> usa a biblioteca de reflexão e compara o conteúdo de todos os campos. Reflection é computacionalmente cara, e pode ser desnecessário comparar a igualdade de cada campo. Se você espera que os usuários para comparar ou classificar instâncias ou usá-los como chaves de tabela de hash, o tipo de valor deve implementar <xref:System.Object.Equals%2A>. Se a linguagem de programação der suporte à sobrecarga de operador, também é necessário fornecer uma implementação dos operadores de igualdade e desigualdade.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação desta regra, forneça uma implementação de <xref:System.Object.Equals%2A>. Se você pode implementar o operador de igualdade.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 É seguro suprimir um aviso dessa regra se as instâncias do tipo de valor não serão comparadas umas às outras.

## <a name="example-of-a-violation"></a>Exemplo de uma violação

### <a name="description"></a>Descrição
 O exemplo a seguir mostra a estrutura (tipo de valor) que violam essa regra.

### <a name="code"></a>Código
 [!code-csharp[FxCop.Performance.OverrideEqualsViolation#1](../code-quality/codesnippet/CSharp/ca1815-override-equals-and-operator-equals-on-value-types_1.cs)]

## <a name="example-of-how-to-fix"></a>Exemplo de como corrigir

### <a name="description"></a>Descrição
 O exemplo a seguir corrige a violação anterior, substituindo <xref:System.ValueType.Equals%2A?displayProperty=fullName> e implementar os operadores de igualdade (= =,! =).

### <a name="code"></a>Código
 [!code-csharp[FxCop.Performance.OverrideEqualsFixed#1](../code-quality/codesnippet/CSharp/ca1815-override-equals-and-operator-equals-on-value-types_2.cs)]

## <a name="related-rules"></a>Regras relacionadas
 [CA2224: substituir Equals ao sobrecarregar o operador Equals](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)

 [CA2231: sobrecarregar operador Equals ao substituir ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)

 [CA2226: os operadores devem ter sobrecargas simétricas](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

## <a name="see-also"></a>Consulte também
 <xref:System.Object.Equals%2A?displayProperty=fullName>