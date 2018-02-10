---
title: "Suprimir avisos da análise de código no Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 01/29/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.topic: article
helpviewer_keywords:
- source suppression, code analysis
- code analysis, source suppression
author: gewarren
ms.author: gewarren
manager: ghogen
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.openlocfilehash: 5862b164c72c8f07c78db8948face95edfde357c
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
---
# <a name="suppressing-code-analysis-warnings"></a>Suprimindo avisos da análise de código

Geralmente é útil indicar que um aviso não é aplicável. Isso indica a membros da equipe que o código foi revisado e que o aviso pode ser suprimido. Na origem supressão (ISS) usa o <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> atributo para suprimir um aviso. O atributo pode ser colocado perto o segmento de código que gerou o aviso. Você pode adicionar o <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> de atributo para o arquivo de origem, digitando-o, ou você pode usar o menu de atalho em um aviso de **lista de erros** para adicioná-lo automaticamente.

O <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> é um atributo condicional que é incluído nos metadados do seu assembly de código gerenciado, IL somente se o símbolo de compilação CODE_ANALYSIS é definido em tempo de compilação.

Em C + + CLI, use as macros da autoridade de certificação\_SUPRIMIR\_mensagem ou autoridade de certificação\_GLOBAL\_SUPPRESS_MESSAGE no arquivo de cabeçalho para adicionar o atributo.

> [!NOTE]
> Você não deve usar as supressões do código-fonte em compilações de versão, para impedir que os metadados de supressão na origem de envio acidentalmente. Além disso, devido ao custo de processamento de supressão de código-fonte, o desempenho do seu aplicativo pode ser degradado.

> [!NOTE]
> Se você migrar um projeto para Visual Studio de 2017, você pode encontrar repentinamente com um número excessivo de avisos da análise de código. Se você não estiver pronto para corrigir os avisos e deseja desativar temporariamente a análise de código, abra as páginas de propriedades do projeto (**projeto** > ***projeto* propriedades...** ) e vá para o **análise de código** guia. Desmarque **habilitar análise de código no Build**e, em seguida, recrie seu projeto. Como alternativa, você pode selecionar uma regra diferente, menor definida para ser executado com o código. Lembre-se de ativar a análise de código em quando estiver pronto para corrigir os avisos.

## <a name="suppressmessage-attribute"></a>Atributo SuppressMessage

Quando você escolhe **suprimir** no menu de contexto ou o botão direito do mouse de um aviso de análise de código no **lista de erros**, um <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> atributo é adicionado no seu código ou para supressão global do projeto arquivo.

O <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> atributo tem o seguinte formato:

```vb
<Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")>
```

```csharp
[Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")]
```

```cpp
CA_SUPPRESS_MESSAGE("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")
```

As propriedades do atributo incluem:

- **Categoria de regra** -a categoria na qual a regra está definida. Para obter mais informações sobre categorias de regras de análise de código, consulte [gerenciados avisos de código](../code-quality/code-analysis-for-managed-code-warnings.md).

- **Id de regra** -o identificador da regra. O suporte inclui tanto um nome curto e longo para o identificador de regra. O nome curto é CAXXXX; o nome longo é CAXXXX:FriendlyTypeName.

- **A justificação** -o texto que é usado para documentar o motivo para suprimir a mensagem.

- **Id de mensagem** -identificador exclusivo de um problema para cada mensagem.

- **Escopo** -o destino no qual o aviso está sendo suprimido. Se o destino não for especificado, ele é definido como o destino do atributo. Escopos com suporte incluem o seguinte:

    - Módulo

    - Namespace

    - Recurso

    - Tipo

    - Membro

- **Destino** - um identificador que é usado para especificar o destino no qual o aviso está sendo suprimido. Ele deve conter um nome totalmente qualificado de item.

## <a name="suppressmessage-usage"></a>Uso de SuppressMessage

Avisos da análise de código são suprimidos no nível ao qual o <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> atributo é aplicado. Por exemplo, o atributo pode ser aplicado no assembly, módulo, tipo, membro ou nível de parâmetro. O objetivo desse é acoplar totalmente as informações de supressão no código onde ocorre a violação.

A forma geral de supressão inclui a categoria de regra e um identificador de regra, que contém uma representação legível opcional do nome da regra. Por exemplo:

`[SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`

Se houver motivos de desempenho estrito para minimizar os metadados de supressão na origem, o nome da regra pode ser omitido. A categoria de regra e sua ID da regra juntos constituem um identificador de regra suficientemente exclusivo. Por exemplo:

`[SuppressMessage("Microsoft.Design", "CA1039")]`

Por motivos de manutenção, não é recomendável omitir o nome da regra.

## <a name="suppressing-selective-violations-within-a-method-body"></a>Suprimindo seletivas violações dentro de um corpo de método

Atributos de supressão podem ser aplicados a um método, mas não podem ser inseridos em um corpo de método. Isso significa que todas as violações de uma determinada regra são suprimidas, se você adicionar o <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> atributo ao método.

