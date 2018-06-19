---
title: Estendendo o Editor e o idioma serviços | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new -
ms.assetid: 8d04f8db-eda7-4b3e-b6eb-c06df104502a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4113a033d4e1a2595f4a980405e1b39d57d60958
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31132568"
---
# <a name="extending-the-editor-and-language-services"></a>Extensão do Editor e serviços de linguagem
Você pode adicionar recursos de serviço de linguagem (como IntelliSense) para o seu próprio editor e estender a maioria dos recursos do editor de código do Visual Studio.  Para obter uma lista completa de como você pode estender, consulte [serviço de linguagem e pontos de extensão de Editor](../extensibility/language-service-and-editor-extension-points.md).  
  
 Você pode estender a maioria dos recursos do editor usando o Managed Extensibility Framework (MEF). Por exemplo, se o recurso de editor que você deseja estender coloração de sintaxe, você pode escrever um MEF *parte do componente* que define as classificações para o qual você deseja diferentes cores e como eles devem ser tratados. O editor também dá suporte a várias extensões do mesmo recurso.  
  
 A camada de apresentação do editor está com base em Windows Presentation Framework (WPF). WPF fornece uma biblioteca de elementos gráficos para formatação de texto flexível e também fornece visualizações como gráficos e animações.  
  
 O SDK do Visual Studio fornece adaptadores conhecidos como *shims* para dar suporte a VSPackages que foram desenvolvidos para versões anteriores. No entanto, se você tiver um VSPackage existente, recomendamos que você atualize para a nova tecnologia para obter melhor desempenho e confiabilidade.  
  
## <a name="related-topics"></a>Tópicos relacionados  
  
|Título|Descrição|  
|-----------|-----------------|  
|[Introdução ao serviço de linguagem e às extensões do editor](../extensibility/getting-started-with-language-service-and-editor-extensions.md)|Explica como criar uma extensão para o editor.|  
|[Dentro do Editor](../extensibility/inside-the-editor.md)|Descreve a estrutura geral do editor e lista alguns dos seus recursos.|  
|[Managed Extensibility Framework no editor](../extensibility/managed-extensibility-framework-in-the-editor.md)|Explica como usar o Managed Extensibility Framework (MEF) com o editor.|  
|[Serviço de linguagem e pontos de extensão do editor](../extensibility/language-service-and-editor-extension-points.md)|Lista os pontos de extensão do editor. Pontos de extensão representam os recursos de editor que podem ser estendidos.|  
|[Passo a passo: Criar um adorno de exibição, comandos e configurações (guias de coluna)](../extensibility/walkthrough-creating-a-view-adornment-commands-and-settings-column-guides.md)|Percorre e explica a criação de um adorno de exibição que desenha coluna gudie linhas para ajudá-lo a manter o código para uma determinada largura de exibição.  Também mostra ler e gravar configurações, bem como declarar e implementação de comandos que você pode chamar na janela de comando.|  
|[Importações do editor](../extensibility/editor-imports.md)|Lista os serviços que uma extensão pode importar.|  
|[Adaptando um código herdado para o Editor](../extensibility/adapting-legacy-code-to-the-editor.md)|Explica as diferentes maneiras de adaptar o código herdado (pré-Visual Studio 2010) para estender o editor.|  
|[Migrar um serviço de linguagem herdado](../extensibility/internals/migrating-a-legacy-language-service.md)|Explica como migrar um serviço de linguagem VSPackage com base.|  
|[Passo a passo: Vincular um tipo de conteúdo a uma extensão de nome de arquivo](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)|Mostra como vincular um tipo de conteúdo a uma extensão de nome de arquivo.|  
|[Passo a passo: Criar um glifo de margem](../extensibility/walkthrough-creating-a-margin-glyph.md)|Mostra como adicionar um ícone para uma margem.|  
|[Passo a passo: Realçar o texto](../extensibility/walkthrough-highlighting-text.md)|Mostra como usar *marcas* para realçar o texto.|  
|[Passo a passo: Estruturar em tópicos](../extensibility/walkthrough-outlining.md)|Mostra como adicionar a estrutura de tópicos para tipos específicos de chaves.|  
|[Passo a passo: Exibir chaves correspondentes](../extensibility/walkthrough-displaying-matching-braces.md)|Mostra como realçar a correspondência de chaves.|  
|[Passo a passo: Exibir dicas de ferramenta de informação rápida](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)|Mostra como exibir pop-ups Inforapida que descrevem os elementos de código, como propriedades, métodos e eventos.|  
|[Passo a passo: Exibir a ajuda da assinatura](../extensibility/walkthrough-displaying-signature-help.md)|Mostra como exibir pop-ups que fornecem informações sobre o número e tipos de parâmetros em uma assinatura.|  
|[Walkthrough: Displaying Statement Completion (Passo a passo: exibindo o preenchimento de declaração)](../extensibility/walkthrough-displaying-statement-completion.md)|Mostra como implementar a conclusão de instrução.|  
|[Passo a passo: Implementar trechos de código](../extensibility/walkthrough-implementing-code-snippets.md)|Mostra como implementar a expansão de trecho de código.|  
|[Passo a passo: Exibir sugestões de lâmpada](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)|Mostra como exibir lâmpadas para obter sugestões de código.|  
|[Passo a passo: Usar um comando de Shell com uma extensão do editor](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)|Mostra como associar um comando de menu em um VSPackage com um componente MEF.|  
|[Passo a passo: Usar uma chave de atalho com uma extensão do editor](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)|Mostra como associar um atalho de menu em um VSPackage com um componente MEF.|  
|[MEF (Managed Extensibility Framework)](/dotnet/framework/mef/index)|Fornece informações sobre o Managed Extensibility Framework (MEF).|  
|[Windows Presentation Foundation](/dotnet/framework/wpf/index)|Fornece informações sobre o Windows Presentation Foundation (WPF).|  
  
## <a name="reference"></a>Referência  
 Editor do Visual Studio inclui os seguintes namespaces.  
  
 <xref:Microsoft.VisualStudio.Language.Intellisense>  
  
 <xref:Microsoft.VisualStudio.Language.StandardClassification>  
  
 <xref:Microsoft.VisualStudio.Editor>  
  
 <xref:Microsoft.VisualStudio.Text>  
  
 <xref:Microsoft.VisualStudio.Text.Adornments>  
  
 <xref:Microsoft.VisualStudio.Text.Classification>  
  
 <xref:Microsoft.VisualStudio.Text.Differencing>  
  
 <xref:Microsoft.VisualStudio.Text.Document>  
  
 <xref:Microsoft.VisualStudio.Text.Editor>  
  
 <xref:Microsoft.VisualStudio.Text.Editor.OptionsExtensionMethods>  
  
 <xref:Microsoft.VisualStudio.Text.Formatting>  
  
 <xref:Microsoft.VisualStudio.Text.IncrementalSearch>  
  
 <xref:Microsoft.VisualStudio.Text.Operations>  
  
 <xref:Microsoft.VisualStudio.Text.Outlining>  
  
 <xref:Microsoft.VisualStudio.Text.Projection>  
  
 <xref:Microsoft.VisualStudio.Text.Tagging>  
  
 <xref:Microsoft.VisualStudio.Utilities>