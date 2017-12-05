---
title: "Configurações de Conversão de Codificação .NET para o EditorConfig | Microsoft Docs"
ms.custom: 
ms.date: 10/13/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
helpviewer_keywords: editor
ms.assetid: 
caps.latest.revision: "1"
author: kuhlenh
ms.author: kaseyu
manager: ghogen
ms.technology: vs-ide-general
ms.openlocfilehash: f59065777de938c07a88d722cabdba82d6b19c02
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="net-coding-convention-settings-for-editorconfig"></a>Configurações de convenção de codificação do .NET para o EditorConfig
Você pode definir e manter um estilo de código consistente em sua base de código com o uso de um arquivo [EditorConfig](https://docs.microsoft.com/en-us/visualstudio/ide/create-portable-custom-editor-options). O EditorConfig inclui várias propriedades de formatação de núcleo, como `indent_style` e `indent_size`. No Visual Studio, as definições de convenções de codificação do .NET também podem ser configuradas usando um arquivo EditorConfig. Os arquivos EditorConfig permitem habilitar ou desabilitar convenções individuais de codificação do .NET e configurar o grau de imposição da convenção por meio de um nível de gravidade. Para saber mais sobre como usar o EditorConfig para impor a consistência em sua base de código, leia [Criar opções portáteis de editor personalizado](https://docs.microsoft.com/en-us/visualstudio/ide/create-portable-custom-editor-options). Você também pode examinar o [arquivo .editorconfig da plataforma do compilador do .NET](https://github.com/dotnet/roslyn/blob/master/.editorconfig) como exemplo.  

Há três categorias de convenção de codificação .NET com suporte:  
- [Convenções de Linguagem](#language-conventions)  
   Regras referentes à linguagem C# ou Visual Basic. Por exemplo, você pode especificar regras sobre o uso de `var` ou tipos explícitos ao definir variáveis ou dar preferência a membros aptos para expressão.  
- [Convenções de Formatação](#formatting-conventions)  
   Regras sobre o layout e a estrutura do seu código para facilitar a leitura. Por exemplo, você pode especificar regras em relação a chaves Allman ou dar preferência a espaços em blocos de controle.  
- [Convenções de Nomenclatura](#naming-conventions)  
   Regras relacionadas a nomenclatura dos elementos de código. Por exemplo, você pode especificar que os métodos `async` devem terminar com "Async".  

## <a name="language-conventions"></a>Convenções de linguagem  
As regras para convenções de linguagem têm o seguinte formato:  

`options_name = false|true : none|suggestion|warning|error`  

Para cada regra de convenção de linguagem, você deve especificar **true** (dê preferência a esse estilo) ou **false** (não dê preferência a esse estilo) e uma **gravidade**. A gravidade especifica o nível de imposição para aquele estilo.  

A tabela a seguir lista os valores possíveis de gravidade e seus efeitos:  

Severidade | Efeito
:------- | ------
nenhuma ou silenciosa | Não mostra nada para o usuário quando esta regra é violada. As funcionalidades de geração de código vão gerar código neste estilo, no entanto.  
sugestão | Quando esta regra de estilo for violada, deverá ser mostrada ao usuário como uma sugestão. As sugestões aparecem como três pontos de cor cinza sob os dois primeiros caracteres.  
aviso | Quando esta regra de estilo for violada, deverá ser exibido um aviso do compilador.  
erro | Quando esta regra de estilo for violada, deverá ser exibido um erro do compilador.  

A lista a seguir mostra as regras convenção de linguagem permitidas:  

- Configurações de Estilo de Código do .NET
    - [Qualificadores "This." e "Me."](#this_and_me)
        - dotnet\_style\_qualification\_for_field
        - dotnet\_style\_qualification\_for_property
        - dotnet\_style\_qualification\_for_method
        - dotnet\_style\_qualification\_for_event
    - [Palavras-chave de linguagem em vez de nomes de tipos de estrutura para referências de tipo](#language_keywords)
        - dotnet\_style\_predefined\_type\_for\_locals\_parameters_members
        - dotnet\_style\_predefined\_type\_for\_member_access
    - [Preferências de nível de expressão](#expression_level)
        - dotnet\_style\_object_initializer
        - dotnet\_style\_collection_initializer
        - dotnet\_style\_explicit\_tuple_names
        - dotnet\_style\_coalesce_expression
        - dotnet\_style\_null_propagation
- Configurações de Estilo de Código de C#
    - [Tipos implícitos e explícitos](#var)
        - csharp\_style\_var\_for\_built\_in_types
        - csharp\_style\_var\_when\_type\_is_apparent
        - csharp\_style\_var_elsewhere
    - [Membros de expressão incorporada](#expression_bodied_members)
        - csharp\_style\_expression\_bodied_methods
        - csharp\_style\_expression\_bodied_constructors
        - csharp\_style\_expression\_bodied_operators
        - csharp\_style\_expression\_bodied_properties
        - csharp\_style\_expression\_bodied_indexers
        - csharp\_style\_expression\_bodied_accessors
    - [Correspondência de padrões](#pattern_matching)
        - csharp\_style\_pattern\_matching\_over\_is\_with\_cast_check
        - csharp\_style\_pattern\_matching\_over\_as\_with\_null_check
    - [Declarações de variável embutida](#inlined_variable_declarations)
        - csharp\_style\_inlined\_variable_declaration
    - [Preferências de nível de expressão](#expression_level_csharp)
        - csharp\_prefer\_simple\_default_expression
    - [Preferências da verificação de "null"](#null_checking)
        - csharp\_style\_throw_expression
        - csharp\_style\_conditional\_delegate_call
    - [Preferências de bloco de código](#code_block)
        - csharp\_prefer_braces

### <a name="net-code-style-settings"></a>Configurações de estilo de código do .NET  
As regras de estilo nesta seção são aplicáveis tanto para C# quanto para Visual Basic. Para ver exemplos de código na sua linguagem de programação preferida, escolha no menu suspenso **Linguagem**, no canto superior direito da janela do navegador.  

#### <a name="this_and_me">Qualificadores "This." e "Me."</a>
Essa regra de estilo (IDs de regra IDE0003 e IDE0009) pode ser aplicada a campos, propriedades, métodos ou eventos. Um valor **true** significa a preferência pelo símbolo de código ser precedido de `this.` em C# ou `Me.` no Visual Basic. Um valor **false** significa a preferência pelo elemento de código _não_ ser precedido de `this.` ou `Me.`.  

A tabela a seguir mostra os nomes das regras, as linguagens de programação aplicáveis, os valores padrão e a primeira versão compatível do Visual Studio:  

| Nome da regra | Linguagens aplicáveis | Valor padrão do Visual Studio | Versão compatível |
| ----------- | -------------------- | ----------------------| ----------------  |
| dotnet_style_qualification_for_field | C# e Visual Basic | false:none | Visual Studio 2017 RTW |
| dotnet_style_qualification_for_property | C# e Visual Basic | false:none | Visual Studio 2017 RTW |
| dotnet_style_qualification_for_method | C# e Visual Basic | false:none | Visual Studio 2017 RTW |
| dotnet_style_qualification_for_event | C# e Visual Basic | false:none | Visual Studio 2017 RTW |   

**dotnet\_style\_qualification\_for_field**  
Quando essa regra é definida como **true**, prefira que campos sejam precedidos com `this.` em C# ou `Me.` no Visual Basic.  
Quando essa regra é definida como **false**, prefira que os campos _não_ sejam precedidos com `this.` ou `Me.`.  

Exemplos de código:  

```csharp
// dotnet_style_qualification_for_field = true
this.capacity = 0;

// dotnet_style_qualification_for_field = false
capacity = 0;
```
```vb
' dotnet_style_qualification_for_field = true
Me.capacity = 0

' dotnet_style_qualification_for_field = false
capacity = 0
```  

**dotnet\_style\_qualification\_for_property**  
Quando essa regra é definida como **true**, prefira que as propriedades sejam precedidas com `this.` em C# ou `Me.` no Visual Basic.  
Quando essa regra é definida como **false**, prefira que as propriedades _não_ sejam precedidas com `this.` ou `Me.`.  

Exemplos de código:  

```csharp
// dotnet_style_qualification_for_property = true
this.ID = 0;

// dotnet_style_qualification_for_property = false
ID = 0;
```
```vb
' dotnet_style_qualification_for_property = true
Me.ID = 0

' dotnet_style_qualification_for_property = false
ID = 0
```  

**dotnet\_style\_qualification\_for_method**  
Quando essa regra é definida como **true**, prefira que os métodos sejam precedidos com `this.` em C# ou `Me.` no Visual Basic.  
Quando essa regra é definida como **false**, prefira que os métodos _não_ sejam precedidos com `this.` ou `Me.`.  

Exemplos de código:  

```csharp
// dotnet_style_qualification_for_method = true
this.Display();

// dotnet_style_qualification_for_method = false
Display();
```
```vb
' dotnet_style_qualification_for_method = true
Me.Display()

' dotnet_style_qualification_for_method = false
Display()
```  

**dotnet\_style\_qualification\_for_event**  
Quando essa regra é definida como **true**, prefira que os eventos sejam precedidos com `this.` em C# ou `Me.` no Visual Basic.  
Quando essa regra é definida como **false**, prefira que os eventos _não_ sejam precedidos com `this.` ou `Me.`.  

Exemplos de código:  

```csharp
// dotnet_style_qualification_for_event = true
this.Elapsed += Handler;

// dotnet_style_qualification_for_event = false
Elapsed += Handler;
```
```vb
' dotnet_style_qualification_for_event = true
AddHandler Me.Elapsed, AddressOf Handler

' dotnet_style_qualification_for_event = false
AddHandler Elapsed, AddressOf Handler
```  

Essas regras podem aparecer em um arquivo .editorconfig, assim como mostrado a seguir:  

```
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_qualification_for_field = false:suggestion
dotnet_style_qualification_for_property = false:suggestion
dotnet_style_qualification_for_method = false:suggestion
dotnet_style_qualification_for_event = false:suggestion
```

#### <a name="language_keywords">Palavras-chave de linguagem em vez de nomes de tipos de estrutura para referências de tipo</a>
Essa regra de estilo pode ser aplicada a variáveis locais, parâmetros de método e membros de classe ou como uma regra separada para expressões de acesso a membro de tipo. Um valor **true** significa preferência pela palavra-chave de linguagem (por exemplo, `int` ou `Integer`) em vez do nome do tipo (por exemplo, `Int32`) para tipos que têm uma palavra-chave para representá-los. Um valor **false** significa preferência pelo nome do tipo em vez da palavra-chave de linguagem.  

A tabela a seguir mostra os nomes das regras, as IDs das regras, as linguagens de programação aplicáveis, os valores padrão e a primeira versão compatível do Visual Studio:  

| Nome da regra | ID da regra | Linguagens Aplicáveis | Padrão do Visual Studio | Versão compatível |
| --------- | ------- | -------------------- | ----------------------| ----------------  |
| dotnet_style_predefined_type_for_locals_parameters_members | IDE0012 e IDE0014 | C# e Visual Basic | true:none | Visual Studio 2017 RTW |
| dotnet_style_predefined_type_for_member_access | IDE0013 e IDE0015 | C# e Visual Basic | true:none | Visual Studio 2017 RTW |  

**dotnet\_style\_predefined\_type\_for\_locals\_parameters_members**  
Quando essa regra é definida como **true**, prefira a palavra-chave de linguagem para variáveis locais, parâmetros de método e membros de classe, em vez do nome de tipo, para tipos que têm uma palavra-chave para representá-los.  
Quando essa regra é definida como **false**, prefira o nome do tipo para variáveis locais, parâmetros de método e membros de classe, em vez da palavra-chave de linguagem.  

Exemplos de código:  

```csharp
// dotnet_style_predefined_type_for_locals_parameters_members = true
private int _member;

// dotnet_style_predefined_type_for_locals_parameters_members = false
private Int32 _member;
```
```vb
' dotnet_style_predefined_type_for_locals_parameters_members = true
Private _member As Integer

' dotnet_style_predefined_type_for_locals_parameters_members = false
Private _member As Int32
``` 

**dotnet\_style\_predefined\_type\_for\_member_access**   
Quando essa regra é definida como **true**, prefira a palavra-chave de linguagem para expressões de acesso a membro, em vez do nome de tipo, para tipos que têm uma palavra-chave para representá-los.  
Quando essa regra é definida como **false**, prefira o nome do tipo para expressões de acesso a membro, em vez da palavra-chave de linguagem.  

Exemplos de código:  

```csharp
// dotnet_style_predefined_type_for_member_access = true
var local = int.MaxValue;

// dotnet_style_predefined_type_for_member_access = false
var local = Int32.MaxValue;
```
```vb
' dotnet_style_predefined_type_for_member_access = true
Dim local = Integer.MaxValue

' dotnet_style_predefined_type_for_member_access = false
Dim local = Int32.MaxValue
```  

Essas regras podem aparecer em um arquivo .editorconfig, assim como mostrado a seguir:  

```
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_predefined_type_for_locals_parameters_members = true:suggestion
dotnet_style_predefined_type_for_member_access = true:suggestion
``` 

#### <a name="expression_level">Preferências de nível de expressão</a>  
As regras de estilo nesta seção referem-se a preferências de nível de expressão, incluindo o uso de inicializadores de objeto, inicializadores de coleção, nomes de tupla explícita, expressões de união nula versus operadores ternários e o operador condicional nulo.  

A tabela a seguir mostra os nomes das regras, as IDs de regra, as linguagens de programação aplicáveis, os valores padrão e a primeira versão compatível do Visual Studio:  

| Nome da regra | ID da regra | Linguagens Aplicáveis | Padrão do Visual Studio | Versão compatível |
| --------- | ------- | -------------------- | ----------------------| ----------------  |
| dotnet_style_object_initializer | IDE0017 | C# e Visual Basic | true:suggestion | Visual Studio 2017 RTW |
| dotnet_style_collection_initializer | IDE0028 | C# e Visual Basic | true:suggestion | Visual Studio 2017 RTW |
| dotnet_style_explicit_tuple_names | IDE0033 | C# 7.0+ e Visual Basic 15+ | true:suggestion | Visual Studio 2017 RTW |
| dotnet_style_coalesce_expression | IDE0029 | C# e Visual Basic | true:suggestion | Visual Studio 2017 RTW |
| dotnet_style_null_propagation | IDE0031 | C# 6.0+ e Visual Basic 14+ | true:suggestion | Visual Studio 2017 RTW | 

**dotnet\_style\_object_initializer**  
Quando essa regra é definida como **true**, prefira que objetos sejam inicializados usando inicializadores de objeto quando possível.  
Quando essa regra é definida como **false**, prefira que objetos *não* sejam inicializados usando inicializadores de objeto.  

Exemplos de código:  

```csharp
// dotnet_style_object_initializer = true
var c = new Customer() { Age = 21 };

// dotnet_style_object_initializer = false
var c = new Customer();
c.Age = 21;
```
```vb
' dotnet_style_object_initializer = true
Dim c = New Customer() With {.Age = 21}

' dotnet_style_object_initializer = false
Dim c = New Customer()
c.Age = 21
```

**dotnet\_style\_collection_initializer**  
Quando essa regra é definida como **true**, prefira que coleções sejam inicializadas usando inicializadores de coleção quando possível.  
Quando essa regra é definida como **false**, prefira que as coleções *não* sejam inicializadas usando inicializadores de coleção.

Exemplos de código:

```csharp
// dotnet_style_collection_initializer = true
var list = new List<int> { 1, 2, 3 };

// dotnet_style_collection_initializer = false
var list = new List<int>();
list.Add(1);
list.Add(2);
list.Add(3);
```
```vb
' dotnet_style_collection_initializer = true
Dim list = New List(Of Integer) From {1, 2, 3}

' dotnet_style_collection_initializer = false
Dim list = New List(Of Integer)
list.Add(1)
list.Add(2)
list.Add(3)
```  

**dotnet\_style\_explicit\_tuple_names**  
Quando essa regra é definida como **true**, prefira nomes de tupla a propriedades ItemX.  
Quando essa regra é definida como **false**, prefira propriedades ItemX a nomes de tupla.  

Exemplos de código:  

```csharp
// dotnet_style_explicit_tuple_names = true
(string name, int age) customer = GetCustomer();
var name = customer.name;

// dotnet_style_explicit_tuple_names = false
(string name, int age) customer = GetCustomer();
var name = customer.Item1;
```
```vb
 ' dotnet_style_explicit_tuple_names = true
Dim customer As (name As String, age As Integer) = GetCustomer()
Dim name = customer.name

' dotnet_style_explicit_tuple_names = false
Dim customer As (name As String, age As Integer) = GetCustomer()
Dim name = customer.Item1
```

**dotnet\_style\_coalesce_expression**  
Quando essa regra é definida como **true**, prefira expressões de união nula a verificação do operador ternário.  
Quando essa regra é definida como **false**, prefira a verificação do operador ternário a expressões de união nula.

Exemplos de código:  

```csharp
// dotnet_style_coalesce_expression = true
var v = x ?? y;

// dotnet_style_coalesce_expression = false
var v = x != null ? x : y; // or
var v = x == null ? y : x;
```
```vb
' dotnet_style_coalesce_expression = true
Dim v = If(x, y)

' dotnet_style_coalesce_expression = false
Dim v = If(x Is Nothing, y, x) ' or
Dim v = If(x IsNot Nothing, x, y)
```

**dotnet\_style\_null_propagation**  
Quando essa regra é definida como **true**, prefira usar o operador condicional nulo quando possível.  
Quando essa regra é definida como **false**, prefira o uso da verificação de ternário nulo sempre que possível.  

Exemplos de código:  

```csharp
// dotnet_style_null_propagation = true
var v = o?.ToString();

// dotnet_style_null_propagation = false
var v = o == null ? null : o.ToString(); // or
var v = o != null ? o.String() : null;
```
```vb
' dotnet_style_null_propagation = true
Dim v = o?.ToString()

' dotnet_style_null_propagation = false
Dim v = If(o Is Nothing, Nothing, o.ToString()) ' or
Dim v = If(o IsNot Nothing, o.ToString(), Nothing)
```  

Essas regras podem aparecer em um arquivo .editorconfig, assim como mostrado a seguir:  

```
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_object_initializer = true:suggestion
dotnet_style_collection_initializer = true:suggestion
dotnet_style_explicit_tuple_names = true:suggestion
dotnet_style_coalesce_expression = true:suggestion
dotnet_style_null_propagation = true:suggestion
``` 

### <a name="c-code-style-settings"></a>Configurações de estilo de código de C#  
As regras de estilo nesta seção são aplicáveis somente á linguagem C#.  

#### <a name="var">Tipos implícitos e explícitos</a>
As regras de estilo nesta seção (IDs de regra IDE0007 e IDE0008) referem-se ao uso da palavra-chave [var](/dotnet/csharp/language-reference/keywords/var) em vez de um tipo explícito em uma declaração de variável. Essa regra pode ser aplicada separadamente a tipos internos, quando o tipo é aparente e em qualquer outro local.  

A tabela a seguir mostra os nomes das regras, as linguagens de programação aplicáveis, os valores padrão e a primeira versão compatível do Visual Studio:  

| Nome da regra | Linguagens Aplicáveis | Padrão do Visual Studio | Versão compatível |
| ----------- | -------------------- | ----------------------| ----------------  |
| csharp_style_var_for_built_in_types | C# | true:none | Visual Studio 2017 RTW |
| csharp_style_var_when_type_is_apparent | C# | true:none | Visual Studio 2017 RTW |
| csharp_style_var_elsewhere | C# | true:none | Visual Studio 2017 RTW |

**csharp\_style\_var\_for\_built\_in_types**  
Quando essa regra é definida como **true**, prefira que `var` seja usada para declarar variáveis com tipos de sistema internos, como `int`.  
Quando essa regra é definida como **false**, prefira tipo explícito em vez de `var` para declarar variáveis com tipos de sistema internos, como `int`.

Exemplos de código:  

```csharp
// csharp_style_var_for_built_in_types = true
var x = 5;

// csharp_style_var_for_built_in_types = false
int x = 5;
```

**csharp\_style\_var\_when\_type\_is_apparent**  
Quando essa regra é definida como **true**, prefira `var` quando o tipo já tiver sido mencionado no lado direito de uma expressão de declaração.  
Quando essa regra é definida como **false**, prefira tipo explícito em vez de `var` quando o tipo já tiver sido mencionado no lado direito de uma expressão de declaração.  

Exemplos de código:  

```csharp
// csharp_style_var_when_type_is_apparent = true
var obj = new Customer();

// csharp_style_var_when_type_is_apparent = false
Customer obj = new Customer();
```

**csharp\_style\_var_elsewhere**  
Quando essa regra é definida como **true**, prefira `var` em vez de tipo explícito em todos os casos, a menos que a regra seja substituída por outra regra de estilo de código.  
Quando essa regra é definida como **false**, prefira tipo explícito em vez de `var` em todos os casos, a menos que a regra seja substituída por outra regra de estilo de código.  

Exemplos de código:  

```csharp
// csharp_style_var_elsewhere = true
var f = this.Init();

// csharp_style_var_elsewhere = false
bool f = this.Init();
```

Exemplo de arquivo .editorconfig:  

```
# CSharp code style settings:
[*.cs]
csharp_style_var_for_built_in_types = true:suggestion
csharp_style_var_when_type_is_apparent = true:suggestion
csharp_style_var_elsewhere = true:suggestion
``` 

#### <a name="expression_bodied_members">Membros de expressão incorporada</a>
As regras de estilo nesta seção envolvem o uso de [membros aptos para expressão](/dotnet/csharp/programming-guide/statements-expressions-operators/expression-bodied-members) quando a lógica consiste em uma única expressão. Essa regra pode ser aplicada a métodos, construtores, operadores, propriedades, indexadores e acessadores.  

A tabela a seguir mostra os nomes das regras, as IDs de regra, as versões de linguagem aplicáveis, os valores padrão e a primeira versão compatível do Visual Studio:  

| Nome da regra | ID da regra | Linguagens Aplicáveis | Padrão do Visual Studio | Versão compatível |
| --------- | ------- | -------------------- | ----------------------| ----------------  |
| csharp_style_expression_bodied_methods | IDE0022 | C# 6.0+ | false:none | Visual Studio 2017 RTW |
| csharp_style_expression_bodied_constructors | IDE0021 | C# 7.0+ | false:none | Visual Studio 2017 RTW |
| csharp_style_expression_bodied_operators | IDE0023 e IDE0024 | C# 7.0+ | false:none | Visual Studio 2017 RTW |
| csharp_style_expression_bodied_properties | IDE0025 | C# 7.0+ | true:none | Visual Studio 2017 RTW |
| csharp_style_expression_bodied_indexers | IDE0026 | C# 7.0+ | true:none | Visual Studio 2017 RTW |
| csharp_style_expression_bodied_accessors | IDE0027 | C# 7.0+ | true:none | Visual Studio 2017 RTW |  

**csharp\_style\_expression\_bodied_methods**  
Quando essa regra é definida como **true**, prefira membros aptos para expressão para métodos.  
Quando essa regra é definida como **false**, não prefira membros aptos para expressão para métodos.  

Exemplos de código:  

```csharp
// csharp_style_expression_bodied_methods = true
public int GetAge() => this.Age;

// csharp_style_expression_bodied_methods = false
public int GetAge() { return this.Age; }
```  

**csharp\_style\_expression\_bodied_constructors**  
Quando essa regra é definida como **true**, prefira membros aptos para expressão para construtores.  
Quando essa regra é definida como **false**, não prefira membros aptos para expressão para construtores.  

Exemplos de código:  

```csharp
// csharp_style_expression_bodied_constructors = true
public Customer(int age) => Age = age;

// csharp_style_expression_bodied_constructors = false
public Customer(int age) { Age = age; }
```  

**csharp\_style\_expression\_bodied_operators**  
Quando essa regra é definida como **true**, prefira membros aptos para expressão para operadores.  
Quando essa regra é definida como **false**, não prefira membros aptos para expressão para operadores.  

Exemplos de código:  

```csharp
// csharp_style_expression_bodied_operators = true
public static ComplexNumber operator +(ComplexNumber c1, ComplexNumber c2)
    => new ComplexNumber(c1.Real + c2.Real, c1.Imaginary + c2.Imaginary);

// csharp_style_expression_bodied_operators = false
public static ComplexNumber operator +(ComplexNumber c1, ComplexNumber c2)
{ return new ComplexNumber(c1.Real + c2.Real, c1.Imaginary + c2.Imaginary); }
```  

**csharp\_style\_expression\_bodied_properties**  
Quando essa regra é definida como **true**, prefira membros aptos para expressão para propriedades.  
Quando essa regra é definida como **false**, não prefira membros aptos para expressão para propriedades.  

Exemplos de código:  

```csharp
// csharp_style_expression_bodied_properties = true
public int Age => _age;

// csharp_style_expression_bodied_properties = false
public int Age { get { return _age; }}
```  

**csharp\_style\_expression\_bodied_indexers**  
Quando essa regra é definida como **true**, prefira membros aptos para expressão para indexadores.  
Quando essa regra é definida como **false**, não prefira membros aptos para expressão para indexadores.  

Exemplos de código:  

```csharp
// csharp_style_expression_bodied_indexers = true
public T this[int i] => _value[i];

// csharp_style_expression_bodied_indexers = false
public T this[int i] { get { return _values[i]; } }
```  

**csharp\_style\_expression\_bodied_accessors**  
Quando essa regra é definida como **true**, prefira membros aptos para expressão para acessadores.  
Quando essa regra é definida como **false**, não prefira membros aptos para expressão para acessadores.  

Exemplos de código:  

```csharp
// csharp_style_expression_bodied_accessors = true
public int Age { get => _age; set => _age = value; }

// csharp_style_expression_bodied_accessors = false
public int Age { get { return _age; } set { _age = value; } }
```  

Exemplo de arquivo .editorconfig:  

```
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_methods = false:none
csharp_style_expression_bodied_constructors = false:none
csharp_style_expression_bodied_operators = false:none
csharp_style_expression_bodied_properties = true:none
csharp_style_expression_bodied_indexers = false:none
csharp_style_expression_bodied_accessors = false:none
```  

#### <a name="pattern_matching">Correspondência de padrões</a>
As regras de estilo nesta seção envolvem o uso de [correspondência de padrões](/dotnet/csharp/pattern-matching) em C#.  

A tabela a seguir mostra os nomes das regras, as IDs de regra, as versões de linguagem aplicáveis, os valores padrão e a primeira versão compatível do Visual Studio:  

| Nome da regra | ID da regra | Linguagens Aplicáveis | Padrão do Visual Studio | Versão compatível |
| --------- | ------- | -------------------- | ----------------------| ----------------  |
| csharp_style_pattern_matching_over_is_with_cast_check | IDE0020 | C# 7.0+ | true:suggestion | Visual Studio 2017 RTW |
| csharp_style_pattern_matching_over_as_with_null_check | IDE0019 | C# 7.0+ | true:suggestion | Visual Studio 2017 RTW |

**csharp\_style\_pattern\_matching\_over\_is\_with\_cast_check**  
Quando essa regra é definida como **true**, prefira a correspondência de padrões em vez de expressões `is` com conversões de tipo.  
Quando essa regra é definida como **false**, prefira expressões `is` com conversões de tipo em vez de correspondência de padrões.  

Exemplos de código:  

```csharp
// csharp_style_pattern_matching_over_is_with_cast_check = true
if (o is int i) {...}

// csharp_style_pattern_matching_over_is_with_cast_check = false
if (o is int) {var i = (int)o; ... }
```

**csharp\_style\_pattern\_matching\_over\_as\_with\_null_check**  
Quando essa regra é definida como **true**, prefira correspondência de padrões em vez de expressões `as` com verificações nulas para determinar se algo é de um tipo específico.  
Quando essa regra é definida como **false**, prefira expressões `as` com verificações nula em vez de correspondência de padrões para determinar se algo é de um tipo específico.  

Exemplos de código:  

```csharp
// csharp_style_pattern_matching_over_as_with_null_check = true
if (o is string s) {...}

// csharp_style_pattern_matching_over_as_with_null_check = false
var s = o as string;
if (s != null) {...}
```

Exemplo de arquivo .editorconfig:  

```
# CSharp code style settings:
[*.cs]
csharp_style_pattern_matching_over_is_with_cast_check = true:suggestion
csharp_style_pattern_matching_over_as_with_null_check = true:suggestion
```

#### <a name="inlined_variable_declarations">Declarações de variável embutida</a>
Essa regra de estilo é relacionada a se as variáveis `out` são declaradas embutidas ou não. Após o C#7, você pode [declarar uma variável de saída na lista de argumentos de uma chamada de método](/dotnet/csharp/language-reference/keywords/out-parameter-modifier#calling-a-method-with-an-out-argument) em vez de declará-la em uma declaração de variável separada.  

A tabela a seguir mostra o nome da regra, a ID da regra, as versões de linguagem aplicáveis, os valores padrão e a primeira versão compatível do Visual Studio:  

| Nome da regra | ID da regra | Linguagens Aplicáveis | Padrão do Visual Studio | Versão compatível |
| --------- | -------- | -------------------- | ----------------------| ----------------  |
| csharp_style_inlined_variable_declaration | IDE0018 | C# 7.0+ | true:suggestion | Visual Studio 2017 RTW |

**csharp\_style\_inlined\_variable_declaration**  
Quando essa regra é definida como **true**, prefira que as variáveis `out` sejam declaradas embutidas na lista de argumentos de uma chamada de método quando possível.  
Quando essa regra é definida como **false**, prefira que as variáveis `out` sejam declaradas antes da chamada de método.  

Exemplos de código:  

```csharp
// csharp_style_inlined_variable_declaration = true
if (int.TryParse(value, out int i) {...}

// csharp_style_inlined_variable_declaration = fale
int i;
if (int.TryParse(value, out i) {...}
```

Exemplo de arquivo .editorconfig:  

```
# CSharp code style settings:
[*.cs]
csharp_style_inlined_variable_declaration = true:suggestion
```

#### <a name="expression_level_csharp">Preferências de nível de expressão</a>
Essa regra de estilo refere-se ao uso do [literal `default` para expressões de valor padrão](/dotnet/csharp/programming-guide/statements-expressions-operators/default-value-expressions#default-literal-and-type-inference) quando o compilador pode inferir o tipo da expressão.  

A tabela a seguir mostra o nome da regra, a ID da regra, as versões de linguagem aplicáveis, os valores padrão e a primeira versão compatível do Visual Studio:  

| Nome da regra | ID da regra | Linguagens Aplicáveis | Padrão do Visual Studio | Versão compatível |
| --------- | ------- | -------------------- | ----------------------| ----------------  |
| csharp_prefer_simple_default_expression | IDE0034 | C# 7.1+ | true:suggestion | Visual Studio 2017 v. 15.3 |

**csharp\_prefer\_simple\_default_expression**  
Quando essa regra é definida como **true**, prefira `default` em vez de `default(T)`.  
Quando essa regra é definida como **false**, prefira `default(T)` em vez de `default`.  

Exemplos de código:  

```csharp 
// csharp_prefer_simple_default_expression = true
void DoWork(CancellationToken cancellationToken = default) { ... }

// csharp_prefer_simple_default_expression = false
void DoWork(CancellationToken cancellationToken = default(CancellationToken)) { ... }
```

Exemplo de arquivo .editorconfig:  

```
# CSharp code style settings:
[*.cs]
csharp_prefer_simple_default_expression = true:suggestion
``` 

#### <a name="null_checking">Preferências da verificação de "null"</a>
Essas regras de estilo referem-se à sintaxe da verificação de `null`, incluindo o uso de expressões `throw` ou instruções `throw`, e se é desejável executar uma verificação nula ou usar o operador de união condicional (`?.`) ao invocar uma [expressão lambda](/dotnet/csharp/lambda-expressions).  

A tabela a seguir mostra os nomes das regras, as IDs de regra, as versões de linguagem aplicáveis, os valores padrão e a primeira versão compatível do Visual Studio:  

| Nome da regra | ID da regra | Linguagens Aplicáveis | Padrão do Visual Studio | Versão compatível |
| --------- | ------- | -------------------- | ----------------------| ----------------  |
| csharp_style_throw_expression | IDE0016 | C# 7.0+ | true:suggestion | Visual Studio 2017 RTW |
| csharp_style_conditional_delegate_call | IDE0041 | C# 6.0+ | true:suggestion | Visual Studio 2017 RTW |

**csharp\_style\_throw_expression**  
Quando essa regra é definida como **true**, prefira usar expressões `throw` em vez de instruções `throw`.  
Quando essa regra é definida como **false**, prefira usar instruções `throw` em vez de expressões `throw`.  

Exemplos de código:  

```csharp
// csharp_style_throw_expression = true
this.s = s ?? throw new ArgumentNullException(nameof(s));

// csharp_style_throw_expression = false
if (s == null) { throw new ArgumentNullException(nameof(s)); }
this.s = s;
```

**csharp\_style\_conditional\_delegate_call**   
Quando essa regra é definida como **true**, prefira usar o operador de união condicional (`?.`) ao invocar uma expressão lambda, em vez de realizar uma verificação nula.  
Quando essa regra é definida como **false**, prefira realizar uma verificação nula antes de invocar uma expressão lambda, em vez de usar o operador de união condicional (`?.`).  

Exemplos de código:  

```csharp
// csharp_style_conditional_delegate_call = true
func?.Invoke(args);

// csharp_style_conditional_delegate_call = false
if (func != null) { func(args); }
```

Exemplo de arquivo .editorconfig:  

```
# CSharp code style settings:
[*.cs]
csharp_style_throw_expression = true:suggestions:
csharp_style_conditional_delegate_call = false:suggestion
```

#### <a name="code_block">Preferências de bloco de código</a>
Essa regra de estilo diz respeito ao uso de chaves `{ }` para cercar blocos de código.  

A tabela a seguir mostra o nome da regra, a ID da regra, as versões de linguagem aplicáveis, os valores padrão e a primeira versão compatível do Visual Studio:  

| Nome da regra | ID da regra | Linguagens Aplicáveis | Padrão do Visual Studio | Versão compatível |
| --------- | ------- | -------------------- | ----------------------| ----------------  |
| csharp_prefer_braces | IDE0011 | C# | true:none | Visual Studio 2017 v. 15.3 |

**csharp\_prefer\_braces**   
Quando essa regra é definida como **true**, prefira chaves, até mesmo para uma linha de código.  
Quando essa regra é definida como **false**, prefira não usar chaves, se permitido.  

Exemplos de código:  

```csharp
// csharp_prefer_braces = true
if (test) { this.Display(); }

// csharp_prefer_braces = false
if (test) this.Display();
```

Exemplo de arquivo .editorconfig:  

```
# CSharp code style settings:
[*.cs]
csharp_prefer_braces = true:none
```

## <a name="formatting-conventions"></a>Convenções de formatação
A maioria das regras para as convenções de formatação tem o seguinte formato:  

`rule_name = false|true`  

Você especifica **true** (dê preferência a esse estilo) ou **false** (não dê preferência a esse estilo). Você não especifica uma gravidade. Para algumas regras, em vez de true ou false, você especifica outros valores para descrever quando e onde aplicar a regra.  

A lista a seguir mostra as regras de convenção de formatação disponíveis no Visual Studio:  

- Configurações de Formatação do .NET
    - [Organizar Usos](#usings)
        - dotnet_sort_system_directives_first
- Configurações de Formatação de C#
    - [Opções de Nova Linha](#newline)
        - csharp_new_line_before_open_brace
        - csharp_new_line_before_else
        - csharp_new_line_before_catch
        - csharp_new_line_before_finally
        - csharp_new_line_before_members_in_object_initializers
        - csharp_new_line_before_members_in_anonymous_types
        - csharp_new_line_between_query_expression_clauses
    - [Opções de Recuo](#indent)
        - csharp_indent_case_contents
        - csharp_indent_switch_labels
        - csharp_indent_labels
    - [Opções de Espaçamento](#spacing)
        - csharp_space_after_cast
        - csharp_space_after_keywords_in_control_flow_statements
        - csharp_space_between_method_declaration_parameter_list_parentheses
        - csharp_space_between_method_call_parameter_list_parentheses
        - csharp_space_between_parentheses
    - [Opções de Disposição](#wrapping)
        - csharp_preserve_single_line_statements
        - csharp_preserve_single_line_blocks

### <a name="net-formatting-settings"></a>Configurações de formatação do .NET
As regras de formatação nesta seção são aplicáveis ao C# e Visual Basic.  

#### <a name="usings">Organizar usos</a>
Essa regra de formatação diz respeito ao posicionamento de diretivas using System.* em relação a outras diretivas using.  

A tabela a seguir mostra o nome da regra, as linguagens aplicáveis, o valor padrão e a primeira versão compatível do Visual Studio:  

| Nome da regra | Linguagens Aplicáveis | Padrão do Visual Studio | Versão compatível |
| ----------- | -------------------- | ----------------------| ----------------  |
| dotnet_sort_system_directives_first |  C# e Visual Basic | true | Visual Studio 2017 v. 15.3  |

**dotnet\_sort\_system\_directives_first**  
Quando essa regra é definida como **true**, classifique as diretivas using System.* em ordem alfabética e posicione-as antes de outras usings.  
Quando essa regra é definida como **false**, não posicione diretivas using System.* antes de outras diretivas using.  

Exemplos de código:  

```csharp
// dotnet_sort_system_directives_first = true
using System.Collections.Generic;
using System.Threading.Tasks;
using Octokit;

// dotnet_sort_system_directives_first = false
using System.Collections.Generic;
using Octokit;
using System.Threading.Tasks;
```

Exemplo de arquivo .editorconfig:  

```
# .NET formatting settings:
[*.{cs,vb}]
dotnet_sort_system_directives_first = true
``` 

### <a name="csharp_formatting">Configurações de formatação de C#</a>  
As regras de formatação nesta seção aplicam-se somente a código em C#.  

#### <a name="newline">Opções de Nova Linha</a>  
Essas regras de formatação envolvem o uso de novas linhas para formatar o código.  

A tabela a seguir mostra os nomes das regras "nova linha", as linguagens aplicáveis, os valores padrão e a primeira versão compatível do Visual Studio:  

| Nome da regra | Linguagens Aplicáveis | Padrão do Visual Studio | Versão compatível |
| ----------- | -------------------- | ----------------------| ----------------  |
| csharp_new_line_before_open_brace |  C# | all | Visual Studio 2017 v. 15.3  |
| csharp_new_line_before_else |  C# | true | Visual Studio 2017 v. 15.3  |
| csharp_new_line_before_catch |  C# | true | Visual Studio 2017 v. 15.3  |
| csharp_new_line_before_finally |  C# | true | Visual Studio 2017 v. 15.3  |
| csharp_new_line_before_members_in_object_initializers |  C# | true | Visual Studio 2017 v. 15.3  |
| csharp_new_line_before_members_in_anonymous_types |  C# | true | Visual Studio 2017 v. 15.3  |
| csharp_new_line_between_query_expression_clauses |  C# | true | Visual Studio 2017 v. 15.3  |

**csharp\_new\_line\_before\_open_brace**  
Essa regra está relacionada a se uma chave de abertura `{` devem ser colocada na mesma linha que a do código anterior ou em uma nova linha. Para esta regra, você não especifica **true** ou **false**. Em vez disso, você especifica **all**, **none** ou um ou mais elementos de código, como **methods** ou **properties**, para definir quando essa regra deve ser aplicada. A lista completa de valores permitidos é mostrada na tabela a seguir:  

| Valor | Descrição 
| ------------- |:-------------|
| acessadores, métodos_anônimos, tipos_anônimos, blocos_de_controle, eventos, indexadores, lambdas, funções_locais, métodos, coleção_de_objetos, propriedades, tipos.<br>(Para vários tipos, separe com ","). | Exigir que chaves estejam em uma nova linha para os elementos de código especificados (também conhecido como estilo "Allman") |
| all | Requer que as chaves estejam em uma nova linha para todas as expressões (estilo "Allman") |
| nenhum | Requer que as chaves estejam na mesma linha para todas as expressões ("K&R") |

Exemplos de código:  

```csharp
// csharp_new_line_before_open_brace = all
void MyMethod() 
{
    if (...) 
    {
        ...
    }
}

// csharp_new_line_before_open_brace = none
void MyMethod() {
    if (...) {
        ...
    }
}
```

**csharp\_new\_line\_before_else**  
Quando essa regra é definida como **true**, posicione as instruções `else` em uma nova linha.  
Quando essa regra é definida como **false**, posicione as instruções `else` na mesma linha.  

Exemplos de código:  

```csharp
// csharp_new_line_before_else = true
if (...) {
    ...
}
else {
    ...
}

// csharp_new_line_before_else = false
if (...) {
    ...
} else {
    ...
}
```

**csharp\_new\_line\_before_catch**    
Quando essa regra é definida como **true**, posicione as instruções `catch` em uma nova linha.  
Quando essa regra é definida como **false**, posicione as instruções `catch` na mesma linha.  

Exemplos de código:  

```csharp
// csharp_new_line_before_catch = true
try {
    ...
}
catch (Exception e) {
    ...
}

// csharp_new_line_before_catch = false
try {
    ...
} catch (Exception e) {
    ...
}
```

**csharp\_new\_line\_before_finally**      
Quando essa regra é definida como **true**, exigir que as instruções `finally` estejam em uma nova linha após a chave de fechamento.  
Quando essa regra é definida como **false**, exigir que as instruções `finally` estejam na mesma linha que a chave de fechamento.  

Exemplos de código:  

```csharp
// csharp_new_line_before_finally = true
try {
    ...
}
catch (Exception e) {
    ...
}
finally {
    ...
}

// csharp_new_line_before_finally = false
try {
    ...
} catch (Exception e) {
    ...
} finally {
    ...
}
```

**csharp\_new\_line\_before\_members\_in\_object_initializers**       
Quando essa regra é definida como **true**, exigir que membros dos inicializadores de objeto estejam em linhas separadas.  
Quando essa regra é definida como **false**, exigir que membros dos inicializadores de objeto estejam na mesma linha.  

Exemplos de código:  

```csharp
// csharp_new_line_before_members_in_object_initializers = true
var z = new B()
{
    A = 3,
    B = 4
}

// csharp_new_line_before_members_in_object_initializers = false
var z = new B()
{
    A = 3, B = 4
}
```

**csharp\_new\_line\_before\_members\_in\_anonymous_types**       
Quando essa regra é definida como **true**, exigir que membros dos tipos anônimos estejam em linhas separadas.  
Quando essa regra é definida como **false**, exigir que membros dos tipos anônimos estejam na mesma linha.  

Exemplos de código:  

```csharp
// csharp_new_line_before_members_in_anonymous_types = true
var z = new
{
    A = 3,
    B = 4
}

// csharp_new_line_before_members_in_anonymous_types = false
var z = new
{
    A = 3, B = 4
}
```

**csharp_new_line_between_query_expression_clauses**       
Quando essa regra é definida como **true**, exigir que elementos das cláusulas de expressão de consulta estejam em linhas separadas.  
Quando essa regra é definida como **false**, exigir que elementos das cláusulas de expressão de consulta estejam na mesma linha.  

Exemplos de código:  

```csharp
// csharp_new_line_between_query_expression_clauses = true
var q = from a in e
        from b in e
        select a * b;

// csharp_new_line_between_query_expression_clauses = false
var q = from a in e from b in e
        select a * b;
```

Exemplo de arquivo .editorconfig:  

```
# CSharp formatting settings:
[*.cs]
csharp_new_line_before_open_brace = methods, properties, control_blocks, types
csharp_new_line_before_else = true
csharp_new_line_before_catch = true
csharp_new_line_before_finally = true
csharp_new_line_before_members_in_object_initializers = true
csharp_new_line_before_members_in_anonymous_types = true
csharp_new_line_between_query_expression_clauses = true
``` 

#### <a name="indent">Opções de recuo</a>  
Essas regras de formatação envolvem o uso de recuo para formatar o código.  

A tabela a seguir mostra os nomes das regras, as linguagens aplicáveis, os valores padrão e a primeira versão compatível do Visual Studio:  

| Nome da regra | Linguagens Aplicáveis | Padrão do Visual Studio | Versão compatível |
| ----------- | -------------------- | ----------------------| ----------------  |
| csharp_indent_case_contents |  C# | true | Visual Studio 2017 v. 15.3  |
| csharp_indent_switch_labels |  C# | true | Visual Studio 2017 v. 15.3  |
| csharp_indent_labels |  C# | no_change | Visual Studio 2017 v. 15.3  |

**csharp\_indent\_case_contents**  
Quando essa regra é definida como **true**, recue os conteúdos de caso `switch`.  
Quando essa regra é definida como **false**, não recue os conteúdos de caso `switch`.  

Exemplos de código:  

```csharp
// csharp_indent_case_contents = true
switch(c) {
    case Color.Red:
        Console.WriteLine("The color is red");
        break;
    case Color.Blue:
        Console.WriteLine("The color is blue");
        break;
    default:
        Console.WriteLine("The color is unknown.");
        break;
}

// csharp_indent_case_contents = false
switch(c) {
    case Color.Red:
    Console.WriteLine("The color is red");
    break;
    case Color.Blue:
    Console.WriteLine("The color is blue");
    break;
    default:
    Console.WriteLine("The color is unknown.");
    break;
}
```

**csharp\_indent\_switch_labels**  
Quando essa regra é definida como **true**, recue os rótulos `switch`.  
Quando essa regra é definida como **false**, não recue os rótulos `switch`.  

Exemplos de código:  

```csharp
// csharp_indent_switch_labels = true
switch(c) {
    case Color.Red:
        Console.WriteLine("The color is red");
        break;
    case Color.Blue:
        Console.WriteLine("The color is blue");
        break;
    default:
        Console.WriteLine("The color is unknown.");
        break;
}

// csharp_indent_switch_labels = false
switch(c) {
case Color.Red:
    Console.WriteLine("The color is red");
    break;
case Color.Blue:
    Console.WriteLine("The color is blue");
    break;
default:
    Console.WriteLine("The color is unknown.");
    break;
}
```

**csharp\_indent_labels**  
Essa regra não aceita um valor **true** ou **false**; em vez disso, ela aceita um valor da tabela a seguir:  

| Valor | Descrição |
| ----- |:----------- |
| flush_left | Os rótulos são posicionados na coluna mais à esquerda |
| one_less_than_current | Os rótulos são posicionados em um recuo a menos do que o contexto atual |
| no_change | Os rótulos são posicionados no mesmo recuo do contexto atual |

Exemplos de código:  

```csharp
// csharp_indent_labels= flush_left
class C
{
    private string MyMethod(...) 
    {
        if (...) {
            goto error;
        }
error:
        throw new Exception(...);
    }
}

// csharp_indent_labels = one_less_than_current
class C
{
    private string MyMethod(...) 
    {
        if (...) {
            goto error;
        }
    error:
        throw new Exception(...);
    }
}

// csharp_indent_labels= no_change
class C
{
    private string MyMethod(...) 
    {
        if (...) {
            goto error;
        }
        error:
        throw new Exception(...);
    }
}
```

Exemplo de arquivo .editorconfig:  

```
# CSharp formatting settings:
[*.cs]
csharp_indent_case_contents = true
csharp_indent_switch_labels = true
csharp_indent_labels = flush_left
``` 

#### <a name="spacing">Opções de Espaçamento</a>  
Essas regras de formatação envolvem o uso de caracteres de espaço para formatar o código.  

A tabela a seguir mostra os nomes das regras, as linguagens aplicáveis, os valores padrão e a primeira versão compatível do Visual Studio:  

| Nome da regra | Linguagens Aplicáveis | Padrão do Visual Studio | Versão compatível |
| ----------- | -------------------- | ----------------------| ----------------  |
| csharp_space_after_cast |  C# | false | Visual Studio 2017 v. 15.3  |
| csharp_space_after_keywords_in_control_flow_statements |  C# | true | Visual Studio 2017 v. 15.3  |
| csharp_space_between_method_declaration_parameter_list_parentheses |  C# | false | Visual Studio 2017 v. 15.3  |
| csharp_space_between_method_call_parameter_list_parentheses |  C# | false | Visual Studio 2017 v. 15.3  |
| csharp_space_between_parentheses |  C# | false | Visual Studio 2017 v. 15.3  |

**csharp\_space\_after_cast**  
Quando essa regra é definida como **true**, exigir um espaço entre uma conversão e o valor.  
Quando essa regra é definida como **false**, _não_ exigir espaço entre a conversão e o valor.  

Exemplos de código:

```csharp
// csharp_space_after_cast = true
int y = (int) x;

// csharp_space_after_cast = false
int y = (int)x;
```

**csharp_space_after_keywords_in_control_flow_statements**  
Quando essa regra é definida como **true**, exigir um espaço depois de uma palavra-chave em uma instrução de fluxo de controle, como um `for` loop.  
Quando essa regra é definida como **false**, _não_ exigir um espaço depois de uma palavra-chave em uma instrução de fluxo de controle, como um loop `for`.  

Exemplos de código:

```csharp
// csharp_space_after_keywords_in_control_flow_statements = true
for (int i;i<x;i++) { ... }

// csharp_space_after_keywords_in_control_flow_statements = false
for(int i;i<x;i++) { ... }
```

**csharp_space_between_method_declaration_parameter_list_parentheses**  
Quando essa regra é definida como **true**, posicionar um caractere de espaço após o parêntese de abertura e antes do parêntese de fechamento de uma lista de parâmetros de declaração de método.  
Quando essa regra é definida como **false**, não posicionar caracteres de espaço após o parêntese de abertura e antes do parêntese de fechamento de uma lista de parâmetros de declaração de método.  

Exemplos de código:

```csharp
// csharp_space_between_method_declaration_parameter_list_parentheses = true
void Bark( int x ) { ... }

// csharp_space_between_method_declaration_parameter_list_parentheses = false
void Bark(int x) { ... }
```

**csharp_space_between_method_call_parameter_list_parentheses**  
Quando essa regra é definida como **true**, posicionar um caractere de espaço após o parêntese de abertura e antes do parêntese de fechamento de uma chamada de método.  
Quando essa regra é definida como **false**, não posicionar caracteres de espaço após o parêntese de abertura e antes do parêntese de fechamento de uma chamada de método.  

Exemplos de código:

```csharp
// csharp_space_between_method_call_parameter_list_parentheses = true
MyMethod( argument );

// csharp_space_between_method_call_parameter_list_parentheses = false
MyMethod(argument);
```

**csharp_space_between_parentheses**  
Essa regra não aceita um valor **true** ou **false**; em vez disso, ela aceita um valor da tabela a seguir:  

| Valor | Descrição |
| ----- |:------------|
| control_flow_statements | Inserir espaço entre parênteses das instruções de fluxo de controle |
| expressões | Inserir espaço entre os parênteses das expressões |
| type_casts | Inserir espaço entre os parênteses nas conversões de tipo |

Exemplos de código:

```csharp
// csharp_space_between_parentheses = control_flow_statements
for( int i;i<x;i++ ) { ... }

// csharp_space_between_parentheses = expressions
var z = ( x * y ) - ( ( y - x ) * 3);

// csharp_space_between_parentheses = type_casts
int y = ( int )x;
```

Exemplo de arquivo .editorconfig:  

```
# CSharp formatting settings:
[*.cs]
csharp_space_after_cast = true
csharp_space_after_keywords_in_control_flow_statements = true
csharp_space_between_method_declaration_parameter_list_parentheses = true
csharp_space_between_method_call_parameter_list_parentheses = true
csharp_space_between_parentheses = control_flow_statements, type_casts
``` 

#### <a name="wrapping">Opções de encapsulamento</a>
Essas regras de formatação referem-se ao uso de linhas únicas em comparação com linhas separadas para instruções e blocos de código.  

A tabela a seguir mostra os nomes das regras, as linguagens aplicáveis, os valores padrão e a primeira versão compatível do Visual Studio:  

| Nome da regra | Linguagens Aplicáveis | Padrão do Visual Studio | Versão compatível |
| ----------- | -------------------- | ----------------------| ----------------  |
| csharp_preserve_single_line_statements |  C# | true | Visual Studio 2017 v. 15.3  |
| csharp_preserve_single_line_blocks |  C# | true | Visual Studio 2017 v. 15.3  |

**csharp_preserve_single_line_statements**   
Quando essa regra é definida como **true**, deixar instruções e declarações de membro na mesma linha.  
Quando essa regra é definida como **false**, deixar instruções e declarações de membro em linhas diferentes.  

Exemplos de código:  

```csharp
//csharp_preserve_single_line_statements = true
int i = 0; string name = "John";

//csharp_preserve_single_line_statements = false
int i = 0; 
string name = "John";
```

**csharp_preserve_single_line_blocks**  
Quando essa regra é definida como **true**, deixar o bloco de código em linha única.  
Quando essa regra é definida como **false**, deixar o bloco de código em linhas separadas.  

Exemplos de código:  

```csharp
//csharp_preserve_single_line_blocks = true
public int Foo { get; set; }

//csharp_preserve_single_line_blocks = false
public int MyProperty
{ 
    get; set;
}
```

Exemplo de arquivo .editorconfig:  

```
# CSharp formatting settings:
[*.cs]
csharp_preserve_single_line_statements = true
csharp_preserve_single_line_blocks = true
```

## <a name="naming-conventions"></a>Convenções de nomenclatura  
As convenções de nomenclatura referem-se à nomenclatura dos elementos de código, como classes, propriedades e métodos. Por exemplo, você pode especificar que os métodos assíncronos devem terminar com "Async". As convenções de nomenclatura devem ser ordenadas da mais específica à menos específica. A primeira regra encontrada que pode ser aplicada é a única regra que é aplicada.  

Para cada regra de convenção de nomenclatura, identificada por **namingRuleTitle**, você deve especificar os **símbolos** aos quais ela se aplica, um **estilo** de nomenclatura e uma **gravidade**:  
  
`dotnet_naming_rule.<namingRuleTitle>.symbols = <symbolTitle>`  
`dotnet_naming_rule.<namingRuleTitle>.style = <styleTitle>`  
`dotnet_naming_rule.<namingRuleTitle>.severity = none|suggestion|warning|error`  

### <a name="symbols"></a>Símbolos
Identificar um grupo de símbolos ao qual aplicar uma regra de nomenclatura com essa propriedade: `dotnet_naming_rule.<namingRuleTitle>.symbols = <symbolTitle>`. Especificar quais tipos de símbolos, quais modificadores e quais níveis de acessibilidade estão incluídos no grupo usando as seguintes propriedades:  

| Propriedade | Valores possíveis |
| ------------- |:-------------:|
| dotnet\_naming\_symbols.\<symbolTitle\>.applicable\_kinds | *, class, struct, interface, enum, property, method, field, event, namespace, delegate, type_parameter |
| dotnet\_naming\_symbols.\<symbolTitle\>.applicable_accessibilities | *, public, internal (C#), friend (Visual Basic), private, protected, protected\_internal (C#), protected\_friend (Visual Basic) |
| dotnet\_naming\_symbols.\<symbolTitle\>.required\_modifiers | abstract (C#), must_inherit (Visual Basic), async, const, readonly, static (C#), shared (Visual Basic) |  

### <a name="style"></a>Estilo
Identificar o estilo de nomenclatura a ser aplicado a um grupo de símbolos com essa propriedade: `dotnet_naming_rule.<namingRuleTitle>.style = <styleTitle>`.  

Especificar o estilo de nomenclatura usando uma ou mais das seguintes propriedades:  

|  Propriedade | Valores possíveis |
| ------------- |:-------------:|
| dotnet_naming_style.\<styleTitle\>.required_prefix | Caracteres necessários que devem aparecer no início do identificador. |  
| dotnet_naming_style.\<styleTitle\>.required_suffix | Caracteres necessários que devem aparecer no final do identificador. |  
| dotnet_naming_style.\<styleTitle\>.word_separator | Caractere necessário entre as palavras no identificador. | 
| dotnet_naming_style.\<styleTitle\>.capitalization | pascal_case, camel_case, first_word_upper, all_upper, all_lower |

> [!NOTE]
> Você deve especificar um estilo de capitalização como parte do seu estilo de nomenclatura, caso contrário, o estilo de nomenclatura será ignorado.  

#### <a name="severity"></a>Severidade
Identificar o nível de gravidade de uma regra de nomenclatura com essa propriedade: `dotnet_naming_rule.<namingRuleTitle>.severity`.  

A tabela a seguir mostra as opções de valor de gravidade:  

Severidade | Efeito
------------ | -------------
nenhuma ou silenciosa | Quando esse estilo não estiver sendo seguido, não mostrar nada ao usuário. No entanto, os recursos de geração de código gerarão código novo nesse estilo.  
sugestão | Quando esse estilo não estiver sendo seguido, mostre-o para o usuário como uma sugestão (pontos subjacentes nos dois primeiros caracteres). Isso não terá nenhum efeito em tempo de compilação.  
aviso | Quando esse estilo não estiver sendo seguido, mostre um aviso do compilador.  
erro | Quando esse estilo não estiver sendo seguido, mostre um erro do compilador.   

### <a name="example-editorconfig-file-with-naming-conventions"></a>Arquivo .editorconfig de exemplo com as convenções de nomenclatura
```
# Dotnet Naming Conventions
[*.{cs,vb}] 
dotnet_naming_rule.async_methods_end_in_async.symbols  = any_async_methods
dotnet_naming_rule.async_methods_end_in_async.style    = end_in_async
dotnet_naming_rule.async_methods_end_in_async.severity = suggestion

dotnet_naming_symbols.any_async_methods.applicable_kinds           = method
dotnet_naming_symbols.any_async_methods.applicable_accessibilities = *
dotnet_naming_symbols.any_async_methods.required_modifiers         = async

dotnet_naming_style.end_in_async.required_suffix = Async
dotnet_naming_style.end_in_async.capitalization  = pascal_case
``` 

## <a name="see-also"></a>Consulte também
[Ações rápidas](../ide/quick-actions.md)  
[Criar opções do editor portátil e personalizado](https://docs.microsoft.com/en-us/visualstudio/ide/create-portable-custom-editor-options)  
[Arquivo .editorconfig da plataforma do compilador do .NET](https://github.com/dotnet/roslyn/blob/master/.editorconfig)  
