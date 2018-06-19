---
title: 'CA1006: não aninhar tipos genéricos em assinaturas de membro'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotNestGenericTypesInMemberSignatures
- CA1006
helpviewer_keywords:
- CA1006
- DoNotNestGenericTypesInMemberSignatures
ms.assetid: dfc867bc-f4af-45d7-b071-db04a248f9fc
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f6303cf96e3e8f6c4c0920336602cdbb76cc400a
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31901156"
---
# <a name="ca1006-do-not-nest-generic-types-in-member-signatures"></a>CA1006: não aninhar tipos genéricos em assinaturas de membro
|||
|-|-|
|NomeDoTipo|DoNotNestGenericTypesInMemberSignatures|
|CheckId|CA1006|
|Categoria|Microsoft.Design|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Um membro visível externamente tem uma assinatura que contém um argumento de tipo aninhado.

## <a name="rule-description"></a>Descrição da Regra
 Um argumento de tipo aninhado é um argumento de tipo que também é um tipo genérico. Para chamar um membro cuja assinatura contenha um argumento de tipo aninhado, o usuário deve criar uma instância de um tipo genérico e passar esse tipo para o construtor de um segundo tipo genérico. O procedimento e a sintaxe obrigatórios são complexos e devem ser evitados.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação desta regra, altere o design para remover o argumento de tipo aninhado.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra. Fornecer genéricos em uma sintaxe que seja fácil de entender e usar reduz o tempo que é necessário para saber mais e aumenta a taxa de adoção de novas bibliotecas.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra um método que viola a regra e a sintaxe necessária para chamar o método de violação.

 [!code-vb[FxCop.Design.NestedGenerics#1](../code-quality/codesnippet/VisualBasic/ca1006-do-not-nest-generic-types-in-member-signatures_1.vb)]
 [!code-csharp[FxCop.Design.NestedGenerics#1](../code-quality/codesnippet/CSharp/ca1006-do-not-nest-generic-types-in-member-signatures_1.cs)]

## <a name="related-rules"></a>Regras relacionadas
 [CA1005: evitar parâmetros excessivos em tipos genéricos](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010: as coleções devem implementar a interface genérica](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000: não declarar membros estáticos em tipos genéricos](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002: não expor listas genéricas](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1004: os métodos genéricos devem fornecer o parâmetro de tipo](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003: usar instâncias do manipulador de eventos genéricos](../code-quality/ca1003-use-generic-event-handler-instances.md)

 [CA1007: usar genéricos quando apropriado](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Consulte também
 [Genéricos](/dotnet/csharp/programming-guide/generics/index)