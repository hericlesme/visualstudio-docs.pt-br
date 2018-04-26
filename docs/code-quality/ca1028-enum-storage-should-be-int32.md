---
title: 'CA1028: o armazenamento de enum deve ser Int32'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1028
- EnumStorageShouldBeInt32
helpviewer_keywords:
- EnumStorageShouldBeInt32
- CA1028
ms.assetid: 87160825-9f39-4142-8d7f-a31fe7ac7b84
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f0f9dec006f3684259541811e905eaf75a790c3a
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="ca1028-enum-storage-should-be-int32"></a>CA1028: o armazenamento de enum deve ser Int32
|||
|-|-|
|NomeDoTipo|EnumStorageShouldBeInt32|
|CheckId|CA1028|
|Categoria|Microsoft.Design|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 O tipo subjacente de uma enumeração pública não é <xref:System.Int32?displayProperty=fullName>.

## <a name="rule-description"></a>Descrição da Regra
 Uma enumeração é um tipo de valor que define um conjunto de constantes nomeadas relacionadas. Por padrão, o <xref:System.Int32?displayProperty=fullName> tipo de dados é usado para armazenar o valor da constante. Embora você possa alterar esse tipo subjacente, não é necessário ou recomendado na maioria dos cenários. Observe que nenhum ganho de desempenho significativa é obtido usando um tipo de dados que é menor do que <xref:System.Int32>. Se você não pode usar o tipo de dados padrão, você deve usar um do sistema CLS (Common Language)-compatível com tipos integrais, <xref:System.Byte>, <xref:System.Int16>, <xref:System.Int32>, ou <xref:System.Int64> para certificar-se de que todos os valores da enumeração podem ser representados em Linguagens de programação compatíveis com CLS.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação desta regra, a menos que existem problemas de tamanho ou compatibilidade, use <xref:System.Int32>. Em situações onde <xref:System.Int32> não é grande o suficiente para manter os valores, use <xref:System.Int64>. Se a compatibilidade com versões anteriores requer um tipo de dados menor, use <xref:System.Byte> ou <xref:System.Int16>.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Suprima um aviso dessa regra somente se os problemas de compatibilidade com versões anteriores a exige. Em aplicativos, falha de acordo com esta regra, geralmente não causa problemas. Em bibliotecas, onde a interoperabilidade de linguagem é necessária, falha de acordo com essa regra pode afetar adversamente a seus usuários.

## <a name="example-of-a-violation"></a>Exemplo de uma violação

### <a name="description"></a>Descrição
 O exemplo a seguir mostra duas enumerações que não usam o tipo de dados subjacente recomendado.

### <a name="code"></a>Código
 [!code-vb[FxCop.Design.EnumIntegralType#1](../code-quality/codesnippet/VisualBasic/ca1028-enum-storage-should-be-int32_1.vb)]
 [!code-csharp[FxCop.Design.EnumIntegralType#1](../code-quality/codesnippet/CSharp/ca1028-enum-storage-should-be-int32_1.cs)]

## <a name="example-of-how-to-fix"></a>Exemplo de como corrigir

### <a name="description"></a>Descrição
 O exemplo a seguir corrige a violação anterior, alterando o tipo de dados subjacente para <xref:System.Int32>.

### <a name="code"></a>Código
 [!code-csharp[FxCop.Design.EnumIntegralTypeFixed#1](../code-quality/codesnippet/CSharp/ca1028-enum-storage-should-be-int32_2.cs)]
 [!code-vb[FxCop.Design.EnumIntegralTypeFixed#1](../code-quality/codesnippet/VisualBasic/ca1028-enum-storage-should-be-int32_2.vb)]

## <a name="related-rules"></a>Regras relacionadas
 [CA1008: as enums devem ter valor zero](../code-quality/ca1008-enums-should-have-zero-value.md)

 [CA1027: marcar enums com FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

 [CA2217: não marcar enums com FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

 [CA1700: não nomear valores de enum como 'Reservados'](../code-quality/ca1700-do-not-name-enum-values-reserved.md)

 [CA1712: não usar valores de enum como prefixo com o nome do tipo](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)

## <a name="see-also"></a>Consulte também
 <xref:System.Byte?displayProperty=fullName> <xref:System.Int16?displayProperty=fullName> <xref:System.Int32?displayProperty=fullName> <xref:System.Int64?displayProperty=fullName>