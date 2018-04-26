---
title: 'CA1714: os enums de sinalizadores devem ter nomes plurais'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- FlagsEnumsShouldHavePluralNames
- CA1714
helpviewer_keywords:
- CA1714
- FlagsEnumsShouldHavePluralNames
ms.assetid: 95ef5b43-7681-49e9-a5a3-ac0357cf1be7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1e00c0e7eaf3b88588f0914d78a23db40082d63f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="ca1714-flags-enums-should-have-plural-names"></a>CA1714: os enums de sinalizadores devem ter nomes plurais
|||
|-|-|
|NomeDoTipo|FlagsEnumsShouldHavePluralNames|
|CheckId|CA1714|
|Categoria|Microsoft.Naming|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Uma enumeração pública tem o <xref:System.FlagsAttribute?displayProperty=fullName> e seu nome não pode terminar em '.

## <a name="rule-description"></a>Descrição da Regra
 Tipos que são marcados com <xref:System.FlagsAttribute> têm nomes no plural porque o atributo indica que mais de um valor pode ser especificado. Por exemplo, uma enumeração que define os dias da semana pode servir para uso em um aplicativo onde você pode especificar vários dias. Esta enumeração deve ter o <xref:System.FlagsAttribute> e podem ser denominados 'Dias'. Uma enumeração semelhante que permite que um único dia seja especificada não terá o atributo e pode ser chamado 'Day'.

 Convenções de nomenclatura fornecem uma aparência comum para bibliotecas de destino do common language runtime. Isso reduz a curva de aprendizado que é necessário para novas bibliotecas de software e aumenta a confiança do cliente que a biblioteca foi desenvolvida por uma pessoa com experiência em desenvolvimento de código gerenciado.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Verifique o nome da enumeração uma palavra no plural, ou remova o <xref:System.FlagsAttribute> atributo se vários valores de enumeração não devem ser especificados simultaneamente.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 É seguro suprimir uma violação, se o nome é uma palavra no plural, mas não termina em do '. Por exemplo, se a enumeração de vários dias descrito anteriormente foram nomeada 'DaysOfTheWeek', isso viola a lógica da regra, mas não sua intenção. Essas violações devem ser suppressd.

## <a name="related-rules"></a>Regras relacionadas
 [CA1027: marcar enums com FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

 [CA2217: não marcar enums com FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Consulte também
 <xref:System.FlagsAttribute?displayProperty=fullName> [Design de enum](/dotnet/standard/design-guidelines/enum)