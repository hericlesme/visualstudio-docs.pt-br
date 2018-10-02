---
title: 'CA1064: As exceções devem ser públicas | Microsoft Docs'
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
- CA1064
- ExceptionsShouldBePublic
helpviewer_keywords:
- ExceptionsShouldBePublic
- CA1064
ms.assetid: 83eb224c-2456-4368-acf4-3b3378e67759
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: c35906c41a4c39557b2f72c83308b25cf650f676
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47587216"
---
# <a name="ca1064-exceptions-should-be-public"></a>CA1064: as exceções devem ser públicas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [CA1064: as exceções devem ser públicas](https://docs.microsoft.com/visualstudio/code-quality/ca1064-exceptions-should-be-public).

|||
|-|-|
|NomeDoTipo|ExceptionsShouldBePublic|
|CheckId|CA1064|
|Categoria|Microsoft.Design|
|Alteração Significativa|Não separável|

## <a name="cause"></a>Causa
 Uma exceção não público deriva diretamente <xref:System.Exception>, <xref:System.SystemException>, ou <xref:System.ApplicationException>.

## <a name="rule-description"></a>Descrição da Regra
 Uma exceção interna só é visível dentro de seu próprio escopo interno. Depois que a exceção falha fora do escopo interno, somente a exceção de base pode ser usada para capturar a exceção. Se a exceção interna for herdada de <xref:System.Exception>, <xref:System.SystemException>, ou <xref:System.ApplicationException>, o código externo não terá informações suficientes para saber o que fazer com a exceção.

 Mas, se o código tem uma exceção de pública que é usada posteriormente como base para uma exceção interna, é razoável pressupor que o código ainda mais out será capaz de fazer algo inteligentes com a exceção de base. A exceção pública terão mais informações do que aquelas fornecidas pelo T:System.Exception, T:System.SystemException ou T:System.ApplicationException.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Verifique a exceção público ou derivar a exceção interna de uma exceção de pública que não seja <xref:System.Exception>, <xref:System.SystemException>, ou <xref:System.ApplicationException>.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Suprima uma mensagem a partir dessa regra, se você tiver certeza em todos os casos que o privado exceção será capturada dentro de seu próprio escopo interno.

## <a name="example"></a>Exemplo
 Essa regra é acionada no primeiro método de exemplo, FirstCustomException porque a classe de exceção deriva diretamente da exceção e é interna. A regra não é disparado na classe SecondCustomException porque, embora a classe também deriva diretamente da exceção, a classe é declarada pública. A terceira classe também não dispara a regra porque ele não deriva diretamente <xref:System.Exception?displayProperty=fullName>, <xref:System.SystemException?displayProperty=fullName>, ou <xref:System.ApplicationException?displayProperty=fullName>.

 [!code-csharp[FxCop.Design.ExceptionsShouldBePublic.CA1064#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.design.exceptionsshouldbepublic.ca1064/cs/ca1064 - exceptionsshouldbepublic.cs#1)]



