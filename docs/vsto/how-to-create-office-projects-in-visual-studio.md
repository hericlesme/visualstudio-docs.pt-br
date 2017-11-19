---
title: 'Como: criar projetos do Office no Visual Studio | Microsoft Docs'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VST.SelectDocWizard.Page1
- VST.SelectDocWizard.Http
- VST.SelectDocWizard.Extension
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- add-ins [Office development in Visual Studio], creating projects
- Office applications [Office development in Visual Studio], creating
- Office projects [Office development in Visual Studio]
- projects [Office development in Visual Studio], creating
- document-level customizations [Office development in Visual Studio], creating
- application-level add-ins [Office development in Visual Studio], creating projects
ms.assetid: 0037dbd8-0d2a-4766-90ea-81c819379582
caps.latest.revision: "96"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f97cac11c943b75f5bc74e5cb67c9810b9ba7032
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-create-office-projects-in-visual-studio"></a>Como criar projetos do Office no Visual Studio
  Você pode usar [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] para criar o suplemento do VSTO e nível de documento personalizações para aplicativos do Microsoft Office. Para obter mais informações sobre esses tipos de projetos, consulte [visão geral de desenvolvimento de soluções do Office &#40; VSTO &#41; ](../vsto/office-solutions-development-overview-vsto.md).  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-vsto-add-in-project"></a>Para criar um projeto de suplemento do VSTO  
  
1.  No menu **Arquivo**, escolha **Novo**, **Projeto**. Se seu ambiente de desenvolvimento integrado (IDE) está definido para usar [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] configurações de desenvolvimento, no **arquivo** menu, escolha **novo**, **projeto**.  
  
     A caixa de diálogo **Novo Projeto** é exibida.  
  
    > [!NOTE]  
    >  Destino de projetos do Office a [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] por padrão. Para obter mais informações, consulte [.NET Framework Client Profile](/dotnet/framework/deployment/client-profile).  
  
2.  No painel modelos, sob o nó para o idioma que você deseja usar, expanda **Office/SharePoint**.  
  
3.  Escolha o **suplementos do Office** nó.  
  
4.  Na lista de modelos de projeto, selecione um modelo de projeto de suplemento do VSTO. Para obter uma lista do modelos de projeto do suplemento do VSTO disponíveis, consulte [visão geral de modelos de projeto do Office](../vsto/office-project-templates-overview.md).  
  
    > [!NOTE]  
    >  Se os modelos de projeto não são visíveis quando você seleciona o **suplementos do Office** nó, verifique se **.NET Framework 4** ou posterior está selecionado na caixa de combinação na parte superior da caixa de diálogo. Modelos de projeto do Office são visíveis para ambas as versões do .NET Framework.  
  
5.  No **nome** , digite um nome para o projeto. Por padrão, o nome do projeto também é usado como o nome da solução.  
  
6.  No **local** , digite o caminho onde você deseja criar o projeto. Você pode usar caminhos absoluto e universal de nomenclatura UNC (convenção). Não use HTTP, FTP ou outros caminhos de protocolo.  
  
     Locais têm os seguintes formatos:  
  
    -   [*unidade*\]: \  
  
    -   \\\\*Servidor*\\*compartilhamento*  
  
     Não use esses caracteres no local:  
  
    -   Asterisco (*)  
  
    -   Barra vertical (|)  
  
    -   Dois-pontos (:) (Exceto após a letra da unidade).  
  
    -   Aspas duplas (") (caminhos que contêm espaços não é necessário para as aspas.)  
  
    -   Menor que (\<)  
  
    -   Maior que (>)  
  
    -   Ponto de interrogação (?)  
  
    -   Sinal de porcentagem (%)  
  
7.  Selecione o botão **OK**.  
  
    > [!NOTE]  
    >  Projetos de suplemento sempre são salvas quando eles são criados. Eles não podem ser criados como projetos temporários. Para obter mais informações sobre projetos temporários, consulte [projetos temporários](http://msdn.microsoft.com/en-us/9cf1944c-7045-44cc-8701-7b0eb4099f2b).  
  
### <a name="to-create-a-document-level-customization-project"></a>Para criar um projeto de personalização de nível de documento  
  
1.  No menu **Arquivo**, escolha **Novo**, **Projeto**. Se seu IDE está definido para usar configurações de desenvolvimento do Visual Basic, no **arquivo** menu, escolha **novo**, **projeto**.  
  
     A caixa de diálogo **Novo Projeto** é exibida.  
  
    > [!NOTE]  
    >  Destino de projetos do Office a [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] por padrão.  Para obter mais informações, consulte [.NET Framework Client Profile](/dotnet/framework/deployment/client-profile).  
  
2.  No painel modelos, sob o nó para o idioma que você deseja usar, expanda **Office/SharePoint**.  
  
3.  Selecione o **suplementos do Office** nó.  
  
4.  Na lista de modelos de projeto, selecione um modelo de projeto no nível do documento. Para obter uma lista de modelos de projeto de nível de documento disponíveis, consulte [visão geral de modelos de projeto do Office](../vsto/office-project-templates-overview.md).  
  
    > [!NOTE]  
    >  Se os modelos de projeto não são visíveis quando você seleciona o **suplementos do Office** nó, verifique se **.NET Framework 4** ou posterior está selecionado na caixa de combinação na parte superior da caixa de diálogo. Modelos de projeto do Office são visíveis para ambas as versões do .NET Framework.  
  
5.  No **nome** , digite um nome para o projeto. Por padrão, esse nome também é usado para o documento. Se seu IDE está definido para usar configurações de desenvolvimento do Visual c# ou configurações de desenvolvimento geral, insira também um local e o nome da solução.  
  
    > [!NOTE]  
    >  Você não pode usar caracteres substitutos no caminho do local do projeto ou no nome do projeto. Além disso, se você planeja implantar a solução para uso offline, os caracteres no nome do projeto devem ajustar as especificações de protocolo HTTP.  
  
6.  Selecione o botão **OK**.  
  
     O **Visual Studio Tools para Office Project Wizard** é aberto.  
  
7.  Selecione **criar um novo documento** se você deseja criar um novo documento para a solução, ou selecione **copiar um documento existente** se você desejar personalizar um documento existente.  
  
     Se você criar um novo documento, especifique o nome no **nome** caixa e selecione o formato do documento usando o **formato** caixa. Para obter mais informações sobre os formatos disponíveis, consulte [arquitetura de personalizações em nível de documento](../vsto/architecture-of-document-level-customizations.md).  
  
     Se você usar um documento existente, especifique o local do documento no **caminho completo do documento existente** caixa. Você pode usar absolute e caminhos UNC. Não use HTTP, FTP ou outros caminhos de protocolo para o documento.  
  
     Locais têm os seguintes formatos:  
  
    -   [*unidade*\]: \  
  
    -   \\\\*Servidor*\\*compartilhamento*  
  
     Não use esses caracteres no local:  
  
    -   Asterisco (*)  
  
    -   Barra vertical (|)  
  
    -   Dois-pontos (:) (Exceto após a letra da unidade).  
  
    -   Aspas duplas (") (caminhos que contêm espaços não é necessário para as aspas.)  
  
    -   Menor que (\<)  
  
    -   Maior que (>)  
  
    -   Ponto de interrogação (?)  
  
    -   Sinal de porcentagem (%)  
  
    > [!NOTE]  
    >  Se você usar um documento existente em um [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] de projeto, use apenas os documentos que foram criados ou convertidos em [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)]. Da mesma forma, se você usar um documento existente em uma palavra 2010 do projeto, use somente os documentos que foram criados ou convertidos para o Word 2010. Determinados recursos serão desabilitados no documento se você usar um documento que foi criado em uma versão anterior do Word. Se você tentar escrever código que use esses recursos, você poderá encontrar erros em seu projeto. Para converter um documento, abra-o em [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] ou Word 2010, no **arquivo** guia na faixa de opções, escolha **informações**, **converter**.  
  
8.  Escolha **concluir**.  
  
9. Adicione a pasta do projeto e suas subpastas à lista de locais confiáveis na Central de confiabilidade do Word nos seguintes casos:  
  
    -   Você está criando um documento do Word que é baseado em um arquivo. docm, e o documento contém um projeto do VBA ou hospeda controles de formulários do Windows. Adicionando a pasta do projeto para a lista de locais confiáveis ajudará a garantir que o documento funciona conforme o esperado em tempo de design.  
  
    -   Você está criando um projeto de modelo do Word que é baseado em um arquivo. dotx. Você deve adicionar a pasta do projeto à lista de locais confiáveis para que você pode executar e depurar o projeto.  
  
     Para obter mais informações sobre como adicionar um documento os locais confiáveis, consulte o site Microsoft Office Online [criar, remover ou alterar um local confiável para seus arquivos](https://support.office.com/en-au/article/Create-remove-or-change-a-trusted-location-for-your-files-f5151879-25ea-4998-80a5-4208b3540a62).  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral de modelos de projeto do Office](../vsto/office-project-templates-overview.md)   
 [Colaboração de desenvolvimento de soluções do Office](../vsto/collaborative-development-of-office-solutions.md)   
 [Projetando e criando soluções do Office](../vsto/designing-and-creating-office-solutions.md)   
 [Introdução aos suplementos de programação VSTO](../vsto/getting-started-programming-vsto-add-ins.md)  
  
  