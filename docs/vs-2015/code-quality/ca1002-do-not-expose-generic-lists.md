---
title: 'CA1002: Não expor listas genéricas | Microsoft Docs'
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
- DoNotExposeGenericLists
- CA1002
helpviewer_keywords:
- CA1002
- DoNotExposeGenericLists
ms.assetid: 5caac810-1a79-47df-a27b-c46c5040bf34
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 03435b59381f5127aeb7662df16c11e1e085824d
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47587293"
---
# <a name="ca1002-do-not-expose-generic-lists"></a>CA1002: não expor listas genéricas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [CA1002: não expor listas genéricas](https://docs.microsoft.com/visualstudio/code-quality/ca1002-do-not-expose-generic-lists).

|||
|-|-|
|NomeDoTipo|DoNotExposeGenericLists|
|CheckId|CA1002|
|Categoria|Microsoft.Design|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Um tipo contém um membro visível externamente que é um <xref:System.Collections.Generic.List%601?displayProperty=fullName> digitar, retorna um <xref:System.Collections.Generic.List%601?displayProperty=fullName> tipo ou cuja assinatura inclui um <xref:System.Collections.Generic.List%601?displayProperty=fullName> parâmetro.

## <a name="rule-description"></a>Descrição da Regra
 <xref:System.Collections.Generic.List%601?displayProperty=fullName> é uma coleção genérica que foi projetada para desempenho e não herança. <xref:System.Collections.Generic.List%601?displayProperty=fullName> não contém membros virtuais que o tornam mais fácil de alterar o comportamento de uma classe herdada. As seguintes coleções genéricas projetadas para herança e devem ser expostas em vez de <xref:System.Collections.Generic.List%601?displayProperty=fullName>.

-   <xref:System.Collections.ObjectModel.Collection%601?displayProperty=fullName>

-   <xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=fullName>

-   <xref:System.Collections.ObjectModel.KeyedCollection%602?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, altere o <xref:System.Collections.Generic.List%601?displayProperty=fullName> tipo para uma das coleções genéricas que se destina a herança.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra, a menos que o assembly que gera este aviso não deve ser uma biblioteca reutilizável. Por exemplo, seria seguro suprimir este aviso em um aplicativo de desempenho ajustado em que um benefício de desempenho foi obtido com o uso de listas genéricos.

## <a name="related-rules"></a>Regras relacionadas
 [CA1005: evitar parâmetros excessivos em tipos genéricos](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010: as coleções devem implementar a interface genérica](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000: não declarar membros estáticos em tipos genéricos](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1006: não aninhar tipos genéricos em assinaturas de membro](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004: os métodos genéricos devem fornecer o parâmetro de tipo](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003: usar instâncias do manipulador de eventos genéricos](../code-quality/ca1003-use-generic-event-handler-instances.md)

 [CA1007: usar genéricos quando apropriado](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Consulte também
 [Genéricos](http://msdn.microsoft.com/library/75ea8509-a4ea-4e7a-a2b3-cf72482e9282)



