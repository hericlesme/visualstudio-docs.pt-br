---
title: 'CA2225: As sobrecargas de operador possuem alternativas nomeadas | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- OperatorOverloadsHaveNamedAlternates
- CA2225
helpviewer_keywords:
- OperatorOverloadsHaveNamedAlternates
- CA2225
ms.assetid: af8f7ab1-63ad-4861-afb9-b7a7a2be15e1
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 07d15e5ec123e645a7607f16b6020487d4c0fc2a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="ca2225-operator-overloads-have-named-alternates"></a>CA2225: as sobrecargas do operador têm alternativas nomeadas
|||  
|-|-|  
|NomeDoTipo|OperatorOverloadsHaveNamedAlternates|  
|CheckId|CA2225|  
|Categoria|Microsoft.Usage|  
|Alteração Significativa|Não separáveis|  
  
## <a name="cause"></a>Causa  
 Uma sobrecarga de operador foi detectada, e o método alternativo nomeado esperado não foi encontrado.  
  
## <a name="rule-description"></a>Descrição da Regra  
 Sobrecarga de operador permite o uso de símbolos para representar os cálculos para um tipo. Por exemplo, um tipo que sobrecarrega o símbolo de adição (+) para adição normalmente teria um membro alternativo denominado 'Add'. O membro alternativo nomeado fornece acesso para a mesma funcionalidade que o operador e é fornecido para os desenvolvedores que programa em idiomas que não dão suporte a operadores sobrecarregados.  
  
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
|<<|<<|<<|LeftShift|  
|<<=|<<=|<<=|LeftShift|  
|<|<|<|Comparar|  
|<=|<=|\<=|Comparar|  
|&&|N/D|&&|LogicalAnd|  
|&#124;&#124;|N/D|&#124;&#124;|LogicalOr|  
|!|N/D|!|LogicalNot|  
|%|Mod|%|Mod ou restante|  
|%=|N/D|%=|Mod|  
|* (binário)|*|*|Multiplicar|  
|*=|N/D|*=|Multiplicar|  
|~|Não|~|OnesComplement|  
|>>|>>|>>|RightShift|  
=|N/D|>>=|RightShift|  
|-(binário)|-(binário)|-(binário)|Subtração|  
|-=|N/D|-=|Subtração|  
|true|IsTrue|N/D|IsTrue (propriedade)|  
|-(unário)|N/D|-|Negar|  
|+ (unário)|N/D|+|adição|  
|false|IsFalse|False|IsTrue (propriedade)|  
  
 N/d = = não pode ser sobrecarregado no idioma selecionado.  
  
 A regra também verifica os operadores de conversão implícita e explícita em um tipo (`SomeType`) Verificando métodos chamados `ToSomeType` e `FromSomeType`.  
  
 No c#, quando um operador binário é sobrecarregado, o operador de atribuição correspondente, se houver, também é implicitamente sobrecarregado.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Para corrigir uma violação desta regra, implemente o método alternativo para o operador; o nome usando o nome alternativo recomendado.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 Não suprima um aviso de que essa regra se você estiver implementando uma biblioteca compartilhada. Aplicativos podem ignorar um aviso dessa regra.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir define uma estrutura que viola essa regra. Para corrigir o exemplo, adicione um público `Add(int x, int y)` método para a estrutura.  
  
 [!code-csharp[FxCop.Usage.OperatorOverloadsHaveNamedAlternates#1](../code-quality/codesnippet/CSharp/ca2225-operator-overloads-have-named-alternates_1.cs)]  
  
## <a name="related-rules"></a>Regras relacionadas  
 [CA1046: não sobrecarregar operador Equals em tipos de referência](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)  
  
 [CA2226: os operadores devem ter sobrecargas simétricas](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)  
  
 [CA2224: substituir Equals ao sobrecarregar o operador Equals](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)  
  
 [CA2218: substituir GetHashCode em igualdades de substituição](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)  
  
 [CA2231: sobrecarregar operador Equals ao substituir ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)