---
title: "Analisadores de Roslyn e reconhecimento de código de biblioteca para ImmutableArrays | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0b0afa22-3fca-4d59-908e-352464c1d903
caps.latest.revision: "5"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 6870f1733d507f2cf46d196b2bba027b998b5ba4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="roslyn-analyzers-and-code-aware-library-for-immutablearrays"></a>Analisadores de Roslyn e reconhecimento de código de biblioteca para ImmutableArrays

O [plataforma de compilador .NET](https://github.com/dotnet/roslyn) ("Roslyn") ajuda a criar bibliotecas de código.  Uma biblioteca com reconhecimento de código fornece funcionalidade que você pode usar e ferramentas (Roslyn analisadores) para ajudá-lo a usar a biblioteca da melhor maneira ou para evitar erros.  Este tópico mostra como criar um analisador de Roslyn do mundo real para capturar erros comuns ao usar o [System.Collections.Immutable](https://www.nuget.org/packages/System.Collections.Immutable) pacote NuGet.  O exemplo também demonstra como fornecer uma correção de código para um problema de código encontrado pelo analisador.  Os usuários Consulte correções de código de lâmpada da interface do usuário do Visual Studio e podem aplicar uma correção para o código automaticamente.

## <a name="getting-started"></a>Guia de Introdução

Você precisa do seguinte para criar este exemplo:

* Visual Studio 2015 (não uma edição Express) ou uma versão posterior.  Você pode usar a versão gratuita [Visual Studio Community Edition](https://www.visualstudio.com/products/visual-studio-community-vs)
* [SDK do Visual Studio](../extensibility/visual-studio-sdk.md).  Você também pode, ao instalar o Visual Studio, verificar ferramentas de extensibilidade do Visual Studio em ferramentas comuns para instalar o SDK ao mesmo tempo.  Se você já tiver instalado o Visual Studio, você também pode instalar o SDK, vá ao menu principal **arquivo &#124; Novo &#124; Projeto...** , escolhendo c# no painel de navegação esquerdo e, em seguida, extensibilidade.  Quando você escolhe o "**instalar as ferramentas de extensibilidade do Visual Studio**" modelo de projeto de navegação estrutural, ele solicitará que você baixe e instale o SDK.
* [Plataforma de compilador .NET ("Roslyn") SDK](http://aka.ms/roslynsdktemplates).  Você também pode instalar o SDK, vá ao menu principal **arquivo &#124; Novo &#124; Projeto...** , escolhendo **c#** no painel de navegação esquerdo e, em seguida, escolhendo **extensibilidade**.  Quando você escolhe "**baixar o SDK de plataforma do compilador .NET**" modelo de projeto de navegação estrutural, ele solicitará que você baixe e instale o SDK.  Esse SDK inclui o [Roslyn sintaxe visualizador](https://github.com/dotnet/roslyn/wiki/Syntax%20Visualizer).  Isso o ajuda a ferramenta extremamente útil saber quais tipos de modelo de código você deve procurar no seu analisador.  As chamadas de infraestrutura de analisador em seu código para tipos de modelo de código específico, para que seu código só é executada quando necessário e pode se concentrar apenas em análise de código relevante.

## <a name="whats-the-problem"></a>Qual é o problema?

Imagine que você fornecer uma biblioteca com ImmutableArray (por exemplo, <xref:System.Collections.Immutable.ImmutableArray%601?displayProperty=fullName>) oferecem suporte.  Os desenvolvedores do c# tem muita experiência com matrizes de .NET.  No entanto, devido à natureza de técnicas de ImmutableArrays e de otimização usada na implementação, intuitions de desenvolvedor c# fazer com que os usuários da sua biblioteca escrever código desfeito, conforme explicado a seguir.  Além disso, os usuários não veem seus erros tempo de execução, o que não é a experiência de qualidade que são usados para no Visual Studio com .NET.

Os usuários estão familiarizados com a escrita de código semelhante ao seguinte:

```csharp
var a1 = new int[0];
Console.WriteLine("a1.Length = { 0}", a1.Length);
var a2 = new int[] { 1, 2, 3, 4, 5 };
Console.WriteLine("a2.Length = { 0}", a2.Length);
```

Criação de matrizes vazias para preencher com linhas subsequentes de código e usando a sintaxe do inicializador de coleção são muito familiares para desenvolvedores do c#.  No entanto, o código para um ImmutableArray escrevendo o mesmo falha em tempo de execução:

```csharp
var b1 = new ImmutableArray<int>();
Console.WriteLine("b1.Length = { 0}", b1.Length);
var b2 = new ImmutableArray<int> { 1, 2, 3, 4, 5 };
Console.WriteLine("b2.Length = { 0}", b2.Length);
```

É o primeiro erro devido a implementação de ImmutableArray usando uma estrutura para encapsular o armazenamento de dados subjacente. Estruturas devem ter construtores sem parâmetros para que `default(T)` expressões podem retornar com todas as estruturas de zero ou nulo membros.  Quando o código acessa `b1.Length`, há uma tempo de execução cancelamento de referência nula erro porque não há nenhuma matriz de armazenamento subjacente na estrutura ImmutableArray.  A maneira correta para criar um ImmutableArray vazio é `ImmutableArray<int>.Empty`.

Erro com inicializadores de coleção acontece porque o método ImmutableArray.Add retorna novas instâncias de cada vez que você chamá-lo.  Como ImmutableArrays nunca ser alterado, quando você adiciona um novo elemento, você voltar um novo objeto de ImmutableArray (que pode compartilhar o armazenamento por motivos de desempenho com um ImmutableArray já existente).  Porque `b2` aponta para a primeira ImmutableArray antes de chamar `Add()` cinco vezes, `b2` é um padrão ImmutableArray.  Chamando comprimento nele também falha com um valor nulo desreferenciamento do erro.  A maneira correta de inicializar um ImmutableArray sem manualmente chamar o método Add é usar `ImmutableArray.CreateRange(new int[] {1, 2, 3, 4, 5})`.

## <a name="finding-relevant-syntax-node-types-to-trigger-your-analyzer"></a>Localizando os tipos de nó de sintaxe relevantes para disparar o analisador

 Para começar a criar o analisador, primeiro descobrir que tipo de SyntaxNode necessário procurar. Inicie o Visualizador de sintaxe no menu **exibição &#124; Outras janelas &#124; Visualizador de sintaxe Roslyn**.

Coloque o cursor do editor na linha que declara `b1`.  Você verá o Visualizador de sintaxe mostra estão em um `LocalDeclarationStatement` nó da árvore de sintaxe.  Este nó tem um `VariableDeclaration`, que por sua vez tem um `VariableDeclarator`, que por sua vez tem um `EqualsValueClause`e, finalmente, há um `ObjectCreationExpression`.  Ao clicar na árvore de sintaxe Visualizador de nós, a sintaxe na janela do editor realça para mostrar o código representado por esse nó.  Os nomes dos tipos sub SyntaxNode corresponder os nomes usados na gramática do c#.

## <a name="creating-the-analyzer-project"></a>Criando o projeto do analisador

No menu principal, escolha **arquivo &#124; Novo &#124; Projeto...** .  No **novo projeto** caixa de diálogo, em **c#** projetos na barra de navegação à esquerda, escolha a extensibilidade em no painel direito, escolha o **analisador com correções de código** projeto modelo.  Insira um nome e confirmar a caixa de diálogo.

O modelo abre um arquivo de DiagnosticAnalyzer.cs.  Escolha esse editor de guia de buffer.  Este arquivo tem uma classe de analisador (formado do nome que você atribuiu o projeto) que deriva de `DiagnosticAnalyzer` (um tipo Roslyn API).  Sua nova classe tiver um `DiagnosticAnalyzerAttribute` declarar o analisador é relevante para a linguagem c# para que o compilador detecta e carrega o analisador.

```csharp
[DiagnosticAnalyzer(LanguageNames.CSharp)]
public class ImmutableArrayAnalyzerAnalyzer : DiagnosticAnalyzer
{}
```

Você pode implementar um analisador usando o Visual Basic que se destina a código c#, e vice-versa.  É mais importante em DiagnosticAnalyzerAttribute para escolher se o analisador tem como alvo um idioma ou ambos.  Analisadores mais sofisticadas que exigem modelagem detalhada da linguagem podem direcionar apenas um único idioma.  Se o analisador, por exemplo, verifica apenas nomes de tipo ou membro público, pode ser possível usar o modelo de linguagem comum que roslyn oferece em Visual Basic e c#.  Por exemplo, o FxCop avisa que implementa uma classe <xref:System.Runtime.Serialization.ISerializable>, mas a classe não tem o <xref:System.SerializableAttribute> atributo é independente de linguagem e funciona para o código do Visual Basic e c#.

## <a name="initalizing-the-analyzer"></a>Inicializar o analisador

 Role para baixo um pouco no `DiagnosticAnalyzer` classe para ver o `Initialize` método.  O compilador chama esse método ao ativar um analisador.  O método usa um `AnalysisContext` objeto que permite que o analisador para obter informações de contexto e registrar retornos de chamada para eventos para os tipos de código que você deseja analisar.

```csharp
public override void Initialize(AnalysisContext context) {}

```

Abrir uma nova linha neste método e o tipo de "contexto." Para ver uma lista de conclusão do IntelliSense.  Você pode ver na lista de conclusão, existem vários `Register...` métodos para lidar com vários tipos de eventos.  Por exemplo, o primeiro deles, `RegisterCodeBlockAction`, chamadas para o seu código para um bloco, que normalmente é o código entre as chaves.  Registrar-se para um bloco também chama seu código para o inicializador de um campo, o valor fornecido para um atributo ou o valor de um parâmetro opcional.

Como outro exemplo, `RegisterCompilationStartAction`, chamadas para o seu código no início de uma compilação, o que é útil quando você precisa coletar estado em vários locais.  Você pode criar uma estrutura de dados, digamos, para coletar todos os símbolos usados, e cada vez que o analisador é o retorno de chamada para alguns sintaxe ou o símbolo, você pode salvar informações sobre cada local em sua estrutura de dados.  Quando você voltar devido ao final de compilação, você pode analisar todos os locais que você salvou, por exemplo, para relatar os símbolos que usa o código de cada `using` instrução.

Usando o **sintaxe visualizador**, você aprendeu que você deseja ser chamado quando o compilador processa um ObjectCreationExpression.  Use este código para configurar o retorno de chamada:

```csharp
context.RegisterSyntaxNodeAction(c => AnalyzeObjectCreation(c),
                                 SyntaxKind.ObjectCreationExpression);
```

Você se registrar para um nó de sintaxe e filtrar apenas criação sintaxe nós de objeto.  Por convenção, os autores do analisador usam uma expressão lambda ao registrar ações, que ajuda a manter os analisadores sem monitoração de estado.  Você pode usar o recurso do Visual Studio **gerar de uso** para criar o `AnalyzeObjectCreation` método.  Isso gera muito o tipo correto de parâmetro de contexto para você.

## <a name="setting-properties-for-users-of-your-analyzer"></a>Propriedades de configuração para os usuários do seu Analyzer

Para que o analisador aparece na interface de usuário do Visual Studio corretamente, procure e modifique a seguinte linha de código para identificar o analisador de:

```csharp
internal const string Category = "Naming";
```

Change `"Naming"` to `"API Guidance"`.

Em seguida localize e abra a `Resources.resx` arquivo no seu projeto usando o **Gerenciador de soluções**.  Você pode colocar em uma descrição para o analisador, título, etc.  Você pode alterar o valor para todos eles para `"Don't use ImmutableArray<T> constructor"` por enquanto.  Você pode colocar a cadeia de caracteres de formatação de argumentos na sua cadeia de caracteres ({0}, \\{1 \\}, etc.) e posteriormente, quando você chamar `Diagnostic.Create()`, você pode fornecer um `params` matriz de argumentos a serem passados.

## <a name="analyzing-an-object-creation-expression"></a>Analisar uma expressão de criação de objeto

O `AnalyzeObjectCreation` método usa um tipo de contexto fornecido pela estrutura de analisador de código diferente.  O método de inicialização `AnalysisContext` permite registrar retornos de chamada de ação para configurar o analisador.  O `SyntaxNodeAnalysisContext`, por exemplo, tem um `CancellationToken` que você pode passar ao redor.  Se um usuário começa a digitar no editor, Roslyn cancelará analisadores em execução para salvar o trabalho e melhorar o desempenho.  Como outro exemplo, neste contexto tem uma propriedade de nó que retorna o nó de sintaxe de criação do objeto.

Obtém o nó, que você pode considerar é o tipo para o qual você filtrado a ação de nó de sintaxe:

```csharp
var objectCreation = (ObjectCreationExpressionSyntax)context.Node;
```

### <a name="launching-visual-studio-with-your-analyzer-the-first-time"></a>Iniciar o Visual Studio com o analisador na primeira vez

Inicie o Visual Studio por compilar e executar o analisador (pressione **F5**).  Porque a inicialização do projeto no **Solution Explorer** é o projeto VSIX, executando as compilações de código seu código e um VSIX e, em seguida, inicia o Visual Studio com esse VSIX instalada.  Quando você inicia o Visual Studio dessa maneira, ela inicia com um hive de registro distintas para que seu uso principal do Visual Studio não será afetado por suas instâncias de teste durante a criação de analisadores.  Na primeira vez que você iniciar dessa forma, o Visual Studio faz várias inicializações semelhantes quando é iniciado pela primeira vez o Visual Studio depois da instalação.

Crie um projeto de console e, em seguida, insira o código de matriz para o método de principal de aplicativos de console:

```csharp
var b1 = new ImmutableArray<int>();
Console.WriteLine("b1.Length = {0}", b1.Length);
var b2 = new ImmutableArray<int> { 1, 2, 3, 4, 5 };
Console.WriteLine("b2.Length = {0}", b2.Length);
```

As linhas de código com `ImmutableArray` tem linhas onduladas porque você precisa obter o pacote NuGet imutável e adicionar um `using` instrução ao seu código.  Pressione o botão direito do ponteiro no nó do projeto no **Solution Explorer** e escolha **gerenciar pacotes NuGet...** .  No Gerenciador do NuGet, digite "Imutável" na caixa de pesquisa e escolher o item "System.Collections.Immutable" (não escolher "Microsoft.Bcl.Immutable") no painel esquerdo e pressione o botão instalar no painel direito.  Instalando o pacote adiciona uma referência para as referências do projeto.

Você ainda vir linhas onduladas vermelhas sob `ImmutableArray`, assim, coloque o cursor na identificador e pressione **CTRL +.** (ponto) para acessar o menu de correção sugerida e optar por adicionar apropriada `using` instrução.

**Salve e feche** a segunda instância do Visual Studio agora para colocá-lo em um estado limpo para continuar.

## <a name="finishing-the-analyzer-using-edit-and-continue"></a>Usando o analisador de terminar de editar e continuar

Na primeira instância do Visual Studio, defina um ponto de interrupção no início de sua `AnalyzeObjectCreation` método pressionando **F9** com o cursor na primeira linha.

Iniciar o analisador novamente com **F5**e na segunda instância do Visual Studio, abra novamente o seu aplicativo de console é criada na última vez.

Retornar para a primeira instância do Visual Studio no ponto de interrupção porque o compilador Roslyn viu uma expressão de criação de objeto e chamada para o analisador.

**Obtém o nó de criação do objeto.** Passar sobre a linha que define o `objectCreation` variável pressionando **F10**e no **janela imediata** avaliar a expressão `"objectCreation.ToString()"`.  Você verá que a variável aponta para o nó de sintaxe está o código `"new ImmutableArray<int>()"`, apenas o que você está procurando.

**Obter ImmutableArray < T\> objeto de tipo.** Você precisa verificar se o tipo que está sendo criado é ImmutableArray.  Primeiro, você obtém o objeto que representa esse tipo.  Você verificar tipos usando o modelo semântico para garantir que você tem exatamente o tipo correto, e não comparar a cadeia de caracteres de ToString ().  Digite a seguinte linha de código no final da função:

```csharp
var immutableArrayOfTType =
    context.SemanticModel
           .Compilation
           .GetTypeByMetadataName("System.Collections.Immutable.ImmutableArray`1");
```

Você designar tipos genéricos em metadados com backquotes (') e o número de parâmetros genéricos.  Por essa razão, você não vir "... ImmutableArray\<T > "no nome de metadados.

O modelo semântico tem muitos recursos úteis que lhe permitem fazer perguntas sobre símbolos, fluxo de dados, tempo de vida de variável, etc.  Roslyn separa os nós de sintaxe do modelo semântico por várias razões de engenharia (desempenho, modelagem códigos incorretos, etc.).  Você deseja que o modelo de compilação para pesquisar informações contidas nas referências para comparação de precisa.

Você pode arrastar o ponteiro de execução amarelo no lado esquerdo da janela do editor.  Arraste-o até a linha que define o `objectCreation` variável e passar sobre a nova linha de código usando **F10**.  Se você passar o ponteiro do mouse sobre a variável `immutableArrayOfType`, você verá que encontramos o tipo exato do modelo semântico.

**Obtém o tipo da expressão de criação de objeto.** "Type" é usado em algumas maneiras neste artigo, mas isso significa que se você tiver "Foo novo" expressão, você precisa obter um modelo de Foo.  Você precisa obter o tipo da expressão de criação de objeto para ver se ele é a ImmutableArray\<T > tipo.  Use o modelo semântico novamente para obter informações de símbolo para o símbolo de tipo (ImmutableArray) na expressão de criação de objeto.  Digite a seguinte linha de código no final da função:

```csharp
var symbolInfo = context.SemanticModel.GetSymbolInfo(objectCreation.Type).Symbol as INamedTypeSymbol;
```

Porque o analisador precisa lidar com código incompleto ou incorreto em buffers do editor (por exemplo, há uma falta `using` instrução), você deve verificar `symbolInfo` sendo `null`.  Você precisa obter um tipo nomeado (INamedTypeSymbol) do objeto de informações de símbolo para concluir a análise.

**Compare os tipos.** Como há um tipo genérico aberto de T que estamos procurando, e o tipo no código é um tipo genérico concreto, consultar as informações de símbolo para que o tipo é construído a partir (um tipo genérico aberto) e comparar o resultado com `immutableArrayOfTType`.  Digite o seguinte no final do método:

```csharp
if (symbolInfo != null &&
    symbolInfo.ConstructedFrom.Equals(immutableArrayOfTType))
{}
```

**Relatório de diagnóstico.** Relatório de diagnóstico é muito fácil.  Você usar a regra criada para você no modelo de projeto, que é definido antes do método Initialize.  Como essa situação em que o código de erro, você pode alterar a linha que inicializado regra substituir `DiagnosticSeverity.Warning` (Rabisco verde) com `DiagnosticSeverity.Error` (Rabisco vermelho).  O restante da regra inicializa a partir dos recursos que você editou próximo ao início do passo a passo.  Você também precisa o local para o rabisco, que é o local da especificação de tipo da expressão de criação de objeto de relatório.  Insira este código no `if` bloco:

```csharp
context.ReportDiagnostic(Diagnostic.Create(Rule, objectCreation.Type.GetLocation()));
```

A função deve ser assim (talvez formatadas diferentemente):

```csharp
private void AnalyzeObjectCreation(SyntaxNodeAnalysisContext context)
{
    var objectCreation = (ObjectCreationExpressionSyntax)context.Node;
    var immutableArrayOfTType =
        context.SemanticModel
               .Compilation
               .GetTypeByMetadataName(
                   "System.Collections.Immutable.ImmutableArray`1");
    var symbolInfo = context.SemanticModel.GetSymbolInfo(objectCreation.Type).Symbol as
        INamedTypeSymbol;
    if (symbolInfo != null &&
        symbolInfo.ConstructedFrom.Equals(immutableArrayOfTType))
    {
        context.ReportDiagnostic(
            Diagnostic.Create(Rule, objectCreation.Type.GetLocation()));
    }
}
```

Remova o ponto de interrupção para que você possa ver o trabalho de analisador (e parem de retornar para a primeira instância do Visual Studio).  Arraste o ponteiro de execução para o início do método e pressione **F5** para continuar a execução.  Quando você alternar de volta para a segunda instância do Visual Studio, o compilador será iniciado para examinar o código novamente, e ele chamará o analisador.  Você pode ver um rabisco sob `ImmutableType<int>`.

## <a name="adding-a-code-fix-for-the-code-issue"></a>Adicionando uma correção"código" para o problema de código

Antes de começar, feche a segunda instância do Visual Studio e parar a depuração na primeira instância do Visual Studio (onde você está desenvolvendo o analisador de).

**Adicione uma nova classe.** Use o menu de atalho (botão de ponteiro à direita) no nó do seu projeto no Gerenciador de soluções e escolha Adicionar um novo item.  Adicionar uma classe chamada `BuildCodeFixProvider`.  Essa classe deve derivar de `CodeFixProvider`, e você precisará usar **CTRL +.** (ponto) para invocar a correção de código que adiciona o correto `using` instrução.  Essa classe também precisa ser anotada com `ExportCodeFixProvider` atributo e você precisará adicionar um `using` instrução para resolver o `LanguageNames` enum.  Você deve ter um arquivo de classe com o seguinte código:

```csharp
using Microsoft.CodeAnalysis;
using Microsoft.CodeAnalysis.CodeFixes;

namespace ImmutableArrayAnalyzer
{
    [ExportCodeFixProvider(LanguageNames.CSharp)]
    class BuildCodeFixProvider : CodeFixProvider
    {}

```

**Um stub membros derivados.** Agora, coloque o cursor do editor no identificador de `CodeFixProvider` e pressione **CTRL +.** (ponto) para a implementação para essa classe base abstrata de stub.  Isso gera uma propriedade e um método para você.

**Implementa a propriedade.** Preencha o `FixableDiagnosticIds` da propriedade `get` corpo com o código a seguir:

```csharp
return ImmutableArray.Create(ImmutableArrayAnalyzerAnalyzer.DiagnosticId);
```

Roslyn reúne diagnósticos e correções combinando esses identificadores que são apenas cadeias de caracteres.  O modelo de projeto gerado uma ID de diagnóstica para você, e você é livre para alterá-la.  O código na propriedade retorna apenas a ID da classe de analisador.

**O método RegisterCodeFixAsync recebe um contexto.** O contexto é importante porque uma correção de código pode ser aplicadas a vários diagnóstico ou pode haver mais de um problema em uma linha de código.  Se você digitar "context". no corpo do método, a lista de conclusão do IntelliSense mostrará alguns membros útil.  Há um membro de CancellationToken que você pode verificar para ver se algo que deseja cancelar a correção.  Há um membro de documentos tem muitos membros úteis e permite que você obtenha a objetos de modelo de projeto e solução.  Existe um membro de alcance que é o início e término do local do código especificado quando o diagnóstico relatado.

**Definir o método assíncrono.** A primeira coisa que você precisa fazer é corrigir a declaração de método gerado para ser um `async` método.  A correção de código para arrancar a implementação de uma classe abstrata não inclui o `async` palavra-chave mesmo que o método retorna um `Task`.

**Obter a raiz da árvore de sintaxe.** Para modificar o código que você precisa para produzir uma nova árvore de sintaxe com as alterações a correção de código faz.  É necessário o `Document` do contexto para chamar `GetSyntaxRootAsync`.  Isso é um método assíncrono porque não há trabalho desconhecido para obter a árvore de sintaxe, possivelmente incluindo obtendo o arquivo de disco, analisá-lo e criar o modelo de código do Roslyn para ele.  Interface do usuário do Visual Studio deve ser responsiva durante esse tempo, qual usando `async` permite.  Substitua a linha de código no método com o seguinte:

```csharp
var root = await context.Document
                        .GetSyntaxRootAsync(context.CancellationToken);
```

**Localize o nó com o problema.** Você passa no alcance do contexto, mas o nó que você localizar pode não ser o código que você precisa alterar.  O diagnóstico relatado fornecida apenas a extensão para o identificador de tipo (onde o Rabisco pertencia), mas você precisa substituir a expressão de criação de objeto inteiro, incluindo o `new` palavra-chave no início e os parênteses no final.  Adicione o seguinte código ao seu método (e usar **CTRL +.** Para adicionar um `using` instrução para `ObjectCreationExpressionSyntax`):

```csharp
var objectCreation = root.FindNode(context.Span)
                         .FirstAncestorOrSelf<ObjectCreationExpressionSyntax>();
```

**Registre sua correção de código de lâmpada da interface do usuário.** Ao registrar sua correção de código, Roslyn conecta-se de lâmpada da interface do usuário do Visual Studio automaticamente.  Os usuários finais verão usarem **CTRL +.** (período) quando o analisador squiggles um ruim `ImmutableArray<T>` uso do construtor.  Porque o provedor de correção de código é executado somente quando há um problema, você pode assumir que a expressão de criação do objeto que estava procurando.  Do parâmetro de contexto, você pode registrar a nova correção de código, adicionando o seguinte código ao final da `RegisterCodeFixAsync` método:

```csharp
context.RegisterCodeFix(
            CodeAction.Create("Use ImmutableArray<T>.Empty",
                              c => ChangeToImmutableArrayEmpty(objectCreation,
                                                               context.Document,
                                                               c)),
            context.Diagnostics[0]);
```

Você precisa colocar o cursor do editor no identificador de `CodeAction`, em seguida, use **CTRL +.** (ponto) para adicionar apropriada `using` instrução para este tipo.

Em seguida, coloque o cursor do editor no `ChangeToImmutableArrayEmpty` identificador e use **CTRL +.** novamente para gerar o stub do método para você.

Este último trecho de código que você adicionou registra a correção de código, passando um `CodeAction` e a ID de diagnóstica para o tipo de problema encontrado.  Neste exemplo, há apenas um ID de diagnóstico que esse código fornece correções para, para passar apenas o primeiro elemento da matriz de IDs de diagnóstico.  Quando você cria o `CodeAction`, você passa o texto que deve usar a lâmpada da interface do usuário como uma descrição da correção do código.  Você também pode passar de uma função que usa um CancellationToken e retorna um novo documento.  O novo documento tem uma nova árvore de sintaxe que inclui o patch código que chama `ImmutableArray.Empty`.  Este trecho de código usa uma expressão lambda para que ele pode fechar o nó objectCreation e documento do contexto.

**Construa nova árvore de sintaxe.** No `ChangeToImmutableArrayEmpty` método cujo stub gerada anteriormente, insira a linha de código: `ImmutableArray<int>.Empty;`.  Se você exibir a janela de ferramentas do Visualizador de sintaxe novamente, você pode ver que essa sintaxe é um nó de SimpleMemberAccessExpression.  É o que esse método precisa para construir e retornar em um novo documento.

A primeira alteração para `ChangeToImmutableArrayEmpty` é adicionar `async` antes de `Task<Document>` porque os geradores de código não podem assumir o método deve ser assíncrona.

Preencha o corpo com o código a seguir para que o método é semelhante ao seguinte:

```csharp
private async Task<Document> ChangeToImmutableArrayEmpty(
    ObjectCreationExpressionSyntax objectCreation, Document document,
    CancellationToken c)
{
    var generator = SyntaxGenerator.GetGenerator(document);
    var memberAccess =
        generator.MemberAccessExpression(objectCreation.Type, "Empty");
    var oldRoot = await document.GetSyntaxRootAsync(c);
    var newRoot = oldRoot.ReplaceNode(objectCreation, memberAccess);
    return document.WithSyntaxRoot(newRoot);
}
```

Você precisará colocar o cursor do editor no `SyntaxGenerator` identificador e use **CTRL +.** (ponto) para adicionar apropriada `using` instrução para este tipo.

Esse código usa `SyntaxGenerator`, que é um tipo muito útil para construir o novo código.  Depois de obter um gerador para o documento que tem o problema de código, `ChangeToImmutableArrayEmpty` chamadas `MemberAccessExpression`, passando o tipo que tem o membro que você deseja acessar e passando o nome do membro como uma cadeia de caracteres.

Em seguida, o método de busca a raiz do documento e como isso pode envolver arbitrário trabalho em geral, o código aguarda essa chamada e passa o token de cancelamento.  Modelos de código do Roslyn são imutáveis, semelhante a trabalhar com uma cadeia de caracteres do .NET; Quando você atualizar a cadeia de caracteres, você obtém um novo objeto de cadeia de caracteres de retorno.  Quando você chama `ReplaceNode`, você recebe um novo nó de raiz.  A maioria da árvore de sintaxe é compartilhado (porque ele é imutável), mas o `objectCreation` nó é substituído com o `memberAccess` nó, bem como todos os nós pai até a raiz da árvore de sintaxe.

## <a name="trying-your-code-fix"></a>Tentativa de corrigir seu código

Agora, você pode pressionar **F5** para executar o analisador em uma segunda instância do Visual Studio.  Abra o projeto de console usado anteriormente.  Agora você deverá ver a lâmpada onde sua nova expressão de criação de objeto é para `ImmutableArray<int>`.  Se você pressionar **CTRL +.** (período), em seguida, você verá seu código corrigir e você verá uma visualização de diferença do código gerado automaticamente no lâmpada da interface do usuário.  Roslyn cria isso para você.

**Dica de Pro:** se você iniciar a segunda instância do Visual Studio e você não vir a lâmpada com sua correção de código, talvez seja necessário limpar o cache de componente do Visual Studio.  Limpar o cache força o Visual Studio para examinar novamente os componentes para que o Visual Studio, em seguida, escolha o seu componente mais recente.  Primeiro, desligue a segunda instância do Visual Studio.  No Windows Explorer, vá para o diretório de usuário (c:\users\\< userid\>) e localizar AppData\Local\Microsoft\VisualStudio\14.0Roslyn\\.  Nesse diretório, exclua o diretório de sub ComponentModelCache.  As alterações para a versão com o Visual Studio "14".

## <a name="talk-video-and-finish-code-project"></a>Vídeo de conversa e projetos de código de término

Você pode ver esse exemplo desenvolvido e discutido mais [essa conversa](http://channel9.msdn.com/events/Build/2015/3-725).  A conversa demonstra o analisador de trabalho e orienta você criá-lo.

Você pode ver todo o código concluído [aqui](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers).  As subpastas DoNotUseImmutableArrayCollectionInitializer e DoNotUseImmutableArrayCtor têm um arquivo c# para localizar problemas e um arquivo c# que implementa as correções de código que aparecem de lâmpada da interface do usuário do Visual Studio.  Observe que o código concluído tem abstração mais um pouco para evitar a busca a ImmutableArray\<T > tipo de objeto repetidamente.  Ele usa aninhadas ações registradas para salvar o objeto de tipo em um contexto que está disponível sempre que as ações de sub (analisar a criação do objeto e analisar inicializações de coleção) execute.

## <a name="see-also"></a>Consulte também

* [\\Solicite \Build 2015](http://channel9.msdn.com/events/Build/2015/3-725)
* [Código concluído no GitHub](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers)
* [Vários exemplos no GitHub, agrupados em três tipos de analisadores](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)
* [Outros documentos no site do GitHub OSS](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)
* [Regras FxCop implementadas com Roslyn analisadores no GitHub](https://github.com/dotnet/roslyn/tree/master/src/Diagnostics/FxCop)
