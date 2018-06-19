---
title: 'CA1003: usar instâncias do manipulador de eventos genéricos'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseGenericEventHandlerInstances
- CA1003
helpviewer_keywords:
- CA1003
- UseGenericEventHandlerInstances
ms.assetid: 402101b6-555d-4cf7-b223-1d9fdfaaf1cd
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e605cb0188ca72cb74905e34ee5196a07f748cd6
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31899958"
---
# <a name="ca1003-use-generic-event-handler-instances"></a>CA1003: usar instâncias do manipulador de eventos genéricos
|||
|-|-|
|NomeDoTipo|UseGenericEventHandlerInstances|
|CheckId|CA1003|
|Categoria|Microsoft.Design|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Um tipo contém um delegado que retorna void, cuja assinatura contém dois parâmetros (o primeiro um objeto e o segundo um tipo que pode ser atribuído a EventArgs) e os destinos de assembly contendo [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)].

## <a name="rule-description"></a>Descrição da Regra
 Antes de [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)], para passar informações personalizadas para o manipulador de eventos, um novo delegado teve de ser declarada que especificou uma classe que deriva do <xref:System.EventArgs?displayProperty=fullName> classe. Isso não ocorre mais no [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)], que introduziu o <xref:System.EventHandler%601?displayProperty=fullName> delegate. Este delegado genérico permite que qualquer classe que é derivada de <xref:System.EventArgs> a ser usado junto com o manipulador de eventos.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação desta regra, remova o delegado e substituir seu uso usando o <xref:System.EventHandler%601?displayProperty=fullName> delegate. Se o representante é gerado automaticamente pelo [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] compilador, alterar a sintaxe da declaração de evento para usar o <xref:System.EventHandler%601?displayProperty=fullName> delegate.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra um delegado que viola a regra. No [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] exemplo, comentários descrevem como modificar o exemplo para satisfazer a regra. Para obter o exemplo c#, segue um exemplo que mostra o código modificado.

 [!code-vb[FxCop.Design.CustomEventHandler#1](../code-quality/codesnippet/VisualBasic/ca1003-use-generic-event-handler-instances_1.vb)]
 [!code-csharp[FxCop.Design.CustomEventHandler#1](../code-quality/codesnippet/CSharp/ca1003-use-generic-event-handler-instances_1.cs)]

## <a name="example"></a>Exemplo
 O exemplo a seguir remove a declaração de delegado do exemplo anterior, que atende a regra e substitui seu uso no `ClassThatRaisesEvent` e `ClassThatHandlesEvent` métodos usando o <xref:System.EventHandler%601?displayProperty=fullName> delegate.

 [!code-csharp[FxCop.Design.GenericEventHandler#1](../code-quality/codesnippet/CSharp/ca1003-use-generic-event-handler-instances_2.cs)]

## <a name="related-rules"></a>Regras relacionadas
 [CA1005: evitar parâmetros excessivos em tipos genéricos](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010: as coleções devem implementar a interface genérica](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000: não declarar membros estáticos em tipos genéricos](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002: não expor listas genéricas](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006: não aninhar tipos genéricos em assinaturas de membro](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004: os métodos genéricos devem fornecer o parâmetro de tipo](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1007: usar genéricos quando apropriado](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Consulte também
 [Genéricos](/dotnet/csharp/programming-guide/generics/index)