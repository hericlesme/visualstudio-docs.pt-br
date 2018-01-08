---
title: "Usando o serviço de projeto do SharePoint | Microsoft Docs"
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
- SharePoint project service
- SharePoint development in Visual Studio, extensibility features
ms.assetid: bfb6cbc7-6c28-4e1a-abb4-88f149e7712c
caps.latest.revision: "34"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 6bf5ac3acb0b0693c6c53de6705fee105f7f3404
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="using-the-sharepoint-project-service"></a>Usando o serviço de projeto do SharePoint
  O sistema de projeto do SharePoint inclui um serviço de projeto que você pode usar para executar tarefas relacionadas ao sistema de projeto. O serviço de projeto é um <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> objeto.  
  
 Você pode acessar o serviço de projeto do SharePoint em qualquer extensão de ferramentas do SharePoint. Você também pode acessá-lo em outros tipos de extensões do Visual Studio, como add-ins e VSPackages. Para obter mais informações, consulte [como: recuperar o serviço de projeto do SharePoint](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md).  
  
## <a name="project-service-features"></a>Recursos do serviço de projeto  
 A tabela a seguir lista as tarefas que você pode executar usando o serviço de projeto do SharePoint e o <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> método ou propriedade a ser usada para executar cada tarefa.  
  
|Tarefa|Membro a ser usado|  
|----------|-------------------|  
|Acesse qualquer projeto do SharePoint que está aberto no Visual Studio.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Projects%2A>propriedade.|  
|Acesse todos os tipos de item de projeto do SharePoint que estão disponíveis (incluindo os tipos de item de projeto internos e personalizados).|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.ProjectItemTypes%2A>propriedade.|  
|Acesse todas as etapas de implantação que estão disponíveis para projetos do SharePoint (incluindo as etapas de implantação internas e personalizadas).|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.DeploymentSteps%2A>propriedade.|  
|Eventos de acesso que são gerados quando um desenvolvedor refatora o código em um projeto do SharePoint.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.CodeRefactoringEvents%2A>propriedade.|  
|Executar um personalizado *comando SharePoint* que chama o modelo de objeto de servidor do SharePoint. Para obter mais informações sobre comandos do SharePoint, consulte [chamando os modelos de objeto do SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointConnection%2A>propriedade.|  
|Converter um tipo no sistema de projeto do SharePoint para um tipo no modelo de objeto de automação do Visual Studio ou modelo de objeto de integração e vice-versa. Para obter mais informações, consulte [converter entre SharePoint sistema de tipos de projeto e outros tipos de projeto Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).|Método <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A>.|  
|Gravar mensagens para o **saída** janela ou **lista de erros** janela no Visual Studio.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Logger%2A>propriedade.|  
|Acesse outros serviços que estão disponíveis no Visual Studio.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.ServiceProvider%2A>propriedade.|  
|Recupere o caminho para a pasta de instalação do site do SharePoint local que é usado para depurar a solução.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointInstallPath%2A>propriedade.|  
|Determinar se [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] ou [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] está instalado no computador.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.IsSharePointInstalled%2A>propriedade.|  
|Valide um pacote em uma solução do SharePoint ou um recurso.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.PackageValidationProvider%2A>propriedade.|  
  
## <a name="see-also"></a>Consulte também  
 [Converter entre tipos de sistema de projeto do SharePoint e outros tipos de projeto do Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)   
 [Como: recuperar o serviço de projeto do SharePoint](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md)   
 [Estendendo as ferramentas do SharePoint no Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)   
 [Extensões de ferramentas de visão geral do modelo de programação do SharePoint](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)   
 [Como obter um serviço do objeto DTE](http://msdn.microsoft.com/library/bb166401.aspx)  
  
  