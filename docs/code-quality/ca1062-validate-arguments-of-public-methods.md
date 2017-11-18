---
title: "CA1062: Validar argumentos de métodos públicos | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1062
- ValidateArgumentsOfPublicMethods
- Validate arguments of public methods
helpviewer_keywords:
- CA1062
- ValidateArgumentsOfPublicMethods
ms.assetid: db1f69ca-68f7-477e-94f3-d135cc5dfcbc
caps.latest.revision: "27"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8f225159e551dac2327c35774db846eec4ccc6fc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="ca1062-validate-arguments-of-public-methods"></a>CA1062: validar argumentos de métodos públicos
|||  
|-|-|  
|NomeDoTipo|ValidateArgumentsOfPublicMethods|  
|CheckId|CA1062|  
|Categoria|Microsoft.Design|  
|Alteração Significativa|Não separáveis|  
  
## <a name="cause"></a>Causa  
 Um método externamente visível cancela a referência de um de seus argumentos de referência sem verificar se esse argumento é `null` (`Nothing` no Visual Basic).  
  
## <a name="rule-description"></a>Descrição da Regra  
 Todos os argumentos de referência que são passados para métodos externamente visíveis devem ser verificados em relação a `null`. Se apropriado, lance uma <xref:System.ArgumentNullException> quando o argumento é `null`.  
  
 Se um método pode ser chamado de um assembly desconhecido porque está declarado como público ou protegido, você deve validar todos os parâmetros do método. Se o método é projetado para ser chamado somente por assemblies conhecidos, você deve tornar o método interno e aplicar o <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> de atributo para o assembly que contém o método.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Para corrigir uma violação desta regra, validar cada argumento de referência em `null`.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 Se você tiver certeza de que o parâmetro desreferenciado foi validado por outra chamada do método na função, você pode suprimir um aviso dessa regra.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra um método que viola a regra e um método que satisfaz a regra.  
  
 ```csharp
 using System;

namespace DesignLibrary
{
    public class Test
    {
        // This method violates the rule.
        public void DoNotValidate(string input)
        {
            if (input.Length != 0)
            {
                Console.WriteLine(input);
            }
        }

        // This method satisfies the rule.
        public void Validate(string input)
        {
            if (input == null)
            {
                throw new ArgumentNullException("input");
            }
            if (input.Length != 0)
            {
                Console.WriteLine(input);
            }
        }
    }
}
```

```vb
Imports System

Namespace DesignLibrary

    Public Class Test

        ' This method violates the rule.
        Sub DoNotValidate(ByVal input As String)

            If input.Length <> 0 Then
                Console.WriteLine(input)
            End If

        End Sub

        ' This method satisfies the rule.
        Sub Validate(ByVal input As String)

            If input Is Nothing Then
                Throw New ArgumentNullException("input")
            End If

            If input.Length <> 0 Then
                Console.WriteLine(input)
            End If

        End Sub

    End Class

End Namespace
```
  
## <a name="example"></a>Exemplo  
 Em [!INCLUDE[vsprvslong](../code-quality/includes/vsprvslong_md.md)], essa regra não detecta que os parâmetros estão sendo passados para outro método que realiza a validação.  

```csharp
public string Method(string value)
{
    EnsureNotNull(value);

    // Fires incorrectly    
    return value.ToString();
}

private void EnsureNotNull(string value)
{
    if (value == null)
        throw new ArgumentNullException("value");
}
```

```vb
Public Function Method(ByVal value As String) As String
    EnsureNotNull(value)

    ' Fires incorrectly    
    Return value.ToString()
End Function

Private Sub EnsureNotNull(ByVal value As String)
    If value Is Nothing Then
        Throw (New ArgumentNullException("value"))
    End If
End Sub
```

## <a name="example"></a>Exemplo  
 Construtores de cópia que preencher o campo ou propriedades que são objetos de referência também podem violar a regra de CA1062. A violação ocorre porque o objeto copiado que é passado para o construtor de cópia pode ser `null` (`Nothing` no Visual Basic). Para resolver a violação, use um método estático (compartilhado no Visual Basic) para verificar se o objeto copiado não é nulo.  
  
 A seguir `Person` exemplo de classe, o `other` objeto que é passado para o `Person` construtor de cópia pode ser `null`.  
  
```csharp  
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
 No exemplo a seguir revisado `Person` exemplo, o `other` objeto que é passado para o construtor de cópia é verificado para null no `PassThroughNonNull` método.  
  
```csharp  
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