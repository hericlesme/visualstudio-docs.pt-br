---
title: 'CA1025: Substituir argumentos repetitivos por matriz params | Microsoft Docs'
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
- CA1025
- ReplaceRepetitiveArgumentsWithParamsArray
helpviewer_keywords:
- ReplaceRepetitiveArgumentsWithParamsArray
- CA1025
ms.assetid: f009b340-dea3-4459-8fe1-2143aa8b5d0b
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 2496876369e2b0449f33b098a8a646914a4d2f11
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47587138"
---
# <a name="ca1025-replace-repetitive-arguments-with-params-array"></a>CA1025: substituir argumentos repetitivos por matriz de parâmetros
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [CA1025: substituir argumentos repetitivos por matriz params](https://docs.microsoft.com/visualstudio/code-quality/ca1025-replace-repetitive-arguments-with-params-array).

|||
|-|-|
|NomeDoTipo|ReplaceRepetitiveArgumentsWithParamsArray|
|CheckId|CA1025|
|Categoria|Microsoft.Design|
|Alteração Significativa|Não são significativas|

## <a name="cause"></a>Causa
 Um método público ou protegido em um tipo público tem mais de três parâmetros e seus três últimos parâmetros são do mesmo tipo.

## <a name="rule-description"></a>Descrição da Regra
 Use uma matriz de parâmetros em vez de argumentos repetidos, quando o número exato de argumentos é desconhecido e os argumentos variáveis forem do mesmo tipo, ou podem ser passados como o mesmo tipo. Por exemplo, o <xref:System.Console.WriteLine%2A> método fornece uma sobrecarga de uso geral que usa uma matriz de parâmetros para aceitar qualquer número de <xref:System.Object> argumentos.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, substitua os argumentos repetidos com uma matriz de parâmetros.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 É sempre seguro suprimir um aviso nessa regra; No entanto, esse design pode causar problemas de usabilidade.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra um tipo que viola essa regra.

 [!code-csharp[FxCop.Design.RepeatArgs#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.RepeatArgs/cs/FxCop.Design.RepeatArgs.cs#1)]



