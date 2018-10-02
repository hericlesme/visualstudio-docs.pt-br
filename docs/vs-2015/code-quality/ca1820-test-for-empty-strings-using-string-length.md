---
title: 'CA1820: Teste para cadeias de caracteres vazias usando o comprimento da cadeia de caracteres | Microsoft Docs'
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
- TestForEmptyStringsUsingStringLength
- CA1820
helpviewer_keywords:
- TestForEmptyStringsUsingStringLength
- CA1820
ms.assetid: da1e70c8-b1dc-46b9-8b8f-4e6e48339681
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 17def2bda544a188d6144affc9d7fccb24c3b079
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47587245"
---
# <a name="ca1820-test-for-empty-strings-using-string-length"></a>CA1820: teste para cadeias de caracteres vazias usando o comprimento da cadeia de caracteres
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [CA1820: teste para cadeias de caracteres vazias usando o comprimento da cadeia de caracteres](https://docs.microsoft.com/visualstudio/code-quality/ca1820-test-for-empty-strings-using-string-length).

|||
|-|-|
|NomeDoTipo|TestForEmptyStringsUsingStringLength|
|CheckId|CA1820|
|Categoria|Microsoft.Performance|
|Alteração Significativa|Não são significativas|

## <a name="cause"></a>Causa
 Uma cadeia de caracteres é comparado com a cadeia de caracteres vazia usando <xref:System.Object.Equals%2A?displayProperty=fullName>.

## <a name="rule-description"></a>Descrição da Regra
 Comparando cadeias de caracteres usando o <xref:System.String.Length%2A?displayProperty=fullName> propriedade ou o <xref:System.String.IsNullOrEmpty%2A?displayProperty=fullName> método é significativamente mais rápido do que usar <xref:System.Object.Equals%2A>. Isso ocorre porque <xref:System.Object.Equals%2A> executa significativamente mais instruções MSIL que ambos <xref:System.String.IsNullOrEmpty%2A> ou o número de instruções executadas para recuperar o <xref:System.String.Length%2A> propriedade de valor e compará-la como zero.

 Você deve estar ciente que <xref:System.Object.Equals%2A> e <xref:System.String.Length%2A> = = 0 se comportam de forma diferente para cadeias de caracteres nulas. Se você tentar obter o valor de <xref:System.String.Length%2A> propriedade em uma cadeia de caracteres nula, o common language runtime lançará uma <xref:System.NullReferenceException?displayProperty=fullName>. Se você realizar uma comparação entre uma cadeia de caracteres nula e a cadeia de caracteres vazia, o common language runtime não lançar uma exceção; a comparação retorna `false`. Testando null não afeta significativamente o desempenho relativo dessas duas abordagens. Ao direcionar [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)], use o <xref:System.String.IsNullOrEmpty%2A> método. Caso contrário, use o <xref:System.String.Length%2A> = = comparação sempre que possível.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, altere a comparação para usar o <xref:System.String.Length%2A> propriedade e teste para a cadeia de caracteres nula. Se o objetivo [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)], use o <xref:System.String.IsNullOrEmpty%2A> método.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 É seguro suprimir um aviso nessa regra, se o desempenho não for um problema.

## <a name="example"></a>Exemplo
 O exemplo a seguir ilustra as técnicas diferentes que são usadas para procurar uma cadeia de caracteres vazia.

 [!code-csharp[FxCop.Performance.StringTest#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.StringTest/cs/FxCop.Performance.StringTest.cs#1)]



