---
title: 'CA1700: Não nomeie valores de enumeração &#39;reservado&#39;'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1700
- DoNotNameEnumValuesReserved
helpviewer_keywords:
- DoNotNameEnumValuesReserved
- CA1700
ms.assetid: 7a7e01c3-ae7d-4c82-a646-91b58864a749
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8d2e7b501019ed2891a30d1f0359aee6405c4444
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31918443"
---
# <a name="ca1700-do-not-name-enum-values-39reserved39"></a>CA1700: Não nomeie valores de enumeração &#39;reservado&#39;
|||
|-|-|
|NomeDoTipo|DoNotNameEnumValuesReserved|
|CheckId|CA1700|
|Categoria|Microsoft.Naming|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 O nome de um membro de enumeração contém a palavra "reservados".

## <a name="rule-description"></a>Descrição da Regra
 Esta regra pressupõe que um membro da enumeração que tenha um nome que contém "reserved" não é usado atualmente, mas é um espaço reservado a ser renomeado ou removido em uma versão futura. Renomear ou remover um membro é uma alteração drástica. Você não deve esperar os usuários ignorem um membro apenas porque seu nome contém "reservados", nem você pode confiar em usuários para ler ou obedecer a documentação. Além disso, como membros reservados aparecem em pesquisadores de objetos e ambientes de desenvolvimento integrado inteligentes, eles podem causar confusão sobre quais membros estão sendo realmente usados.

 Em vez de usar um membro reservado, adicione um novo membro de enumeração na versão futura. Na maioria dos casos a adição do novo membro não é uma alteração significativa, como a adição não faz com que os valores dos membros originais para alterar.

 Em um número limitado de casos a adição de um membro é uma alteração significativa, mesmo quando os membros originais mantém seus valores originais. Basicamente, o novo membro não pode ser retornado de caminhos de código existente sem quebrar os chamadores que usam um `switch` (`Select` em [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) instrução no valor de retorno que abrange a lista inteira de membro e que gerará uma exceção do caso padrão. Uma preocupação secundária é que o código do cliente pode não tratar a alteração no comportamento dos métodos de reflexão como <xref:System.Enum.IsDefined%2A?displayProperty=fullName>. Da mesma forma, se o novo membro deve ser retornado de métodos existentes ou uma incompatibilidade de aplicativos conhecidos ocorre devido ao uso de reflexão ruim, a única solução incondicional é:

1.  Adicione uma nova enumeração que contém os membros originais e novos.

2.  Marque a enumeração original com o <xref:System.ObsoleteAttribute?displayProperty=fullName> atributo.

 Siga o mesmo procedimento para qualquer tipos visíveis externamente ou membros que expõem a enumeração original.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação desta regra, remova ou renomeie o membro.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 É seguro suprimir um aviso dessa regra para um membro que é usado no momento ou para bibliotecas tiveram enviado anteriormente.

## <a name="related-rules"></a>Regras relacionadas
 [CA2217: não marcar enums com FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

 [CA1712: não usar valores de enum como prefixo com o nome do tipo](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)

 [CA1028: o armazenamento de enum deve ser Int32](../code-quality/ca1028-enum-storage-should-be-int32.md)

 [CA1008: as enums devem ter valor zero](../code-quality/ca1008-enums-should-have-zero-value.md)

 [CA1027: marcar enums com FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)