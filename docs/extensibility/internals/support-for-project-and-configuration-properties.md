---
title: Suporte para o projeto e as propriedades de configuração | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project properties, supporting with Visual Studio SDK
- configuration properties, suppporting with Visual Studio SDK
ms.assetid: 9fcfaa0f-7b41-4b68-82ec-7a151dca5d7e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 823bfa0453d3e33fea2daa51779b1fe4800a1a86
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="support-for-project-and-configuration-properties"></a>Suporte para o projeto e as propriedades de configuração
O **propriedades** janela no [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente de desenvolvimento integrado (IDE) pode exibir as propriedades de projeto e configuração. Você pode fornecer uma página de propriedades para seu próprio tipo de projeto para que o usuário pode definir propriedades de seu aplicativo.  
  
 Selecionando um nó de projeto em **Solution Explorer** e, em seguida, clicando em **propriedades** no **projeto** menu, você pode abrir uma caixa de diálogo que inclui o projeto e configuração Propriedades. Em [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] e [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]e tipos derivados desses idiomas, esta caixa de diálogo aparece como uma página com guias de projeto a [geral, ambiente, caixa de diálogo Opções](../../ide/reference/general-environment-options-dialog-box.md). Para obter mais informações, consulte [não está em compilação: passo a passo: expondo o projeto e as propriedades de configuração (c#)](http://msdn.microsoft.com/en-us/d850d63b-25e2-4505-9f3d-eb038d7c1d0e).  
  
 A estrutura de pacote gerenciado para projetos (MPFProj) fornece classes auxiliares para criar e gerenciar o novo sistema de projeto. Você pode encontrar a fonte de instruções de código e compilação em [MPF de projetos - Visual Studio 2013](http://mpfproj12.codeplex.com/).  
  
## <a name="persistence-of-project-and-configuration-properties"></a>Persistência de projeto e as propriedades de configuração  
 Propriedades do projeto e configuração são mantidas em um arquivo de projeto que tem qualquer extensão de nome de arquivo associado ao tipo de projeto, por exemplo,. csproj,. vbproj e .myproj. Projetos de linguagem geralmente usam um arquivo de modelo para gerar o arquivo de projeto. No entanto, há realmente várias maneiras para associar modelos e tipos de projeto. Para obter mais informações, consulte [descrição do modelo do diretório (. Arquivos Vsdir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md).  
  
 Propriedades do projeto e configuração são criadas com a adição de itens para o arquivo de modelo. Essas propriedades, em seguida, estão disponíveis para qualquer projeto criado usando o tipo de projeto que usa este modelo. [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] projetos e o MPFProj ambos usam o [não está em compilação: Visão geral do MSBuild](http://msdn.microsoft.com/en-us/b588fd73-a45b-4706-908f-cc131bccfbde) esquema para arquivos de modelo. Esses arquivos têm uma seção PropertyGroup para cada configuração. Propriedades de projetos normalmente são mantidas na primeira seção PropertyGroup, que tem um argumento de configuração definido como uma cadeia de caracteres nula.  
  
 O código a seguir mostra o início de um arquivo de projeto MSBuild básico.  
  
```  
<Project MSBuildVersion="2.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <PropertyGroup>  
    <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
    <Name>SomeProjectSix</Name>  
    <SchemaVersion>2.0</SchemaVersion>  
  </PropertyGroup>  
  <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">  
    <Optimize>false</Optimize>  
  </PropertyGroup>  
  <PropertyGroup Condition=" '$(Configuration)' == 'Release' ">  
    <Optimize>true</Optimize>  
```  
  
 Nesse arquivo de projeto, `<Name>` e `<SchemaVersion>` são propriedades do projeto, e `<Optimize>` é uma propriedade de configuração.  
  
 É responsabilidade do projeto para persistir as propriedades de projeto e a configuração do arquivo do projeto.  
  
> [!NOTE]
>  Um projeto pode otimizar persistência persistentes somente valores de propriedade que são diferentes dos seus valores padrão.  
  
## <a name="support-for-project-and-configuration-properties"></a>Suporte para o projeto e as propriedades de configuração  
 O `Microsoft.VisualStudio.Package.SettingsPage` classe implementa as páginas de propriedades de projeto e configuração. A implementação padrão de `SettingsPage` oferece propriedades públicas para um usuário em uma grade de propriedade genérica. O `Microsoft.VisualStudio.Package.HierarchyNode.GetPropertyPageGuids` método seleciona classes derivadas de `SettingsPage` para grades de propriedades do projeto. O `Microsoft.VisualStudio.Package.ProjectNode.GetConfigPropertyPageGuids` método seleciona classes derivadas de `SettingsPage` para grades de propriedades de configuração. O tipo de projeto deve substituir esses métodos para selecionar as páginas de propriedade apropriada.  
  
 O `SettingsPage` classe e o `Microsoft.VisualStudio.Package.ProjectNode` classe oferecer esses métodos para manter as propriedades do projeto e configuração:  
  
-   `Microsoft.VisualStudio.Package.ProjectNode.GetProjectProperty` e `Microsoft.VisualStudio.Package.ProjectNode.SetProjectProperty` persistir as propriedades do projeto.  
  
-   `Microsoft.VisualStudio.Package.SettingsPage.GetConfigProperty` e `Microsoft.VisualStudio.Package.SettingsPage.SetConfigProperty` persistir as propriedades de configuração.  
  
    > [!NOTE]
    >  As implementações do `Microsoft.VisualStudio.Package.SettingsPage` e `Microsoft.VisualStudio.Package.ProjectNode` uso de classes de `Microsoft.Build.BuildEngine` métodos (MSBuild) para obter e definir propriedades do projeto e configuração do arquivo de projeto.  
  
 A classe que deriva de `SettingsPage` deve implementar `Microsoft.VisualStudio.Package.SettingsPage.ApplyChanges` e `Microsoft.VisualStudio.Package.SettingsPage.BindProperties` para manter o projeto ou a configuração de propriedades do arquivo do projeto.  
  
## <a name="provideobjectattribute-and-registry-path"></a>ProvideObjectAttribute e o caminho do registro  
 Classes derivadas de `SettingsPage` são projetados para ser compartilhado entre VSPackages. Para tornar um VSPackage criar uma classe derivada de `SettingsPage`, adicione um `Microsoft.VisualStudio.Shell.ProvideObjectAttribute` para uma classe derivada de `Microsoft.VisualStudio.Shell.Package`.  
  
 [!code-csharp[VSSDKSupportProjectConfigurationProperties#1](../../extensibility/internals/codesnippet/CSharp/support-for-project-and-configuration-properties_1.cs)]
 [!code-vb[VSSDKSupportProjectConfigurationProperties#1](../../extensibility/internals/codesnippet/VisualBasic/support-for-project-and-configuration-properties_1.vb)]  
  
 O VSPackage à qual o atributo está conectado não tem importância. Quando um VSPackage é registrado com [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], a id de classe (CLSID) de qualquer objeto que pode ser criado é registrada para que uma chamada para <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry.CreateInstance%2A> pode criá-lo.  
  
 O caminho do registro de um objeto que pode ser criado é determinado pela combinação <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>, o word, CLSID e o guid do tipo de objeto. Se `MyProjectPropertyPage` classe tiver um guid de {3c693da2-5bca-49b3-bd95-ffe0a39dd723} e o UserRegistryRoot é HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp, o caminho do registro seria \SourceControl \8.0Exp\CLSID\\{3c693da2-5bca-49b3-bd95-ffe0a39dd723}.  
  
## <a name="project-and-configuration-property-attributes-and-layout"></a>Projeto e os atributos de propriedade de configuração e o Layout  
 O <xref:System.ComponentModel.CategoryAttribute>, <xref:System.ComponentModel.DisplayNameAttribute>, e <xref:System.ComponentModel.DescriptionAttribute> atributos determinam o layout, a rotulação e a descrição das propriedades de projeto e configuração em uma página de propriedade genérica. Esses atributos determine a categoria, exiba o nome e descrição da opção, respectivamente.  
  
> [!NOTE]
>  Atributos equivalentes, SRCategory, LocDisplayName e SRDescription, use recursos de cadeia de caracteres para localização e são definidos em [MPF de projetos - Visual Studio 2013](http://mpfproj12.codeplex.com/).  
  
 Considere o fragmento de código a seguir:  
  
 [!code-vb[VSSDKSupportProjectConfigurationProperties#2](../../extensibility/internals/codesnippet/VisualBasic/support-for-project-and-configuration-properties_2.vb)]
 [!code-csharp[VSSDKSupportProjectConfigurationProperties#2](../../extensibility/internals/codesnippet/CSharp/support-for-project-and-configuration-properties_2.cs)]  
  
 O `MyConfigProp` propriedade configuração aparece na página de propriedades de configuração como **Minhas propriedades de configuração** na categoria, **Categoria Meus**. Se a opção for selecionada, a descrição, **descrição meu**, será exibida no painel de descrição.  
  
## <a name="see-also"></a>Consulte também  
 [Adicionando e removendo páginas de propriedade](../../extensibility/adding-and-removing-property-pages.md)   
 [Projetos](../../extensibility/internals/projects.md)   
 [Arquivos de descrição do diretório do modelo (.Vsdir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)
