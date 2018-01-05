---
title: "CA2229: Implementar construtores de serialização | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2229
- ImplementSerializationConstructors
helpviewer_keywords:
- CA2229
- ImplementSerializationConstructors
ms.assetid: 8e04d5fe-dfad-445a-972e-0648324fac45
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: f954626a45035aa84633f82ba3a2da0f2a682421
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ca2229-implement-serialization-constructors"></a>CA2229: implementar construtores de serialização
|||  
|-|-|  
|NomeDoTipo|ImplementSerializationConstructors|  
|CheckId|CA2229|  
|Categoria|Microsoft.Usage|  
|Alteração Significativa|Não separáveis|  
  
## <a name="cause"></a>Causa  
 O tipo implementa o <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> de interface, não é um delegado ou a interface e uma das seguintes condições for verdadeira:  
  
-   O tipo não tem um construtor que aceita um <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName> objeto e um <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> (a assinatura do construtor de serialização) do objeto.  
  
-   O tipo é sem lacre e o modificador de acesso para o construtor de serialização não é protegida (família).  
  
-   O tipo é fechado e o modificador de acesso para o construtor de serialização não é privado.  
  
## <a name="rule-description"></a>Descrição da Regra  
 Essa regra é relevante para tipos que oferecem suporte a serialização personalizada. Um tipo oferece suporte à serialização personalizada se ele implementa o <xref:System.Runtime.Serialization.ISerializable> interface. O construtor de serialização é necessário para desserializar ou recriar os objetos que foi serializados usando o <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> método.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Para corrigir uma violação dessa regra, implemente o construtor de serialização. Para uma classe lacrada, torne o construtor particular; do contrário, deixe-o protegido.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 Não suprima uma violação da regra. O tipo não serão desserializável e não funcionará em muitos cenários.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra um tipo que atenda a regra.  
  
 [!code-csharp[FxCop.Usage.ISerializableCtor#1](../code-quality/codesnippet/CSharp/ca2229-implement-serialization-constructors_1.cs)]  
  
## <a name="related-rules"></a>Regras relacionadas  
 [CA2237: marcar tipos ISerializable com SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>   
 <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>   
 <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>