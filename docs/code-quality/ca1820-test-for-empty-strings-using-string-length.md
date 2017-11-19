---
title: 'CA1820: Teste para cadeias de caracteres vazias usando tamanho da cadeia de caracteres | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- TestForEmptyStringsUsingStringLength
- CA1820
helpviewer_keywords:
- TestForEmptyStringsUsingStringLength
- CA1820
ms.assetid: da1e70c8-b1dc-46b9-8b8f-4e6e48339681
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7bfacf70dd1d23d0596815ad2f9fa3f51986aaad
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="ca1820-test-for-empty-strings-using-string-length"></a>CA1820: teste para cadeias de caracteres vazias usando o comprimento da cadeia de caracteres
|||  
|-|-|  
|NomeDoTipo|TestForEmptyStringsUsingStringLength|  
|CheckId|CA1820|  
|Categoria|Microsoft.Performance|  
|Alteração Significativa|Não recentes|  
  
## <a name="cause"></a>Causa  
 Uma cadeia de caracteres é comparada à cadeia de caracteres vazia usando <xref:System.Object.Equals%2A?displayProperty=fullName>.  
  
## <a name="rule-description"></a>Descrição da Regra  
 Comparando cadeias de caracteres usando o <xref:System.String.Length%2A?displayProperty=fullName> propriedade ou o <xref:System.String.IsNullOrEmpty%2A?displayProperty=fullName> método é significativamente mais rápido do que usar <xref:System.Object.Equals%2A>. Isso ocorre porque <xref:System.Object.Equals%2A> executa instruções da MSIL significativamente mais que o <xref:System.String.IsNullOrEmpty%2A> ou o número de instruções executadas para recuperar o <xref:System.String.Length%2A> propriedade de valor e compará-lo a zero.  
  
 Você deve estar ciente que <xref:System.Object.Equals%2A> e <xref:System.String.Length%2A> = = 0 se comportam de maneira diferente para cadeias de caracteres nulas. Se você tentar obter o valor da <xref:System.String.Length%2A> propriedade em uma cadeia de caracteres nula, o common language runtime lança um <xref:System.NullReferenceException?displayProperty=fullName>. Se você executar uma comparação entre uma cadeia de caracteres nula e a cadeia de caracteres vazia, o common language runtime não lançar uma exceção; Retorna a comparação `false`. Testando null não afeta significativamente o desempenho relativo dessas duas abordagens. Durante o direcionamento [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)], use o <xref:System.String.IsNullOrEmpty%2A> método. Caso contrário, use o <xref:System.String.Length%2A> = = comparação sempre que possível.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Para corrigir uma violação desta regra, altere a comparação para usar o <xref:System.String.Length%2A> propriedade e teste para a cadeia de caracteres nula. Se o objetivo [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)], use o <xref:System.String.IsNullOrEmpty%2A> método.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 É seguro suprimir um aviso de que essa regra se o desempenho não for um problema.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra as técnicas diferentes que são usadas para procurar uma cadeia de caracteres vazia.  
  
 [!code-csharp[FxCop.Performance.StringTest#1](../code-quality/codesnippet/CSharp/ca1820-test-for-empty-strings-using-string-length_1.cs)]