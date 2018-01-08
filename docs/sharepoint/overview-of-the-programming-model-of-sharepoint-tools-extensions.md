---
title: "Extensões de ferramentas de visão geral do modelo de programação do SharePoint | Microsoft Docs"
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
helpviewer_keywords:
- Visual Studio, extending tools
- SharePoint development in Visual Studio, extensibility object models
- SharePoint development in Visual Studio, extending tools
ms.assetid: aec8165b-dff9-47be-82a5-3fa38e579297
caps.latest.revision: "55"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 3b8d869dab81273262d23b7aa905370f530b24c5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="overview-of-the-programming-model-of-sharepoint-tools-extensions"></a>Visão geral do modelo de programação das extensões de ferramentas do SharePoint
  Quando você cria uma extensão para as ferramentas do SharePoint no Visual Studio, começar com a implementação de uma ou mais interfaces de extensibilidade que são expostas pelas ferramentas do SharePoint. Na maioria dos casos, você também usará outros tipos fornecidos pelas ferramentas do SharePoint para implementar recursos em sua extensão. Em alguns cenários, você também pode usar tipos de outros modelos de objeto fornecidos pelo Visual Studio e do SharePoint. Você deve entender a finalidade de cada um desses modelos de objeto e como usá-los uns com os outros para criar extensões para ferramentas do SharePoint.  
  
