---
title: 'CA2242: Teste para NaN corretamente | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- TestForNaNCorrectly
- CA2242
helpviewer_keywords: CA2242
ms.assetid: e12dcffc-e255-4e1e-8fdf-3c6054d44abe
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: dd7f648880debe4b982d10e97aa7133419e0e840
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="ca2242-test-for-nan-correctly"></a>CA2242: teste para NaN corretamente
|||  
|-|-|  
|NomeDoTipo|TestForNaNCorrectly|  
|CheckId|CA2242|  
|Categoria|Microsoft.Usage|  
|Alteração Significativa|Não separáveis|  
  
## <a name="cause"></a>Causa  
 Uma expressão testa um valor em relação a <xref:System.Single.NaN?displayProperty=fullName> ou <xref:System.Double.NaN?displayProperty=fullName>.  
  
## <a name="rule-description"></a>Descrição da Regra  
 <xref:System.Double.NaN?displayProperty=fullName>, que representa não numéricos, resultados quando uma operação aritmética é indefinida. Qualquer expressão que testa a igualdade entre um valor e <xref:System.Double.NaN?displayProperty=fullName> sempre retorna `false`. Qualquer expressão que testa a desigualdade entre um valor e <xref:System.Double.NaN?displayProperty=fullName> sempre retorna `true`.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Para corrigir uma violação desta regra e precisa determinar se um valor representa <xref:System.Double.NaN?displayProperty=fullName>, use <xref:System.Single.IsNaN%2A?displayProperty=fullName> ou <xref:System.Double.IsNaN%2A?displayProperty=fullName> para testar o valor.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 Não suprima um aviso nessa regra.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra duas expressões que teste incorretamente um valor em relação a <xref:System.Double.NaN?displayProperty=fullName> e uma expressão que use corretamente <xref:System.Double.IsNaN%2A?displayProperty=fullName> para testar o valor.  
  
 [!code-vb[FxCop.Usage.TestForNaN#1](../code-quality/codesnippet/VisualBasic/ca2242-test-for-nan-correctly_1.vb)]
 [!code-csharp[FxCop.Usage.TestForNaN#1](../code-quality/codesnippet/CSharp/ca2242-test-for-nan-correctly_1.cs)]