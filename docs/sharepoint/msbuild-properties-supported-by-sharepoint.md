---
title: Propriedades de MSBuild suportadas por SharePoint | Microsoft Docs
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, MSBuild properties
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 115896965eb47eb6dc4a9cdbb0b9df8dd8972c5f
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="msbuild-properties-supported-by-sharepoint"></a>Propriedades de MSBuild suportadas por SharePoint
  Qualquer [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] propriedade definida no arquivo Microsoft.VisualStudio.SharePoint.targets, arquivo de projeto ou arquivo de usuário de projeto pode ser usada em [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projetos do SharePoint. Além de comuns [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] propriedades fornecidas pelo projeto, do SharePoint define propriedades adicionais que são específicas para projetos do SharePoint.  
  
 Para obter uma lista de comuns [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] propriedades, consulte [propriedades comuns de projeto MSBuild](http://go.microsoft.com/fwlink/?LinkID=168687). Para obter uma lista completa das propriedades com suporte a linguagem de programação, examinar o arquivo. targets, o arquivo de projeto (. csproj ou. vbproj) ou o arquivo de usuário do projeto (csproj.user ou. vbproj.user).  
  
## <a name="msbuild-properties-specific-to-sharepoint"></a>MSBuild propriedades específicas do SharePoint  
 A seguinte tabela lista [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] propriedades que se aplicam especificamente aos projetos do SharePoint no [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Existem outras propriedades, mas eles são para uso interno.  
  
|Nome da Propriedade|Descrição|  
|-------------------|-----------------|  
|SharePointSiteUrl|Uma cadeia de caracteres que representa o [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] no site do SharePoint.|  
|SandboxedSolution|Um valor booliano que indica se a solução é uma solução em área restrita.|  
|ActiveDeploymentConfiguration|A configuração de implantação ativa.|  
|IncludeAssemblyInPackage|Um valor booliano que indica se o assembly está incluído no arquivo do pacote.|  
|PreDeploymentCommand|Um valor de cadeia de caracteres que representa o comando para executar a etapa de comando antes da implantação.|  
|PostDeploymentCommand|Um valor de cadeia de caracteres que representa o comando para executar a etapa de comando de pós-implantação.|  
|CustomBeforeSharePointTargets|Uma cadeia de caracteres que representa o caminho de um [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] arquivo de destino. Se o arquivo de destino existe e está definido, ele será importado antes que qualquer dado de destinos do SharePoint. Essa propriedade permite que você personalize o processo de pacote por predefinindo as propriedades relacionadas ao empacotamento sem modificar o arquivo de destinos do SharePoint fornecido, mas o arquivo de destino ainda se aplica a todos os projetos do SharePoint.|  
|CustomAfterSharePointTargets|Uma cadeia de caracteres que representa o caminho de um [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] arquivo de destino. Se o arquivo de destino existe e está definido, é importado depois que todos os dados de destinos do SharePoint. Essa propriedade permite que você personalize o processo de pacote, substituindo as propriedades relacionadas ao empacotamento e destinos sem a necessidade de modificar o arquivo de destinos do SharePoint fornecido, mas o arquivo de destino ainda se aplica a todos os projetos do SharePoint.|  
|LayoutPath|Uma cadeia de caracteres que representa o diretório raiz onde cada um dos arquivos sejam empacotados são colocados temporariamente os antes de serem adicionados ao arquivo. wsp. Esse caminho pode ser útil saber quando você substituir os destinos BeforeLayout e AfterLayout para adicionar, remover ou modificar arquivos sejam empacotados, porque você pode usá-lo para alterar o conteúdo do arquivo. wsp.|  
|BasePackagePath|Uma cadeia de caracteres que representa a pasta na qual o pacote é colocado. Este valor usa o diretório de saída do projeto, como Bin\Debug.|  
|PackageExtension|Uma cadeia de caracteres que representa a extensão de nome de arquivo para acrescentar ao pacote. O valor padrão é wsp.|  
|AssemblyDeploymentTarget|Uma cadeia de caracteres que representa o local em que o assembly de projeto é implantado no servidor do SharePoint. Seu valor é GlobalAssemblyCache (o padrão) ou aplicativo Web. Essa propriedade também pode ser definida na janela Propriedades.|  
|PackageWithValidation|Um valor booleano que especifica se a validação é executada antes do empacotamento. Essa propriedade permite que você ignore erros de validação durante a criação de pacotes.|  
|ValidatePackageDependsOn|Uma cadeia de caracteres que define os destinos adicionais a serem executados antes do destino ValidatePackage.|  
|TokenReplacementFileExensions|Uma cadeia de caracteres que define os arquivos que têm seus tokens substituídos durante o empacotamento.|  
  
## <a name="using-msbuild-properties-in-the-properties-page"></a>Usando propriedades MSBuild na página de propriedades  
 Para obter flexibilidade, em vez de usar cadeias de caracteres codificadas no **linha de comando de pré-implantação** e **linha de comando de pós-implantação** caixas na página de propriedades do SharePoint, você pode usar o SharePoint propriedades como argumentos. Por exemplo, em vez de especificar um determinado [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] cadeia de caracteres para o site do SharePoint, você pode usar `$(SharePointSiteUrl)`.  
  
> [!NOTE]  
>  Você pode usar o [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] sintaxe variável `$(` *propertyName* `)` ou a sintaxe de variável de ambiente `%` *propertyName* `%` para especificar uma propriedade.  
  
## <a name="see-also"></a>Consulte também  
 [Referência do MSBuild](/visualstudio/msbuild/msbuild-reference)  
  
  