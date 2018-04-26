---
title: 'CA2101: Especificar marshaling para argumentos de cadeia de caracteres P Invoke'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- SpecifyMarshalingForPInvokeStringArguments
- CA2101
helpviewer_keywords:
- CA2101
- SpecifyMarshalingForPInvokeStringArguments
ms.assetid: 9d1abfc3-d320-41e0-9f6e-60cefe6ffe1b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dc32aedf38430ab3ce9657f3a7e4d8d9e416fa57
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="ca2101-specify-marshaling-for-pinvoke-string-arguments"></a>CA2101: especificar marshaling para argumentos da cadeia de caracteres P/Invoke
|||
|-|-|
|NomeDoTipo|SpecifyMarshalingForPInvokeStringArguments|
|CheckId|CA2101|
|Categoria|Microsoft.Globalization|
|Alteração Significativa|Não recentes|

## <a name="cause"></a>Causa
 Invocação de uma plataforma membro permite chamadores parcialmente confiáveis, tem um parâmetro de cadeia de caracteres e não empacotar explicitamente a cadeia de caracteres.

## <a name="rule-description"></a>Descrição da Regra
 Quando você converter de Unicode em ANSI, é possível que nem todos os caracteres Unicode podem ser representados em uma página de código ANSI específica. *Mapeamento de melhor ajuste* tenta resolver esse problema, substituindo um caractere para o caractere que não pode ser representado. O uso desse recurso pode causar uma potencial vulnerabilidade de segurança porque você não pode controlar o caractere que é escolhido. Por exemplo, um código mal-intencionado pode criar uma cadeia de caracteres Unicode que contém caracteres que não são encontrados em uma página de código específico, que são convertidos em caracteres especiais do sistema de arquivos, como intencionalmente '... ' ou '/'. Observe também que as verificações de segurança para caracteres especiais ocorrem com frequência para que a cadeia de caracteres é convertida em ANSI.

 Mapeamento de melhor ajuste é o padrão para a conversão não gerenciado, WChar para MByte. A menos que você desabilite explicitamente o mapeamento de melhor ajuste, seu código pode conter uma vulnerabilidade de segurança explorável devido a esse problema.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação desta regra, tipos de dados de cadeia de caracteres para empacotá-lo explicitamente.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra um método que viola essa regra e, em seguida, mostra como corrigir a violação.

 [!code-csharp[FxCop.Security.PinvokeAnsiUnicode#1](../code-quality/codesnippet/CSharp/ca2101-specify-marshaling-for-p-invoke-string-arguments_1.cs)]