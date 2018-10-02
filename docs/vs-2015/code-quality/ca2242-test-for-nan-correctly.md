---
title: 'CA2242: Testar para NaN corretamente | Microsoft Docs'
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
- TestForNaNCorrectly
- CA2242
helpviewer_keywords:
- CA2242
ms.assetid: e12dcffc-e255-4e1e-8fdf-3c6054d44abe
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: dcbfd5e5bd52be2919835cbe5bdfb06119f2a688
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47587152"
---
# <a name="ca2242-test-for-nan-correctly"></a>CA2242: teste para NaN corretamente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [CA2242: testar para NaN corretamente](https://docs.microsoft.com/visualstudio/code-quality/ca2242-test-for-nan-correctly).

|||
|-|-|
|NomeDoTipo|TestForNaNCorrectly|
|CheckId|CA2242|
|Categoria|Microsoft.Usage|
|Alteração Significativa|Não separável|

## <a name="cause"></a>Causa
 Uma expressão testa um valor em <xref:System.Single.NaN?displayProperty=fullName> ou <xref:System.Double.NaN?displayProperty=fullName>.

## <a name="rule-description"></a>Descrição da Regra
 <xref:System.Double.NaN?displayProperty=fullName>, que representa não é um número, o que resulta quando uma operação aritmética é indefinida. Qualquer expressão que testa a igualdade entre um valor e <xref:System.Double.NaN?displayProperty=fullName> sempre retorna `false`. Qualquer expressão que testa a desigualdade entre um valor e <xref:System.Double.NaN?displayProperty=fullName> sempre retorna `true`.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra e determinar com precisão se um valor representa <xref:System.Double.NaN?displayProperty=fullName>, use <xref:System.Single.IsNaN%2A?displayProperty=fullName> ou <xref:System.Double.IsNaN%2A?displayProperty=fullName> para testar o valor.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra duas expressões que testam incorretamente um valor em relação ao <xref:System.Double.NaN?displayProperty=fullName> e uma expressão que usa corretamente <xref:System.Double.IsNaN%2A?displayProperty=fullName> para testar o valor.

 [!code-csharp[FxCop.Usage.TestForNaN#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.TestForNaN/cs/FxCop.Usage.TestForNaN.cs#1)]
 [!code-vb[FxCop.Usage.TestForNaN#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.TestForNaN/vb/FxCop.Usage.TestForNaN.vb#1)]



