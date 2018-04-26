---
title: 'CA1041: fornecer mensagem ObsoleteAttribute'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1041
- ProvideObsoleteAttributeMessage
helpviewer_keywords:
- ProvideObsoleteAttributeMessage
- CA1041
ms.assetid: be5bee69-d2d2-44e1-be2e-3ea451969003
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7ac873aa7a6a86e2c4fe9964d0b690950aa0fb9e
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="ca1041-provide-obsoleteattribute-message"></a>CA1041: fornecer mensagem ObsoleteAttribute
|||
|-|-|
|NomeDoTipo|ProvideObsoleteAttributeMessage|
|CheckId|CA1041|
|Categoria|Microsoft.Design|
|Alteração Significativa|Não recentes|

## <a name="cause"></a>Causa
 Um tipo ou membro está marcado usando uma <xref:System.ObsoleteAttribute?displayProperty=fullName> atributo que não tem seu <xref:System.ObsoleteAttribute.Message%2A?displayProperty=fullName> propriedade especificada.

## <a name="rule-description"></a>Descrição da Regra
 <xref:System.ObsoleteAttribute> é usado para marcar preterido biblioteca de tipos e membros. Os consumidores de biblioteca devem evitar o uso de qualquer tipo ou membro que está marcado como obsoleto. Isso ocorre porque ele talvez não tenha suporte e será removido de versões posteriores da biblioteca. Quando um tipo ou membro marcado usando <xref:System.ObsoleteAttribute> é compilado, o <xref:System.ObsoleteAttribute.Message%2A> propriedade do atributo é exibida. Isso dá ao usuário informações sobre o tipo ou o membro obsoleto. Essas informações incluem geralmente quanto tempo o tipo obsoleto ou membro terão suporte, os designers de biblioteca e a substituição preferencial a ser usado.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação desta regra, adicione o `message` parâmetro para o <xref:System.ObsoleteAttribute> construtor.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprimir um aviso dessa regra porque o <xref:System.ObsoleteAttribute.Message%2A> propriedade fornece informações importantes sobre o tipo ou membro obsoleto.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra um membro obsoleto que tenha declarado corretamente <xref:System.ObsoleteAttribute>.

 [!code-cpp[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/CPP/ca1041-provide-obsoleteattribute-message_1.cpp)]
 [!code-csharp[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/CSharp/ca1041-provide-obsoleteattribute-message_1.cs)]
 [!code-vb[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/VisualBasic/ca1041-provide-obsoleteattribute-message_1.vb)]

## <a name="see-also"></a>Consulte também
 <xref:System.ObsoleteAttribute?displayProperty=fullName>