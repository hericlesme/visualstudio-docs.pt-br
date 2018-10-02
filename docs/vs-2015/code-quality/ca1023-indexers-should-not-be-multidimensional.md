---
title: 'CA1023: Os indexadores não devem ser multidimensionais | Microsoft Docs'
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
- IndexersShouldNotBeMultidimensional
- CA1023
helpviewer_keywords:
- CA1023
- IndexersShouldNotBeMultidimensional
ms.assetid: ae499879-97f6-434e-a61d-1fedd231d2fb
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: e1b1022484db26e6ff8fbc0046333f187753bb53
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47586967"
---
# <a name="ca1023-indexers-should-not-be-multidimensional"></a>CA1023: os indexadores não devem ser multidimensionais
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [CA1023: os indexadores não devem ser multidimensionais](https://docs.microsoft.com/visualstudio/code-quality/ca1023-indexers-should-not-be-multidimensional).

|||
|-|-|
|NomeDoTipo|IndexersShouldNotBeMultidimensional|
|CheckId|CA1023|
|Categoria|Microsoft.Design|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Um tipo público ou protegido contém um indexador público ou protegido que usa mais de um índice.

## <a name="rule-description"></a>Descrição da Regra
 Indexadores, ou seja, propriedades indexadas, devem usar um único índice. Indexadores multidimensionais podem reduzir significativamente a usabilidade da biblioteca. Se o projeto requer vários índices, reconsidere se o tipo representa um armazenamento de dados lógicos. Caso contrário, use um método.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, alterar o design para usar um índice de cadeia de caracteres ou inteiro solitário ou usar um método em vez do indexador.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Suprima um aviso nessa regra somente após considerar cuidadosamente a necessidade do indexador não padrão.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra um tipo, `DayOfWeek03`, com um indexador multidimensional que viola a regra. O indexador pode ser visto como um tipo de conversão e, portanto, mais apropriado é exposto como um método. O tipo é reprojetado no `RedesignedDayOfWeek03` para satisfazer a regra.

 [!code-cpp[FxCop.Design.OneDimensionForIndexer#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.OneDimensionForIndexer/cpp/FxCop.Design.OneDimensionForIndexer.cpp#1)]
 [!code-csharp[FxCop.Design.OneDimensionForIndexer#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.OneDimensionForIndexer/cs/FxCop.Design.OneDimensionForIndexer.cs#1)]
 [!code-vb[FxCop.Design.OneDimensionForIndexer#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.OneDimensionForIndexer/vb/FxCop.Design.OneDimensionForIndexer.vb#1)]

## <a name="related-rules"></a>Regras relacionadas
 [CA1043: usar argumento integral ou de cadeia de caracteres para indexadores](../code-quality/ca1043-use-integral-or-string-argument-for-indexers.md)

 [CA1024: usar propriedades quando apropriado](../code-quality/ca1024-use-properties-where-appropriate.md)



