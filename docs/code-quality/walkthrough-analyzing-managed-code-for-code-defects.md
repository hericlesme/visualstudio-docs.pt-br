---
title: Instruções passo a passo Analisando código gerenciado em busca de defeitos de código | Microsoft Docs
ms.date: 01/29/2018
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis [Visual Studio]
- managed code, analyzing
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 98d1bbd347870bd704a0d17d7ae559da00e9adb5
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/19/2018
---
# <a name="walkthrough-analyzing-managed-code-for-code-defects"></a>Passo a passo: Analisando código gerenciado para código defeitos

Neste passo a passo, você poderá analisar um projeto gerenciado em busca de defeitos de código usando a ferramenta de análise de código.

Este passo a passo o orienta o processo de usar a análise de código para analisar seus assemblies de código gerenciado do .NET para conformidade com as diretrizes de design do Microsoft .NET Framework.

## <a name="create-a-class-library"></a>Criar uma biblioteca de classes

### <a name="to-create-a-class-library"></a>Para criar uma biblioteca de classes

1. No menu **Arquivo**, escolha **Novo** > **Projeto...**.

1. No **novo projeto** caixa de diálogo caixa, expanda **instalado** > **Visual C#** e, em seguida, escolha **área de trabalho clássica do Windows**.

1. Escolha o **biblioteca de classes (.NET Framework)** modelo.

1. No **nome** caixa de texto, digite **CodeAnalysisManagedDemo** e, em seguida, clique em **Okey**.

1. Depois que o projeto é criado, abra a *Class1.cs* arquivo.

1. Substitua o texto existente em Class1. cs com o código a seguir:

   ```csharp
   using System;

   namespace testCode
   {
       public class demo : Exception
       {
           public static void Initialize(int size) { }
           protected static readonly int _item;
           public static int item { get { return _item; } }
       }
   }
   ```

1. Salve o arquivo Class1.cs.

## <a name="analyze-the-project"></a>Analisar o projeto

### <a name="to-analyze-a-managed-project-for-code-defects"></a>Para analisar um projeto gerenciado em busca de defeitos de código

1. Selecione o projeto CodeAnalysisManagedDemo na **Gerenciador de soluções**.

1. No menu **Projeto**, clique em **Propriedades**.

     A página de propriedades CodeAnalysisManagedDemo é exibida.

1. Escolha o **análise de código** guia.

1. Verifique se **habilitar análise de código na compilação** é verificada.

1. Do **executar esse conjunto de regras** lista suspensa, selecione **Microsoft todas as regras**.

1. Sobre o **arquivo** menu, clique em **salvar itens selecionados**e, em seguida, feche as páginas de propriedades.

1. No **criar** menu, clique em **CodeAnalysisManagedDemo criar**.

    Os avisos de compilação de projeto CodeAnalysisManagedDemo são mostrados no **lista de erros** e **saída** windows.

## <a name="correct-the-code-analysis-issues"></a>Corrija os problemas de análise de código

### <a name="to-correct-code-analysis-rule-violations"></a>Para corrigir as violações de regras de análise de código

1. Sobre o **exibição** menu, escolha **lista de erros**.

    Dependendo do perfil de desenvolvedor que você escolheu, talvez você precise aponte para **outras janelas** no **exibição** menu e, em seguida, escolha **lista de erros**.

1. Em **Solution Explorer**, escolha **Mostrar todos os arquivos**.

1. Expanda o nó de propriedades e, em seguida, abra o *AssemblyInfo.cs* arquivo.

