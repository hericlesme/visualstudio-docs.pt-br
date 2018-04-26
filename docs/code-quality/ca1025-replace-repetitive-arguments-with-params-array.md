---
title: 'CA1025: substituir argumentos repetitivos por matriz de parâmetros'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1025
- ReplaceRepetitiveArgumentsWithParamsArray
helpviewer_keywords:
- ReplaceRepetitiveArgumentsWithParamsArray
- CA1025
ms.assetid: f009b340-dea3-4459-8fe1-2143aa8b5d0b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f1ce14b7da80775a9837b5e92f25d141276226cf
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="ca1025-replace-repetitive-arguments-with-params-array"></a>CA1025: substituir argumentos repetitivos por matriz de parâmetros
|||
|-|-|
|NomeDoTipo|ReplaceRepetitiveArgumentsWithParamsArray|
|CheckId|CA1025|
|Categoria|Microsoft.Design|
|Alteração Significativa|Não recentes|

## <a name="cause"></a>Causa
 Um método público ou protegido em um tipo público tem mais de três parâmetros e seus três parâmetros são do mesmo tipo.

## <a name="rule-description"></a>Descrição da Regra
 Use uma matriz de parâmetros em vez de argumentos repetidos quando o número exato de argumentos é desconhecido e os argumentos de variável são do mesmo tipo, ou podem ser passados como o mesmo tipo. Por exemplo, o <xref:System.Console.WriteLine%2A> método fornece uma sobrecarga de uso geral que usa uma matriz de parâmetros para aceitar qualquer número de <xref:System.Object> argumentos.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação desta regra, substitua os argumentos repetidos com uma matriz de parâmetros.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 É sempre seguro suprimir um aviso dessa regra; No entanto, esse design pode causar problemas de usabilidade.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra um tipo que violam essa regra.

 [!code-csharp[FxCop.Design.RepeatArgs#1](../code-quality/codesnippet/CSharp/ca1025-replace-repetitive-arguments-with-params-array_1.cs)]