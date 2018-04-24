---
title: 'CA1036: substituir métodos em tipos comparáveis'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1036
- OverrideMethodsOnComparableTypes
helpviewer_keywords:
- OverrideMethodsOnComparableTypes
- CA1036
ms.assetid: 2329f844-4cb8-426d-bee2-cd065d1346d0
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 12254202e2bae5a0846d2772006514eb470b5bdf
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/19/2018
---
# <a name="ca1036-override-methods-on-comparable-types"></a>CA1036: substituir métodos em tipos comparáveis
|||
|-|-|
|NomeDoTipo|OverrideMethodsOnComparableTypes|
|CheckId|CA1036|
|Categoria|Microsoft.Design|
|Alteração Significativa|Não recentes|

## <a name="cause"></a>Causa
 Um tipo público ou protegido implementa o <xref:System.IComparable?displayProperty=fullName> interface e não substituir <xref:System.Object.Equals%2A?displayProperty=fullName> ou não sobrecarregar o operador de idioma específico para igualdade, desigualdade, menor ou maior. A regra não relatará uma violação se o tipo herda somente uma implementação da interface.

## <a name="rule-description"></a>Descrição da Regra
 Os tipos que definem uma ordem de classificação personalizada implementar o <xref:System.IComparable> interface. O <xref:System.IComparable.CompareTo%2A> método retorna um valor inteiro que indica a ordem de classificação correta para que duas instâncias do tipo. Essa regra identifica os tipos de definir uma ordem de classificação. Isso implica que o significado comum de igualdade, desigualdade, menor e maior que não se aplicam. Quando você fornecer uma implementação de <xref:System.IComparable>, você normalmente deve também substituir <xref:System.Object.Equals%2A> para que ele retorna valores que são consistentes com <xref:System.IComparable.CompareTo%2A>. Se você substituir <xref:System.Object.Equals%2A> e codificar em um idioma que oferece suporte a sobrecargas de operador, você também deve fornecer os operadores que são consistentes com <xref:System.Object.Equals%2A>.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação desta regra, substituir <xref:System.Object.Equals%2A>. Se a linguagem de programação dá suporte a sobrecarga de operador, forneça os seguintes operadores:

-   op_Equality

-   op_Inequality

-   op_LessThan

-   op_GreaterThan

 No c#, os tokens que são usados para representar esses operadores são os seguintes: = =,! =, \<, e >.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 É seguro suprimir um aviso dessa regra quando a violação é causada por falta de operadores e a linguagem de programação não oferece suporte a sobrecarga de operador, como é o caso com o Visual Basic. Também é seguro suprimir um aviso para essa regra quando ele é acionado em operadores de igualdade que op_Equality se você determinar que os operadores a implementação não faz sentido no contexto de seu aplicativo. No entanto, você deve sempre sobre op_Equality e o operador = = se substitui Object. Equals.

## <a name="example"></a>Exemplo
 O exemplo a seguir contém um tipo que implementa corretamente <xref:System.IComparable>. Comentários de código identificam os métodos que atendem várias regras relacionadas a <xref:System.Object.Equals%2A> e <xref:System.IComparable> interface.

 [!code-csharp[FxCop.Design.IComparable#1](../code-quality/codesnippet/CSharp/ca1036-override-methods-on-comparable-types_1.cs)]

## <a name="example"></a>Exemplo
 O aplicativo a seguir testa o comportamento do <xref:System.IComparable> implementação foi mostrada anteriormente.

 [!code-csharp[FxCop.Design.TestIComparable#1](../code-quality/codesnippet/CSharp/ca1036-override-methods-on-comparable-types_2.cs)]

## <a name="see-also"></a>Consulte também
 <xref:System.IComparable?displayProperty=fullName> <xref:System.Object.Equals%2A?displayProperty=fullName> [Operadores de igualdade](/dotnet/standard/design-guidelines/equality-operators)