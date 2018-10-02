---
title: 'CA1714: Enums de sinalizadores devem ter nomes plurais | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- FlagsEnumsShouldHavePluralNames
- CA1714
helpviewer_keywords:
- CA1714
- FlagsEnumsShouldHavePluralNames
ms.assetid: 95ef5b43-7681-49e9-a5a3-ac0357cf1be7
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: c778267df8a54c474e956a5e41388a7f971823f4
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47476448"
---
# <a name="ca1714-flags-enums-should-have-plural-names"></a>CA1714: os enums de sinalizadores devem ter nomes plurais
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [CA1714: enums de sinalizadores devem ter nomes plurais](https://docs.microsoft.com/visualstudio/code-quality/ca1714-flags-enums-should-have-plural-names).

|||
|-|-|
|NomeDoTipo|FlagsEnumsShouldHavePluralNames|
|CheckId|CA1714|
|Categoria|Microsoft.Naming|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Uma enumeração pública tem o <xref:System.FlagsAttribute?displayProperty=fullName> e seu nome não termina em '.

## <a name="rule-description"></a>Descrição da Regra
 Tipos que são marcados com <xref:System.FlagsAttribute> têm nomes que estão no plurais porque o atributo indica que mais de um valor pode ser especificado. Por exemplo, uma enumeração que define os dias da semana pode ser destinada para uso em um aplicativo onde você pode especificar vários dias. Esta enumeração deve ter o <xref:System.FlagsAttribute> e poderia ser chamado 'Dias'. Uma enumeração semelhante que permite que um único dia seja especificada não teria o atributo e pode ser chamado 'Day'.

 Convenções de nomenclatura de fornecem uma aparência comum para bibliotecas que direcionam o common language runtime. Isso reduz a curva de aprendizado que é necessário para novas bibliotecas de software e aumenta a confiança do cliente que a biblioteca foi desenvolvida por alguém que tenha experiência em desenvolvimento de código gerenciado.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Verifique o nome da enumeração uma palavra no plural ou remova o <xref:System.FlagsAttribute> atributo se vários valores de enumeração não devem ser especificados simultaneamente.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 É seguro suprimir uma violação, se o nome é uma palavra no plural, mas não termina com do '. Por exemplo, se a enumeração de vários dias que foi descrita anteriormente foram nomeada 'DaysOfTheWeek', isso violaria a lógica da regra, mas não sua intenção. Tais violações devem ser suppressd.

## <a name="related-rules"></a>Regras relacionadas
 [CA1027: marcar enums com FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

 [CA2217: não marcar enums com FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Consulte também
 <xref:System.FlagsAttribute?displayProperty=fullName> [Design de enumeração](http://msdn.microsoft.com/library/dd53c952-9d9a-4736-86ff-9540e815d545)



