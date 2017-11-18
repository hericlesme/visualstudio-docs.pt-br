---
title: 'CA2240: Implementar ISerializable corretamente | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2240
- ImplementISerializableCorrectly
helpviewer_keywords:
- CA2240
- ImplementISerializableCorrectly
ms.assetid: cf05936d-0d6c-49ed-a1b4-220032e50b97
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c8e3f9ba0e3cb182ec08dd802dc87728a0fb9dc0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="ca2240-implement-iserializable-correctly"></a>CA2240: implementar ISerializable corretamente
|||  
|-|-|  
|NomeDoTipo|ImplementISerializableCorrectly|  
|CheckId|CA2240|  
|Categoria|Microsoft.Usage|  
|Alteração Significativa|Não separáveis|  
  
## <a name="cause"></a>Causa  
 Um tipo visível externamente é atribuível para o <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> interface e uma das seguintes condições for verdadeira:  
  
-   O tipo herdado, mas não substitui o <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> método e o tipo declara os campos de instância que não são marcados com o <xref:System.NonSerializedAttribute?displayProperty=fullName> atributo.  
  
-   O tipo não for fechado e o tipo implementa um <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> método que não seja externamente visível e substituível.  
  
## <a name="rule-description"></a>Descrição da Regra  
 Os campos são declarados em um tipo que herda da instância de <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> interface não são incluídos automaticamente no processo de serialização. Para incluir os campos, o tipo deve implementar o <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> método e o construtor de serialização. Se os campos não devem ser serializados, aplique a <xref:System.NonSerializedAttribute> para os campos para indicar explicitamente a decisão de atributo.  
  
 Em tipos que não são bloqueados, implementações de <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> método deve ser visível externamente. Portanto, o método pode ser chamado por tipos derivados e é substituível.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Para corrigir uma violação desta regra, verifique o <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> método visível e substituível e verifique se todos os campos de instância são incluídos no processo de serialização ou marcados explicitamente com o <xref:System.NonSerializedAttribute> atributo.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 Não suprima um aviso nessa regra.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra dois tipos serializáveis que violam a regra.  
  
 [!code-csharp[FxCop.Usage.ImplementISerializableCorrectly#1](../code-quality/codesnippet/CSharp/ca2240-implement-iserializable-correctly_1.cs)]
 [!code-cpp[FxCop.Usage.ImplementISerializableCorrectly#1](../code-quality/codesnippet/CPP/ca2240-implement-iserializable-correctly_1.cpp)]
 [!code-vb[FxCop.Usage.ImplementISerializableCorrectly#1](../code-quality/codesnippet/VisualBasic/ca2240-implement-iserializable-correctly_1.vb)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir corrige as duas violações anteriores, fornecendo uma implementação substituível de <xref:System.Runtime.Serialization.ISerializable.GetObjectData> na classe do catálogo e fornecendo uma implementação de `GetObjectData` na classe de biblioteca.  
  
 [!code-cpp[FxCop.Usage.ImplementISerializableCorrectly2#1](../code-quality/codesnippet/CPP/ca2240-implement-iserializable-correctly_2.cpp)]
 [!code-csharp[FxCop.Usage.ImplementISerializableCorrectly2#1](../code-quality/codesnippet/CSharp/ca2240-implement-iserializable-correctly_2.cs)]
 [!code-vb[FxCop.Usage.ImplementISerializableCorrectly2#1](../code-quality/codesnippet/VisualBasic/ca2240-implement-iserializable-correctly_2.vb)]  
  
## <a name="related-rules"></a>Regras relacionadas  
 [CA2236: chamar métodos de classe base em tipos ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)  
 [CA2229: implementar construtores de serialização](../code-quality/ca2229-implement-serialization-constructors.md)  
 [CA2238: implementar métodos de serialização corretamente](../code-quality/ca2238-implement-serialization-methods-correctly.md)  
 [CA2235: marcar todos os campos não serializáveis](../code-quality/ca2235-mark-all-non-serializable-fields.md)  
 [CA2237: marcar tipos ISerializable com SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)  
 [CA2239: fornecer métodos de desserialização para campos opcionais](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)  
 [CA2120: proteger construtores de serialização](../code-quality/ca2120-secure-serialization-constructors.md)  
