---
title: 'CA1717: apenas enums FlagsAttribute devem ter nomes plurais'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1717
- OnlyFlagsEnumsShouldHavePluralNames
helpviewer_keywords:
- OnlyFlagsEnumsShouldHavePluralNames
- CA1717
ms.assetid: a6855d8b-d78a-42c1-834e-61c31f5572ed
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: eddcdd47a79b925bf6601c25cf1343eacfa60aa0
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/19/2018
---
# <a name="ca1717-only-flagsattribute-enums-should-have-plural-names"></a>CA1717: apenas enums FlagsAttribute devem ter nomes plurais
|||
|-|-|
|NomeDoTipo|OnlyFlagsEnumsShouldHavePluralNames|
|CheckId|CA1717|
|Categoria|Microsoft.Naming|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 O nome de uma enumeração visível externamente termina em uma palavra no plural e a enumeração não está marcada com o <xref:System.FlagsAttribute?displayProperty=fullName> atributo.

## <a name="rule-description"></a>Descrição da Regra
 Convenções de nomenclatura determinam se um nome no plural de uma enumeração indica que mais de um valor da enumeração pode ser especificado simultaneamente. O <xref:System.FlagsAttribute> informa compiladores que a enumeração deve ser tratada como um campo de bits que permite operações bit a bit na enumeração.

 Se apenas um valor de uma enumeração pode ser especificado em um momento, o nome da enumeração deve ser uma única palavra. Por exemplo, uma enumeração que define os dias da semana pode servir para uso em um aplicativo onde você pode especificar vários dias. Esta enumeração deve ter o <xref:System.FlagsAttribute> e podem ser denominados 'Dias'. Uma enumeração semelhante que permite que um único dia seja especificada não terá o atributo e pode ser chamado 'Day'.

 Convenções de nomenclatura fornecem uma aparência comum para bibliotecas de destino do common language runtime. Isso reduz o tempo que é necessário para aprender uma nova biblioteca de software e aumenta a confiança do cliente que a biblioteca foi desenvolvida por uma pessoa com experiência em desenvolvimento de código gerenciado.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Verifique o nome da enumeração uma única palavra ou adicionar o <xref:System.FlagsAttribute>.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 É seguro suprimir um aviso de que a regra se o nome termina em uma única palavra.

## <a name="related-rules"></a>Regras relacionadas
 [CA1714: enums de sinalizadores devem ter nomes plurais](../code-quality/ca1714-flags-enums-should-have-plural-names.md)

 [CA1027: marcar enums com FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

 [CA2217: não marcar enums com FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Consulte também
 <xref:System.FlagsAttribute?displayProperty=fullName> [Design de enum](/dotnet/standard/design-guidelines/enum)