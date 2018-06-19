---
title: Espaço de trabalho de compilação do Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 02/21/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 813f7a5e-f298-4469-9f4c-a5bddf5a6e14
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: f7415c99c68436519f9bab721fe88a48f750fa1c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31143921"
---
# <a name="workspace-build"></a>Compilação de espaço de trabalho

Suporte à compilação [Abrir pasta](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) cenários exige um extensor para fornecer [indexado](workspace-indexing.md) e [contexto arquivo](workspace-file-contexts.md) dados para o [espaço de trabalho](workspaces.md), como Assim como a ação de compilação para executar.

Abaixo está uma descrição das quais sua extensão será necessário.

## <a name="build-file-context"></a>Criar o contexto de arquivo

- Fábrica de provedor
  - `ExportFileContextProviderAttribute` atributo com `supportedContextTypeGuids` como aplicável `string` constantes de `BuildContextTypes`
  - implementa `IWorkspaceProviderFactory<IFileContextProvider>`
  - Provedor de contexto do arquivo
    - Retornar um `FileContext` para cada compilação com suporte de configuração e operação
      - `contextType` De <xref:Microsoft.VisualStudio.Workspace.Build.BuildContextTypes>
      - `context` implementa <xref:Microsoft.VisualStudio.Workspace.Build.IBuildConfigurationContext> com o `Configuration` a propriedade como a configuração de compilação (por exemplo `"Debug|x86"`, `"ret"`, ou `null` se não for aplicável). Como alternativa, use uma instância de <xref:Microsoft.VisualStudio.Workspace.Build.BuildConfigurationContext>. O valor de configuração **deve** corresponde à configuração do valor de dados de arquivo indexado.

## <a name="indexed-build-file-data-value"></a>Valor de dados de arquivo de compilação indexada

- Fábrica de provedor
  - `ExportFileScannerAttribute` atributo com `IReadOnlyCollection<FileDataValue>` como um tipo com suporte
  - implementa `IWorkspaceProviderFactory<IFileScanner>`
- Scanner no arquivo `ScanContentAsync<T>`
  - Retorna dados quando `FileScannerTypeConstants.FileDataValuesType` é o argumento de tipo
  - Retorna um valor de dados de arquivo para cada configuração construído com:
    - `type` como `BuildConfigurationContext.ContextTypeGuid`
    - `context` como a configuração de compilação (por exemplo `"Debug|x86"`, `"ret"`, ou `null` se não for aplicável). Esse valor **deve** corresponde à configuração do contexto de arquivo.

## <a name="build-file-context-action"></a>Ação de contexto do arquivo de compilação

- Fábrica de provedor
  - `ExportFileContextActionProvider` atributo com `supportedContextTypeGuids` como aplicável `string` constantes de `BuildContextTypes`
  - implementa `IWorkspaceProviderFactory<IFileContextActionProvider>`
- Provedor de ação no `IFileContextActionProvider.GetActionsAsync`
  - Retornar um `IFileContextAction` que corresponde a determinado `FileContext.ContextType` valor
- Ação de contexto do arquivo
  - Implementa `IFileContextAction` e <xref:Microsoft.VisualStudio.Workspace.Extensions.VS.IVsCommandItem>
  - `CommandGroup` propriedade retorna `16537f6e-cb14-44da-b087-d1387ce3bf57`
  - `CommandId` é `0x1000` para compilação, `0x1010` recriação, ou `0x1020` para limpar

>[!NOTE]
>Desde o `FileDataValue` precisa ser indexada, haverá algum período de tempo entre abrindo o espaço de trabalho e o ponto em que o arquivo será examinado para a funcionalidade de compilação completa. O atraso será visto na primeira abertura de uma pasta porque não há nenhum índice armazenados em cache anteriormente.

## <a name="reporting-messages-from-a-build"></a>Mensagens de relatório de uma compilação

A compilação pode superfície informações, aviso e mensagens de erro aos usuários uma das duas maneiras. De maneira simples é usar o <xref:Microsoft.VisualStudio.Workspace.Build.IBuildMessageService> e fornecer um <xref:Microsoft.VisualStudio.Workspace.Build.BuildMessage>, da seguinte forma:

```csharp
using Microsoft.VisualStudio.Workspace;
using Microsoft.VisualStudio.Workspace.Build;

private static void OutputBuildMessage(IWorkspace workspace)
{
    IBuildMessageService buildMessageService = workspace.GetBuildMessageService();

    if (buildMessageService != null)
    {
      // Example error build message. See the documentation for BuildMessage for more information.
      var message = new BuildMessage()
      {
          Type = BuildMessage.TaskType.Error,
          Code = "MY1001",
          TaskText = "This is a sample error",
          ProjectFile = "buildfile.bld",
          File = "sourcefile.src"
          LogMessage = $"This is sample text that will only go to the Build output window pane.\n"

          // And any other properties to set
      };

      buildMessageService.ReportBuildMessages(new BuildMessage[] { message });
    }
}
```

`BuildMessage.Type` e `BuildMessage.LogMessage` controlar o comportamento de onde as informações são apresentadas ao usuário. Qualquer `BuildMessage.TaskType` valor diferente de `None` produzirá um **lista de erros** entrada com os detalhes de determinado. `LogMessage` sempre serão geradas no **criar** painel do **saída** janela da ferramenta.

Como alternativa, as extensões podem interagir diretamente com o **lista de erros** ou **criar** painel. Existe um bug em versões anteriores do Visual Studio 2017 versão 15,7 onde o `pszProjectUniqueName` argumento de <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane2.OutputTaskItemStringEx2*> é ignorado.

>[!WARNING]
>Os chamadores de `IFileContextAction.ExecuteAsync` pode fornecer implementações subjacentes arbitrárias para o `IProgress<IFileContextActionProgressUpdate>` argumento. Nunca invocar `IProgress<IFileContextActionProgressUpdate>.Report(IFileContextActionProgressUpdate)` diretamente. Atualmente, não há nenhum diretrizes gerais para o uso desse argumento, mas essas diretrizes estão sujeitos a alterações.

## <a name="build-related-apis"></a>APIs relacionadas à compilação

- <xref:Microsoft.VisualStudio.Workspace.Build.IBuildConfigurationContext> Fornece detalhes de configuração de compilação.
- <xref:Microsoft.VisualStudio.Workspace.Build.IBuildMessageService> mostra <xref:Microsoft.VisualStudio.Workspace.Build.BuildMessage>s para os usuários.

## <a name="tasksvsjson-and-launchvsjson"></a>Tasks.vs.JSON e launch.vs.json

Para obter informações sobre a criação de um arquivo tasks.vs.json ou launch.vs.json, consulte [personalizar compilação e tarefas de depuração](../ide/customize-build-and-debug-tasks-in-visual-studio.md).

## <a name="next-steps"></a>Próximas etapas

* [Protocolo de servidor de idioma](language-server-protocol.md) -Saiba como integrar os servidores de linguagem no Visual Studio.