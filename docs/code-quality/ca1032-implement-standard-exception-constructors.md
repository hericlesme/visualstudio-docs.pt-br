---
title: 'CA1032: implementar construtores de exceção padrão'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1032
- ImplementStandardExceptionConstructors
helpviewer_keywords:
- CA1032
- ImplementStandardExceptionConstructors
ms.assetid: a8623c56-273a-4c95-8d83-95911a042be7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 014dd8d7afcdfefd365637aba297524d7b9480ff
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="ca1032-implement-standard-exception-constructors"></a>CA1032: implementar construtores de exceção padrão
|||
|-|-|
|NomeDoTipo|ImplementStandardExceptionConstructors|
|CheckId|CA1032|
|Categoria|Microsoft.Design|
|Alteração Significativa|Não recentes|

## <a name="cause"></a>Causa
 Estende um tipo <xref:System.Exception?displayProperty=fullName> e não declarar todos os construtores.

## <a name="rule-description"></a>Descrição da Regra
 Tipos de exceção devem implementar construtores a seguir:

-   NewException() pública

-   NewException(string) pública

-   público NewException (cadeia de caracteres, exceção)

-   NewException protegida ou privada (SerializationInfo, StreamingContext)

 Deixar de fornecer o conjunto completo de construtores pode dificultar o tratamento correto das exceções. Por exemplo, o construtor que tem a assinatura `NewException(string, Exception)` é usado para criar exceções causadas por outras exceções. Sem esse construtor não é possível criar e lançar uma instância de sua exceção personalizada que contém a exceção interna (aninhada), que é o código gerenciado deve fazer nesta situação. Os construtores de três exceção primeiro são públicos por convenção. O quarto construtor é protegido em classes não lacradas e privado em classes lacradas. Para obter mais informações, consulte [CA2229: implementar construtores de serialização](../code-quality/ca2229-implement-serialization-constructors.md)

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação desta regra, adicione os construtores ausentes para a exceção e certifique-se de que eles tenham acessibilidade correta.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 É seguro suprimir um aviso dessa regra quando a violação é causada pelo uso de um nível de acesso diferentes para os construtores públicos.

## <a name="example"></a>Exemplo
 O exemplo a seguir contém um tipo de exceção que violam essa regra e um tipo de exceção que é implementado corretamente.

 [!code-csharp[FxCop.Design.ExceptionMultipleCtors#1](../code-quality/codesnippet/CSharp/ca1032-implement-standard-exception-constructors_1.cs)]