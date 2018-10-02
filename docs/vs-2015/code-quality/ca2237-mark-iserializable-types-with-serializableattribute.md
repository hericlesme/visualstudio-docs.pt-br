---
title: 'CA2237: Marcar tipos ISerializable com SerializableAttribute | Microsoft Docs'
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
- CA2237
- MarkISerializableTypesWithSerializable
helpviewer_keywords:
- MarkISerializableTypesWithSerializable
- CA2237
ms.assetid: 9bd6bb24-a527-43dd-9952-043c0c694f46
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: d2bcbca460c404a977b2172f17dfe98164dd52bf
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47587318"
---
# <a name="ca2237-mark-iserializable-types-with-serializableattribute"></a>CA2237: marcar tipos ISerializable com SerializableAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [CA2237: marcar tipos ISerializable com SerializableAttribute](https://docs.microsoft.com/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute).

|||
|-|-|
|NomeDoTipo|MarkISerializableTypesWithSerializable|
|CheckId|CA2237|
|Categoria|Microsoft.Usage|
|Alteração Significativa|Não separável|

## <a name="cause"></a>Causa
 Um tipo visível externamente implementa o <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> interface e o tipo não está marcado com o <xref:System.SerializableAttribute?displayProperty=fullName> atributo. A regra ignora os tipos derivados cujo tipo base não é serializável.

## <a name="rule-description"></a>Descrição da Regra
 Para serem reconhecidos pelo common language runtime como serializáveis, os tipos devem ser marcados com o <xref:System.SerializableAttribute> mesmo se o tipo usa uma rotina de serialização personalizada por meio da implementação do atributo a <xref:System.Runtime.Serialization.ISerializable> interface.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, aplicar o <xref:System.SerializableAttribute> para o tipo de atributo.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra para classes de exceção, porque eles devem ser serializáveis para funcionar corretamente entre domínios de aplicativo.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra um tipo que viola a regra. Remova o <xref:System.SerializableAttribute> linha satisfazer a regra de atributo.

 [!code-csharp[FxCop.Usage.MarkSerializable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.MarkSerializable/cs/FxCop.Usage.MarkSerializable.cs#1)]
 [!code-vb[FxCop.Usage.MarkSerializable#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.MarkSerializable/vb/FxCop.Usage.MarkSerializable.vb#1)]

## <a name="related-rules"></a>Regras relacionadas
 [CA2236: chamar métodos de classe base em tipos ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

 [CA2240: implementar ISerializable corretamente](../code-quality/ca2240-implement-iserializable-correctly.md)

 [CA2229: implementar construtores de serialização](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2238: implementar métodos de serialização corretamente](../code-quality/ca2238-implement-serialization-methods-correctly.md)

 [CA2235: marcar todos os campos não serializáveis](../code-quality/ca2235-mark-all-non-serializable-fields.md)

 [CA2239: fornecer métodos de desserialização para campos opcionais](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

 [CA2120: proteger construtores de serialização](../code-quality/ca2120-secure-serialization-constructors.md)



