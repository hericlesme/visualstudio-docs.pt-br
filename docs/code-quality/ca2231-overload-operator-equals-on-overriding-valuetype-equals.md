---
title: 'CA2231: Sobrecarregar operador equals ao substituir ValueType. Equals | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- OverloadOperatorEqualsOnOverridingValueTypeEquals
- CA2231
- OverrideOperatorEqualsOnOverridingValueTypeEquals
helpviewer_keywords:
- OverloadOperatorEqualsOnOverridingValueTypeEquals
- CA2231
ms.assetid: 114c0161-261a-40ad-8b2c-0932d6909d2a
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0295b7379fbac1ae3e1c84afca651503d6984ba6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="ca2231-overload-operator-equals-on-overriding-valuetypeequals"></a>CA2231: sobrecarregar igualdades de operador em ValueType.Equals substituídos
|||  
|-|-|  
|NomeDoTipo|OverloadOperatorEqualsOnOverridingValueTypeEquals|  
|CheckId|CA2231|  
|Categoria|Microsoft.Usage|  
|Alteração Significativa|Não separáveis|  
  
## <a name="cause"></a>Causa  
 Um tipo de valor substitui <xref:System.Object.Equals%2A?displayProperty=fullName> mas não implementa o operador de igualdade.  
  
## <a name="rule-description"></a>Descrição da Regra  
 Na maioria das linguagens de programação, não há nenhuma implementação padrão do operador de igualdade (= =) para tipos de valor. Se a linguagem de programação oferece suporte a sobrecargas de operador, considere a possibilidade de implementar o operador de igualdade. Seu comportamento deve ser idêntico de <xref:System.Object.Equals%2A>.  
  
 Você não pode usar o operador de igualdade padrão em uma implementação sobrecarregada do operador de igualdade. Isso fará com que um estouro de pilha. Para implementar o operador de igualdade, use o método Object. Equals em sua implementação. Por exemplo:  
  
```vb  
If (Object.ReferenceEquals(left, Nothing)) Then  
    Return Object.ReferenceEquals(right, Nothing)  
Else  
    Return left.Equals(right)  
End If  
```  
  
```csharp  
if (Object.ReferenceEquals(left, null))   
    return Object.ReferenceEquals(right, null);  
return left.Equals(right);  
```  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Para corrigir uma violação desta regra, implementa o operador de igualdade.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 É seguro suprimir um aviso dessa regra; No entanto, é recomendável que você forneça o operador de igualdade se possível.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir define um tipo que violam essa regra.  
  
 [!code-csharp[FxCop.Usage.EqualsGetHashCode#1](../code-quality/codesnippet/CSharp/ca2231-overload-operator-equals-on-overriding-valuetype-equals_1.cs)]  
  
## <a name="related-rules"></a>Regras relacionadas  
 [CA1046: não sobrecarregar operador Equals em tipos de referência](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)  
  
 [CA2225: as sobrecargas do operador têm alternativos nomeados](../code-quality/ca2225-operator-overloads-have-named-alternates.md)  
  
 [CA2226: os operadores devem ter sobrecargas simétricas](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)  
  
 [CA2224: substituir Equals ao sobrecarregar o operador Equals](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)  
  
 [CA2218: substituir GetHashCode em igualdades de substituição](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Object.Equals%2A?displayProperty=fullName>