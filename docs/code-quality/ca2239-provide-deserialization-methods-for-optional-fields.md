---
title: 'CA2239: fornecer métodos de desserialização para campos opcionais'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2239
- ProvideDeserializationMethodsForOptionalFields
helpviewer_keywords:
- ProvideDeserializationMethodsForOptionalFields
- CA2239
ms.assetid: 6480ff5e-0caa-4707-814e-2f927cdafef5
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 04d3e40c73a02c43ecfb13eda0abcfabcb0d3ad5
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="ca2239-provide-deserialization-methods-for-optional-fields"></a>CA2239: fornecer métodos de desserialização para campos opcionais
|||
|-|-|
|NomeDoTipo|ProvideDeserializationMethodsForOptionalFields|
|CheckId|CA2239|
|Categoria|Microsoft.Usage|
|Alteração Significativa|Não separáveis|

## <a name="cause"></a>Causa
 Um tipo tem um campo que está marcado com o <xref:System.Runtime.Serialization.OptionalFieldAttribute?displayProperty=fullName> atributo e o tipo não fornece métodos de manipulação de eventos de desserialização.

## <a name="rule-description"></a>Descrição da Regra
 O <xref:System.Runtime.Serialization.OptionalFieldAttribute> atributo não tem nenhum efeito na serialização; um campo marcado com o atributo é serializado. No entanto, o campo será ignorado na desserialização e retém o valor padrão associado com seu tipo. Manipuladores de eventos de desserialização devem ser declarado como definir o campo durante o processo de desserialização.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação desta regra, adicione métodos para o tipo de manipulação de eventos de desserialização.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 É seguro suprimir um aviso de que essa regra se o campo deve ser ignorado durante o processo de desserialização.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra métodos de manipulação de um tipo com um campo opcional e um evento de desserialização.

 [!code-csharp[FxCop.Usage.OptionalFields#1](../code-quality/codesnippet/CSharp/ca2239-provide-deserialization-methods-for-optional-fields_1.cs)]
 [!code-vb[FxCop.Usage.OptionalFields#1](../code-quality/codesnippet/VisualBasic/ca2239-provide-deserialization-methods-for-optional-fields_1.vb)]

## <a name="related-rules"></a>Regras relacionadas
 [CA2236: chamar métodos de classe base em tipos ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

 [CA2240: implementar ISerializable corretamente](../code-quality/ca2240-implement-iserializable-correctly.md)

 [CA2229: implementar construtores de serialização](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2238: implementar métodos de serialização corretamente](../code-quality/ca2238-implement-serialization-methods-correctly.md)

 [CA2235: marcar todos os campos não serializáveis](../code-quality/ca2235-mark-all-non-serializable-fields.md)

 [CA2237: marcar tipos ISerializable com SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

 [CA2120: proteger construtores de serialização](../code-quality/ca2120-secure-serialization-constructors.md)