1. Use as dicas a seguir para corrigir os avisos:

   [CA1014: Marcar assemblies com CLSCompliantAttribute](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md): Microsoft.Design: 'demonstração' deve ser marcada com CLSCompliantAttribute e seu valor deve ser true.

   1. Adicione o código `using System;` para o arquivo AssemblyInfo.

   1. Em seguida, adicione o código `[assembly: CLSCompliant(true)]` até o final do arquivo AssemblyInfo.

   [CA1032: Implementar construtores de exceção padrão](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: Adicione o seguinte construtor para essa classe: demo(String) pública

   1. Adicionar o construtor `public demo (String s) : base(s) { }` para a classe `demo`.

   [CA1032: Implementar construtores de exceção padrão](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: Adicione o seguinte construtor para essa classe: demonstração pública (cadeia de caracteres, exceção)

   1. Adicionar o construtor `public demo (String s, Exception e) : base(s, e) { }` para a classe `demo`.

   [CA1032: Implementar construtores de exceção padrão](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: Adicione o seguinte construtor para essa classe: protegido demonstração (SerializationInfo, StreamingContext)

   1. Adicione o código `using System.Runtime.Serialization;` para o início do arquivo Class1.cs.

   1. Em seguida, adicione o construtor `protected demo (SerializationInfo info, StreamingContext context) : base(info, context) { } to the class demo.`

   [CA1032: Implementar construtores de exceção padrão](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: Adicione o seguinte construtor para essa classe: demo() pública

   1. Adicionar o construtor `public demo () : base() { }` para a classe `demo` **.**

   [CA1709: Os identificadores devem ter maiusculas e minúsculas corretamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming: corrija o uso de maiusculas e minúsculas do nome do namespace 'testCode' alterando-o para 'TestCode'.

   1. Alterar o uso de maiusculas e minúsculas do namespace `testCode` para `TestCode`.

   [CA1709: Os identificadores devem ter maiusculas e minúsculas corretamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming: corrija o uso de maiusculas e minúsculas do tipo nome 'demonstração' alterando-o para 'Demonstração'.

   1. Alterar o nome do membro `Demo`.

   [CA1709: Os identificadores devem ter maiusculas e minúsculas corretamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming: corrija o uso de maiusculas e minúsculas do item' nome de membro' alterando-o para 'Item'.

   1. Alterar o nome do membro `Item`.

   [CA1710: Os identificadores devem ter sufixo correto](../code-quality/ca1710-identifiers-should-have-correct-suffix.md): Microsoft.Naming: Renomear 'testCode.demo' termine em 'Exception'.

   1. Alterar o nome da classe e seus construtores para `DemoException`.

   [CA2210: Os Assemblies devem ter nomes fortes válidos](../code-quality/ca2210-assemblies-should-have-valid-strong-names.md): assinar 'CodeAnalysisManagedDemo' com uma chave de nome forte.

   1. Sobre o **projeto** menu, escolha **CodeAnalysisManagedDemo propriedades**.

      As propriedades de projeto aparecem.

   1. Escolha a guia **Assinatura**.

   1. Selecione o **assinar o assembly** caixa de seleção.

   1. No **escolher um arquivo de chave de nome de cadeia de caracteres** lista, selecione  **\<novo... >**.

      O **criar chave de nome forte** caixa de diálogo é exibida.

   1. No **nome do arquivo de chave**, digite TestKey.

   1. Insira uma senha e, em seguida, escolha **Okey**.

   1. Sobre o **arquivo** menu, escolha **salvar itens selecionados**e, em seguida, feche as páginas de propriedades.

   [CA2237: Marcar tipos ISerializable com SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md): Microsoft.Usage: adicionar um atributo [Serializable] para o tipo 'demonstração', pois este tipo implementa ISerializable.

   1. Adicionar o `[Serializable ()]` de atributo para a classe `demo`.

   Depois de concluir as alterações, o arquivo Class1.cs deve parecer com o seguinte:

   ```csharp
   using System;
   using System.Runtime.Serialization;

   namespace TestCode
   {
       [Serializable()]
       public class DemoException : Exception
       {
           public DemoException () : base() { }
           public DemoException(String s) : base(s) { }
           public DemoException(String s, Exception e) : base(s, e) { }
           protected DemoException(SerializationInfo info, StreamingContext context) : base(info, context) { }

           public static void Initialize(int size) { }
           protected static readonly int _item;
           public static int Item { get { return _item; } }
       }
   }
   ```

1. Recompile o projeto.

## <a name="exclude-code-analysis-warnings"></a>Excluir avisos da análise de código

### <a name="to-exclude-code-defect-warnings"></a>Para excluir os avisos de defeito de código

1. Para cada um dos avisos restantes, faça o seguinte:

    1. Selecione o aviso no **lista de erros**.

    1. No menu de contexto ou o botão direito do mouse, escolha **suprimir** > **no arquivo de supressão**.

1. Recompile o projeto.

     O projeto é compilado sem avisos ou erros.

## <a name="see-also"></a>Consulte também

[Análise de código para código gerenciado](../code-quality/code-analysis-for-managed-code-overview.md)