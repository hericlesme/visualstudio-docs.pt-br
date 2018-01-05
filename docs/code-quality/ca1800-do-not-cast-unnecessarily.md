---
title: "CA1800: Não converter desnecessariamente | Microsoft Docs"
ms.custom: 
ms.date: 10/26/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1800
- DoNotCastUnnecessarily
helpviewer_keywords:
- DoNotCastUnnecessarily
- CA1800
ms.assetid: b79a010a-6627-421e-8955-6007e32fa808
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
dev_langs:
- VB
- CSharp
ms.workload: multiple
ms.openlocfilehash: 260ced17d030d083854022ff3d1812184700d20d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ca1800-do-not-cast-unnecessarily"></a>CA1800: não converter desnecessariamente
|||  
|-|-|  
|NomeDoTipo|DoNotCastUnnecessarily|  
|CheckId|CA1800|  
|Categoria|Microsoft.Performance|  
|Alteração Significativa|Não recentes|  
  
## <a name="cause"></a>Causa  
Um método executa conversões duplicadas em um de seus argumentos ou variáveis locais.

Para concluir a análise por essa regra, o assembly testado deve ser compilado usando as informações de depuração e o arquivo de banco de dados (. PDB) do programa associado deve estar disponível.  
  
## <a name="rule-description"></a>Descrição da Regra  
As conversões duplicadas diminui o desempenho, especialmente quando as conversões são realizadas em instruções de iteração compactas. Para operações de conversão explícita de duplicados, armazenar o resultado da conversão em uma variável local e use a variável local em vez de operações de conversão duplicados.  
  
Se c# `is` operador é usado para testar se a conversão será bem-sucedida antes que a conversão real é executada, Experimente testar o resultado da `as` operador em vez disso. Isso fornece a mesma funcionalidade sem a operação de conversão implícita é executada pelo `is` operador. Ou, no c# 7.0 e posterior, use o `is` operador com [correspondência de padrões](/dotnet/csharp/language-reference/keywords/is#pattern-matching-with-is) para verificar se a conversão de tipo e converter a expressão para uma variável de tipo em uma única etapa.
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Para corrigir uma violação desta regra, modifique a implementação do método para minimizar o número de operações de conversão.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 É seguro para suprimir um aviso dessa regra, ou para ignorar a regra completamente, se o desempenho não for uma preocupação.  
  
## <a name="examples"></a>Exemplos  
 O exemplo a seguir mostra um método que viola a regra usando o c# `is` operador. Um segundo método satisfaz a regra, substituindo o `is` operador com um teste em relação ao resultado da `as` operador, que reduz o número de operações de conversão por iteração de dois para um. Um terceiro método também atende a regra usando `is` com [correspondência de padrões](/dotnet/csharp/language-reference/keywords/is#pattern-matching-with-is) para criar uma variável do tipo desejado se a conversão de tipo teria êxito.
  
 [!code-csharp[FxCop.Performance.UnnecessaryCastsAsIs#1](../code-quality/codesnippet/CSharp/ca1800-do-not-cast-unnecessarily_1.cs)]  

 O exemplo a seguir mostra um método `start_Click`, que tem várias conversões explícitas duplicados que viola a regra e um método `reset_Click`, que atende a regra armazenando a conversão em uma variável local.  
  
 [!code-vb[FxCop.Performance.UnnecessaryCasts#1](../code-quality/codesnippet/VisualBasic/ca1800-do-not-cast-unnecessarily_2.vb)]
 [!code-csharp[FxCop.Performance.UnnecessaryCasts#1](../code-quality/codesnippet/CSharp/ca1800-do-not-cast-unnecessarily_2.cs)]  
  
## <a name="see-also"></a>Consulte também  
[como (referência de c#)](/dotnet/csharp/language-reference/keywords/as)   
[é (referência de c#)](/dotnet/csharp/language-reference/keywords/is)