---
title: "Opções e páginas de opções | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], managed package framework support
- managed package framework, Tools Options pages support
- support, Tools Options pages
- Tools Options pages [Visual Studio SDK], layouts
- Tools Options pages [Visual Studio SDK], attributes
ms.assetid: e6c0e636-5ec3-450e-b395-fc4bb9d75918
caps.latest.revision: "34"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 1177a9a4df1f07c93540fa039117c5fa81289e17
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="options-and-options-pages"></a>Opções e páginas de opções
Clicando em **opções** no **ferramentas** menu abre o **opções** caixa de diálogo. As opções na caixa de diálogo são coletivamente chamadas de páginas de opções. O controle de árvore no painel de navegação inclui as categorias de opções, e cada categoria tem páginas de opções. Quando você selecionar uma página, suas opções são exibidas no painel direito. Essas páginas permitem que você altere os valores das opções que determinam o estado de um VSPackage.  
  
## <a name="support-for-options-pages"></a>Suporte para páginas de opções  
 O <xref:Microsoft.VisualStudio.Shell.Package> classe oferece suporte para a criação de categorias de opções e páginas de opções. O <xref:Microsoft.VisualStudio.Shell.DialogPage> classe implementa uma página de opções.  
  
 A implementação padrão de <xref:Microsoft.VisualStudio.Shell.DialogPage> oferece suas propriedades públicas para um usuário em uma grade genérico de propriedades. Você pode personalizar esse comportamento, substituindo os vários métodos na página para criar uma página de opções personalizada que tem sua própria interface de usuário (IU). Para obter mais informações, consulte [criando uma página de opções](../../extensibility/creating-an-options-page.md).  
  
 O <xref:Microsoft.VisualStudio.Shell.DialogPage> classe implementa <xref:Microsoft.VisualStudio.Shell.IProfileManager>, que fornece a persistência de páginas de opções e configurações do usuário. As implementações padrão da <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> e <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToStorage%2A> métodos manter alterações de propriedade em uma seção do usuário do registro se a propriedade pode ser convertida em uma cadeia de caracteres.  
  
## <a name="options-page-registry-path"></a>Caminho de registro da página de opções  
 Por padrão, o caminho do registro das propriedades gerenciadas por uma página de opções é determinado pela combinação <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>, a palavra DialogPage e o nome do tipo de classe da página de opções. Por exemplo, uma classe de página de opções pode ser definida da seguinte maneira.  
  
 [!code-csharp[VSSDKSupportForOptionsPages#1](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_1.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#1](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_1.vb)]  
  
 Se o <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A> é HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp, em seguida, os pares de nome e valor de propriedade são subchaves do HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp\DialogPage\ Company.OptionsPage.OptionsPageGeneral.  
  
 O caminho do registro da página de opções em si é determinado pela combinação <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, o word, ToolsOptionsPages e as opções da página categoria e nome. Por exemplo, se a página de opções personalizada tiver a categoria, páginas de opção Meu e o <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> é HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp, em seguida, a página de opções tem a chave do registro, HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ VisualStudio\8.0Exp\ToolsOptionsPages\My opção Pages\Custom.  
  
## <a name="toolsoptions-page-attributes-and-layout"></a>Layout e os atributos de página Ferramentas/opções  
 O <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> atributo determina o agrupamento de páginas de opções personalizadas em categorias na árvore de navegação do **opções** caixa de diálogo. O <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> atributo associa uma página de opções com o VSPackage que fornece a interface. Considere o fragmento de código a seguir:  
  
 [!code-csharp[VSSDKSupportForOptionsPages#2](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_2.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#2](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_2.vb)]  
  
 Isso declara MyPackage fornece duas páginas de opções, OptionsPageGeneral e OptionsPageCustom. No **opções** ambas as páginas de opções de caixa de diálogo, aparecem no **minhas páginas de opção** categoria como **geral** e **personalizado**, respectivamente.  
  
## <a name="option-attributes-and-layout"></a>Atributos de opção e o Layout  
 A interface do usuário (UI) que fornece a página determina a aparência das opções em uma página de opções personalizadas. O layout, a rotulação e a descrição das opções em uma página de opções genéricas são determinados pelos seguintes atributos:  
  
-   <xref:System.ComponentModel.CategoryAttribute>Determina a categoria da opção.  
  
-   <xref:System.ComponentModel.DisplayNameAttribute>Determina o nome de exibição da opção.  
  
-   <xref:System.ComponentModel.DescriptionAttribute>Determina a descrição da opção.  
  
    > [!NOTE]
    >  Atributos equivalentes, SRCategory, LocDisplayName e SRDescription, use recursos de cadeia de caracteres para localização e são definidos no [exemplo de projeto gerenciado](http://go.microsoft.com/fwlink/?LinkId=122774).  
  
 Considere o fragmento de código a seguir:  
  
 [!code-csharp[VSSDKSupportForOptionsPages#3](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_3.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#3](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_3.vb)]  
  
 A opção OptionInteger aparece na página de opções como **opção inteiro** no **minhas opções** categoria. Se a opção for selecionada, a descrição, **minha opção inteiro**, é exibido na caixa de descrição.  
  
## <a name="accessing-options-pages-from-another-vspackage"></a>Acessando páginas de opções de VSPackage outro  
 Um VSPackage que hospeda e gerencia uma página de opções pode ser acessado por meio de programação de VSPackage outro usando o modelo de automação. Por exemplo, no código a seguir um VSPackage é registrado como uma página de opção de hospedagem.  
  
 [!code-csharp[VSSDKSupportForOptionsPages#4](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_4.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#4](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_4.vb)]  
  
 O fragmento de código a seguir obtém o valor de OptionInteger de MyOptionPage:  
  
 [!code-csharp[VSSDKSupportForOptionsPages#5](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_5.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#5](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_5.vb)]  
  
 Quando o <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> atributo registra uma página de opções, a página está registrada em AutomationProperties chave se o `SupportsAutomation` argumento do atributo é `true`. Automação examina essa entrada de registro para encontrar o VSPackage associado e a automação e acessa a propriedade através da página de opções hospedado, nesse caso, minha página da grade.  
  
 O caminho do registro da propriedade de automação é determinado pela combinação <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, o word, AutomationProperties e as opções da página categoria e nome. Por exemplo, se a página de opções tem a categoria My Category, o nome de minha página da grade e o <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp e, em seguida, a propriedade de automação tem a chave do registro HKEY_LOCAL_MACHINE\SOFTWARE\ Página de grade Category\My Microsoft\VisualStudio\8.0Exp\AutomationProperties\My.  
  
> [!NOTE]
>  O nome canônico, minha página de grade Category.My, é o valor da subchave nome dessa chave.