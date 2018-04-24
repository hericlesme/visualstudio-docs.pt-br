---
title: 'CA1008: os enums devem ter valor zero'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1008
- EnumsShouldHaveZeroValue
helpviewer_keywords:
- CA1008
- EnumsShouldHaveZeroValue
ms.assetid: 3503a73c-360c-416d-8ee4-c2aa44365a05
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4109bf7b455c7a77daa5b9d31b6fe1286cf69c77
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/19/2018
---
# <a name="ca1008-enums-should-have-zero-value"></a>CA1008: os enums devem ter valor zero
|||
|-|-|
|NomeDoTipo|EnumsShouldHaveZeroValue|
|CheckId|CA1008|
|Categoria|Microsoft.Design|
|Alteração Significativa|Separação de não - quando você for solicitado a adicionar um **nenhum** valor para uma enumeração de sinalizador não. Quebrando - quando você for solicitado a renomear ou remover quaisquer valores de enumeração.|

## <a name="cause"></a>Causa
 Uma enumeração sem um aplicado <xref:System.FlagsAttribute?displayProperty=fullName> não definir um membro que tem um valor de zero; ou uma enumeração que tem um aplicado <xref:System.FlagsAttribute> define um membro que tem um valor de zero, mas seu nome não é 'None' ou a enumeração define vários com valor zero membros.

## <a name="rule-description"></a>Descrição da Regra
 Uma enumeração não inicializado, assim como outros tipos de valor, o valor padrão é zero. Uma enumeração de sinalizadores não atribuído deve definir um membro que tem o valor de zero para que o valor padrão é um valor válido da enumeração. Se apropriado, nome do membro 'None'. Caso contrário, atribua zero para o membro usado com mais frequência. Observe que, por padrão, se o valor do primeiro membro de enumeração não está definido na declaração, seu valor é zero.

 Se uma enumeração que tem o <xref:System.FlagsAttribute> aplicado define um membro com valor de zero, o nome deve ser 'None' para indicar que não há valores foram definidos na enumeração. Usando um membro com valor de zero para qualquer outra finalidade é contrária a ela o uso do <xref:System.FlagsAttribute> em que a e e ou operadores bit a bit são inúteis com o membro. Isso significa que somente um membro deve ser atribuído o valor zero. Observe que, se vários membros que têm o valor zero ocorre em uma enumeração de sinalizadores atribuído `Enum.ToString()` retorna resultados incorretos para os membros que não são zero.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação desta regra para enumerações sinalizadores não atribuído, definir um membro que tem o valor de zero. Essa é uma alteração de incondicional. Para enumerações atribuído sinalizadores que definem um membro com valor de zero, chamar esse membro de 'Nenhum' e excluir outros membros que têm um valor de zero. Isso é uma alteração significativa.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso dessa regra, exceto enumerações atribuído sinalizadores fornecidos anteriormente.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra duas enumerações que atendem à regra e uma enumeração `BadTraceOptions`, que viola a regra.

 [!code-cpp[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/CPP/ca1008-enums-should-have-zero-value_1.cpp)]
 [!code-csharp[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/CSharp/ca1008-enums-should-have-zero-value_1.cs)]
 [!code-vb[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/VisualBasic/ca1008-enums-should-have-zero-value_1.vb)]

## <a name="related-rules"></a>Regras relacionadas
 [CA2217: não marcar enums com FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

 [CA1700: não nomear valores de enum como 'Reservados'](../code-quality/ca1700-do-not-name-enum-values-reserved.md)

 [CA1712: não usar valores de enum como prefixo com o nome do tipo](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)

 [CA1028: o armazenamento de enum deve ser Int32](../code-quality/ca1028-enum-storage-should-be-int32.md)

 [CA1027: marcar enums com FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Consulte também
 <xref:System.Enum?displayProperty=fullName>