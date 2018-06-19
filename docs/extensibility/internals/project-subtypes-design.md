---
title: Design de subtipos de projeto | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project subtypes, design
ms.assetid: 405488bb-1362-40ed-b0f1-04a57fc98c56
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6a931d6509b5a8a90f371986f4ddb8955c64387d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31133793"
---
# <a name="project-subtypes-design"></a>Design de subtipos de projeto
Subtipos de projeto permitem VSPackages estender projetos com base no Microsoft Build Engine (MSBuild). O uso de agregação permite reutilizar a maior parte do sistema de projeto principal gerenciado implementado em [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ainda ainda personalizar o comportamento de um determinado cenário.  
  
 Os tópicos a seguir detalham o design básico e a implementação de subtipos de projeto:  
  
-   Design de subtipo de projeto.  
  
-   Agregação de vários nível.  
  
-   Interfaces de suporte.  
  
## <a name="project-subtype-design"></a>Design de subtipo de projeto  
 A inicialização de um subtipo de projeto é obtida agregando principal <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> objetos. Essa agregação permite que um subtipo de projeto substituir ou aumentar a maioria dos recursos do projeto base. Subtipos de projeto ter a chance de primeiro para manipular propriedades usando <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>, comandos usando <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>e o gerenciamento de item de projeto usando <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>. Também podem estender os subtipos de projeto:  
  
-   Objetos de configuração do projeto.  
  
-   Objetos de configuração dependente.  
  
-   Objetos de configuração independente procurar.  
  
-   Objetos de automação do projeto.  
  
-   Coleções de propriedade de automação do projeto.  
  
 Para obter mais informações sobre extensibilidade por subtipos de projeto, consulte [propriedades e métodos estendidos por projeto subtipos](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md).  
  
##### <a name="policy-files"></a>Arquivos de política  
 O [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente fornece um exemplo de estender o sistema de projeto base com um subtipo de projeto em sua implementação de arquivos de política. Um arquivo de política permite que a formatação do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente por meio do gerenciamento de recursos que incluem o Gerenciador de soluções, **Adicionar projeto** caixa de diálogo, **Adicionar Novo Item** caixa de diálogo e o  **Propriedades** caixa de diálogo. O subtipo de política substitui e aprimora esses recursos por meio de <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg>, `IOleCommandTarget` e <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> implementações.  
  
##### <a name="aggregation-mechanism"></a>Mecanismo de agregação  
 Mecanismo de agregação de subtipo de projeto do ambiente dá suporte a vários níveis de agregação, permitindo um subtipo avançado para ser implementada por mais de um projeto de um flavoring. Além disso, os objetos de suporte de um projeto de subtipo, como <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>, foram projetados para permitir vários níveis de camadas. Para manter as restrições de COM e COM regras de agregação, subtipos de projeto e projetos base precisam ser programados de forma cooperativa para permitir o subtipo interno ou a base participar corretamente a delegação de chamadas de método e gerenciando contagens de referência . Ou seja, o projeto prestes a ser agregada deve ser programado para dar suporte a agregação.  
  
 A ilustração a seguir mostra uma representação esquemática de uma agregação de subtipo de projeto de vários níveis.  
  
 ![Gráfico de projectflavor de vários níveis do Visual Studio](../../extensibility/internals/media/vs_multilevelprojectflavor.gif "VS_MultilevelProjectFlavor")  
Subtipo de projeto de vários níveis  
  
 Uma agregação de subtipo de vários níveis de projeto consiste em três níveis, um projeto de base, que é agregada por um subtipo de projeto, em seguida, agregadas por um subtipo de projeto avançadas. A figura se concentra em algumas das interfaces de suporte que são fornecidas como parte do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] arquitetura de subtipo de projeto.  
  
##### <a name="deployment-mechanisms"></a>Mecanismos de implantação  
 Entre muitos do sistema de projeto base funcionalidades aprimoradas por um subtipo de projeto são mecanismos de implantação. Um subtipo de projeto influencia mecanismos de implantação com a implementação de interfaces de configuração (como <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>) que são recuperados pela chamada de QueryInterface no <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider>. Em um cenário em que o subtipo de projeto e o subtipo de projeto avançadas adicionam implementações de configuração diferentes, o projeto base chama `QueryInterface` no subtipo de projeto avançadas `IUnknown`. Se o subtipo de projeto interna contém a implementação de configuração que está solicitando o projeto de base, o subtipo de projeto avançadas delega para a implementação fornecida pelo subtipo de projeto interna. Como um mecanismo para persistir o estado do nível de uma agregação para outro, todos os níveis de subtipos de projeto implementam <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> manter a compilação não relacionadas a dados XML nos arquivos de projeto. Para obter mais informações, consulte [persistência de dados no arquivo de projeto MSBuild](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md). <xref:EnvDTE80.IInternalExtenderProvider> é implementado como um mecanismo para recuperar os extensores de automação de subtipos de projeto.  
  
 A ilustração a seguir se concentra na implementação de extensor de automação, o objeto de procura de configuração de projeto em particular, usado por subtipos de projeto para estender o sistema de projeto base.  
  
 ![Gráfico de extensor de automático de tipo de projeto do VS](../../extensibility/internals/media/vs_projectflavorautoextender.gif "VS_ProjectFlavorAutoExtender")  
Extensor de automação de subtipo de projeto.  
  
 Subtipos de projeto adicional podem estender o sistema de projeto base estendendo o modelo de objeto de automação. Eles são definidos como parte do objeto de automação de DTE e são usados para estender o objeto de projeto, o `ProjectItem` objeto e o `Configuration` objeto. Para obter mais informações, consulte [estendendo o modelo de objeto do projeto Base](../../extensibility/internals/extending-the-object-model-of-the-base-project.md).  
  
## <a name="multi-level-aggregation"></a>Agregação de vários nível  
 Uma implementação de subtipo de projeto que encapsula um subtipo de projeto de nível inferior precisa ser programados de forma cooperativa para permitir que o subtipo de projeto interna funcionar corretamente. Inclui uma lista de responsabilidades de programação:  
  
-   O <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> deve ser delegado a implementação do subtipo do projeto que está encapsulando o subtipo interno de <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> implementação do subtipo do projeto interna para ambos <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Load%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Save%2A> métodos.  
  
-   O <xref:EnvDTE80.IInternalExtenderProvider> implementação do subtipo de projeto do wrapper deve delegar ao de seu subtipo de projeto interna. Em particular, a implementação de <xref:EnvDTE80.IInternalExtenderProvider.GetExtenderNames%2A> deve obter a cadeia de caracteres de nomes do subtipo de projeto interna e, em seguida, concatenar cadeias de caracteres que deseja adicionar como extensores.  
  
-   O <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> deve criar uma instância de implementação de um subtipo de projeto de wrapper de <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg> objeto do seu interna subtipo de projeto e mantê-la como um delegado particular, já que somente o objeto de configuração de projeto do projeto base diretamente sabe que o wrapper objeto de configuração do subtipo de projeto existe. O subtipo de projeto externa inicialmente escolha interfaces de configuração que deseja tratar diretamente e, então, delegar o restante para a implementação do subtipo de projeto interna de <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg.get_CfgType%2A>.  
  
## <a name="supporting-interfaces"></a>Interfaces de suporte  
 O projeto base delega chamadas para dar suporte a interfaces adicionadas por um subtipo de projeto, para estender a vários aspectos da sua implementação. Isso inclui a extensão de objetos de configuração de projeto e de vários objetos de navegador de propriedade. Essas interfaces são recuperadas chamando `QueryInterface` na `punkOuter` (um ponteiro para o `IUnknown`) do agregador de subtipo de projeto externo.  
  
|Interface|Subtipo de projeto|  
|---------------|---------------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>|Permite que o subtipo de projeto para:<br /><br /> -Fornecer uma implementação de <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>.<br />-Controlar a inicialização do depurador, permitindo que o subtipo de projeto fornecer sua própria implementação de <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>.<br />-Desabilite a avaliação da expressão de tempo de design ao manipular adequadamente a `DBGLAUNCH_DesignTimeExprEval` maiusculas em sua implementação de <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.QueryDebugLaunch%2A>.|  
|<xref:EnvDTE80.IInternalExtenderProvider>|Permite que o subtipo de projeto para:<br /><br /> -Estender o <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> do projeto para adicionar ou remover propriedades de configuração independente do projeto.<br />-Estender o objeto de automação do projeto (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>) do projeto.<br /><br /> Valores de propriedade acima são tirados <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> enumeração.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>|Permite que o subtipo de projeto mapear para o <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg> objeto, considerando o objeto de procura de configuração de projeto.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBrowseObject>|Permite que o subtipo de projeto mapear para o <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> ou `VSITEMID` objeto, considerando o objeto de procura de configuração de projeto.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>|Permite que o subtipo de projeto manter os dados XML estruturado arbitrários para o arquivo de projeto (. vbproj ou. csproj). Esses dados não são visíveis para o MSBuild.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>|Permite que o subtipo de projeto para:<br /><br /> -Adicione novas propriedades de MSBuild a ser mantido.<br />-Remova propriedades desnecessárias do MSBuild.<br />-Consulta para um valor atual de uma propriedade de MSBuild.<br />-Altere o valor atual de uma propriedade de MSBuild.|  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>