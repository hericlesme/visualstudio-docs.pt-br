---
title: 'CA2126: demandas do link de tipo exigem demandas de herança'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2126
- TypeLinkDemandsRequireInheritanceDemands
helpviewer_keywords:
- CA2126
- TypeLinkDemandsRequireInheritanceDemands
ms.assetid: 07b604e5-5579-4df9-a578-dadd0d8370a7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a9ee3817d445144c3c83756cda07da2ed41adee6
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/19/2018
---
# <a name="ca2126-type-link-demands-require-inheritance-demands"></a>CA2126: demandas do link de tipo exigem demandas de herança
|||
|-|-|
|NomeDoTipo|TypeLinkDemandsRequireInheritanceDemands|
|CheckId|CA2126|
|Categoria|Microsoft.Security|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Um tipo público for protegido com uma demanda de link, tem um método substituível e o tipo, nem o método é protegido com uma demanda de herança.

## <a name="rule-description"></a>Descrição da Regra
 Um link em um método ou seu tipo declarativo exige o chamador imediato do método para ter a permissão especificada. Uma demanda de herança em um método exige um método de substituição para ter a permissão especificada. Uma demanda de herança em um tipo requer uma classe derivada para ter a permissão especificada.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação desta regra, proteja o tipo ou o método com uma demanda de herança para a mesma permissão que a demanda de link.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra um tipo que viola a regra.

 [!code-cpp[FxCop.Security.TypesWithLinkDemands#1](../code-quality/codesnippet/CPP/ca2126-type-link-demands-require-inheritance-demands_1.cpp)]
 [!code-vb[FxCop.Security.TypesWithLinkDemands#1](../code-quality/codesnippet/VisualBasic/ca2126-type-link-demands-require-inheritance-demands_1.vb)]
 [!code-csharp[FxCop.Security.TypesWithLinkDemands#1](../code-quality/codesnippet/CSharp/ca2126-type-link-demands-require-inheritance-demands_1.cs)]

## <a name="related-rules"></a>Regras relacionadas
 [CA2108: examinar segurança declarativa em tipos de valor](../code-quality/ca2108-review-declarative-security-on-value-types.md)

 [CA2112: os tipos seguros não devem expor campos](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

 [CA2122: não expor indiretamente métodos com demandas de link](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)

 [CA2123: as demandas de link de substituição devem ser idênticas à base](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)

## <a name="see-also"></a>Consulte também
 [Diretrizes de codificação segura](/dotnet/standard/security/secure-coding-guidelines) [demandas de Link](/dotnet/framework/misc/link-demands)
