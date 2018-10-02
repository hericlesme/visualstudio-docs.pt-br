---
title: 'CA1053: Os tipos de espaços reservados estáticos não devem ter construtores | Microsoft Docs'
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
- StaticHolderTypesShouldNotHaveConstructors
- CA1053
helpviewer_keywords:
- CA1053
- StaticHolderTypesShouldNotHaveConstructors
ms.assetid: 10302b9a-fa5e-4935-a06a-513d9600f613
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: fb4d397a5262245771ffd54aadc08a29c5cfcee8
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47586997"
---
# <a name="ca1053-static-holder-types-should-not-have-constructors"></a>CA1053: os tipos de suporte estático não devem ter construtores
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [CA1053: os tipos de espaços reservados estáticos não devem ter construtores](https://docs.microsoft.com/visualstudio/code-quality/ca1053-static-holder-types-should-not-have-constructors).

|||
|-|-|
|NomeDoTipo|StaticHolderTypesShouldNotHaveConstructors|
|CheckId|CA1053|
|Categoria|Microsoft.Design|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Um tipo público ou público aninhado declara apenas membros estáticos e tem um construtor padrão público ou protegido.

## <a name="rule-description"></a>Descrição da Regra
 O construtor é desnecessário porque chamar membros estáticos não exige uma instância do tipo. Além disso, porque o tipo não tem membros não estáticos, criando uma instância não fornece acesso a qualquer um dos membros do tipo.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, remova o construtor padrão ou torná-la particular.

> [!NOTE]
>  Alguns compiladores criar automaticamente um construtor padrão público se o tipo de não definir nenhum construtor. Se esse for o caso com seu tipo, adicione um construtor padrão particular para eliminar a violação.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra. A presença do construtor sugere que o tipo não é um tipo estático.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra um tipo que viola essa regra. Observe que não há nenhum construtor padrão no código-fonte. Quando esse código é compilado em um assembly, o compilador c# irá inserir um construtor padrão, que irá violar essa regra. Para corrigir isso, declare um construtor particular.

 [!code-csharp[FxCop.Design.StaticTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.StaticTypes/cs/FxCop.Design.StaticTypes.cs#1)]



