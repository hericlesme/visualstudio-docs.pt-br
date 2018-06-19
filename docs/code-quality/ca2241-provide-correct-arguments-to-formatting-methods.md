---
title: 'CA2241: fornecer argumentos corretos para métodos de formatação'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2241
- Provide correct arguments to formatting methods
- ProvideCorrectArgumentsToFormattingMethods
helpviewer_keywords:
- ProvideCorrectArgumentsToFormattingMethods
- CA2241
ms.assetid: 83639bc4-4c91-4a07-a40e-dc5e49a84494
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5c695c9f6e8af0e61bed88fd5a880e5655ecb7d6
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31918997"
---
# <a name="ca2241-provide-correct-arguments-to-formatting-methods"></a>CA2241: fornecer argumentos corretos para métodos de formatação
|||
|-|-|
|NomeDoTipo|ProvideCorrectArgumentsToFormattingMethods|
|CheckId|CA2241|
|Categoria|Microsoft.Usage|
|Alteração Significativa|Não separáveis|

## <a name="cause"></a>Causa
 O `format` argumento passado para um método como cadeia de caracteres <xref:System.Console.WriteLine%2A>, <xref:System.Console.Write%2A>, ou <xref:System.String.Format%2A?displayProperty=fullName> não contém um item de formato que corresponde ao argumento de cada objeto, ou vice-versa.

## <a name="rule-description"></a>Descrição da Regra
 Os argumentos de métodos como <xref:System.Console.WriteLine%2A>, <xref:System.Console.Write%2A>, e <xref:System.String.Format%2A> consistem em uma cadeia de caracteres de formato seguida por vários <xref:System.Object?displayProperty=fullName> instâncias. A cadeia de caracteres de formato consiste em texto e itens de formato inserida no formato {índice [, alinhamento] [: formatString]}. 'index' é um inteiro de base zero que indica que os objetos para formatar. Se um objeto não tem um índice correspondente na cadeia de caracteres de formato, o objeto será ignorado. Se o objeto especificado por 'index' não existe, um <xref:System.FormatException?displayProperty=fullName> é gerada em tempo de execução.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação desta regra, forneça um item de formato para cada argumento de objeto e fornecer um argumento de objeto para cada item de formato.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra dois violações da regra.

 [!code-vb[FxCop.Usage.FormattingArguments#1](../code-quality/codesnippet/VisualBasic/ca2241-provide-correct-arguments-to-formatting-methods_1.vb)]
 [!code-csharp[FxCop.Usage.FormattingArguments#1](../code-quality/codesnippet/CSharp/ca2241-provide-correct-arguments-to-formatting-methods_1.cs)]