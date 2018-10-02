---
title: 'CA1052: os tipos de suporte estático devem ser lacrados'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- StaticHolderTypesShouldBeSealed
- CA1052
helpviewer_keywords:
- CA1052
- StaticHolderTypesShouldBeSealed
ms.assetid: 51a3165d-781e-4a55-aa0d-ea25fee7d4f2
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 2c5d22db6a973947faf228e2e3844d63a916e24e
ms.sourcegitcommit: ad5fb20f18b23eb8bd2568717f61edc6b7eee5e7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47859491"
---
# <a name="ca1052-static-holder-types-should-be-sealed"></a>CA1052: os tipos de suporte estático devem ser lacrados

|||
|-|-|
|NomeDoTipo|StaticHolderTypesShouldBeSealed|
|CheckId|CA1052|
|Categoria|Microsoft.Design|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Um tipo público ou protegido contém apenas membros estáticos e não é declarado com o [lacrado](/dotnet/csharp/language-reference/keywords/sealed) ([NotInheritable](/dotnet/visual-basic/language-reference/modifiers/notinheritable)) modificador.

## <a name="rule-description"></a>Descrição da regra
 Esta regra pressupõe que um tipo que contém apenas membros estáticos não foi projetado para ser herdadas, pois o tipo não fornece nenhuma funcionalidade que pode ser substituída em um tipo derivado. Um tipo que não se destina a ser herdada que deve ser marcado com o `sealed` modificador para proibir o uso como um tipo base.

## <a name="how-to-fix-violations"></a>Como corrigir violações
 Para corrigir uma violação dessa regra, marque o tipo como `sealed`. Se você estiver direcionando o .NET Framework 2.0 ou posterior, uma abordagem melhor é marcar o tipo como `static`. Dessa forma, você não precisa declarar um construtor particular para impedir que a classe que está sendo criado.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
 Suprima um aviso nessa regra somente se o tipo foi projetado para ser herdada. A ausência do `sealed` modificador sugere que o tipo é útil como um tipo base.

## <a name="example-of-a-violation"></a>Exemplo de uma violação

### <a name="description"></a>Descrição
 O exemplo a seguir mostra um tipo que viola a regra.

### <a name="code"></a>Código
 [!code-csharp[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/CSharp/ca1052-static-holder-types-should-be-sealed_1.cs)]
 [!code-vb[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/VisualBasic/ca1052-static-holder-types-should-be-sealed_1.vb)]
 [!code-cpp[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/CPP/ca1052-static-holder-types-should-be-sealed_1.cpp)]

## <a name="fix-with-the-static-modifier"></a>Corrigir com o modificador estático

### <a name="description"></a>Descrição
 O exemplo a seguir mostra como corrigir uma violação dessa regra, marcando o tipo com o `static` modificador.

### <a name="code"></a>Código
 [!code-csharp[FxCop.Design.StaticMembersFixed#1](../code-quality/codesnippet/CSharp/ca1052-static-holder-types-should-be-sealed_2.cs)]

## <a name="related-rules"></a>Regras relacionadas
 [CA1053: os tipos de suporte estático não devem ter construtores](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md)
