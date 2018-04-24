---
title: 'CA2226: os operadores devem ter sobrecargas simétricas'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- OperatorsShouldHaveSymmetricalOverloads
- CA2226
helpviewer_keywords:
- OperatorsShouldHaveSymmetricalOverloads
- CA2226
ms.assetid: d202401a-ea14-4559-b15e-0ea4f5b68789
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 98f5653d326c257e46becd2d7f8ad1091dfcf0c7
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/19/2018
---
# <a name="ca2226-operators-should-have-symmetrical-overloads"></a>CA2226: os operadores devem ter sobrecargas simétricas
|||
|-|-|
|NomeDoTipo|OperatorsShouldHaveSymmetricalOverloads|
|CheckId|CA2226|
|Categoria|Microsoft.Usage|
|Alteração Significativa|Não separáveis|

## <a name="cause"></a>Causa
 Um tipo implementa o operador de igualdade ou de desigualdade e não implementa o operador oposto.

## <a name="rule-description"></a>Descrição da Regra
 Não há nenhuma circunstância onde igualdade ou desigualdade é aplicável a instâncias de um tipo, e o operador oposto é indefinido. Tipos geralmente implementam o operador de desigualdade, retornando o valor negado do operador de igualdade.

 O compilador c# emite um erro para violações desta regra.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação desta regra, implementar a igualdade e operadores de desigualdade ou remova o que está presente.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra. O tipo não funcionará de forma consistente com o [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].

## <a name="related-rules"></a>Regras relacionadas
 [CA1046: não sobrecarregar operador Equals em tipos de referência](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

 [CA2225: as sobrecargas do operador têm alternativos nomeados](../code-quality/ca2225-operator-overloads-have-named-alternates.md)

 [CA2224: substituir Equals ao sobrecarregar o operador Equals](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)

 [CA2218: substituir GetHashCode em igualdades de substituição](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

 [CA2231: sobrecarregar operador Equals ao substituir ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)