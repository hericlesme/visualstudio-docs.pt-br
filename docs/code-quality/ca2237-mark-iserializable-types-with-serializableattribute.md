---
title: 'CA2237: Marcar tipos ISerializable com SerializableAttribute | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2237
- MarkISerializableTypesWithSerializable
helpviewer_keywords:
- MarkISerializableTypesWithSerializable
- CA2237
ms.assetid: 9bd6bb24-a527-43dd-9952-043c0c694f46
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ecb9934ddefe0458f2974af0d73560532a17cc07
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="ca2237-mark-iserializable-types-with-serializableattribute"></a>CA2237: marcar tipos ISerializable com SerializableAttribute
|||  
|-|-|  
|NomeDoTipo|MarkISerializableTypesWithSerializable|  
|CheckId|CA2237|  
|Categoria|Microsoft.Usage|  
|Alteração Significativa|Não separáveis|  
  
## <a name="cause"></a>Causa  
 Um tipo visível externamente implementa o <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> interface e o tipo não está marcado com o <xref:System.SerializableAttribute?displayProperty=fullName> atributo. A regra ignora os tipos derivados cujo tipo de base não é serializável.  
  
## <a name="rule-description"></a>Descrição da Regra  
 Para ser reconhecidos pelo common language runtime como serializável, os tipos devem ser marcados com o <xref:System.SerializableAttribute> atributo mesmo que o tipo usa uma rotina de serialização personalizada por meio da implementação do <xref:System.Runtime.Serialization.ISerializable> interface.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Para corrigir uma violação desta regra, aplicar o <xref:System.SerializableAttribute> para o tipo de atributo.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 Não suprima um aviso dessa regra para classes de exceção porque eles devem ser serializáveis funcione corretamente em domínios de aplicativo.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra um tipo que viola a regra. Remova o <xref:System.SerializableAttribute> linha para satisfazer a regra de atributo.  
  
 [!code-vb[FxCop.Usage.MarkSerializable#1](../code-quality/codesnippet/VisualBasic/ca2237-mark-iserializable-types-with-serializableattribute_1.vb)]
 [!code-csharp[FxCop.Usage.MarkSerializable#1](../code-quality/codesnippet/CSharp/ca2237-mark-iserializable-types-with-serializableattribute_1.cs)]  
  
## <a name="related-rules"></a>Regras relacionadas  
 [CA2236: chamar métodos de classe base em tipos ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)  
  
 [CA2240: implementar ISerializable corretamente](../code-quality/ca2240-implement-iserializable-correctly.md)  
  
 [CA2229: implementar construtores de serialização](../code-quality/ca2229-implement-serialization-constructors.md)  
  
 [CA2238: implementar métodos de serialização corretamente](../code-quality/ca2238-implement-serialization-methods-correctly.md)  
  
 [CA2235: marcar todos os campos não serializáveis](../code-quality/ca2235-mark-all-non-serializable-fields.md)  
  
 [CA2239: fornecer métodos de desserialização para campos opcionais](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)  
  
 [CA2120: proteger construtores de serialização](../code-quality/ca2120-secure-serialization-constructors.md)