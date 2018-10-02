---
title: 'CA1062: Validar argumentos de métodos públicos | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1062
- ValidateArgumentsOfPublicMethods
- Validate arguments of public methods
helpviewer_keywords:
- CA1062
- ValidateArgumentsOfPublicMethods
ms.assetid: db1f69ca-68f7-477e-94f3-d135cc5dfcbc
caps.latest.revision: 29
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 8fd4534c333dfe31801d13a99b6ee7b3f0c25e33
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47587344"
---
# <a name="ca1062-validate-arguments-of-public-methods"></a>CA1062: validar argumentos de métodos públicos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [CA1062: validar argumentos de métodos públicos](https://docs.microsoft.com/visualstudio/code-quality/ca1062-validate-arguments-of-public-methods).

|||
|-|-|
|NomeDoTipo|ValidateArgumentsOfPublicMethods|
|CheckId|CA1062|
|Categoria|Microsoft.Design|
|Alteração Significativa|Não separável|

## <a name="cause"></a>Causa
 Um método visível externamente desreferencia um de seus argumentos de referência sem verificar se esse argumento é `null` (`Nothing` no Visual Basic).

## <a name="rule-description"></a>Descrição da Regra
 Todos os argumentos de referência que são passados para métodos externamente visíveis devem ser verificados em relação a `null`. Se apropriado, lance uma <xref:System.ArgumentNullException> quando o argumento é `null`.

 Se um método pode ser chamado de um assembly desconhecido porque está declarado como público ou protegido, você deve validar todos os parâmetros do método. Se o método foi projetado para ser chamado apenas por assemblies conhecidos, você deve tornar o método interno e aplicar o <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atributo ao assembly que contém o método.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, validar cada argumento de referência em relação a `null`.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Se você tiver certeza de que o parâmetro deferência foi validado por outra chamada de método na função, você pode suprimir um aviso nessa regra.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra um método que viola a regra e um método que satisfaz a regra.

 [!code-csharp[FxCop.Design.ValidateArguments#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/cs/fxcop.design.validatearguments.copyctors.cs#1)]
 [!code-csharp[FxCop.Design.ValidateArguments#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/cs/FxCop.Design.ValidateArguments.cs#1)]
 [!code-vb[FxCop.Design.ValidateArguments#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/vb/FxCop.Design.ValidateArguments.vb#1)]

## <a name="example"></a>Exemplo
 No [!INCLUDE[vsprvslong](../includes/vsprvslong-md.md)], essa regra não detecta que os parâmetros estão sendo passados para outro método que faz a validação.

 [!code-csharp[FxCop.Design.ValidateArguments#2](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/cs/fxcop.design.validatearguments.copyctors.cs#2)]
 [!code-csharp[FxCop.Design.ValidateArguments#2](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/cs/FxCop.Design.ValidateArguments.cs#2)]
 [!code-vb[FxCop.Design.ValidateArguments#2](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/vb/FxCop.Design.ValidateArguments.vb#2)]

## <a name="example"></a>Exemplo
 Construtores de cópia que preencher campos ou propriedades que são objetos de referência também podem violar a regra de CA1062. A violação ocorre porque o objeto copiado que é passado para o construtor de cópia pode ser `null` (`Nothing` no Visual Basic). Para resolver a violação, use um método estático (compartilhado no Visual Basic) para verificar se o objeto copiado não é nulo.

 A seguir `Person` exemplo de classe, o `other` objeto é passado para o `Person` construtor de cópia pode ser `null`.

```

public class Person
{
    public string Name { get; private set; }
    public int Age { get; private set; }

    public Person(string name, int age)
    {
        Name = name;
        Age = age;
    }

    // Copy constructor CA1062 fires because other is dereferenced
    // without being checked for null
    public Person(Person other)
        : this(other.Name, other.Age)
    {
    }
}

```

## <a name="example"></a>Exemplo
 A seguir revisado `Person` exemplo, o `other` objeto é passado para o construtor de cópia primeiro é verificado para null no `PassThroughNonNull` método.

```
public class Person
{
    public string Name { get; private set; }
    public int Age { get; private set; }

    public Person(string name, int age)
    {
        Name = name;
        Age = age;
    }

    // Copy constructor
    public Person(Person other)
        : this(PassThroughNonNull(other).Name,
          PassThroughNonNull(other).Age)
    {
    }

    // Null check method
    private static Person PassThroughNonNull(Person person)
    {
        if (person == null)
            throw new ArgumentNullException("person");
        return person;
    }
}

```



