---
title: "CA1813: Evitar atributos não lacrados | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1813
- AvoidUnsealedAttributes
helpviewer_keywords:
- CA1813
- AvoidUnsealedAttributes
ms.assetid: f5e31b4c-9f8b-49e1-a2a8-bb5f1140729a
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 9ad548bd51985484ebcb39cb6022e994a5e0534a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ca1813-avoid-unsealed-attributes"></a>CA1813: evitar atributos não lacrados
|||  
|-|-|  
|NomeDoTipo|AvoidUnsealedAttributes|  
|CheckId|CA1813|  
|Categoria|Microsoft.Performance|  
|Alteração Significativa|Quebra|  
  
## <a name="cause"></a>Causa  
 Um tipo público herda de <xref:System.Attribute?displayProperty=fullName>, não é abstrato e não está lacrado (`NotInheritable` no Visual Basic).  
  
## <a name="rule-description"></a>Descrição da Regra  
 A biblioteca de classes do [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] fornece métodos para recuperar atributos personalizados. Por padrão, esses métodos pesquisar a hierarquia de herança de atributo; Por exemplo <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=fullName> procura o tipo de atributo especificado ou qualquer tipo de atributo que estende o tipo de atributo especificado. Lacrar o atributo elimina a pesquisa por meio da hierarquia de herança e pode melhorar o desempenho.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Para corrigir uma violação desta regra, lacrar o tipo de atributo ou torná-lo abstrata.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 É seguro suprimir um aviso dessa regra. Você deve fazer isso apenas se você estiver definindo uma hierarquia de atributo e não é possível lacrar o atributo ou torná-lo abstrata.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra um atributo personalizado que atenda a essa regra.  
  
 [!code-csharp[FxCop.Performance.AttributesSealed#1](../code-quality/codesnippet/CSharp/ca1813-avoid-unsealed-attributes_1.cs)]
 [!code-vb[FxCop.Performance.AttributesSealed#1](../code-quality/codesnippet/VisualBasic/ca1813-avoid-unsealed-attributes_1.vb)]  
  
## <a name="related-rules"></a>Regras relacionadas  
 [CA1019: definir acessadores para argumentos de atributo](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)  
  
 [CA1018: marcar atributos com AttributeUsageAttribute](../code-quality/ca1018-mark-attributes-with-attributeusageattribute.md)  
  
## <a name="see-also"></a>Consulte também  
 [Atributos](/dotnet/standard/design-guidelines/attributes)