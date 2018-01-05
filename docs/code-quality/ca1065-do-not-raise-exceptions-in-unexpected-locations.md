---
title: "CA1065: Não acione exceções em locais inesperados | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1065
- DoNotRaiseExceptionsInUnexpectedLocations
helpviewer_keywords:
- DoNotRaiseExceptionsInUnexpectedLocations
- CA1065
ms.assetid: 4e1bade4-4ca2-4219-abc3-c7b2d741e157
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 6d34a92c1e71df0c355a9c8a3b5290146dce7240
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ca1065-do-not-raise-exceptions-in-unexpected-locations"></a>CA1065: não acione exceções em locais inesperados
|||  
|-|-|  
|NomeDoTipo|DoNotRaiseExceptionsInUnexpectedLocations|  
|CheckId|CA1065|  
|Categoria|Microsoft.Design|  
|Alteração Significativa|Não separáveis|  
  
## <a name="cause"></a>Causa  
 Um método que não deve acionar exceções aciona uma exceção.  
  
## <a name="rule-description"></a>Descrição da Regra  
 Métodos que não deverão gerar exceções podem ser categorizados da seguinte maneira:  
  
-   Métodos Get de propriedade  
  
-   Métodos de acessador de evento  
  
-   Métodos Equals  
  
-   Métodos de GetHashCode  
  
-   Métodos ToString  
  
-   Construtores estáticos  
  
-   Finalizadores  
  
-   Descartar métodos  
  
-   Operadores de igualdade  
  
-   Operadores de conversão implícita  
  
 As seções a seguir discutem esses tipos de método.  
  
### <a name="property-get-methods"></a>Métodos Get de propriedade  
 Propriedades são campos basicamente inteligentes. Portanto, eles devem se comportar como um campo tanto quanto possível. Campos não emitem exceções e não deve propriedades. Se você tiver uma propriedade que gera uma exceção, considere tornando um método.  
  
 As exceções a seguir têm permissão para ser gerada de um método get da propriedade:  
  
-   <xref:System.InvalidOperationException?displayProperty=fullName>e todos os derivados (incluindo <xref:System.ObjectDisposedException?displayProperty=fullName>)  
  
-   <xref:System.NotSupportedException?displayProperty=fullName>e todos os derivados  
  
-   <xref:System.ArgumentException?displayProperty=fullName>(somente de indexada get)  
  
-   <xref:System.Collections.Generic.KeyNotFoundException>(somente de indexada get)  
  
### <a name="event-accessor-methods"></a>Métodos de acessador de evento  
 Acessadores de evento devem ser operações simples que não lançam exceções. Um evento não deve lançar uma exceção ao tentar adicionar ou remover um manipulador de eventos.  
  
 As exceções a seguir têm permissão para ser gerada de um evento accesor:  
  
-   <xref:System.InvalidOperationException?displayProperty=fullName>e todos os derivados (incluindo <xref:System.ObjectDisposedException?displayProperty=fullName>)  
  
-   <xref:System.NotSupportedException?displayProperty=fullName>e todos os derivados  
  
-   <xref:System.ArgumentException>e derivados  
  
### <a name="equals-methods"></a>Métodos Equals  
 O seguinte **é igual a** métodos não deverão gerar exceções:  
  
-   <xref:System.Object.Equals%2A?displayProperty=fullName>  
  
-   [M:IEquatable.Equals](http://go.microsoft.com/fwlink/?LinkId=113472)  
  
 Um **é igual a** método deve retornar `true` ou `false` em vez de gerar uma exceção. Por exemplo, se for igual a é passado a dois tipos incompatíveis ele apenas retornarão `false` em vez de gerar um <xref:System.ArgumentException>.  
  
### <a name="gethashcode-methods"></a>Métodos de GetHashCode  
 O seguinte **GetHashCode** métodos geralmente não deverão gerar exceções:  
  
-   <xref:System.Object.GetHashCode%2A>  
  
-   [M:IEqualityComparer.GetHashCode(T)](http://go.microsoft.com/fwlink/?LinkId=113477)  
  
 **GetHashCode** sempre deve retornar um valor. Caso contrário, você poderá perder itens na tabela de hash.  
  
 As versões do **GetHashCode** que usam um argumento pode lançar um <xref:System.ArgumentException>. No entanto, **Object. GetHashCode** nunca deve lançar uma exceção.  
  
### <a name="tostring-methods"></a>Métodos ToString  
 O depurador usa <xref:System.Object.ToString%2A?displayProperty=fullName> para ajudar a exibir informações sobre objetos em formato de cadeia de caracteres. Portanto, **ToString** não deve alterar o estado de um objeto e ele não deve lançar exceções.  
  
### <a name="static-constructors"></a>Construtores estáticos  
 Lançar exceções a partir de um construtor estático faz com que o tipo a ser inutilizável no domínio do aplicativo atual. Você deve ter um bom motivo (por exemplo, um problema de segurança) para gerar uma exceção de um construtor estático.  
  
### <a name="finalizers"></a>Finalizadores  
 Gerar uma exceção de um finalizador faz com que o CLR falha rápida, que destrói o processo. Portanto, lançando exceções em um finalizador deve sempre ser evitada.  
  
### <a name="dispose-methods"></a>Descartar métodos  
 Um <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> método não deve lançar uma exceção. Dispose é geralmente chamado como parte de limpar lógica em um `finally` cláusula. Portanto, explicitamente lançar uma exceção de Dispose força o usuário adicione dentro de manipulação de exceção de `finally` cláusula.  
  
 O **Dispose (False)** caminho de código nunca deve lançar exceções, pois quase sempre, isso é chamado de um finalizador.  
  
### <a name="equality-operators--"></a>Operadores de igualdade (= =,! =)  
 Assim como os métodos Equals, operadores de igualdade devem retornar `true` ou `false` e não deverão gerar exceções.  
  
### <a name="implicit-cast-operators"></a>Operadores de conversão implícita  
 Porque o usuário é geralmente não sabem que um operador de conversão implícita foi chamado, uma exceção lançada pelo operador de conversão implícita é completamente inesperada. Portanto, nenhuma exceção deverá ser lançada de operadores de conversão implícita.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Para getters de propriedade, a alterar a lógica para que ele não deve lançar uma exceção, ou alterar a propriedade em um método.  
  
 Para todos os outros tipos de método listados anteriormente, altere a lógica para que ele não deve lançar uma exceção.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 É seguro suprimir um aviso de que essa regra se a violação foi causada por uma declaração de exceção em vez de uma exceção lançada.  
  
## <a name="related-rules"></a>Regras relacionadas  
 [CA2219: não acionar exceções em cláusulas de exceção](../code-quality/ca2219-do-not-raise-exceptions-in-exception-clauses.md)  
  
## <a name="see-also"></a>Consulte também  
 [Avisos de design](../code-quality/design-warnings.md)