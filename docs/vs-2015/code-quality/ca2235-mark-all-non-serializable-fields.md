---
title: 'CA2235: Marcar todos os campos não serializáveis | Microsoft Docs'
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
- CA2235
- MarkAllNonSerializableFields
helpviewer_keywords:
- CA2235
- MarkAllNonSerializableFields
ms.assetid: 599ad877-3a15-426c-bf17-5de15427365f
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 025ee336052bdad010b55e1ba804b2bd37c7e0d7
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47587179"
---
# <a name="ca2235-mark-all-non-serializable-fields"></a>CA2235: marcar todos os campos não serializáveis
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [CA2235: marcar todos os campos não serializáveis](https://docs.microsoft.com/visualstudio/code-quality/ca2235-mark-all-non-serializable-fields).

|||
|-|-|
|NomeDoTipo|MarkAllNonSerializableFields|
|CheckId|CA2235|
|Categoria|Microsoft.Usage|
|Alteração Significativa|Não separável|

## <a name="cause"></a>Causa
 Um campo de instância de um tipo que não seja serializável é declarado em um tipo que é serializável.

## <a name="rule-description"></a>Descrição da Regra
 Um tipo serializável é aquele que é marcado com o <xref:System.SerializableAttribute?displayProperty=fullName> atributo. Quando o tipo é serializado, um <xref:System.Runtime.Serialization.SerializationException?displayProperty=fullName> exceção será gerada se um tipo contém um campo de instância de um tipo que não é serializável.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, aplicar o <xref:System.NonSerializedAttribute?displayProperty=fullName> de atributo para o campo que não é serializável.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Suprimir um aviso nessa regra somente se um <xref:System.Runtime.Serialization.ISerializationSurrogate?displayProperty=fullName> tipo é declarado que permite que instâncias do campo a ser serializado e desserializado.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra um tipo que viola a regra e um tipo que satisfaça a regra.

 [!code-csharp[FxCop.Usage.MarkNonSerializable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.MarkNonSerializable/cs/FxCop.Usage.MarkNonSerializable.cs#1)]
 [!code-vb[FxCop.Usage.MarkNonSerializable#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.MarkNonSerializable/vb/FxCop.Usage.MarkNonSerializable.vb#1)]

## <a name="related-rules"></a>Regras relacionadas
 [CA2236: chamar métodos de classe base em tipos ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

 [CA2240: implementar ISerializable corretamente](../code-quality/ca2240-implement-iserializable-correctly.md)

 [CA2229: implementar construtores de serialização](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2238: implementar métodos de serialização corretamente](../code-quality/ca2238-implement-serialization-methods-correctly.md)

 [CA2237: marcar tipos ISerializable com SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

 [CA2239: fornecer métodos de desserialização para campos opcionais](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

 [CA2120: proteger construtores de serialização](../code-quality/ca2120-secure-serialization-constructors.md)



