---
title: "Parâmetros substituíveis | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, tokens
- tokens [SharePoint development in Visual Studio]
- replaceable parameters [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, replaceable parameters
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: fa002f58ffd749cef9a4cbf9b536a36d7901b105
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="replaceable-parameters"></a>Parâmetros substituíveis
  Parâmetros substituíveis, ou *tokens*, pode ser usado em arquivos de projeto para fornecer valores para os itens de solução do SharePoint cujos valores reais não são conhecidos no tempo de design. Eles são semelhantes em função para o padrão [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] tokens de modelo. Para obter mais informações, consulte [parâmetros de modelo](/visualstudio/ide/template-parameters).  
  
## <a name="token-format"></a>Formato do token  
 Tokens começam e terminam com um caractere de cifrão ($). Todos os tokens usados são substituídos por valores reais quando um projeto é empacotado em um arquivo de pacote (. wsp) de solução do SharePoint no momento da implantação. Por exemplo, o token **$SharePoint.Package.Name$** pode resolver para a cadeia de caracteres "Pacote do SharePoint de teste".  
  
## <a name="token-rules"></a>Regras de token  
 As seguintes regras se aplicam aos tokens:  
  
-   Tokens podem ser especificados em qualquer lugar em uma linha.  
  
-   Tokens não podem abranger várias linhas.  
  
-   O mesmo token pode ser especificado várias vezes na mesma linha e no mesmo arquivo.  
  
-   Tokens diferentes podem ser especificadas na mesma linha.  
  
 Tokens que não seguem estas regras são ignorados sem fornecer um aviso ou erro.  
  
 A substituição de tokens de valores de cadeia de caracteres é feita imediatamente após a transformação de manifesto, permitindo que modelos manifestos editados por um usuário para usar tokens.  
  
### <a name="token-name-resolution"></a>Resolução de nome do token  
 Na maioria dos casos, um token resolve para um valor específico, independentemente de onde ele está contido. No entanto, se o token estiver relacionado a um pacote ou um recurso, valor do token depende de onde ele está contido. Por exemplo, se um recurso está no pacote um, em seguida, o token `$SharePoint.Package.Name$` resolve para o valor "Pacote A." Se o mesmo recurso está no pacote B, em seguida, `$SharePoint.Package.Name$` resolve para o "Pacote B."  
  
## <a name="tokens-list"></a>Lista de tokens  
 A tabela a seguir lista os tokens disponíveis.  
  
|Nome|Descrição|  
|----------|-----------------|  
|$SharePoint.Project.FileName$|O nome do arquivo de projeto que contém, por exemplo, "NewProj.csproj".|  
|$SharePoint.Project.FileNameWithoutExtension$|O nome do arquivo de projeto que contém, sem a extensão de nome de arquivo. Por exemplo, "NewProj".|  
|$SharePoint.Project.AssemblyFullName$|O nome para exibição (nome de alta segurança) do projeto do assembly de saída.|  
|$SharePoint.Project.AssemblyFileName$|O nome do projeto do assembly de saída.|  
|$SharePoint.Project.AssemblyFileNameWithoutExtension$|O nome do projeto do assembly, sem a extensão de nome de arquivo de saída.|  
|$SharePoint.Project.AssemblyPublicKeyToken$|Assembly, convertido em uma cadeia de caracteres de saída do token de chave pública do projeto. (16-caracteres "x2" formato hexadecimal.)|  
|$SharePoint.Package.Name$|O nome do pacote que contém.|  
|$SharePoint.Package.FileName$|O nome do arquivo de definição do pacote que o contém.|  
|$SharePoint.Package.FileNameWithoutExtension$|O nome (sem extensão) do arquivo de definição do pacote que o contém.|  
|$SharePoint.Package.Id$|A ID do SharePoint para o pacote de conteúdo. Se um recurso é usado em mais de um pacote, esse valor será alterado.|  
|$SharePoint.Feature.FileName$|O nome do arquivo de definição do recurso que contém, como Feature1.feature.|  
|$SharePoint.Feature.FileNameWithoutExtension$|O nome do arquivo de definição de recurso, sem a extensão de nome de arquivo.|  
|$SharePoint.Feature.DeploymentPath$|O nome da pasta que contém o recurso no pacote. Esse token é igual à propriedade "Caminho de implantação" no Designer de recursos. Um valor de exemplo é "Project1_Feature1".|  
|$SharePoint.Feature.Id$|A ID do SharePoint do recurso que contém. Esse token, como com todos os tokens de nível de recurso, pode ser usado apenas pelos arquivos incluídos em um pacote por meio de um recurso, não adicionados diretamente a um pacote fora de um recurso.|  
|$SharePoint.ProjectItem.Name$|O nome do item de projeto (não o nome de arquivo), como obtidos de **ISharePointProjectItem.Name**.|  
|$SharePoint.Type. \<GUID >. AssemblyQualifiedName$|O nome qualificado do assembly da correspondência de tipo de [!INCLUDE[TLA2#tla_guid](../sharepoint/includes/tla2sharptla-guid-md.md)] do token. O formato da [!INCLUDE[TLA2#tla_guid](../sharepoint/includes/tla2sharptla-guid-md.md)] é minúsculo e corresponde ao formato Guid.ToString("D") (ou seja, xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx).|  
|$SharePoint.Type. \<GUID >. FullName$|O nome completo do tipo correspondente GUID no token. O formato do GUID é minúsculo e corresponde ao formato Guid.ToString("D") (ou seja, xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx).|  
  
## <a name="adding-extensions-to-the-token-replacement-file-extensions-list"></a>Adicionando extensões para a substituição do Token de lista de extensões de arquivo  
 Embora os tokens, teoricamente, podem ser usados por qualquer arquivo que pertence a um projeto do SharePoint item incluído no pacote, por padrão, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] procura tokens somente em arquivos de pacote, arquivos de manifesto e arquivos que têm as seguintes extensões:  
  
-   [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]  
  
-   ASCX  
  
-   ASPX  
  
-   Web Part  
  
-   DWP  
  
 Essas extensões são definidas pelo `<TokenReplacementFileExtensions>` elemento no arquivo Microsoft.VisualStudio.SharePoint.targets, localizado em de... \\< arquivos de programas\>\MSBuild\Microsoft\VisualStudio\v11.0\SharePointTools pasta.  
  
 No entanto, você pode adicionar extensões de arquivo adicionais à lista. Para fazer isso, adicione um `<TokenReplacementFileExtensions>` elemento para qualquer PropertyGroup no arquivo de projeto do SharePoint que está definido antes do \<importação > do arquivo de destinos do SharePoint.  
  
> [!NOTE]  
>  Como a substituição do token ocorre depois que um projeto é compilado, você não deve adicionar extensões de arquivo para tipos de arquivo que são compilados, como. cs,. vb ou. resx. Tokens são substituídos somente em arquivos que não são compilados.  
  
 Por exemplo, para adicionar as extensões de nome de arquivo ".myextension" e ".yourextension" à lista de extensões de nome de arquivo de substituição do token, adicione o seguinte em um arquivo. csproj:  
  
```  
<Project ToolsVersion="4.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <PropertyGroup>  
    <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
    <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>  
.  
.  
.  
    <!-- Define the following property to add your extension to the list of token replacement file extensions.  -->  
<TokenReplacementFileExtensions>myextension;yourextension</TokenReplacementFileExtensions>  
</PropertyGroup>  
```  
  
 Como alternativa, você pode adicionar a extensão diretamente para o arquivo. targets. No entanto, isso altera a lista de extensões de todos os projetos do SharePoint empacotados no sistema local, não apenas seu próprio. Isso pode ser conveniente quando você o desenvolvedor exclusivo no sistema ou se precisam de mais de seus projetos-lo. No entanto, porque é específicas do sistema, essa abordagem não é muito portáteis e, portanto, é recomendável que você adicionar as extensões para o arquivo de projeto em vez disso.  
  
## <a name="see-also"></a>Consulte também  
 [Desenvolvendo soluções do SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
  