---
title: 'CA1406: evitar argumentos Int64 para clientes do Visual Basic 6'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidInt64ArgumentsForVB6Clients
- CA1406
helpviewer_keywords:
- AvoidInt64ArgumentsForVB6Clients
- CA1406
ms.assetid: d5d0d3fc-f105-43da-be5b-923ab023309c
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 36c8ceb93f4784fa3ff50343b8b9cd7770e69533
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/19/2018
---
# <a name="ca1406-avoid-int64-arguments-for-visual-basic-6-clients"></a>CA1406: evitar argumentos Int64 para clientes do Visual Basic 6
|||
|-|-|
|NomeDoTipo|AvoidInt64ArgumentsForVB6Clients|
|CheckId|CA1406|
|Categoria|Microsoft.Interoperability|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Um tipo que está especificamente marcado como visível para COM Component Object Model () declara um membro que utiliza um <xref:System.Int64?displayProperty=fullName> argumento.

## <a name="rule-description"></a>Descrição da Regra
 Clientes COM do Visual Basic 6 não podem acessar números inteiros de 64 bits.

 Por padrão, os seguintes são visíveis no COM: assemblies, tipos públicos, membros de instância pública em tipos públicos e todos os membros de tipos de valor público. No entanto, para reduzir o número de falsos positivos, essa regra requer a visibilidade de COM do tipo a ser declarado explicitamente; o assembly contendo deve ser marcado com o <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> definida como `false` e o tipo deve ser marcado com o <xref:System.Runtime.InteropServices.ComVisibleAttribute> definido como `true`.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação desta regra para um parâmetro cujo valor sempre pode ser expresso como um inteiro de 32 bits, altere o tipo de parâmetro para <xref:System.Int32?displayProperty=fullName>. Se o valor do parâmetro pode ser maior do que pode ser expresso como um inteiro de 32 bits, altere o tipo de parâmetro para <xref:System.Decimal?displayProperty=fullName>. Observe que tanto <xref:System.Single?displayProperty=fullName> e <xref:System.Double?displayProperty=fullName> perder a precisão em intervalos de superior a <xref:System.Int64> tipo de dados. Se o membro não se destina a ser visíveis no COM, marque-o com o <xref:System.Runtime.InteropServices.ComVisibleAttribute> definido como `false`.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 É seguro suprimir um aviso dessa regra, se você tiver certeza de que os clientes COM do Visual Basic 6 não acessará o tipo.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra um tipo que viola a regra.

 [!code-csharp[FxCop.Interoperability.LongArgument#1](../code-quality/codesnippet/CSharp/ca1406-avoid-int64-arguments-for-visual-basic-6-clients_1.cs)]
 [!code-vb[FxCop.Interoperability.LongArgument#1](../code-quality/codesnippet/VisualBasic/ca1406-avoid-int64-arguments-for-visual-basic-6-clients_1.vb)]

## <a name="related-rules"></a>Regras relacionadas
 [CA1413: evitar campos não públicos em tipos de valor visíveis em COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

 [CA1407: evitar membros estáticos em tipos visíveis em COM](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)

 [CA1017: marcar assemblies com ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>Consulte também
 [Interoperação com código não gerenciado](/dotnet/framework/interop/index) [tipo de dados Long](/dotnet/visual-basic/language-reference/data-types/long-data-type)