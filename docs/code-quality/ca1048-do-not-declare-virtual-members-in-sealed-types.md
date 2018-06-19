---
title: 'CA1048: não declarar membros virtuais em tipos lacrados'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotDeclareVirtualMembersInSealedTypes
- CA1048
helpviewer_keywords:
- DoNotDeclareVirtualMembersInSealedTypes
- CA1048
ms.assetid: 5dcf4a30-6f98-48a8-b8cc-7b89ea757262
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 38ba776cb423773ca6c5a4646bbf30531cd2d27f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31897350"
---
# <a name="ca1048-do-not-declare-virtual-members-in-sealed-types"></a>CA1048: não declarar membros virtuais em tipos lacrados
|||
|-|-|
|NomeDoTipo|DoNotDeclareVirtualMembersInSealedTypes|
|CheckId|CA1048|
|Categoria|Microsoft.Design|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Um tipo público está lacrado e declara um método que é `virtual` (`Overridable` no Visual Basic) e não final. Essa regra não relata violações para tipos de delegado, que devem seguir esse padrão.

## <a name="rule-description"></a>Descrição da Regra
 Os tipos declaram métodos como virtuais de forma que a herança de tipos possa substituir a implementação do método virtual. Por definição, você não pode herdar de um tipo lacrado, fazendo com que um método virtual de um tipo lacrado sem sentido.

 Os compiladores do Visual Basic e c# não permitir que tipos de violam essa regra.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação desta regra, que o método não virtual ou torne o tipo herdado.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra. Deixar o tipo em seu estado atual pode causar problemas de manutenção e não oferece nenhum benefício.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra um tipo que violam essa regra.

 [!code-cpp[FxCop.Design.SealedVirtual#1](../code-quality/codesnippet/CPP/ca1048-do-not-declare-virtual-members-in-sealed-types_1.cpp)]