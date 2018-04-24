---
title: 'CA2105: os campos da matriz não devem ser somente leitura'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2105
- ArrayFieldsShouldNotBeReadOnly
helpviewer_keywords:
- ArrayFieldsShouldNotBeReadOnly
- CA2105
ms.assetid: 0bdc3421-3ceb-4182-b30c-a992fbfcc35d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 57b652247ea727c59a9e0d0d0c6850039be52634
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/19/2018
---
# <a name="ca2105-array-fields-should-not-be-read-only"></a>CA2105: os campos da matriz não devem ser somente leitura
|||
|-|-|
|NomeDoTipo|ArrayFieldsShouldNotBeReadOnly|
|CheckId|CA2105|
|Categoria|Microsoft.Security|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Um campo público ou protegido que contém uma matriz é declarado como somente leitura.

## <a name="rule-description"></a>Descrição da Regra
 Quando você aplica o `readonly` (`ReadOnly` em [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) modificador para um campo que contém uma matriz, o campo não pode ser alterado para fazer referência a uma matriz diferente. No entanto, os elementos da matriz que são armazenados em um campo somente leitura podem ser alterados. Código que toma decisões ou realize operações com base nos elementos de uma matriz de somente leitura que podem ser acessados publicamente pode conter uma vulnerabilidade de segurança explorável.

 Observe que ter um campo público também viola a regra de criação [CA1051: não declarar campos de instância visíveis](../code-quality/ca1051-do-not-declare-visible-instance-fields.md).

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir a vulnerabilidade de segurança que é identificada por essa regra, não confie no conteúdo de uma matriz de somente leitura que podem ser acessados publicamente. É altamente recomendável que você use um dos procedimentos a seguir:

-   Substitua a matriz com uma coleção fortemente tipada que não pode ser alterada. Para obter mais informações, consulte <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>.

-   Substitua o campo público com um método que retorna um clone de uma matriz privada. Como o seu código não se baseia no clone, não há nenhum risco se os elementos são modificados.

 Se você escolher a segunda abordagem, não substitua o campo com uma propriedade; propriedades que retornam matrizes negativamente afetam o desempenho. Para obter mais informações, consulte [CA1819: propriedades não devem retornar matrizes](../code-quality/ca1819-properties-should-not-return-arrays.md).

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Exclusão de um aviso de que essa regra é altamente desaconselhável. Quase não há situações ocorrer onde o conteúdo de um campo somente leitura não é importante. Se esse for o caso com seu cenário, remova o `readonly` modificador em vez de excluir a mensagem.

## <a name="example"></a>Exemplo
 Este exemplo demonstra os perigos de violam essa regra. A primeira parte mostra uma biblioteca de exemplo que tem um tipo `MyClassWithReadOnlyArrayField`, que contém dois campos (`grades` e `privateGrades`) que não são seguras. O campo `grades` é público e, portanto, vulnerável a qualquer chamador. O campo `privateGrades` for privado, mas ainda estará vulnerável porque ele é retornado para chamadores pelo `GetPrivateGrades` método. O `securePrivateGrades` campo é exposto de maneira segura, o `GetSecurePrivateGrades` método. Ele é declarado como privado, seguir práticas recomendadas de um bom design. A segunda parte mostra código que altera os valores armazenados na `grades` e `privateGrades` membros.

 A biblioteca de classes de exemplo é exibido no exemplo a seguir.

 [!code-csharp[FxCop.Security.ArrayFieldsNotReadOnly#1](../code-quality/codesnippet/CSharp/ca2105-array-fields-should-not-be-read-only_1.cs)]

## <a name="example"></a>Exemplo
 O código a seguir usa a biblioteca de classes de exemplo para ilustrar os problemas de segurança de matriz de somente leitura.

 [!code-csharp[FxCop.Security.TestArrayFieldsRead#1](../code-quality/codesnippet/CSharp/ca2105-array-fields-should-not-be-read-only_2.cs)]

 A saída deste exemplo é:

 **Antes da violação: notas: 90, 90, 90 notas de particular: 90, 90, 90 seguro notas, 90, 90, 90**
**depois de violações: notas: 90, 555, 90 notas de privada: 90, 555, 90 seguro notas, 90, 90, 90**
## <a name="see-also"></a>Consulte também
 <xref:System.Array?displayProperty=fullName> <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>