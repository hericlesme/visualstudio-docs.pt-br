---
title: 'CA1053: os tipos de suporte estático não devem ter construtores'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- StaticHolderTypesShouldNotHaveConstructors
- CA1053
helpviewer_keywords:
- CA1053
- StaticHolderTypesShouldNotHaveConstructors
ms.assetid: 10302b9a-fa5e-4935-a06a-513d9600f613
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d7f99804abeac1c9f536c94c542f6e031bf16ec6
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="ca1053-static-holder-types-should-not-have-constructors"></a>CA1053: os tipos de suporte estático não devem ter construtores
|||
|-|-|
|NomeDoTipo|StaticHolderTypesShouldNotHaveConstructors|
|CheckId|CA1053|
|Categoria|Microsoft.Design|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Um tipo público ou público aninhado declara apenas membros estáticos e tem um construtor padrão público ou protegido.

## <a name="rule-description"></a>Descrição da Regra
 O construtor é desnecessário porque chamar membros estáticos não exige uma instância do tipo. Além disso, porque o tipo não tem membros não estáticos, criar uma instância não fornece acesso a qualquer um dos membros do tipo.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação desta regra, remova o construtor padrão ou torná-lo particular.

> [!NOTE]
>  Alguns compiladores cria automaticamente um construtor padrão público se o tipo não define nenhum construtor. Se esse for o caso com seu tipo, adicione um construtor privado padrão para eliminar a violação.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra. A presença do construtor sugere o tipo não é um tipo estático.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra um tipo que violam essa regra. Observe que não há nenhum construtor padrão no código-fonte. Quando esse código é compilado em um assembly, o compilador c# inserirá um construtor padrão, que será violam essa regra. Para corrigir isso, declare um construtor particular.

 [!code-csharp[FxCop.Design.StaticTypes#1](../code-quality/codesnippet/CSharp/ca1053-static-holder-types-should-not-have-constructors_1.cs)]