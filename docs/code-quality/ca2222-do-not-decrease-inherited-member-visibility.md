---
title: 'CA2222: não diminuir a visibilidade de membro herdada'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotDecreaseInheritedMemberVisibility
- CA2222
helpviewer_keywords:
- DoNotDecreaseInheritedMemberVisibility
- CA2222
ms.assetid: 066c8675-381f-43cc-956c-d757cc494028
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8d91425ecb5be33d23b1d7775caac04c616c89a9
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31921238"
---
# <a name="ca2222-do-not-decrease-inherited-member-visibility"></a>CA2222: não diminuir a visibilidade de membro herdada
|||
|-|-|
|NomeDoTipo|DoNotDecreaseInheritedMemberVisibility|
|CheckId|CA2222|
|Categoria|Microsoft.Usage|
|Alteração Significativa|Não separáveis|

## <a name="cause"></a>Causa
 Um método privado em um tipo tem uma assinatura que é idêntica a um método público declarado em um tipo base. O método particular não é final.

## <a name="rule-description"></a>Descrição da Regra
 Você não deve alterar o modificador de acesso para membros herdados. A alteração de um membro herdado para particular não impede que os chamadores acessem a implementação da classe base do método. Se o membro é privado e o tipo é sem lacre, a herança de tipos pode chamar a implementação de pública última do método na hierarquia de herança. Se você precisar alterar o modificador de acesso, o método deve ser marcado como final ou seu tipo deve ser lacrado para impedir que o método que está sendo substituído.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação desta regra, altere o acesso para ser não-particulares. Como alternativa, se a linguagem de programação dá suporte a ele, você pode fazer o método final.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra um tipo que violam essa regra.

 [!code-vb[FxCop.Usage.InheritedPublic#1](../code-quality/codesnippet/VisualBasic/ca2222-do-not-decrease-inherited-member-visibility_1.vb)]
 [!code-csharp[FxCop.Usage.InheritedPublic#1](../code-quality/codesnippet/CSharp/ca2222-do-not-decrease-inherited-member-visibility_1.cs)]