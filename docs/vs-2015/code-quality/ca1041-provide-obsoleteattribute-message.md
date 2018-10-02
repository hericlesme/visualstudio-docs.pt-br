---
title: 'CA1041: Fornecer mensagem ObsoleteAttribute | Microsoft Docs'
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
- CA1041
- ProvideObsoleteAttributeMessage
helpviewer_keywords:
- ProvideObsoleteAttributeMessage
- CA1041
ms.assetid: be5bee69-d2d2-44e1-be2e-3ea451969003
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 298f6d3cbfc8b71443fe9e8e9733e5729963cea8
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47587343"
---
# <a name="ca1041-provide-obsoleteattribute-message"></a>CA1041: fornecer mensagem ObsoleteAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [CA1041: fornecer ObsoleteAttribute mensagem](https://docs.microsoft.com/visualstudio/code-quality/ca1041-provide-obsoleteattribute-message).

|||
|-|-|
|NomeDoTipo|ProvideObsoleteAttributeMessage|
|CheckId|CA1041|
|Categoria|Microsoft.Design|
|Alteração Significativa|Não são significativas|

## <a name="cause"></a>Causa
 Um tipo ou membro marcado usando um <xref:System.ObsoleteAttribute?displayProperty=fullName> atributo que não tem seu <xref:System.ObsoleteAttribute.Message%2A?displayProperty=fullName> propriedade especificada.

## <a name="rule-description"></a>Descrição da Regra
 <xref:System.ObsoleteAttribute> é usado para marcar membros e tipos de biblioteca preterido. Os clientes de biblioteca devem evitar o uso de qualquer tipo ou membro que está marcado como obsoleto. Isso ocorre porque ele não poderá ter suporte e eventualmente será removido de versões posteriores da biblioteca. Quando um tipo ou membro marcado usando <xref:System.ObsoleteAttribute> é compilado, o <xref:System.ObsoleteAttribute.Message%2A> propriedade do atributo é exibida. Isso dá ao usuário informações sobre o tipo ou o membro obsoleto. Essas informações geralmente incluem quanto o tipo obsoleto ou membro será compatível com os designers de biblioteca e da substituição de preferência para usar.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, adicione a `message` parâmetro para o <xref:System.ObsoleteAttribute> construtor.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprimir um aviso nessa regra porque o <xref:System.ObsoleteAttribute.Message%2A> propriedade fornece informações essenciais sobre o tipo ou membro obsoleto.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra um membro obsoleto que tenha declarado corretamente <xref:System.ObsoleteAttribute>.

 [!code-cpp[FxCop.Design.ObsoleteAttributeOnMember#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.ObsoleteAttributeOnMember/cpp/FxCop.Design.ObsoleteAttributeOnMember.cpp#1)]
 [!code-csharp[FxCop.Design.ObsoleteAttributeOnMember#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ObsoleteAttributeOnMember/cs/FxCop.Design.ObsoleteAttributeOnMember.cs#1)]
 [!code-vb[FxCop.Design.ObsoleteAttributeOnMember#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ObsoleteAttributeOnMember/vb/FxCop.Design.ObsoleteAttributeOnMember.vb#1)]

## <a name="see-also"></a>Consulte também
 <xref:System.ObsoleteAttribute?displayProperty=fullName>



