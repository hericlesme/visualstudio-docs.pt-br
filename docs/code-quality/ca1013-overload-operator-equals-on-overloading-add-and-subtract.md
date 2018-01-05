---
title: "CA1013: Sobrecarregar operador equals na sobrecarga de adição e subtração | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- OverrideOperatorEqualsOnOverridingAddAndSubtract
- OverrideOperatorEqualsOnOverloadingAddAndSubtract
- CA1013
- OverloadOperatorEqualsOnOverloadingAddAndSubtract
helpviewer_keywords:
- OverrideOperatorEqualsOnOverloadingAddAndSubtract
- OverrideOperatorEqualsOnOverridingAddAndSubtract
- CA1013
- OverloadOperatorEqualsOnOverloadingAddAndSubtract
ms.assetid: 5bd28d68-c179-49ff-af47-5250b8b18a10
caps.latest.revision: "22"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: d668760159af34e8f22a69bed41de185fa4254e4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ca1013-overload-operator-equals-on-overloading-add-and-subtract"></a>CA1013: sobrecarregar igualdades de operador em add e subtract de sobrecarga
|||  
|-|-|  
|NomeDoTipo|OverloadOperatorEqualsOnOverloadingAddAndSubtract|  
|CheckId|CA1013|  
|Categoria|Microsoft.Design|  
|Alteração Significativa|Não recentes|  
  
## <a name="cause"></a>Causa  
 Um tipo público ou protegido implementa os operadores de adição ou subtração sem implementar o operador de igualdade.  
  
## <a name="rule-description"></a>Descrição da Regra  
 Quando as instâncias de um tipo podem ser combinadas usando operações como adição e subtração, quase sempre você deve definir a igualdade para retornar `true` para quaisquer duas instâncias que têm os mesmos valores constituintes.  
  
 Você não pode usar o operador de igualdade padrão em uma implementação sobrecarregada do operador de igualdade. Isso fará com que um estouro de pilha. Para implementar o operador de igualdade, use o método Object. Equals em sua implementação. Consulte o exemplo a seguir.  
  
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
 Para corrigir uma violação desta regra, implementa o operador de igualdade para que ela seja matematicamente consistente com os operadores de adição e subtração.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 É seguro suprimir um aviso dessa regra quando a implementação padrão do operador de igualdade fornece o comportamento correto para o tipo.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir define um tipo (`BadAddableType`) que violam essa regra. Esse tipo deve implementar o operador de igualdade para tornar qualquer duas instâncias que têm os mesmos valores de campo de teste `true` para igualdade. O tipo `GoodAddableType` mostra a implementação corrigida. Observe que esse tipo também implementa o operador de desigualdade e substitui <xref:System.Object.Equals%2A> para atender a outras regras. Uma implementação completa também deve implementar <xref:System.Object.GetHashCode%2A>.  
  
 [!code-csharp[FxCop.Design.AddAndSubtract#1](../code-quality/codesnippet/CSharp/ca1013-overload-operator-equals-on-overloading-add-and-subtract_1.cs)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir testa a igualdade usando instâncias dos tipos que foram definidos anteriormente neste tópico para ilustrar o padrão e o comportamento correto para o operador de igualdade.  
  
 [!code-csharp[FxCop.Design.TestAddAndSubtract#1](../code-quality/codesnippet/CSharp/ca1013-overload-operator-equals-on-overloading-add-and-subtract_2.cs)]  
  
 Este exemplo gerencia a seguinte saída.  
  
 **Tipo incorreto: {2,2} {2,2} são iguais? Não**  
**Tipo BOM: {3,3} {3,3} são iguais? Sim**  
**Tipo BOM: {3,3} {3,3} são = =?   Sim**  
**Tipo incorreto: {2,2} {9,9} são iguais? Não**  
**Tipo BOM: {3,3} {9,9} são = =?   Não**   
## <a name="see-also"></a>Consulte também  
 [Operadores de igualdade](/dotnet/standard/design-guidelines/equality-operators)