Em alguns casos, você talvez queira suprimir uma instância específica de violação, por exemplo, para que o código futuro não é automaticamente isento da regra de análise de código. Certas regras de análise de código permitem que você faça isso usando o `MessageId` propriedade o <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> atributo. Em geral, herdado regras para violações de uma relação de símbolo específico (uma variável local ou parâmetro) de `MessageId` propriedade. [CA1500:VariableNamesShouldNotMatchFieldNames](../code-quality/ca1500-variable-names-should-not-match-field-names.md) é um exemplo de tal uma regra. No entanto, as regras herdadas de violações de código executável (não símbolo) não respeitam o `MessageId` propriedade. Além disso, os analisadores de plataforma de compilador .NET ("Roslyn") não respeitam o `MessageId` propriedade.

Para suprimir uma violação de símbolo específico de uma regra, especifique o nome do símbolo para o `MessageId` propriedade o <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> atributo. O exemplo a seguir mostra o código com dois violações de [CA1500:VariableNamesShouldNotMatchFieldNames](../code-quality/ca1500-variable-names-should-not-match-field-names.md)&mdash;um para o `name` variável e uma para o `age` variável. Somente a violação para o `age` símbolo será suprimido.

```vb
Public Class Animal
    Dim age As Integer
    Dim name As String

    <CodeAnalysis.SuppressMessage("Microsoft.Maintainability", "CA1500:VariableNamesShouldNotMatchFieldNames", MessageId:="age")>
    Sub PrintInfo()
        Dim age As Integer = 5
        Dim name As String = "Charlie"

        Console.WriteLine("Age {0}, Name {1}", age, name)
    End Sub

End Class
```

```csharp
public class Animal
{
    int age;
    string name;

    [System.Diagnostics.CodeAnalysis.SuppressMessage("Microsoft.Maintainability", "CA1500:VariableNamesShouldNotMatchFieldNames", MessageId = "age")]
    private void PrintInfo()
    {
        int age = 5;
        string name = "Charlie";

        Console.WriteLine($"Age {age}, Name {name}");
    }
}
```

## <a name="generated-code"></a>Código gerado

Compiladores de código gerenciado e algumas ferramentas de terceiros geram código para facilitar o desenvolvimento rápido de código. Código gerado pelo compilador que aparece nos arquivos de origem geralmente é marcado com o `GeneratedCodeAttribute` atributo.

Você pode escolher se deseja suprimir avisos da análise de código e erros de código gerado. Para obter informações sobre como suprimir esses erros e avisos, consulte [como: suprimir avisos para código gerado pelo](../code-quality/how-to-suppress-code-analysis-warnings-for-generated-code.md).

> [!NOTE]
> Análise de código ignora `GeneratedCodeAttribute` quando ele é aplicado a um assembly ou um único parâmetro.

## <a name="global-level-suppressions"></a>Supressões no nível global

A ferramenta de análise de código gerenciado examina `SuppressMessage` atributos aplicados no nível de assembly, módulo, tipo, membro ou parâmetro. Também será acionado violações em relação a recursos e namespaces. Essas violações devem ser aplicadas no nível global no escopo e são direcionadas. Por exemplo, a seguinte mensagem suprime uma violação de namespace:

`[module: SuppressMessage("Microsoft.Design", "CA1020:AvoidNamespacesWithFewTypes", Scope = "namespace", Target = "MyNamespace")]`

> [!NOTE]
> Quando você suprimir um aviso com escopo de namespace, ele suprime o aviso no namespace em si. Ele não suprime o aviso contra tipos no namespace.

Qualquer supressão pode ser expresso com a especificação de um escopo explícito. Esses supressões devem residir no nível global. Você não pode especificar a supressão de nível de membro de decoração de um tipo.

Supressões no nível global são a única maneira de suprimir mensagens que fazem referência ao código gerado pelo compilador que não é mapeado para a origem de usuário fornecido explicitamente. Por exemplo, o código a seguir suprime uma violação em um construtor emitido pelo compilador:

`[module: SuppressMessage("Microsoft.Design", "CA1055:AbstractTypesDoNotHavePublicConstructors", Scope="member", Target="Microsoft.Tools.FxCop.Type..ctor()")]`

> [!NOTE]
> `Target`sempre contém o nome totalmente qualificado de item.

## <a name="global-suppression-file"></a>Arquivo de supressão global

O arquivo de supressão global mantém supressões supressões no nível global ou supressões que não especificam um destino. Por exemplo, supressões de violações de nível de assembly são armazenadas nesse arquivo. Além disso, alguns supressões do ASP.NET são armazenadas neste arquivo porque as configurações de nível de projeto não estão disponíveis para o código por trás de um formulário. Um arquivo de supressão global é criado e adicionado ao seu projeto na primeira vez que você selecionar o **no arquivo de supressão do projeto** opção do **suprimir** do **lista de erros**janela.

## <a name="see-also"></a>Consulte também

<xref:System.Diagnostics.CodeAnalysis>