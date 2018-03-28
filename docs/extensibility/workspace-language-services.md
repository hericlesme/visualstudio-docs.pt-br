---
title: Espaços de trabalho e serviços de linguagem no Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 02/21/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8631ffea-83c8-4fd4-a01e-c59772e89c84
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 59cf2936311bb94c2db1ada6a7a3d5ccf994f027
ms.sourcegitcommit: 768118d470da9c7164d2f23ca918dfe26a4be72f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/28/2018
---
# <a name="workspaces-and-language-services"></a>Espaços de trabalho e serviços de linguagem

Serviços de idioma podem fornecer [Abrir pasta](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) os mesmos recursos de linguagem avançada de usuários são usados para ao trabalhar com soluções e projetos. Um serviço de idioma pode ativar automaticamente com base na extensão de arquivo ou conteúdo de um documento aberto, embora este serviço de linguagem "arquivo flexível" é limitado ao realce de sintaxe. Informações adicionais são necessárias para fornecer uma experiência mais rica durante a edição/revisão de código-fonte. Cada serviço de linguagem tem sua própria API para inicialização com esses dados contextuais extra para um documento. Normalmente, isso é gerenciado por um sistema de projeto, que está acoplado ao serviço de linguagem e para o sistema de compilação.

## <a name="initialization"></a>Inicialização

Em um [espaço de trabalho](workspaces.md), serviços de idioma são inicializados por uma <xref:Microsoft.VisualStudio.Workspace.Intellisense.ILanguageServiceProvider> ponto de extensão que é especializada apenas em que serviço de linguagem e não sabe nada de criação de compilação. Dessa forma, um proprietário de serviço de linguagem pode manter uma única pasta aberta extensão, independentemente de quantas padrões existe dentro de pastas e arquivos para executar seu compilador durante uma compilação (por exemplo MSBuild, makefiles, etc.). Quando os arquivos do qual foi criado um contexto de arquivo são alterados no disco e o contexto do arquivo é atualizado, o provedor de serviço de linguagem é notificado sobre o conjunto atualizado de contextos de arquivo. O provedor de serviço de linguagem pode atualizar seu modelo.

Quando um documento é aberto no editor, o Visual Studio só considera idioma provedores de serviços que exigem tipos de contexto do arquivo para o qual um provedor de contexto do arquivo correspondente pode ser encontrado. Em seguida, passa os contextos de arquivo do provedor correspondente (es) para o provedor de serviço de idioma selecionado por meio de `ILangaugeServiceProvider.InitializeAsync`. O que o provedor de serviço de linguagem faz com que os dados de contexto do arquivo são um detalhe de implementação do provedor de serviço de linguagem, mas a experiência do usuário esperado é um serviço de idioma mais rico para que abriu o documento.

## <a name="using-ilanguageserviceprovider"></a>Usando ILanguageServiceProvider

O serviço de idioma será notificado quando um contexto de arquivo é criado com um `ContextType` que corresponde a um do `SupportedContextTypes` atributo de exportação de valores do servidor do idioma.

Para dar suporte a um serviço de idioma, uma extensão será necessário:

- Uma única `Guid`. Isso será usado para `SupportedContextTypes` argumentos de atributo e, em um `FileContext` objeto.
- Contexto do arquivo de linguagem
  - Fábrica de provedor
    - `ExportFileContextProviderAttribute` atributo com acima exclusivamente gerado `Guid` em `SupportedContextTypes`
    - implementa `IWorkspaceProviderFactory<IFileContextProvider>`
  - Implementação de provedor do `IFileContextProvider.GetContextsForFileAsync`
    - Construir uma nova `FileContext` com o `contextType` argumento de construtor como exclusivamente gerado `Guid`
    - Use o `Context` propriedade o `FileContext` para fornecer dados adicionais para o `ILanguageServiceProvider`
- serviço de linguagem
  - Fábrica de provedor
    - `ExportLanguageServiceProvider` atributo com acima exclusivamente gerado `Guid` em `SupportedContextTypes`
    - implementa `IWorkspaceProviderFactory<ILanguageServiceProvider>`
  - Provider
    - implementa `ILanguageServiceProvider`
    - Use `ILanguageServiceProvider.InitializeAsync` para habilitar os serviços de idioma para os argumentos fornecidos quando um arquivo é aberto.
    - Use `ILanguageServiceProvider.UninitializeAsync` para desabilitar os serviços de idioma para os argumentos fornecidos quando um arquivo está fechado

>[!WARNING]
>O `ILanguageServiceProvider` métodos podem ser invocados pelo espaço de trabalho no thread principal. Considere agendar trabalho em um thread diferente para evitar a introdução de atrasos da interface do usuário.

## <a name="language-server-protocol"></a>Protocolo de idioma do servidor

O `Microsoft.VisualStudio.Workspace.*` APIs não são a única maneira de habilitar o serviço de idioma na pasta aberta. Outra opção é usar um servidor de idioma. Para obter mais informações, leia sobre o [protocolo de servidor de idioma](language-server-protocol.md).

## <a name="related-interfaces"></a>Interfaces relacionadas

- <xref:Microsoft.VisualStudio.Workspace.Intellisense.ILanguageServiceProvider> é chamado quando um arquivo de correspondência de tipos de arquivo é aberto ou fechado para edição.

## <a name="next-steps"></a>Próximas etapas

* [Compilação de espaço de trabalho](workspace-build.md) -Abrir pasta dá suporte à criação de sistemas como MSBuild e makefiles. 