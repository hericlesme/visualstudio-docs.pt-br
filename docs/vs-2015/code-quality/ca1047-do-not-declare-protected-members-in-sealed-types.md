---
title: 'CA1047: Não declarar membros protegidos em tipos lacrados | Microsoft Docs'
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
- DoNotDeclareProtectedMembersInSealedTypes
- CA1047
helpviewer_keywords:
- CA1047
- DoNotDeclareProtectedMembersInSealedTypes
ms.assetid: 829033b5-a9d8-4f26-a719-45494c9dd035
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 8a9c61d3910a550f957b9940c1280f4fd2c17bdc
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47587026"
---
# <a name="ca1047-do-not-declare-protected-members-in-sealed-types"></a>CA1047: não declarar membros protegidos em tipos lacrados
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [CA1047: não declarar membros protegidos em tipos lacrados](https://docs.microsoft.com/visualstudio/code-quality/ca1047-do-not-declare-protected-members-in-sealed-types).

|||
|-|-|
|NomeDoTipo|DoNotDeclareProtectedMembersInSealedTypes|
|CheckId|CA1047|
|Categoria|Microsoft.Design|
|Alteração Significativa|Não são significativas|

## <a name="cause"></a>Causa
 É um tipo público `sealed` (`NotInheritable` no Visual basic) e declara um membro protegido ou um tipo aninhado protegido. Essa regra não relata violações para <xref:System.Object.Finalize%2A> métodos, que devem seguir esse padrão.

## <a name="rule-description"></a>Descrição da Regra
 Os tipos declaram membros protegidos de forma que a herança de tipos possa acessar ou substituir o membro. Por definição, você não pode herdar de um tipo selado, o que significa que métodos em tipos lacrados protegidos não pode ser chamada.

 O compilador c# emite um aviso para esse erro.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, altere o nível de acesso do membro particular ou tornar o tipo herdável.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra. Deixar o tipo em seu estado atual pode causar problemas de manutenção e não oferece nenhum benefício.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra um tipo que viola essa regra.

 [!code-csharp[FxCop.Design.SealedNoProtected#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.SealedNoProtected/cs/FxCop.Design.SealedNoProtected.cs#1)]
 [!code-vb[FxCop.Design.SealedNoProtected#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.SealedNoProtected/vb/FxCop.Design.SealedNoProtected.vb#1)]