## <a name="extending-the-sharepoint-tools-by-implementing-extensibility-interfaces"></a>Estendendo as ferramentas do SharePoint com a implementação de Interfaces de extensibilidade  
 O Visual Studio usa o Managed Extensibility Framework (MEF) no .NET Framework 4 para fornecer o modelo de extensibilidade para as ferramentas do SharePoint. MEF é uma API (implementada no assembly System.ComponentModel.Composition) que permite que os aplicativos para expor pontos de extensibilidade e descobrir e carregar extensões de tempo de execução. Para obter mais informações sobre o MEF, consulte [Managed Extensibility Framework &#40; MEF &#41; ](/dotnet/framework/mef/index).  
  
 Para estender as ferramentas do SharePoint, implemente uma ou mais interfaces de extensibilidade que são expostas pelo Visual Studio. Você também deve aplicar o <xref:System.ComponentModel.Composition.ExportAttribute>, e ferramentas específicas do SharePoint adicional atributos conforme necessário, para sua implementação de interface. A tabela a seguir lista as interfaces que você pode implementar para estender as ferramentas do SharePoint.  
  
|Interface|Descrição|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>|Implemente esta interface para definir um novo tipo de item de projeto do SharePoint. Para obter um exemplo, consulte [como: definir um tipo de Item de projeto do SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).|  
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>|Implemente esta interface para estender um tipo de item de projeto do SharePoint que já está instalado no Visual Studio. Para obter um exemplo, consulte [como: criar uma extensão de Item de projeto do SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).|  
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>|Implemente esta interface para estender a projetos do SharePoint. Para obter um exemplo, consulte [como: criar uma extensão de projeto do SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).|  
|<xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep>|Implemente esta interface para definir uma nova etapa de implantação que pode ser executada quando um item de projeto do SharePoint é implantado ou cancelado. Para obter um exemplo, consulte [passo a passo: Criando uma etapa de implantação personalizada para projetos SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).|  
|<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>|Implementar essa interface para estender um nó existente no **conexões do SharePoint** nó o **Server Explorer** janela. Para obter um exemplo, consulte [como: estender um nó SharePoint no Gerenciador de servidores](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).|  
|<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider>|Implementar essa interface para definir um novo tipo de nó no **conexões do SharePoint** nó o **Server Explorer** janela. Para obter um exemplo, consulte [como: estender um nó SharePoint no Gerenciador de servidores](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).|  
|<xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule>|Implemente esta interface para definir uma regra de validação de recurso personalizado. Para obter um exemplo, consulte [como: Criar recurso de personalizada e regras de validação de pacote para soluções do SharePoint](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).|  
|<xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule>|Implemente esta interface para definir uma regra de validação de pacote personalizado. Para obter um exemplo, consulte [como: Criar recurso de personalizada e regras de validação de pacote para soluções do SharePoint](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).|  
  
 Depois de implementar uma extensão das ferramentas do SharePoint, você deve implantar o assembly de extensão em um pacote de extensão (VSIX) do Visual Studio para permitir que o Visual Studio descobrir e carregar a extensão. Para obter mais informações, consulte [implantação de extensões para ferramentas do SharePoint no Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="understanding-the-object-models-that-you-use-in-sharepoint-tools-extensions"></a>Noções básicas sobre os modelos de objeto que você usa no SharePoint extensões de ferramentas  
 Há vários modelos de objeto, que você pode usar ao criar extensões para ferramentas do SharePoint:  
  
-   *Modelo de objeto de ferramentas do SharePoint*. Esse modelo de objeto fornece as interfaces de extensibilidade que você implementar para criar extensões de ferramentas do SharePoint e outros tipos relacionados.  
  
-   *Modelos de objeto de automação e a integração Visual do Studio*. Use esses modelos de objeto para acessar os recursos do Visual Studio que estão além do escopo do modelo de objeto de ferramentas do SharePoint.  
  
    > [!NOTE]  
    >  Você pode converter alguns objetos no modelo de objeto de ferramentas do SharePoint para objetos de automação do Visual Studio e modelos de objeto de integração e vice-versa, usando o serviço de projeto do SharePoint. Para obter mais informações, consulte [converter entre SharePoint sistema de tipos de projeto e outros tipos de projeto Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).  
  
-   *Os modelos de objeto de cliente e servidor do SharePoint*. Use esses modelos de objeto para modificar um site do SharePoint ou para recuperar dados de um site do SharePoint no contexto de uma extensão de ferramentas do SharePoint.  
  
### <a name="sharepoint-tools-object-model"></a>Modelo de objeto de ferramentas do SharePoint  
 Cada extensão de ferramentas do SharePoint usa tipos no modelo de objeto de ferramentas do SharePoint para definir o comportamento de núcleos e a funcionalidade da extensão. A tabela a seguir descreve os namespaces que estão incluídos neste modelo de objeto.  
  
|Assembly|Namespace|Descrição|  
|--------------|---------------|-----------------|  
|Microsoft.VisualStudio.SharePoint.dll|<xref:Microsoft.VisualStudio.SharePoint>|Contém tipos que podem ser usados para estender e automatizar o sistema de projeto do SharePoint. Por exemplo, você pode estender os itens de projeto e projetos internos do SharePoint, ou você pode criar seus próprios itens de projeto. Para obter mais informações, consulte [estendendo o sistema de projeto do SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).|  
||<xref:Microsoft.VisualStudio.SharePoint.Deployment>|Contém tipos que podem ser usados para estender o processo de implantação para projetos do SharePoint, como criar suas próprias etapas de implantação e configurações de implantação. Para obter mais informações, consulte [estendendo SharePoint empacotamento e implantação](../sharepoint/extending-sharepoint-packaging-and-deployment.md).|  
||<xref:Microsoft.VisualStudio.SharePoint.Explorer>|Contém tipos que podem ser usados para estender nós sob o **conexões do SharePoint** nó no **Server Explorer** janela, ou para definir novos tipos de nós. Para obter mais informações, consulte [estendendo o nó de conexões do SharePoint no Gerenciador de servidores](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).|  
||<xref:Microsoft.VisualStudio.SharePoint.Features>|Contém tipos que você usa para acessar as definições de recurso em um projeto do SharePoint.|  
||<xref:Microsoft.VisualStudio.SharePoint.Packages>|Contém tipos que você usa para acessar a definição do pacote em uma solução do SharePoint.|  
||<xref:Microsoft.VisualStudio.SharePoint.Validation>|Contém tipos que você pode usar para personalizar o comportamento de validação de pacote e de recurso para projetos do SharePoint. Para obter mais informações, consulte [como: Criar recurso de personalizada e regras de validação de pacote para soluções do SharePoint](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).|  
|Microsoft.VisualStudio.SharePoint.Commands.dll|<xref:Microsoft.VisualStudio.SharePoint.Commands>|Contém tipos que você pode usar para criar personalizado *comandos do SharePoint*. Um comando do SharePoint é um método que chama o modelo de objeto de servidor do SharePoint de uma extensão de ferramentas do SharePoint. Para obter mais informações, consulte [chamando os modelos de objeto do SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).|  
|Microsoft.VisualStudio.SharePoint.Explorer.Extensions.dll|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions>|Contém tipos que você pode usar para obter informações sobre interno **Server Explorer** nós que representam componentes individuais em um site do SharePoint, como um nó que representa uma lista, um campo ou um tipo de conteúdo. Para obter mais informações, consulte [estendendo o nó de conexões do SharePoint no Gerenciador de servidores](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).|  
  
### <a name="visual-studio-automation-object-model"></a>Modelo de objeto de automação do Visual Studio  
 O modelo de objeto de automação do Visual Studio fornece APIs que você pode usar para automatizar projetos do Visual Studio e o IDE. Use o modelo de objeto do Visual Studio para executar tarefas relacionadas ao projeto que não são específicas para projetos do SharePoint ou executar outras tarefas de automação geral no Visual Studio. Tradicionalmente, esse modelo de objeto é geralmente usado em macros e suplementos do Visual Studio, mas você também pode usá-lo em extensões de ferramentas do SharePoint.  
  
 A parte principal do modelo de objeto de automação do Visual Studio é definida no assembly EnvDTE.dll. O EnvDTE*versão*. dll assemblies fornecem funcionalidade adicional que foi introduzida em versões específicas do Visual Studio. Esses assemblies são incluídos com o Visual Studio.  
  
 Para obter mais informações sobre o modelo de objeto de automação, consulte [referência de SDK do Visual Studio](../extensibility/visual-studio-sdk-reference.md).  
  
### <a name="visual-studio-integration-object-model"></a>Modelo de objeto de integração do Visual Studio  
 O modelo de objeto de integração fornece APIs que você pode usar para adicionar recursos para o Visual Studio, criando uma *VSPackage*. Um VSPackage é um módulo que estende o Visual Studio IDE, fornecendo recursos personalizados como janelas de ferramentas, editores, designers, serviços e projetos.  
  
 Se você quiser adicionar um novo recurso do Visual Studio que será usado com as ferramentas internas do SharePoint, você pode usar o modelo de objeto de integração. Por exemplo, se você criar um item de projeto do SharePoint personalizado que representa uma ação personalizada para um site do SharePoint, você também pode criar um VSPackage que implementa um designer para a ação personalizada. Você pode associar o designer com a ação personalizada com a adição de um item de menu de atalho para o item de projeto que representa a ação personalizada na **Gerenciador de soluções**. Você pode abrir o designer abrindo o menu de atalho (clicando com o projeto de ação personalizada de item ou selecioná-la e, em seguida, escolhendo o Shift + F10 chaves) e, em seguida, escolhendo **abrir**.  
  
 Esse modelo de objeto é definido em um conjunto de assemblies que são incluídos com o SDK do Visual Studio. Alguns dos assemblies principais neste modelo de objeto incluem Microsoft.VisualStudio.Shell.11.0.dll, Microsoft.VisualStudio.Shell.Interop.dll e Microsoft.VisualStudio.OLE.Interop.dll.  
  
 Para obter mais informações sobre o modelo de objeto de integração, consulte [visão geral do modelo de automação](/visualstudio/extensibility/internals/automation-model-overview) e [referência de SDK do Visual Studio](/visualstudio/extensibility/visual-studio-sdk-reference).  
  
### <a name="sharepoint-object-models"></a>Modelos de objeto do SharePoint  
 Extensões de ferramentas do SharePoint podem usar APIs do SharePoint para modificar um site do SharePoint ou para recuperar dados de um site do SharePoint. [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)]e [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] fornece dois modelos de objeto diferentes: um modelo de objeto de servidor e um modelo de objeto do cliente.  
  
 Você pode usar APIs em qualquer modelo de objeto em uma extensão de ferramentas do SharePoint, mas cada modelo de objeto tem algumas vantagens e desvantagens no contexto de extensões de ferramentas do SharePoint. Para obter mais informações, consulte [chamando os modelos de objeto do SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
|Modelo de objeto|Descrição|  
|------------------|-----------------|  
|Modelo de objeto de servidor|O modelo de objeto do servidor fornece acesso a todos os recursos que [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] e [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] expor por meio de programação. Esse modelo de objeto foi projetado para ser usado por meio de soluções do SharePoint que são executados no servidor do SharePoint. A maioria desse modelo de objeto é definida no assembly Microsoft.SharePoint.dll. Para obter mais informações sobre o modelo de objeto de servidor, consulte [usando o modelo de objeto do lado do servidor do SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=177796).|  
|Modelo de objeto do cliente|O modelo de objeto do cliente é um subconjunto do modelo de objeto de servidor que pode ser usado para interagir com dados do SharePoint de um cliente remoto ou servidor. Ele foi projetado para minimizar o número de viagens de ida e que devem ser executadas para realizar tarefas comuns. A maior parte do modelo de objeto do cliente é definida no assembly Microsoft.SharePoint.Client.dll e Microsoft.SharePoint.Client.Runtime.dll. Para obter mais informações sobre o modelo de objeto do cliente, consulte [modelo de objeto gerenciado do cliente](http://go.microsoft.com/fwlink/?LinkId=177797).|  
  
## <a name="see-also"></a>Consulte também  
 [Estendendo as ferramentas do SharePoint no Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)   
 [A chamada para os modelos de objeto do SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md)   
 [Usando o serviço de projeto do SharePoint](../sharepoint/using-the-sharepoint-project-service.md)  
  
  