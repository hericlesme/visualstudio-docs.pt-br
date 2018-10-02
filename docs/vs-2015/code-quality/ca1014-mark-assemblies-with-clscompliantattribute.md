---
title: 'CA1014: Marcar assemblies com CLSCompliantAttribute | Microsoft Docs'
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
- CA1014
- MarkAssembliesWithClsCompliant
helpviewer_keywords:
- CA1014
- MarkAssembliesWithClsCompliant
ms.assetid: 4fe57449-cf45-4745-bcd2-6345f1ed266d
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 5d68a982c17a3cc4b0cf33a31af7f57749c796fc
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47586966"
---
# <a name="ca1014-mark-assemblies-with-clscompliantattribute"></a>CA1014: marcar assemblies com CLSCompliantAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [CA1014: marcar assemblies com CLSCompliantAttribute](https://docs.microsoft.com/visualstudio/code-quality/ca1014-mark-assemblies-with-clscompliantattribute).

|||
|-|-|
|NomeDoTipo|MarkAssembliesWithClsCompliant|
|CheckId|CA1014|
|Categoria|Microsoft.Design|
|Alteração Significativa|Não são significativas|

## <a name="cause"></a>Causa
 Um assembly não tem o <xref:System.CLSCompliantAttribute?displayProperty=fullName> atributo aplicado a ele.

## <a name="rule-description"></a>Descrição da Regra
 A CLS (Common Language Specification) define restrições de nomenclatura, tipos de dados e regras que assemblies deverão respeitar se forem usados em todas as linguagens de programação. Um bom design determina que todos os assemblies indiquem explicitamente a conformidade com CLS com <xref:System.CLSCompliantAttribute>. Se o atributo não estiver presente em um assembly, o assembly não está em conformidade.

 É possível que um assembly compatível com CLS contêm tipos ou membros que não estão em conformidade de tipo.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, adicione o atributo ao assembly. Em vez de todo o assembly como não compatível de marcação, você deve determinar o tipo ou membros de tipo não estão em conformidade e marcam esses elementos como tal. Se possível, você deve fornecer uma alternativa compatível com CLS para membros não compatíveis para que o maior público possível possa acessar toda a funcionalidade do seu assembly.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra. Se você não quiser que o assembly esteja em conformidade, aplique o atributo e defina seu valor como `false`.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra um assembly que tem o <xref:System.CLSCompliantAttribute?displayProperty=fullName> atributo aplicado que o declara compatíveis com CLS.

 [!code-cpp[FxCop.Design.AssembliesCls#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCls/cpp/FxCop.Design.AssembliesCls.cpp#1)]
 [!code-csharp[FxCop.Design.AssembliesCls#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCls/cs/FxCop.Design.AssembliesCls.cs#1)]
 [!code-vb[FxCop.Design.AssembliesCls#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCls/vb/FxCop.Design.AssembliesCls.vb#1)]

## <a name="see-also"></a>Consulte também
 <xref:System.CLSCompliantAttribute?displayProperty=fullName> [Independência de linguagem e componentes independentes de linguagem](http://msdn.microsoft.com/library/4f0b77d0-4844-464f-af73-6e06bedeafc6)



