---
title: 'CA1011: Considere passar tipos base como parâmetros | Microsoft Docs'
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
- ConsiderPassingBaseTypesAsParameters
- CA1011
helpviewer_keywords:
- CA1011
- ConsiderPassingBaseTypesAsParameters
ms.assetid: ce1e1241-dcf4-419b-9363-1d5bc4989279
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: a2ddf1e4f1edc319fdc5744878d4f962ce5b46bb
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47587319"
---
# <a name="ca1011-consider-passing-base-types-as-parameters"></a>CA1011: considere a passagem dos tipos base como parâmetros
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [CA1011: considere passar tipos base como parâmetros](https://docs.microsoft.com/visualstudio/code-quality/ca1011-consider-passing-base-types-as-parameters).

|||
|-|-|
|NomeDoTipo|ConsiderPassingBaseTypesAsParameters|
|CheckId|CA1011|
|Categoria|Microsoft.Design|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Uma declaração de método inclui um parâmetro formal que é um tipo derivado e o método chama apenas os membros do tipo base do parâmetro.

## <a name="rule-description"></a>Descrição da Regra
 Quando um tipo de base é especificado como um parâmetro em uma declaração de método, qualquer tipo derivado do tipo de base pode ser passado como o argumento correspondente ao método. Quando o argumento é usado dentro do corpo do método, o método específico que é executado depende do tipo do argumento. Se a funcionalidade adicional que é fornecida por um tipo derivado não for necessária, o uso do tipo base permite um uso mais amplo do método.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, altere o tipo do parâmetro para seu tipo base.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 É seguro suprimir um aviso nessa regra

-   Se o método requer a funcionalidade específica que é fornecida por um tipo derivado

     \- ou -

-   para impor que apenas o tipo derivado, ou um tipo mais derivado, é passado para o método.

 Nesses casos, o código será mais robusto devido à forte verificação de tipo que é fornecido pelo compilador e tempo de execução.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra um método `ManipulateFileStream`, que pode ser usado apenas com um <xref:System.IO.FileStream> objeto, o que viola essa regra. Um segundo método, `ManipulateAnyStream`, satisfaz a regra, substituindo o <xref:System.IO.FileStream> parâmetro usando um <xref:System.IO.Stream>.

 [!code-cpp[FxCop.Design.ConsiderPassingBaseTypes#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.ConsiderPassingBaseTypes/cpp/FxCop.Design.ConsiderPassingBaseTypes.cpp#1)]
 [!code-csharp[FxCop.Design.ConsiderPassingBaseTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ConsiderPassingBaseTypes/cs/FxCop.Design.ConsiderPassingBaseTypes.cs#1)]
 [!code-vb[FxCop.Design.ConsiderPassingBaseTypes#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ConsiderPassingBaseTypes/vb/FxCop.Design.ConsiderPassingBaseTypes.vb#1)]

## <a name="related-rules"></a>Regras relacionadas
 [CA1059: os membros não devem expor determinados tipos concretos](../code-quality/ca1059-members-should-not-expose-certain-concrete-types.md)



