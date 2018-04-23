---
title: Espaços de trabalho no Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 02/21/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 3489592a-dc0c-4cd3-9b08-cd367626980a
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 0230201677fd2422817ca1fbeab6679a424e5c05
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="workspaces"></a>Espaços de trabalho

Um espaço de trabalho é como o Visual Studio representa qualquer coleção de arquivos em [Abrir pasta](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md), e é representado pelo <xref:Microsoft.VisualStudio.Workspace.IWorkspace> tipo. Por si só, o espaço de trabalho não entende o conteúdo ou a recursos relacionados a arquivos dentro da pasta. Em vez disso, ele fornece um conjunto geral de APIs para recursos e extensões para produzir e consumir dados que outras pessoas podem agir. Os produtores são compostos por meio de [Managed Extensibility Framework](https://github.com/Microsoft/vs-mef/blob/master/doc/index.md) (MEF) usando vários atributos de exportação.

## <a name="workspace-providers-and-services"></a>Serviços e provedores de espaço de trabalho

Serviços e provedores de espaço de trabalho fornecem os dados e a funcionalidade para reagir ao conteúdo de um espaço de trabalho. Eles podem fornecer informações de arquivo contextuais, símbolos nos arquivos de origem, ou criar funcionalidade.

Ambos os conceitos de usam um [padrão de fábrica](https://en.wikipedia.org/wiki/Factory_method_pattern) e importados por meio de MEF pelo espaço de trabalho. Todos os atributos de exportação implementam `IProviderMetadataBase` ou `IWorkspaceServiceFactoryMetadata`, mas há tipos concretos que as extensões devem usar para tipos exportados.

Uma diferença entre os provedores e serviços é sua relação com o espaço de trabalho. Um espaço de trabalho pode ter muitos provedores de um determinado tipo, mas somente um serviço de um determinado tipo é criado por espaço de trabalho. Por exemplo, um espaço de trabalho tem muitos provedores de scanner de arquivo, mas o espaço de trabalho tem apenas um serviço de indexação por espaço de trabalho.

Outra diferença importante é o consumo de dados de provedores e serviços. O espaço de trabalho é o ponto de entrada para obter dados de provedores por duas razões. Primeiro, provedores normalmente têm alguns estreito conjunto de dados que eles criam. Os dados podem ser símbolos para um arquivo de origem c# ou criar contextos de arquivo para um _CMakeLists.txt_ arquivo. O espaço de trabalho será compatível com a solicitação do cliente para os provedores cujos metadados alinhar com a solicitação. Segundo, alguns cenários permitem que vários provedores contribuir para uma solicitação enquanto outros cenários de usam o provedor com prioridade mais alta.

Por outro lado, as extensões podem obter instâncias do e interagir diretamente com os serviços de área de trabalho. Métodos de extensão em `IWorkspace` estão disponíveis para os serviços fornecidos pelo Visual Studio, como <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetFileWatcherService%2A>. A extensão pode oferecer para componentes de dentro de sua extensão de ou para outras extensões consumir um serviço de espaço de trabalho. Os consumidores devem usar <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetServiceAsync%2A> ou um método de extensão que você fornecer o `IWorkspace` tipo.

>[!WARNING]
> Não crie serviços que estão em conflito com o Visual Studio. Isso pode levar a problemas inesperados.

## <a name="disposal-on-workspace-closure"></a>Descarte no fechamento do espaço de trabalho

No fechamento de um espaço de trabalho, extensores talvez seja necessário descartar mas chamada assíncrona código. O <xref:Microsoft.VisualStudio.Threading.IAsyncDisposable> interface está disponível para tornar esse código fácil de escrita.

## <a name="related-types"></a>Tipos relacionados

- <xref:Microsoft.VisualStudio.Workspace.IWorkspace> é a entidade central para um espaço de trabalho aberto como uma pasta aberta.
- <xref:Microsoft.VisualStudio.Workspace.IWorkspaceProviderFactory`1> cria um provedor por espaço de trabalho instanciado.
- <xref:Microsoft.VisualStudio.Workspace.IWorkspaceServiceFactory> cria um serviço por espaço de trabalho instanciado.
- <xref:Microsoft.VisualStudio.Threading.IAsyncDisposable> devem ser implementados em provedores e serviços que precisam executar código assíncrono durante o descarte.
- <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper> fornece métodos auxiliares para acessar serviços conhecidos ou serviços arbitrários.

## <a name="workspace-settings"></a>Configurações de espaço de trabalho

Espaços de trabalho tem um <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager> serviço simples mas poderosas controle sobre um espaço de trabalho. Para obter uma visão geral básica das configurações, consulte [personalizar compilação e tarefas de depuração](../ide/customize-build-and-debug-tasks-in-visual-studio.md).

Configurações para a maioria dos `SettingsType` tipos são _. JSON_ arquivos, como _VSWorkspaceSettings.json_ e _tasks.vs.json_.

O poder das configurações de espaço de trabalho gira em torno de "escopos", que são simplesmente caminhos no espaço de trabalho. Quando um consumidor chama <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager.GetAggregatedSettings%2A>, todos os escopos que incluem o caminho solicitado e o tipo de configuração são agregados. Prioridade de agregação de escopo é o seguinte:

1. "Configurações locais", que geralmente é a raiz de espaço de trabalho `.vs` directory.
1. O caminho solicitado em si.
1. O diretório pai do caminho solicitado.
1. Todos os pais mais diretórios até e incluindo a raiz do espaço de trabalho.
1. "Configurações", que está em um diretório de usuário.

O resultado é uma instância de <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettings>. Este objeto contém as configurações para um tipo específico e pode ser consultado para nomes de chave de configuração armazenados como `string`. O <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettings.GetProperty%2A> métodos e <xref:Microsoft.VisualStudio.Workspace.Settings.WorkspaceSettingsExtensions> métodos de extensão espera que o chamador para saber o tipo do valor da configuração que está sendo solicitado. Como a maioria dos arquivos de configuração são persistidos como _. JSON_ arquivos, muitas invocações usará `string`, `bool`, `int`e matrizes desses tipos. Também há suporte para tipos de objeto. Nesses casos, você pode usar `IWorkspaceSettings` a próprio como o argumento de tipo. Por exemplo:

```json
{
  "intValue": 1,
  "stringValue": "s",
  "boolValue": true,
  "stringArray": [
    "s1",
    "s2"
  ],
  "nestedIWorkspaceSettings": {
    "nestedString": "ns"
  }
}
```

Supondo que essas configurações foram um usuário _VSWorkspaceSettings.json_, os dados podem ser acessados como:

```csharp
using System.Collections.Generic;
using Microsoft.VisualStudio.Workspace;
using Microsoft.VisualStudio.Workspace.Settings;

private static void ReadSettings(IWorkspace workspace)
{
    IWorkspaceSettingsManager settingsManager = workspace.GetSettingsManager();
    IWorkspaceSettings settings = settingsManager.GetAggregatedSettings(SettingsTypes.Generic);

    // result == WorkspaceSettingsResult.Success
    WorkspaceSettingsResult result = settings.GetProperty("intValue", out int intValue);
    result = settings.GetProperty("stringValue", out string stringValue);
    result = settings.GetProperty("boolValue", out bool boolValue);
    result = settings.GetProperty("stringArray", out string[] stringArray);
    result = settings.GetProperty("nestedIWorkspaceSettings", out IWorkspaceSettings nestedIWorkspaceSettings);
    result = nestedIWorkspaceSettings.GetProperty("nestedString", out string nestedString);

    // Extension method alternative using default values.
    int intValueOrDefault = settings.Property("intValue", /* default */ 42);

    // Missing key. result == WorkspaceSettingsResult.Undefined
    result = settings.GetProperty("missing", out string missing);

    // Wrong type for a key. result == WorkspaceSettingsResult.Error
    result = settings.GetProperty("intValue", out IWorkspaceSettings notSettings);

    // Special ability to union "stringArray" across all scopes.
    IEnumerable<string> allStringArray = settings.UnionPropertyArray<string>("stringArray");
}
```

>[!NOTE]
>Essas configurações APIs estão relacionadas às APIs disponíveis no `Microsoft.VisualStudio.Settings` namespace. Configurações de espaço de trabalho são independentes do host e usam arquivos de configurações específicas de espaço de trabalho ou provedores de configurações dinâmicas.

### <a name="providing-dynamic-settings"></a>Fornecer configurações dinâmicas

As extensões podem fornecer <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsProvider>s. Esses provedores na memória permite que as extensões adicionar configurações ou substituir outras pessoas.

Exportando um `IWorkspaceSettingsProvider` é diferente de outros provedores de espaço de trabalho. A fábrica não é `IWorkspaceProviderFactory` e não há nenhum tipo de atributo especial. Em vez disso, implementar <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsProviderFactory> e usar `[Export(typeof(IWorkspaceSettingsProviderFactory))]`.

```csharp
// Common workspace provider factory pattern
[ExportFeatureProvider(some, args, to, export)]
internal class MyProviderFactory : IWorkspaceProviderFactory<IFeatureProvider>
{
     IFeatureProvider CreateProvider(IWorkspace workspace) => new Provider(workspace);
}

// IWorkspaceSettingsProvider pattern
[Export(typeof(IWorkspaceSettingsProviderFactory))]
internal class MySettingsProviderFactory : IWorkspaceSettingsProviderFactory
{
    // 100 is typically the value used by built-in settings providers. Lower value is higher priority.
    int Priority => 100;

    IWorkspaceSettingsProvider CreateSettingsProvider(IWorkspace workspace) => new MySettingsProvider(workspace);
}
```

>[!TIP]
>Ao implementar métodos que retornam `IWorkspaceSettingsSource` (como `IWorkspaceSettingsProvider.GetSingleSettings`), retornar uma instância de `IWorkspaceSettings` em vez de `IWorkspaceSettingsSource`. `IWorkspaceSettings` fornece mais informações que podem ser úteis durante algumas agregações de configurações.

### <a name="settings-related-apis"></a>APIs de configurações relacionadas

- <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager> lê e agrega as configurações de espaço de trabalho.
- <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetSettingsManager%2A> Obtém o `IWorkspaceSettingsManager` para um espaço de trabalho.
- <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager.GetAggregatedSettings%2A> Obtém as configurações para um determinado escopo agregados em todos os escopos sobrepostos.
- <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettings> contém configurações para um determinado escopo.

## <a name="workspace-suggested-practices"></a>Espaço de trabalho sugerido práticas recomendadas

- Retornar objetos de `IWorkspaceProviderFactory.CreateProvider` ou APIs similares Lembre-se de seus `Workspace` contexto quando criado. Interfaces de provedores são gravados esperando que esse objeto é mantido em criação.
- Salve os caches de espaço de trabalho específicas ou configurações no caminho "Configurações de Local" do espaço de trabalho. Criar um caminho para o arquivo usando `Microsoft.VisualStudio.Workspace.WorkspaceHelper.MakeRootedUnderWorkingFolder` no Visual Studio 2017 versão 15.6 ou posterior. Para versões anteriores à versão 15,6, use o trecho a seguir:

```csharp
using System.IO;
using Microsoft.VisualStudio.Workspace;
using Microsoft.VisualStudio.Workspace.Settings;

private static string MakeRootedUnderWorkingFolder(IWorkspace workspace, string relativePath)
{
    string workingFolder = workspace.GetSettingsManager().GetAggregatedSettings(SettingsTypes.WorkspaceControlSettings).Property<string>("WorkingFolder");
    return Path.Combine(workingFolder, relativePath);
}
```

## <a name="solution-events-and-package-auto-load"></a>Eventos de solução e carregar pacote automaticamente

Carregados pacotes podem implementar `IVsSolutionEvents7` e invocar `IVsSolution.AdviseSolutionEvents`. Isso inclui eventos de abertura e fechamento de uma pasta no Visual Studio.

Um contexto de interface do usuário pode ser usado para carregar automaticamente o pacote. O valor é `4646B819-1AE0-4E79-97F4-8A8176FDD664`.

## <a name="troubleshooting"></a>Solução de problemas

### <a name="the-sourceexplorerpackage-package-did-not-load-correctly"></a>O pacote de SourceExplorerPackage não foi carregado corretamente

Extensibilidade de espaço de trabalho é muito baseada no MEF e erros de composição fará com que o pacote que hospeda a pasta aberta para Falha ao carregar. Por exemplo, se uma extensão exporta um tipo com `ExportFileContextProviderAttribute`, mas o tipo implementa apenas `IWorkspaceProviderFactory<IFileContextActionProvider>`, ocorrerá um erro ao tentar abrir uma pasta no Visual Studio. Detalhes de erro podem ser encontrados em _%LOCALAPPDATA%\Microsoft\VisualStudio\15.0_id\ComponentModelCache\Microsoft.VisualStudio.Default.err_. Resolva quaisquer erros de tipos implementados pela extensão.

## <a name="next-steps"></a>Próximas etapas

* [Contextos de arquivo](workspace-file-contexts.md) -provedores de contexto do arquivo trazer inteligência de código para espaços de trabalho de abrir a pasta. 
* [Indexação](workspace-indexing.md) -espaço de trabalho de indexação coleta e persiste as informações sobre o espaço de trabalho.
