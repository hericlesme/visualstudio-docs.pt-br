---
title: 'CA1014: marcar assemblies com CLSCompliantAttribute'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1014
- MarkAssembliesWithClsCompliant
helpviewer_keywords:
- CA1014
- MarkAssembliesWithClsCompliant
ms.assetid: 4fe57449-cf45-4745-bcd2-6345f1ed266d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 51e5a43a402bb215a939b37354dd30f24e4d5d14
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="ca1014-mark-assemblies-with-clscompliantattribute"></a>CA1014: marcar assemblies com CLSCompliantAttribute
|||
|-|-|
|NomeDoTipo|MarkAssembliesWithClsCompliant|
|CheckId|CA1014|
|Categoria|Microsoft.Design|
|Alteração Significativa|Não recentes|

## <a name="cause"></a>Causa
 Um assembly não tem o <xref:System.CLSCompliantAttribute?displayProperty=fullName> atributo aplicado a ele.

## <a name="rule-description"></a>Descrição da Regra
 A CLS (Common Language Specification) define restrições de nomenclatura, tipos de dados e regras que assemblies deverão respeitar se forem usados em todas as linguagens de programação. Um bom design dita que todos os assemblies indicam explicitamente com compatibilidade com CLS <xref:System.CLSCompliantAttribute>. Se o atributo não estiver presente em um assembly, o assembly não é compatível.

 É possível para um assembly compatível com CLS para conter tipos ou digitar os membros que não são compatíveis.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação desta regra, adicione o atributo para o assembly. Em vez de marcar o conjunto completo como não compatíveis, você deve determinar o tipo ou membros de tipo não são compatíveis e marcar como tal, esses elementos. Se possível, você deve fornecer uma alternativa compatível com CLS para membros não compatíveis para que o maior público possível possa acessar toda a funcionalidade do seu assembly.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra. Se você não quiser que o assembly deve estar em conformidade, aplique o atributo e defina seu valor como `false`.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra um assembly que tem o <xref:System.CLSCompliantAttribute?displayProperty=fullName> atributo aplicado que declara compatível com CLS.

 [!code-csharp[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/CSharp/ca1014-mark-assemblies-with-clscompliantattribute_1.cs)]
 [!code-cpp[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/CPP/ca1014-mark-assemblies-with-clscompliantattribute_1.cpp)]
 [!code-vb[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/VisualBasic/ca1014-mark-assemblies-with-clscompliantattribute_1.vb)]

## <a name="see-also"></a>Consulte também
 <xref:System.CLSCompliantAttribute?displayProperty=fullName> [Independência da linguagem e componentes independentes da linguagem](/dotnet/standard/language-independence-and-language-independent-components)