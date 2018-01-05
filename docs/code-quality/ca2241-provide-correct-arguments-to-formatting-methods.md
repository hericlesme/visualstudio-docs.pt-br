---
title: "CA2241: Fornecer argumentos corretos para métodos de formatação | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2241
- Provide correct arguments to formatting methods
- ProvideCorrectArgumentsToFormattingMethods
helpviewer_keywords:
- ProvideCorrectArgumentsToFormattingMethods
- CA2241
ms.assetid: 83639bc4-4c91-4a07-a40e-dc5e49a84494
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: f5f71926705169d4ed7dc40318e83f265e8603f5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
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