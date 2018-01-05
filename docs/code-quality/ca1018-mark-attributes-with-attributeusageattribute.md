---
title: 'CA1018: Marcar atributos com AttributeUsageAttribute | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1018
- MarkAttributesWithAttributeUsage
helpviewer_keywords:
- CA1018
- MarkAttributesWithAttributeUsage
ms.assetid: 6ab70ec0-220f-4880-af31-45067703133c
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 2b94cb7c11c803e713609036db12c47e2027cb61
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ca1018-mark-attributes-with-attributeusageattribute"></a>CA1018: marcar atributos com AttributeUsageAttribute
|||  
|-|-|  
|NomeDoTipo|MarkAttributesWithAttributeUsage|  
|CheckId|CA1018|  
|Categoria|Microsoft.Design|  
|Alteração Significativa|Quebra|  
  
## <a name="cause"></a>Causa  
 O <xref:System.AttributeUsageAttribute?displayProperty=fullName> atributo não estiver presente no atributo personalizado.  
  
## <a name="rule-description"></a>Descrição da Regra  
 Quando você define um atributo personalizado, marcá-la usando <xref:System.AttributeUsageAttribute> para indicar onde no código-fonte do atributo personalizado pode ser aplicado. O significado e o uso desejado de um atributo determinarão seus locais válidos no código. Por exemplo, você pode definir um atributo que identifica a pessoa que é responsável por manter e aprimorar a cada tipo em uma biblioteca e responsabilidade sempre é atribuída no nível de tipo. Nesse caso, compiladores devem habilitar o atributo em classes, enumerações e interfaces, mas não devem ativá-lo em propriedades, eventos ou métodos. Procedimentos e políticas organizacionais determinaria se o atributo deve ser habilitado em assemblies.  
  
 O <xref:System.AttributeTargets?displayProperty=fullName> enumeração define os destinos que você pode especificar para um atributo personalizado. Se você omitir <xref:System.AttributeUsageAttribute>, o atributo personalizado será válido para todos os destinos, conforme definido pelo `All` valor <xref:System.AttributeTargets> enumeração.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Para corrigir uma violação desta regra, especificar destinos para o atributo usando <xref:System.AttributeUsageAttribute>. Consulte o exemplo a seguir.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 Você deve corrigir uma violação desta regra em vez de excluir a mensagem. Mesmo que o atributo herda <xref:System.AttributeUsageAttribute>, o atributo deve estar presente para simplificar a manutenção do código.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir define dois atributos. `BadCodeMaintainerAttribute`omite incorretamente o <xref:System.AttributeUsageAttribute> instrução, e `GoodCodeMaintainerAttribute` implementa corretamente o atributo que é descrito anteriormente nesta seção. Observe que a propriedade `DeveloperName` é necessária para a regra de criação [CA1019: definir acessadores para argumentos de atributo](../code-quality/ca1019-define-accessors-for-attribute-arguments.md) e é incluído para integridade.  
  
 [!code-csharp[FxCop.Design.AttributeUsage#1](../code-quality/codesnippet/CSharp/ca1018-mark-attributes-with-attributeusageattribute_1.cs)]
 [!code-vb[FxCop.Design.AttributeUsage#1](../code-quality/codesnippet/VisualBasic/ca1018-mark-attributes-with-attributeusageattribute_1.vb)]  
  
## <a name="related-rules"></a>Regras relacionadas  
 [CA1019: definir acessadores para argumentos de atributo](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)  
  
 [CA1813: evitar atributos não lacrados](../code-quality/ca1813-avoid-unsealed-attributes.md)  
  
## <a name="see-also"></a>Consulte também  
 [Atributos](/dotnet/standard/design-guidelines/attributes)