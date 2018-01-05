---
title: "CA2120: Proteger construtores de serialização | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2120
- SecureSerializationConstructors
helpviewer_keywords:
- SecureSerializationConstructors
- CA2120
ms.assetid: e9989da1-55a0-43f8-9aa9-da86afae3b41
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: e28d76315b3ef5844bd9b525764e6f5a5111ef56
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ca2120-secure-serialization-constructors"></a>CA2120: proteger construtores de serialização
|||  
|-|-|  
|NomeDoTipo|SecureSerializationConstructors|  
|CheckId|CA2120|  
|Categoria|Microsoft.Security|  
|Alteração Significativa|Quebra|  
  
## <a name="cause"></a>Causa  
 O tipo implementa o <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> interface, não é um delegado ou a interface e é declarada em um assembly que permite que os chamadores parcialmente confiáveis. O tipo tem um construtor que aceita um <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName> objeto e um <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> (a assinatura do construtor de serialização) do objeto. Este construtor não é protegido por uma verificação de segurança, mas um ou mais dos construtores regulares no tipo é protegido.  
  
## <a name="rule-description"></a>Descrição da Regra  
 Essa regra é relevante para tipos que oferecem suporte a serialização personalizada. Um tipo oferece suporte à serialização personalizada se ele implementa o <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> interface. O construtor de serialização é necessário e é usado para desserializar ou recriar os objetos que foi serializados usando o <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> método. Como o construtor de serialização aloca e inicializa os objetos, verificações de segurança que estão presentes em construtores regulares também devem estar presentes no construtor de serialização. Se violam essa regra, chamadores que, caso contrário, não foi possível criar uma instância podem usar o construtor de serialização para fazer isso.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Para corrigir uma violação desta regra, protege o construtor de serialização com exigências de segurança que são idênticas às Protegendo outros construtores.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 Não suprima uma violação da regra.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra um tipo que viola a regra.  
  
 [!code-csharp[FxCop.Security.SerialCtors#1](../code-quality/codesnippet/CSharp/ca2120-secure-serialization-constructors_1.cs)]  
  
## <a name="related-rules"></a>Regras relacionadas  
 [CA2229: implementar construtores de serialização](../code-quality/ca2229-implement-serialization-constructors.md)  
  
 [CA2237: marcar tipos ISerializable com SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>   
 <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>   
 <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>