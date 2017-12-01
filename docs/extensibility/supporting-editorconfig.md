---
title: "Estendendo um serviço de linguagem para dar suporte a EditorConfig no Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 11/22/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editorconfig [extensibility]
- editorconfig, supporting in a language service
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 111e53ad9beec3a5f5ef013b996a541ea0fa1e72
ms.sourcegitcommit: 5f5587a1bcf4aae995c80d54a67b4b461f8695f3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/29/2017
---
# <a name="supporting-editorconfig-for-your-language-service"></a>EditorConfig de suporte para o serviço de linguagem

[EditorConfig](http://editorconfig.org/) arquivos permitem descrevem opções de editor de texto comuns, como o tamanho do recuo, em uma base por projeto. Para saber mais sobre o suporte do Visual Studio para arquivos EditorConfig, consulte [criar configurações de editor portátil usando EditorConfig](../ide/create-portable-custom-editor-options.md).

Na maioria dos casos, ao implementar um serviço de linguagem do Visual Studio, nenhum trabalho adicional é necessário para dar suporte às propriedades universais do EditorConfig. O editor básico detecta automaticamente e lê o arquivo .editorconfig quando os usuários abrem arquivos e define as opções de buffer e exibição de texto apropriadas. No entanto, para edições como espaços e guias, alguns serviços de idioma optar por usar uma opção de exibição de texto contextual apropriado em vez de usar as configurações globais. Nesses casos, o serviço de linguagem deve ser atualizado para dar suporte aos arquivos do EditorConfig.

A seguir está as alterações que são necessárias para atualizar um serviço de linguagem para dar suporte a arquivos de EditorConfig, substituindo global _específico do idioma_ opção com um _contextuais_ opção:

## <a name="indent-style"></a>Estilo de recuo

Opções específicas do idioma | Opções contextuais
-------|--------
Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.fInsertTabs<br/>Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs|! textBufferOptions.GetOptionValue(DefaultOptions.ConvertTabsToSpacesOptionId)<br/>! textView.Options.GetOptionValue(DefaultOptions.ConvertTabsToSpacesOptionId)

## <a name="indent-size"></a>Tamanho do recuo

Opções específicas do idioma | Opções contextuais
-------|--------
Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.uIndentSize<br/>Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs.IndentSize|textBufferOptions.GetOptionValue(DefaultOptions.IndentSizeOptionId)<br/>textView.Options.GetOptionValue(DefaultOptions.IndentSizeOptionId)

## <a name="tab-size"></a>A guia tamanho

Opções específicas do idioma | Opções contextuais
-------|--------
Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.uTabSize<br/>Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs.TabSize|textBufferOptions.GetOptionValue(DefaultOptions.TabSizeOptionId)<br/>textView.Options.GetOptionValue(DefaultOptions.TabSizeOptionId)

## <a name="see-also"></a>Consulte também

[Criar configurações de editor portátil usando EditorConfig](../ide/create-portable-custom-editor-options.md)  
[Estendendo os serviços de editor e idioma](../extensibility/extending-the-editor-and-language-services.md)