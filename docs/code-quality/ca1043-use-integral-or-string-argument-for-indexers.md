---
title: 'CA1043: Usar argumento integral ou string para indexadores | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1043
- UseIntegralOrStringArgumentForIndexers
helpviewer_keywords:
- CA1043
- UseIntegralOrStringArgumentForIndexers
ms.assetid: d7f14b9e-2220-4f80-b6b8-48c655a05701
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: a75e3cc167f98763cfc0a1747b48e69987a9610b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ca1043-use-integral-or-string-argument-for-indexers"></a>CA1043: usar argumento integral ou da cadeia de caracteres para indexadores
|||  
|-|-|  
|NomeDoTipo|UseIntegralOrStringArgumentForIndexers|  
|CheckId|CA1043|  
|Categoria|Microsoft.Design|  
|Alteração Significativa|Quebra|  
  
## <a name="cause"></a>Causa  
 Um tipo público ou protegido contém um indexador público ou protegido que utiliza um tipo de índice diferente de <xref:System.Int32?displayProperty=fullName>, <xref:System.Int64?displayProperty=fullName>, <xref:System.Object?displayProperty=fullName>, ou <xref:System.String?displayProperty=fullName>.  
  
## <a name="rule-description"></a>Descrição da Regra  
 Indexadores, ou seja, propriedades indexadas, devem usar tipos inteiros ou string para o índice. Esses tipos são normalmente usados para indexar estruturas de dados e aumentam a usabilidade da biblioteca. Usar o <xref:System.Object> tipo deve ser restrito para os casos em que o tipo específico de número inteiro ou cadeia de caracteres não pode ser especificado em tempo de design. Se o projeto requer outros tipos para o índice, reconsidere se o tipo representa um repositório de dados lógico. Se ele não representa um repositório de dados lógicos, use um método.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Para corrigir uma violação desta regra, altere o índice para um tipo inteiro ou cadeia de caracteres ou usar um método em vez de indexador.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 Suprima um aviso dessa regra somente depois de se considerar cuidadosamente a necessidade do indexador não padrão.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra um indexador que usa um <xref:System.Int32> índice.  
  
 [!code-csharp[FxCop.Design.IntegralOrStringIndexers#1](../code-quality/codesnippet/CSharp/ca1043-use-integral-or-string-argument-for-indexers_1.cs)]
 [!code-cpp[FxCop.Design.IntegralOrStringIndexers#1](../code-quality/codesnippet/CPP/ca1043-use-integral-or-string-argument-for-indexers_1.cpp)]
 [!code-vb[FxCop.Design.IntegralOrStringIndexers#1](../code-quality/codesnippet/VisualBasic/ca1043-use-integral-or-string-argument-for-indexers_1.vb)]  
  
## <a name="related-rules"></a>Regras relacionadas  
 [CA1023: os indexadores não devem ser multidimensionais](../code-quality/ca1023-indexers-should-not-be-multidimensional.md)  
  
 [CA1024: usar propriedades quando apropriado](../code-quality/ca1024-use-properties-where-appropriate.md)