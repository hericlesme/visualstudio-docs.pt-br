---
title: 'CA1033: os métodos de interface devem ser chamáveis por tipos filho'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- InterfaceMethodsShouldBeCallableByChildTypes
- CA1033
helpviewer_keywords:
- CA1033
- InterfaceMethodsShouldBeCallableByChildTypes
ms.assetid: 9f171497-a5e3-4769-a77b-7aed755b2662
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d2c1a622519e08d4b56fdd8e6811ec039f9d3871
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="ca1033-interface-methods-should-be-callable-by-child-types"></a>CA1033: os métodos de interface devem ser chamáveis por tipos filho
|||
|-|-|
|NomeDoTipo|InterfaceMethodsShouldBeCallableByChildTypes|
|CheckId|CA1033|
|Categoria|Microsoft.Design|
|Alteração Significativa|Não recentes|

## <a name="cause"></a>Causa
 Um tipo visível externamente sem lacre fornece uma implementação de método explícita de uma interface pública e não fornece um método visível externamente alternativo com o mesmo nome.

## <a name="rule-description"></a>Descrição da Regra
 Considere a possibilidade de um tipo base que explicitamente implementa um método de interface pública. Um tipo derivado do tipo base pode acessar o método de interface herdada por meio de uma referência para a instância atual (`this` em c#) que é convertido para a interface. Se o tipo derivado novamente (explicitamente) implementa o método de interface herdada, a implementação base não pode mais ser acessada. A chamada por meio da referência de instância atual invocará a implementação derivada; Isso causa recursão e um estouro de pilha eventual.

 Essa regra não relata uma violação de uma implementação explícita de <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> quando externamente visível `Close()` ou `System.IDisposable.Dispose(Boolean)` método é fornecido.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação desta regra, implemente um novo método que expõe a mesma funcionalidade e é visível para tipos derivados ou alterar uma implementação não explícitas. Se uma alteração significativa é aceitável, uma alternativa é fazer o tipo lacrado.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 É seguro suprimir um aviso de que essa regra se um método externamente visível for fornecido, que tem a mesma funcionalidade, mas o método implementado explicitamente um nome diferente.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra um tipo `ViolatingBase`, que viola a regra e um tipo, `FixedBase`, que mostra uma correção para a violação.

 [!code-csharp[FxCop.Design.ExplicitMethodImplementations#1](../code-quality/codesnippet/CSharp/ca1033-interface-methods-should-be-callable-by-child-types_1.cs)]

## <a name="see-also"></a>Consulte também
 [Interfaces](/dotnet/csharp/programming-guide/interfaces/index)