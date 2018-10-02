---
title: 'CA1712: Valores enum como prefixo com o nome do tipo | Microsoft Docs'
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
- CA1712
- DoNotPrefixEnumValuesWithTypeName
helpviewer_keywords:
- CA1712
- DoNotPrefixEnumValuesWithTypeName
ms.assetid: df0e3a12-67bf-48f1-a10b-2ef60484a5c7
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 9283c35dacc0d3f3779a167eeb095f90431d7a4c
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47587166"
---
# <a name="ca1712-do-not-prefix-enum-values-with-type-name"></a>CA1712: não use valores enum como prefixo com o nome do tipo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [CA1712: valores enum como prefixo com o nome do tipo](https://docs.microsoft.com/visualstudio/code-quality/ca1712-do-not-prefix-enum-values-with-type-name).

|||
|-|-|
|NomeDoTipo|DoNotPrefixEnumValuesWithTypeName|
|CheckId|CA1712|
|Categoria|Microsoft.Naming|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Uma enumeração contém um membro cujo nome começa com o nome do tipo de enumeração.

## <a name="rule-description"></a>Descrição da Regra
 Nomes dos membros de enumeração não são prefixados com o nome do tipo porque as informações de tipo deve ser fornecido pelas ferramentas de desenvolvimento.

 Convenções de nomenclatura de fornecem uma aparência comum para bibliotecas que direcionam o common language runtime. Isso reduz o tempo que é necessário para aprender uma nova biblioteca de software e aumenta a confiança do cliente que a biblioteca foi desenvolvida por alguém que tenha experiência em desenvolvimento de código gerenciado.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, remova o prefixo de nome de tipo do membro de enumeração.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra uma enumeração nomeada incorretamente seguida a versão corrigida.

 [!code-cpp[FxCop.Naming.EnumValues#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Naming.EnumValues/cpp/FxCop.Naming.EnumValues.cpp#1)]
 [!code-csharp[FxCop.Naming.EnumValues#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Naming.EnumValues/cs/FxCop.Naming.EnumValues.cs#1)]
 [!code-vb[FxCop.Naming.EnumValues#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Naming.EnumValues/vb/FxCop.Naming.EnumValues.vb#1)]

## <a name="related-rules"></a>Regras relacionadas
 [CA1711: os identificadores não devem ter sufixo incorreto](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)

 [CA1027: marcar enums com FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

 [CA2217: não marcar enums com FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Consulte também
 <xref:System.Enum?displayProperty=fullName>



