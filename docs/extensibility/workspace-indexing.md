---
title: Espaço de trabalho de indexação no Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 02/21/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 3163e98c-1c79-48a7-813f-7923be894ba1
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 5004db0d895d1fdc697c18606c346c24cd484527
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="workspace-indexing"></a>Espaço de trabalho de indexação

Em uma solução, sistemas de projeto serão responsáveis por fornecer funcionalidade para compilar, depurar, **GoTo** pesquisa de símbolo e muito mais. Sistemas de projeto podem fazer este trabalho porque eles entender a relação e os recursos de arquivos em um projeto. Um [Abrir pasta](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) o insight mesmo para fornecer recursos avançados do IDE também precisa de espaço de trabalho. A coleta e o armazenamento persistente de dados é um processo chamado de espaço de trabalho de indexação. Esses dados indexados podem ser consultados por meio de um conjunto de APIs assíncronas. Extensores podem participar no processo de indexação, fornecendo <xref:Microsoft.VisualStudio.Workspace.Indexing.IFileScanner>que sabe como tratar determinados tipos de arquivos.

## <a name="types-of-indexed-data"></a>Tipos de dados indexados

Há três tipos de dados que são indexados. Observe que o tipo esperado de scanners de arquivo difere do tipo desserializado do índice.

|Dados|Tipo de scanner de arquivo|Tipo de resultado de consulta do índice|Tipos relacionados|
|--|--|--|--|
|Referências|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceInfo>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceResult>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceInfoType>|
|Símbolos|<xref:Microsoft.VisualStudio.Workspace.Indexing.SymbolDefinition>|<xref:Microsoft.VisualStudio.Workspace.Indexing.SymbolDefinitionSearchResult>|<xref:Microsoft.VisualStudio.Workspace.Indexing.ISymbolService> deve ser usado em vez de `IIndexWorkspaceService` para consultas|
|Valores de dados|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileDataValue>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileDataResult`1>||

## <a name="querying-for-indexed-data"></a>Consultando dados indexados

Há dois tipos de assíncronos disponíveis para acessar dados persistentes. A primeira é por meio de <xref:Microsoft.VisualStudio.Workspace.Indexing.IIndexWorkspaceData>. Ele fornece acesso básico para um único arquivo `FileReferenceResult` e `FileDataResult` dados e armazena em cache os resultados. O segundo é o <xref:Microsoft.VisualStudio.Workspace.Indexing.IIndexWorkspaceService> que não usa o armazenamento em cache, mas permite mais recursos de consulta.

```csharp
using Microsoft.VisualStudio.Workspace;
using Microsoft.VisualStudio.Workspace.Indexing;

private static IIndexWorkspaceData GetCachedIndexedData(IWorkspace workspace)
{
    // Gets access to indexed data wrapped in a cache.
    return workspace?.GetIndexWorkspaceDataService()?.CreateIndexWorkspaceData();
}

private static IIndexWorkspaceService GetDirectIndexedData(IWorkspace workspace)
{
    // Gets direct access to indexed data.
    // Can also be casted to IIndexWorkspaceService2.
    return workspace?.GetIndexWorkspaceService();
}
```

## <a name="participating-in-indexing"></a>Participantes de indexação

Espaço de trabalho de indexação aproximadamente segue a sequência a seguir:

1. A descoberta e persistência de entidades do sistema de arquivos no espaço de trabalho (apenas na verificação inicial de abertura).
1. Por arquivo, o provedor de correspondência com a prioridade mais alta é solicitado para verificar se há `FileReferenceInfo`s.
1. Por arquivo, o provedor de correspondência com a prioridade mais alta é solicitado para verificar se há `SymbolDefinition`s.
1. Por arquivo, todos os provedores são solicitados `FileDataValue`s.

Extensões podem exportar um scanner implementando `IWorkspaceProviderFactory<IFileScanner>` e exportar o tipo com <xref:Microsoft.VisualStudio.Workspace.Indexing.ExportFileScannerAttribute>. O `SupportedTypes` argumento de atributo deve ser um ou mais valores de <xref:Microsoft.VisualStudio.Workspace.Indexing.FileScannerTypeConstants>. Para um scanner de exemplo, consulte o SDK do VS [exemplo](https://github.com/Microsoft/VSSDK-Extensibility-Samples/blob/master/Open_Folder_Extensibility/C%23/SymbolScannerSample/TxtFileSymbolScanner.cs).

> [!WARNING]
> Não exportar um scanner de arquivo com suporte a `FileScannerTypeConstants.FileScannerContentType` tipo. Ele é usado para fins internos de Microsoft, apenas.

Em situações avançadas, uma extensão dinamicamente pode suportar um conjunto de tipos de arquivo arbitrário. Em vez de exportar MEF `IWorkspaceProviderFactory<IFileScanner>`, uma extensão pode exportar `IWorkspaceProviderFactory<IFileScannerProvider>`. Quando a indexação começa, esse tipo de fábrica serão importados, instanciado e ter seu <xref:Microsoft.VisualStudio.Workspace.Indexing.IFileScannerProvider.GetSymbolScannersAsync%2A> método invocado. `IFileScanner` instâncias de suporte de qualquer valor de `FileScannerTpeConstants` será respeitada, não apenas símbolos.

## <a name="next-steps"></a>Próximas etapas

* [Espaços de trabalho e serviços de idioma](workspace-language-services.md) -Saiba como integrar serviços de idioma em um espaço de trabalho de abrir a pasta.
* [Compilação de espaço de trabalho](workspace-build.md) -Abrir pasta dá suporte à criação de sistemas como MSBuild e makefiles.