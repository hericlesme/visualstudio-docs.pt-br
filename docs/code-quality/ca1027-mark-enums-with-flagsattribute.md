---
title: 'CA1027: marcar enums com FlagsAttribute'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MarkEnumsWithFlags
- CA1027
helpviewer_keywords:
- CA1027
- MarkEnumsWithFlags
ms.assetid: 249e882c-8cd1-4c00-a2de-7b6bdc1849ff
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b11b64ffbf6245357cccd04c0e67cf8791f6351f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31899913"
---
# <a name="ca1027-mark-enums-with-flagsattribute"></a>CA1027: marcar enums com FlagsAttribute
|||
|-|-|
|NomeDoTipo|MarkEnumsWithFlags|
|CheckId|CA1027|
|Categoria|Microsoft.Design|
|Alteração Significativa|Não recentes|

## <a name="cause"></a>Causa
 Os valores de uma enumeração pública são potências de dois ou são combinações de outros valores que são definidos na enumeração, e o <xref:System.FlagsAttribute?displayProperty=fullName> atributo não estiver presente. Para reduzir o número de falsos positivos, essa regra não relata uma violação para enumerações que têm valores contíguos.

## <a name="rule-description"></a>Descrição da Regra
 Uma enumeração é um tipo de valor que define um conjunto de constantes nomeadas relacionadas. Aplicar <xref:System.FlagsAttribute> para uma enumeração quando seus constantes nomeadas podem ser combinados significativamente. Por exemplo, considere uma enumeração dos dias da semana em um aplicativo que mantém o controle de recursos do dia que estão disponíveis. Se a disponibilidade de cada recurso é codificada usando a enumeração com <xref:System.FlagsAttribute> presentes, qualquer combinação de dias podem ser representado. Sem o atributo pode ser representado somente um dia da semana.

 Para os campos que armazenam as enumerações podem ser combinadas, os valores de enumeração individuais são tratados como grupos de bits no campo. Portanto, esses campos são às vezes chamados *campos de bit*. Para combinar os valores de enumeração para armazenamento em um campo de bits, use os operadores de condicionais Boolean. Para testar um campo de bits para determinar se há um valor de enumeração específico, use os operadores lógicos Boolean. Para um campo de bits armazenar e recuperar valores de enumeração combinado corretamente, cada valor que é definido na enumeração deve ser uma potência de dois. A menos que isso for verdadeiro, os operadores lógicos Boolean não poderá extrair os valores de enumeração individuais que são armazenados no campo.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação desta regra, adicionar <xref:System.FlagsAttribute> à enumeração.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Suprima um aviso de que essa regra se você não quiser que os valores de enumeração para ser combinável.

## <a name="example"></a>Exemplo
 No exemplo a seguir, `DaysEnumNeedsFlags` é uma enumeração que atenda aos requisitos para usar <xref:System.FlagsAttribute>, mas não a possui. O `ColorEnumShouldNotHaveFlag` enumeração não tem valores que são potências de dois, mas especifica incorretamente <xref:System.FlagsAttribute>. Isso viola a regra [CA2217: não marcar enums com FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md).

 [!code-csharp[FxCop.Design.EnumFlags#1](../code-quality/codesnippet/CSharp/ca1027-mark-enums-with-flagsattribute_1.cs)]

## <a name="related-rules"></a>Regras relacionadas
 [CA2217: não marcar enums com FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Consulte também
 <xref:System.FlagsAttribute?displayProperty=fullName>