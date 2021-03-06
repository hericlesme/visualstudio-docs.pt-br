---
title: 'CA2225: as sobrecargas do operador têm alternativas nomeadas'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- OperatorOverloadsHaveNamedAlternates
- CA2225
helpviewer_keywords:
- OperatorOverloadsHaveNamedAlternates
- CA2225
ms.assetid: af8f7ab1-63ad-4861-afb9-b7a7a2be15e1
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 83dc61c31d2951d230c04fb52d7d1e6ffd932a03
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45550301"
---
# <a name="ca2225-operator-overloads-have-named-alternates"></a>CA2225: as sobrecargas do operador têm alternativas nomeadas
|||
|-|-|
|NomeDoTipo|OperatorOverloadsHaveNamedAlternates|
|CheckId|CA2225|
|Categoria|Microsoft.Usage|
|Alteração Significativa|Não separável|

## <a name="cause"></a>Causa
 Uma sobrecarga de operador foi detectada, e o método alternativo nomeado esperado não foi encontrado.

## <a name="rule-description"></a>Descrição da regra
 Sobrecarga de operador permite o uso de símbolos para representar os cálculos para um tipo. Por exemplo, um tipo que sobrecarrega o símbolo de adição (+) para adição normalmente teria um membro alternativo nomeado 'Adicionar'. O membro alternativo nomeado fornece acesso para a mesma funcionalidade que o operador e é fornecido para os desenvolvedores que programem em linguagens que não dão suporte a operadores sobrecarregados.

 Esta regra examina os operadores listados na tabela a seguir.

|C#|Visual Basic|C++|Nome alternativo|
|---------|------------------|-----------|--------------------|
|+ (binário)|+|+ (binário)|Adicionar|
|+=|+=|+=|Adicionar|
|&|And|&|BitwiseAnd|
|&=|E =|&=|BitwiseAnd|
|&#124;|Ou|&#124;|BitwiseOr|
|&#124;=|Ou =|&#124;=|BitwiseOr|
|--|N/D|--|Decremento|
|/|/|/|Divisão|
|/=|/=|/=|Divisão|
|==|=|==|Igual a|
|^|Xor|^|Xor|
|^=|XOR =|^=|Xor|
|>|>|>|Comparar|
|>=|>=|>=|Comparar|
|++|N/D|++|Incremento|
|<>|!=|Igual a|
|<<|<<|<<|SHIFT esquerda|
|<<=|<<=|<<=|SHIFT esquerda|
|<|<|<|Comparar|
|<=|<=|\<=|Comparar|
|&&|N/D|&&|LogicalAnd|
|&#124;&#124;|N/D|&#124;&#124;|LogicalOr|
|!|N/D|!|LogicalNot|
|%|Mod|%|Mod ou restante|
|%=|N/D|%=|Mod|
|* (binário)|*|*|Multiplicar|
|*=|N/D|*=|Multiplicar|
|~|não|~|OnesComplement|
|>>|>>|>>|SHIFT direita|
=|N/D|>>=|SHIFT direita|
|-(binário)|-(binário)|-(binário)|Subtração|
|-=|N/D|-=|Subtração|
|true|IsTrue|N/D|IsTrue (propriedade)|
|-(unário)|N/D|-|Negar|
|+ (unário)|N/D|+|sinal de adição|
|false|IsFalse|False|IsTrue (propriedade)|

 N/d = = não pode ser sobrecarregado no idioma selecionado.

 A regra também verifica se há operadores de conversão explícita e implícita em um tipo (`SomeType`) através da verificação de métodos chamados `ToSomeType` e `FromSomeType`.

 No c#, quando um operador binário está sobrecarregado, o operador de atribuição correspondente, se houver, também estará implicitamente sobrecarregado.

## <a name="how-to-fix-violations"></a>Como corrigir violações
 Para corrigir uma violação dessa regra, implemente o método alternativo para o operador; Nomeie-o usando o nome alternativo recomendado.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
 Não suprima um aviso nessa regra, se você estiver implementando uma biblioteca compartilhada. Aplicativos podem ignorar um aviso nessa regra.

## <a name="example"></a>Exemplo
 O exemplo a seguir define uma estrutura que viola essa regra. Para corrigir o exemplo, adicione um público `Add(int x, int y)` método à estrutura.

 [!code-csharp[FxCop.Usage.OperatorOverloadsHaveNamedAlternates#1](../code-quality/codesnippet/CSharp/ca2225-operator-overloads-have-named-alternates_1.cs)]

## <a name="related-rules"></a>Regras relacionadas
 [CA1046: não sobrecarregar operador Equals em tipos de referência](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

 [CA2226: os operadores devem ter sobrecargas simétricas](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

 [CA2224: substituir Equals ao sobrecarregar o operador Equals](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)

 [CA2218: substituir GetHashCode em igualdades de substituição](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

 [CA2231: sobrecarregar operador Equals ao substituir ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)