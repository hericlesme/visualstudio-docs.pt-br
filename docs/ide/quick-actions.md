---
title: "Ações Rápidas | Microsoft Docs"
ms.custom: 
ms.date: 11/30/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
dev_langs:
- CSharp
- VB
ms.workload: multiple
ms.openlocfilehash: 7e70e4366ca91e00beeb4fff49ec30d4618bde81
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/05/2018
---
# <a name="quick-actions"></a>Ações Rápidas

As [Ações Rápidas](refactoring-code-generation-quick-actions.md#quick-actions) permitem refatorar, gerar ou, de outro modo, modificar o código de maneira fácil com uma única ação. As Ações Rápidas estão disponíveis para C#, [C++](/cpp/ide/writing-and-refactoring-code-cpp) e os arquivos de código do Visual Basic. Algumas ações são específicas para uma linguagem e outras se aplicam a todas as linguagens. As Ações Rápidas podem ser aplicadas usando o ícone de Lâmpada ![Ícone de lâmpada pequeno](media/vs2015_lightbulbsmall.png "VS2017_LightBulbSmall") ou pressionando **Ctrl** + **.** quando o cursor estiver sobre a linha de código apropriada.

Você verá uma lâmpada se houver um rabisco vermelho e o Visual Studio tiver uma sugestão para corrigir o problema. Por exemplo se você tiver um erro indicado por um rabisco vermelho, uma lâmpada aparecerá quando correções estiverem disponíveis para esse erro. Para qualquer idioma, terceiros podem oferecer diagnóstico e sugestões personalizados, por exemplo, como parte de um SDK, e as lâmpadas do Visual Studio serão acesas de acordo com essas regras.

## <a name="to-see-a-light-bulb"></a>Para ver uma lâmpada

1. Em muitos casos, as lâmpadas aparecem espontaneamente ao focalizar o mouse no ponto de um erro ou na margem esquerda do editor ao mover o cursor em uma linha que contém um erro. Quando você vir um rabisco vermelho, poderá focalizar o mouse sobre ele para exibir a lâmpada. Você também poderá fazer com que uma lâmpada seja exibida ao usar o mouse ou o teclado para ir para qualquer lugar da linha em que ocorre o problema.

1. Pressione **Ctrl** + **.** em qualquer lugar de uma linha para invocar a lâmpada e ir diretamente para a lista de possíveis correções.

   ![Lâmpada com o mouse focalizando](../ide/media/vs2015_lightbulb_hover.png "VS2017_LightBulb_Hover")

## <a name="to-see-potential-fixes"></a>Para ver as possíveis correções

Clique na seta para baixo ou no link Mostrar possíveis correções para exibir uma lista de ações rápidas que a lâmpada pode executar para você.

![Lâmpada expandida](../ide/media/vs2015_lightbulb_hover_expanded.png "VS2017_LightBulb_hover_expanded")

## <a name="common-quick-actions"></a>Ações Rápidas comuns

Estas são algumas das Ações Rápidas comuns que são aplicáveis aos códigos de C# e Visual Basic:

- [Ações que corrigem erros](#fix)
- [Ações que removem código desnecessário](#remove)
- [Ações que adicionam código ausente](#add)
- [Transformações de código](#transform)

### <a id="fix"></a> Ações que corrigem erros

#### <a name="correct-misspelled-symbol-or-keyword"></a>Corrigir o símbolo ou a palavra-chave incorreta

|  ID do erro | Linguagens Aplicáveis |  Versão compatível |
| ------- | -------------------- | ----------------  |
| CS0103, BC30002 | C# e Visual Basic | Visual Studio 2015 Atualização 2 |

Se você digitar incorretamente um tipo ou uma palavra-chave no Visual Studio acidentalmente, essa Ação Rápida corrigirá esse erro de forma automática para você. Você verá esses itens no menu de lâmpada como **“Alterar '*palavra digitada incorretamente*' para '*palavra correta*'**.  Por exemplo:

```csharp
// Before
private viod MyMethod()
{
}

// Change 'viod' to 'void'

// After
private void MyMethod()
{
}
```

```vb
' Before
Function MyFunction as Intger
End Function

' Change 'Intger' to 'Integer'

' After
Function MyFunction as Integer
End Function
```

#### <a name="resolve-git-merge-conflict"></a>Resolver conflitos de mesclagem do git

|  ID do erro | Linguagens Aplicáveis |  Versão compatível |
| ------- | -------------------- | ----------------  |
| CS8300, BC37284  | C# e Visual Basic | Visual Studio 2017 versão 15.3 |

Estas Ações rápidas permitem resolver conflitos de mesclagem do git "fazendo uma alteração", que remove o código e os marcadores conflitantes.  

```csharp
// Before
private void MyMethod()
{
<<<<<<< HEAD
    if (true)
    {

    }
=======
    if (false)
    {

    }
>>>>>>> upstream
}

// Take changes from 'HEAD'

// After
private void MyMethod()
{
    if (true)
    {

    }
}
```

#### <a name="make-method-synchronous"></a>Tornar o método síncrono

|  ID do erro | Linguagens Aplicáveis |  Versão compatível |
| ------- | -------------------- | ----------------  |
| CS1998, BC42356 | C# e Visual Basic | Visual Studio 2015 Atualização 2 |

Ao usar a palavra-chave `async` ou `Async` em um método, espera-se que, em algum lugar desse método, a palavra-chave `await` ou `Await` também seja usada.  No entanto, se esse não for o caso, uma Ação Rápida será exibida, que permitirá tornar o método síncrono, removendo a palavra-chave `async` ou `Async` e alterando o tipo de retorno. Use a opção **Tornar o método síncrono** do menu Ações Rápidas.

```csharp
// Before
async Task<int> MyAsyncMethod()
{
    return 3;
}

// Make method synchronous

// After
int MyAsyncMethod()
{
    return 3;
}
```

```vb
' Before
Async Function MyAsyncMethod() As Task(Of Integer)
    Return 3
End Function

' Make method synchronous

' After
Function MyAsyncMethod() As Integer
    Return 3
End Function
```

#### <a name="make-method-asynchronous"></a>Tornar o método assíncrono

|  ID do erro | Linguagens Aplicáveis |  Versão compatível |
| ------- | -------------------- | ----------------  |
| CS4032, BC37057 | C# e Visual Basic | Visual Studio 2017 |

Ao usar a palavra-chave `await` ou `Await` em um método, espera-se que o próprio método seja marcado com a palavra-chave `async` ou `Async`.  No entanto, se esse não for o caso, uma Ação Rápida será exibida, que permitirá tornar o método assíncrono. Use a opção **Tornar o método ou a função síncrona** do menu Ações Rápidas.

```csharp
// Before
int MyAsyncMethod()
{
    return await Task.Run(...);
}

// Make method asynchronous

// After
async Task<int> MyAsyncMethod()
{
    return await Task.Run(...);
}
```

```vb
' Before
Function MyAsyncMethod() as Integer
    Return  Await Task.Run(...)
End Function

' Make method asynchronous

' After
Async Function MyAsyncMethod() As Task(Of Integer)
    Return Await Task.Run(...)
End Function
```

### <a id="remove"></a> Aços que removem código desnecessário

#### <a name="remove-unnecesary-usingsimports"></a>Remover usos/importações desnecessários

|  Linguagens Aplicáveis |  Versão compatível |
|  -------------------- | ----------------  |
|  C# e Visual Basic | Visual Studio 2015 RTW |

A Ação Rápida **Remover Usos/Importações Desnecessários** removerá todas as instruções `using` e `Import` não utilizadas do arquivo atual.  Ao selecionar esse item, as importações de namespace não utilizadas serão removidas imediatamente.

#### <a name="remove-unnecessary-cast"></a>Remover conversão desnecessária

|  ID do diagnóstico | Linguagens Aplicáveis |  Versão compatível |
| ------- | -------------------- | ----------------  |
| IDE0004 | C# e Visual Basic | Visual Studio 2015 RTW |

Se você converter um tipo em outro que não exige uma conversão, o item de Ação Rápida **Remover Conversão Desnecessária** removerá a conversão do código.

```csharp
// before
int number = (int)3;

// Remove Unnecessary Cast

// after
int number = 3;
```

```vb
' Before
Dim number as Integer = CType(3, Integer)

' Remove Unnecessary Cast

' After
Dim number as Integer = 3
```

#### <a name="remove-unused-variables"></a>Remover variáveis não utilizadas

|  ID do diagnóstico | Linguagens Aplicáveis |  Versão compatível |
| ------- | -------------------- | ----------------  |
| CS0219, BC42024 | C# e Visual Basic | Visual Studio 2017 versão 15.3 |

Essa Ação Rápida permite remover variáveis que foram declaradas, mas nunca foram usadas no código.

```csharp
// Before
public MyMethod()
{
    var unused = 8;
    var used = 1;
    return DoStuff(used);
}

// Remove unused variables

// After
public MyMethod()
{
    var used = 1;
    return DoStuff(used);
}
```

#### <a name="remove-type-from-default-value-expression"></a>Remover o tipo da expressão de valor **padrão**

|  ID do diagnóstico | Linguagens Aplicáveis |  Versão compatível |
| ------- | -------------------- | ----------------  |
| IDE0034 | C# 7.1+ | Visual Studio 2017 versão 15.3 |

Esta Ação rápida remove o tipo de valor de uma expressão de valor padrão e usa o [literal `default`](/dotnet/csharp/programming-guide/statements-expressions-operators/default-value-expressions#default-literal-and-type-inference) quando o compilador pode inferir o tipo da expressão.

```csharp
// Before
void DoWork(CancellationToken cancellationToken = default(CancellationToken)) { ... }

// Simplify default expression

// After
void DoWork(CancellationToken cancellationToken = default) { ... }

```

### <a id="add"></a> Ações que adicionam código ausente

#### <a name="add-usingsimports-for-types-in-reference-assemblies-nuget-packages-or-other-types-in-your-solution"></a>Adicionar usos/importações para tipos em assemblies de referência, pacotes NuGet ou outros tipos na solução

|  ID do diagnóstico | Linguagens Aplicáveis |  Versão compatível |
| ------- | -------------------- | ----------------  |
| CS0103, BC30451 | C# e Visual Basic| Visual Studio 2015 Atualização 2 |

O uso dos tipos localizados em outros projetos da solução exibirá a Ação Rápida automaticamente. No entanto, as outras precisam ser habilitadas na guia **Ferramentas > Opções > C#** ou **Basic > Avançado**:

- Sugerir usos/importações para tipos em assemblies de referência
- Sugerir usos/importações para tipos em pacotes NuGet

Quando essa opção estiver habilitada, se você usar um tipo em um namespace que não foi importado, mas que existe em um assembly de referência ou pacote NuGet, a instrução de uso/importação será criada.

```csharp
// Before
Debug.WriteLine("Hello");

// using System.Diagnostics;

// After
using System.Diagnostics;

Debug.WriteLine("Hello");
```

```vb
' Before
Debug.WriteLine("Hello")

' Imports System.Diagnostics

// After
Imports System.Diagnostics

Debug.WriteLine("Hello")
```

#### <a name="add-missing-casesdefault-caseboth"></a>Adicionar maiúsculas e minúsculas ausentes/maiúsculas e minúsculas padrão/ambas

|  ID do diagnóstico | Linguagens Aplicáveis |  Versão compatível |
| ------- | -------------------- | ----------------  |
| IDE0010 | C# e Visual Basic| Visual Studio 2017 versão 15.3 |

Ao criar uma instrução `switch` no C# ou uma instrução `Select Case` no Visual Basic, é possível usar uma Ação de Código para adicionar automaticamente itens com maiúsculas e minúsculas ausentes, uma instrução com maiúsculas e minúsculas padrão ou ambos.

Considere a seguinte enumeração e a instrução `switch` ou `Select Case` vazia:

```csharp
enum MyEnum
{
    Item1,
    Item2,
    Item3
}

...

MyEnum myEnum = MyEnum.Item1;

switch(myEnum)
{
}
```

```vb
Enum MyEnum
    Item1
    Item2
    Item3
End Enum

...

Dim myEnum as MyEnum = MyEnum.Item1

Select Case myEnum
End Select
```

Ao usar a Ação Rápida **Adicionar Ambos**, os casos que faltam são preenchidos e um caso padrão é adicionado:

```csharp
switch(myEnum)
{
    case MyEnum.Item1:
        break;
    case MyEnum.Item2:
        break;
    case MyEnum.Item3:
        break;
    default:
        break;
}
```

```vb
Select Case myEnum
    Case MyEnum.Item1
        Exit Select
    Case MyEnum.Item2
        Exit Select
    Case Else
        Exit Select
End Select
```

#### <a name="add-null-checks-for-parameters"></a>Adicionar verificações de null para parâmetros

| Linguagens Aplicáveis |  Versão compatível |
| -------------------- | ----------------  |
| C# e Visual Basic| Visual Studio 2017 versão 15.3 |

Essa Ação Rápida permite que você adicione uma verificação ao código para determinar se um parâmetro é nulo.

```csharp
// Before
class MyClass
{
    public string MyProperty { get; set; }

    public MyClass(string myProperty) // cursor inside myProperty
    {
        MyProperty = myProperty;
    }
}

// Add null check

// After
class MyClass
{
    public string MyProperty { get; set; }

    public MyClass(string myProperty)
    {
        MyProperty = myProperty ?? throw new ArgumentNullException(nameof(myProperty));
    }
}
```

#### <a name="add-argument-name"></a>Adicionar nome do argumento

| Linguagens Aplicáveis |  Versão compatível |
| -------------------- | ----------------  |
| C# e Visual Basic| Visual Studio 2017 versão 15.3 |

```csharp
// Before
var date = new DateTime(1997, 7, 8);

// Include argument name 'year' (include trailing arguments)

// After
var date = new DateTime(year: 1997, month: 7, day: 8);
```

#### <a name="add-braces"></a>Adicionar chaves

|  ID do diagnóstico | Linguagens Aplicáveis |  Versão compatível |
| ------- | -------------------- | ----------------  |
| IDE0011 | C# | Visual Studio 2017 RTW |

A Ação rápida Adicionar chaves insere chaves em torno de instruções `if` de linha única.

```csharp
// Before
if (true)
    return "hello,world";

// Add braces

// After
if (true)
{
    return "hello,world";
}
```

#### <a name="add-and-order-modifiers"></a>Adicionar e ordenar modificadores

|  ID do diagnóstico | Linguagens Aplicáveis |  Versão compatível |
| ------- | -------------------- | ----------------  |
| IDE0036 | C# e Visual Basic| Visual Studio 2017 versão 15.5 |
| IDE0040 | C# e Visual Basic| Visual Studio 2017 versão 15.5 |

Estas Ações rápidas ajudam a organizar os modificadores, permitindo que você classifique modificadores de acessibilidade existentes e adicione os que estão ausentes.

```csharp
// Before
enum Color
{
    Red, White, Blue
}

// Add accessibility modifiers

// After
internal enum Color
{
    Red, White, Blue
}
```

```csharp
// Before
static private int thisFieldIsPublic;

// Order modifiers

// After
private static int thisFieldIsPublic;
```

### <a id="transform"></a> Transformações de código

#### <a name="convert-if-construct-to-switch"></a>Converter construtor **se** para **alternar**

| Linguagens Aplicáveis |  Versão compatível |
| -------------------- | ----------------  |
| C# e Visual Basic| Visual Studio 2017 versão 15.3 |

Essa Ação Rápida permite que você converta um construtor **if-then-else** em um construtor **switch**.

```csharp
// Before
if (obj is string s)
{
  Console.WriteLine("obj is a string: " + s);
}

else if (obj is int i && i > 10)
{
  Console.WriteLine("obj is an int greater than 10");
}

// Convert to switch

// After
switch (obj)
{
  case string s:
    Console.WriteLine("Obj is a string: " + s);
    break;
  case int i when i > 10:
    Console.WriteLine("obj is an int greater than 10");
    break;
}
```

```vb
' Before
If TypeOf obj Is String s Then
    Console.WriteLine("obj is a string: " + s)
Else If TypeOf obj Is Integer i And i > 10 Then
    Console.WriteLine("obj is an int greater than 10")
End If

' Convert to switch

' After
Select Case obj
  Case String s
    Console.WriteLine("Obj is a string: " + s)
    Exit Sub
  Case Integer i when i > 10
    Console.WriteLine("obj is an int greater than 10")
    Exit Sub
End Select
```

#### <a name="convert-to-interpolated-string"></a>Converter em cadeia de caracteres interpolada

| Linguagens Aplicáveis |  Versão compatível |
| -------------------- | ----------------  |
| C# 6.0+ e Visual Basic 14+ | Visual Studio 2017 RTW |

[Cadeias de caracteres interpoladas](/dotnet/csharp/language-reference/keywords/interpolated-strings) são uma maneira fácil de expressar cadeias de caracteres com variáveis inseridas, semelhante ao método **[String.Format](https://msdn.microsoft.com/library/system.string.format.aspx)**.  Essa Ação Rápida reconhece maiúsculas e minúsculas nas quais as cadeias de caracteres são concatenadas ou que usam **String.Format** e altera o uso de uma cadeia de caracteres interpolada.

```csharp
// Before
int num = 3;
string s = string.Format("My string with {0} in the middle", num);

// Convert to interpolated string

// After
int num = 3;
string s = $"My string with {num} in the middle";
```

```vb
' Before
Dim num as Integer = 3
Dim s as String = String.Format("My string with {0} in the middle", num)

' Convert to interpolated string

' After
Dim num as Integer = 3
Dim s As String = $"My string with {num} in the middle"
```

#### <a name="use-object-initializers"></a>Usar inicializadores de objeto

| ID do diagnóstico | Linguagens Aplicáveis | Versão compatível |
| ------- | -------------------- | ----------------  |
| IDE0017 | C# e Visual Basic | Visual Studio 2017 RTW |

Esta Ação rápida permite usar [inicializadores de objeto](/dotnet/csharp/programming-guide/classes-and-structs/object-and-collection-initializers) em vez de invocar o construtor e ter linhas adicionais de instruções de atribuição.

```csharp
// Before
var c = new Customer();
c.Age = 21;

// Object initialization can be simplified

// After
var c = new Customer() { Age = 21 };
```

```vb
' Before
Dim c = New Customer()
c.Age = 21

' Object initialization can be simplified

' After
Dim c = New Customer() With {.Age = 21}
```

#### <a name="use-collection-initializers"></a>Usar inicializadores de coleção

| ID do diagnóstico | Linguagens Aplicáveis | Versão compatível |
| ------- | -------------------- | ----------------  |
| IDE0028 | C# e Visual Basic | Visual Studio 2017 RTW |

Esta Ação rápida permite usar [inicializadores de coleção](/dotnet/csharp/programming-guide/classes-and-structs/object-and-collection-initializers) em vez de múltiplas chamadas ao método `Add` da sua classe.

```csharp
// Before
var list = new List<int>();
list.Add(1);
list.Add(2);
list.Add(3);

// Collection initialization can be simplified

// After
var list = new List<int> { 1, 2, 3 };
```

```vb
' Before
Dim list = New List(Of Integer)
list.Add(1)
list.Add(2)
list.Add(3)

' Collection initialization can be simplified

' After
Dim list = New List(Of Integer) From {1, 2, 3}

```

#### <a name="convert-auto-property-to-full-property"></a>Converter a propriedade automática em propriedade completa

|  Linguagens Aplicáveis |  Versão compatível |
|  -------------------- | ----------------  |
| C# e Visual Basic | Visual Studio 2017 versão 15.5 |

Esta Ação rápida permite converter uma propriedade automática em uma propriedade completa e vice-versa.

```csharp
// Before
private int MyProperty { get; set; }

// Convert to full property

// After
private int MyProperty
{
    get { return _myProperty; }
    set { _myProperty = value; }
}
```

```vb
' Before
Public Property Name As String

' Convert to full property

' After
Private _Name As String

Public Property Name As String
    Get
        Return _Name
    End Get
    Set
        _Name = Value
    End Set
End Property
```

#### <a name="convert-block-body-to-expression-bodied-member"></a>Converter o corpo do bloco em membro apto para expressão

|  ID do diagnóstico | Linguagens Aplicáveis |  Versão compatível |
| ------- | -------------------- | ----------------  |
| IDE0021-27 | C# 6.0+ | Visual Studio 2017 RTW |

Esta Ação rápida permite converter corpos do bloco em membros aptos para expressão para métodos, construtores, operadores, propriedades, indexadores e acessadores.

```csharp
//Before
class MyClass4
{
    private int _myProperty;

    public int MyProperty
    {
        get { return _myProperty; }
        set
        {
            _myProperty = value;
        }
    }

    public MyClass4(int myProperty)
    {
        MyProperty = myProperty;
    }

    public void PrintProperty()
    {
        Console.WriteLine(MyProperty);
    }
}

// Use expression body for accessors/constructors/methods

// After
class MyClass4
{
    private int _myProperty;

    public int MyProperty
    {
        get => _myProperty;
        set => _myProperty = value;
    }

    public MyClass4(int myProperty) => MyProperty = myProperty;

    public void PrintProperty() => Console.WriteLine(MyProperty);
}
```

#### <a name="convert-anonymous-function-to-local-function"></a>Converter função anônima em função local

|  ID do diagnóstico | Linguagens Aplicáveis |  Versão compatível |
| ------- | -------------------- | ----------------  |
| IDE0039 | C# 7.0+ | Visual Studio 2017 versão 15.5 |

Esta Ação rápida converte funções anônimas em funções locais.

```csharp
// Before
Func<int, int> fibonacci = null;
fibonacci = (int n) =>
{
    return n <= 1 ? 1 : fibonacci(n - 1) + fibonacci(n - 2);
};

// Use local function

// After
int fibonacci(int n)
{
    return n <= 1 ? 1 : fibonacci(n-1) + fibonacci(n-2);
}
```

#### <a name="convert-referenceequals-to-is-null"></a>Converter `ReferenceEquals` em `is null`

|  ID do diagnóstico | Linguagens Aplicáveis |  Versão compatível |
| ------- | -------------------- | ----------------  |
| IDE0041 | C# 7.0+ | Visual Studio 2017 versão 15.5 |

Esta Ação rápida sugere o uso de [correspondência de padrões](/dotnet/csharp/pattern-matching) em vez do padrão de codificação ```ReferenceEquals```, sempre que possível.

```csharp
// Before
var value = "someString";
if (object.ReferenceEquals(value, null))
{
    return;
}

// Use 'is null' check

// After
var value = "someString";
if (value is null)
{
    return;
}
```

#### <a name="introduce-pattern-matching"></a>Introduzir a correspondência de padrões

| ID do diagnóstico | Linguagens Aplicáveis | Versão compatível |
| ------- | -------------------- | ----------------  |
| IDE0020 | C# 7.0+ | Visual Studio 2017 RTW |
| IDE0019 | C# 7.0+ | Visual Studio 2017 RTW |

Esta Ação rápida sugere o uso da [correspondência de padrões](/dotnet/csharp/pattern-matching) com conversões e verificações nulas em C#.   

```csharp
// Before
if (o is int)
{
    var i = (int)o;
    ...
}

// Use pattern matching

// After
if (o is int i)
{
    ...
}

```

```csharp
// Before
var s = o as string;
if (s != null)
{
    ...
}

// Use pattern matching

// After
if (o is string s)
{
    ...
}
```

#### <a name="change-base-for-numeric-literals"></a>Alterar base para literais numéricas

| Linguagens Aplicáveis | Versão compatível |
| ------- | -------------------- | ----------------  |
| C# 7.0+ e Visual Basic 14+ | Visual Studio 2017 versão 15.3 |

Essa Ação Rápida permite que você converta um literal numérico de um sistema numérico base para outro. Por exemplo, você pode alterar um número para hexadecimal ou formato binário. 

```csharp
// Before
int countdown = 2097152;

// Convert to hex

// After
int countdown = 0x200000;
```

```vb
' Before
Dim countdown As Integer = 2097152

' Convert to hex

' After
Dim countdown As Integer = &H200000
```

#### <a name="insert-digit-separators-into-literals"></a>Inserir separadores de dígitos em literais

| Linguagens Aplicáveis | Versão compatível |
| ------- | -------------------- | ----------------  |
| C# 7.0+ e Visual Basic 14+ | Visual Studio 2017 versão 15.3 |

Essa Ação Rápida permite que você adicione caracteres separadores em valores literais.

```csharp
// Before
int countdown = 1000000;

// Separate thousands

// After
int countdown = 1_000_000;
```

```vb
' Before
Dim countdown As Integer = 1000000

' Separate thousands

' After
Dim countdown As Integer = 1_000_000
```

#### <a name="use-explicit-tuple-names"></a>Usar nomes de tupla explícita

| ID do diagnóstico | Linguagens Aplicáveis | Versão compatível |
| ------- | -------------------- | ----------------  |
| IDE0033 | C# 7.0+ e Visual Basic 15+ | Visual Studio 2017 RTW |

Esta Ação rápida identifica áreas em que o nome da tupla explícita pode ser usado em vez de Item1, Item2, etc.

```csharp
// Before
(string name, int age) customer = GetCustomer();
var name = customer.Item1;

// Use explicit tuple name

// After
(string name, int age) customer = GetCustomer();
var name = customer.name;
```

```vb
' Before
Dim customer As (name As String, age As Integer) = GetCustomer()
Dim name = customer.Item1

' Use explicit tuple name

' After
Dim customer As (name As String, age As Integer) = GetCustomer()
Dim name = customer.name
```

#### <a name="use-inferred-names"></a>Usar nomes inferidos

| ID do diagnóstico | Linguagens Aplicáveis | Versão compatível |
| ------- | -------------------- | ----------------  |
| IDE0037 | C# | Visual Studio 2017 v. 15.5 |
| IDE0037 | C# 7.1+ | Visual Studio 2017 v. 15.5 |

Estas Ações rápidas indicam quando os usuários podem usar nomes de membro inferidos em tipos anônimos ou usar os nomes de elemento de tupla inferidos do C# 7.1.

```csharp
// Before
var anon = new { age = age, name = name };

// Use inferred member name

// After
var anon = new { age, name };
```

```csharp
// Before
var tuple = (age: age, name: name);

// Use inferred tuple element name

// After
var tuple = (age, name);
```

#### <a name="deconstruct-tuple-declaration"></a>Desconstruir declaração de tupla

| ID do diagnóstico | Linguagens Aplicáveis | Versão compatível |
| ------- | -------------------- | ----------------  |
| IDE0042 | C# 7.0+ | Visual Studio 2017 v. 15.5 |

Esta Ação rápida permite desconstruir declarações de variável de tupla. 

```csharp
// Before
var person = GetPersonTuple();
Console.WriteLine($"{person.name} {person.age}");

(int x, int y) point = GetPointTuple();
Console.WriteLine($"{point.x} {point.y}");

//Deconstruct variable declaration

// After
var (name, age) = GetPersonTuple();
Console.WriteLine($"{name} {age}");

(int x, int y) = GetPointTuple();
Console.WriteLine($"{x} {y}");
```

## <a name="see-also"></a>Consulte também

[Estilos de código e ações rápidas](code-styles-and-quick-actions.md)  
[Escrevendo e refatorando código (C++)](/cpp/ide/writing-and-refactoring-code-cpp)
