---
title: "Criando definições de Site do SharePoint | Microsoft Docs"
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
- SharePoint development in Visual Studio, site definitions
- site definitions [SharePoint development in Visual Studio]
ms.assetid: 83db570d-6b9f-4dab-9e71-db41f17b987a
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a4a7c002bd17da5f693955a82ab2e74bf65dc0cd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="creating-site-definitions-for-sharepoint"></a>Criando definições de site do SharePoint
  O projeto de definição de Site do SharePoint no [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] permite que você crie um *definição de site*, que serve como base para um novo site do SharePoint. Essas definições não só determinam a aparência e comportamento de site do SharePoint, mas também seu conteúdo padrão e funcionalidade. Na definição, você pode colocar listas predefinidas, tipos de conteúdo, receptores de evento, imagens e outros itens. Por exemplo, o SharePoint inclui algumas definições de site, como BLOG. Quando você cria um site com base na definição de site de BLOG, o site contém as listas, Web parts e outros itens que requer um site de blog.  
  
 Para obter mais informações sobre definições de site, consulte [definições e modelos de Site](http://go.microsoft.com/fwlink/?LinkId=179134).  
  
## <a name="site-definition-projects"></a>Projetos de Definição do Site  
 Projetos de definição de site [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] fornecer apenas os arquivos básico que precisa de um site do SharePoint, não fornecem nenhuma funcionalidade padrão. Você deve adicionar os arquivos e conteúdo para fornecer a funcionalidade que você deseja. Você pode criar o site manualmente, criando e adicionando os arquivos que você precisa.  
  
## <a name="feature-stapling"></a>Grampeamento do Recurso  
 Uma vantagem de criar definições de site em [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] é que eles usam automaticamente *grampeamento de recurso*. Grampeamento de recurso anexa um recurso a uma definição de site em vez de inserir sua funcionalidade na definição de site em si. Isso permite adicionar o recurso para qualquer site criado usando a definição de site sem modificar a definição do site original. Para obter mais informações, consulte [grampeamento de recurso](http://go.microsoft.com/fwlink/?LinkID=119283).  
  
## <a name="site-definition-project-components"></a>Componentes de Projeto da Definição do Site  
 Quando você cria uma solução de definição de site, os seguintes arquivos padrão são adicionados ao seu **SiteDefinition** nó.  
  
|Nome do Arquivo|Descrição|  
|---------------|-----------------|  
|default. aspx|A página ASPX inicial de padrão para o novo site do SharePoint.|  
|onet.XML|Especifica a configuração do novo site, os componentes do modelo de definição de site e o comportamento padrão. Essas configurações podem incluir atributos como os tipos de conteúdo que são habilitados, os modos de exibição de lista padrão, arquivos de modelo de documento e Web parts incluídas com o site. Por padrão, o `Modules` seção lista os arquivos a serem adicionadas ao site do SharePoint e como eles são configurados.|  
|webtemp_*SiteDefinitionName*. XML|Especifica as configurações de definição de site que aparece no **seleção de modelo** seção o **novo Site do SharePoint** página.|  
  
 Por padrão, todas as definições de site são armazenadas no *unidade:*pasta \Program Files\Microsoft Shared\Web Server Extensions\14\TEMPLATE\SiteTemplates. Cada definição de site tem sua própria subpasta.  
  
## <a name="related-topics"></a>Tópicos relacionados  
  
|Título|Descrição|  
|-----------|-----------------|  
|[Passo a passo: criar um projeto de definição de site básico](../sharepoint/walkthrough-create-a-basic-site-definition-project.md)|Leva você passo a passo durante a criação de um projeto de definição de site básico em [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].|  
|[Como: criar uma definição de Site personalizado e configuração](http://go.microsoft.com/fwlink/?LinkId=183309)|Descreve como criar uma definição de site personalizada no SharePoint copiando uma definição de site existente e modificando essa cópia.|  
|[Webtemp](http://go.microsoft.com/fwlink/?LinkId=183310)|Descreve o arquivo original que especifica as definições de site disponíveis no **seleção de modelo** seção o **novo Site do SharePoint** página.|  
|[Localizando soluções do SharePoint](../sharepoint/localizing-sharepoint-solutions.md)|Descreve como preparar suas soluções do SharePoint para uso global.|  
|[Criando Web Parts para o SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)|Descreve como criar partes de uma página do SharePoint que os usuários podem modificar.|  
|[Criando controles reutilizáveis para Web Parts ou páginas de aplicativo](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)|Descreve como você pode criar controles reutilizáveis que são executados em páginas de aplicativos e Web Parts.|  
|[Visual Web Developer](http://go.microsoft.com/fwlink/?LinkId=178725)|Descreve como usar o designer que aparece quando você abre uma página da Web em seu projeto.|  
|[Visão geral de páginas da Web do ASP.NET](http://go.microsoft.com/fwlink/?LinkId=178726)|Fornece informações gerais sobre a estrutura de [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] páginas da Web, como páginas são processadas pelo [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]e como [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] que está de acordo com os padrões XHTML as páginas são exibidas.|  
|[Sintaxe de página da Web ASP.NET](http://go.microsoft.com/fwlink/?LinkId=178727)|Descreve os elementos de marcação que compõem uma página ASP.NET.|  
|[Páginas da Web ASP.NET de programação](http://go.microsoft.com/fwlink/?LinkId=178728)|Fornece informações sobre como criar manipuladores de eventos [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] páginas e como trabalhar com script de cliente.|  
|[Programação no Windows SharePoint Services](http://go.microsoft.com/fwlink/?LinkId=178729)|Descreve como usar o modelo de objeto gerenciado que é fornecido em [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)].|  
  
## <a name="see-also"></a>Consulte também  
 [Desenvolvendo soluções do SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
  