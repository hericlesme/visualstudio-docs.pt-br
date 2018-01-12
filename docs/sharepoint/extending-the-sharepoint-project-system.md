---
title: Estendendo o sistema de projeto do SharePoint | Microsoft Docs
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
- SharePoint development in Visual Studio, extending projects
- SharePoint development in Visual Studio, extending project items
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: e79808ef9d5d4712d67426b202046615c8ab14b2
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="extending-the-sharepoint-project-system"></a>Estendendo o sistema de projeto do SharePoint
  Você pode criar soluções do SharePoint usando um conjunto de modelos de projeto e modelos de item no Visual Studio. Esses modelos atendem aos requisitos de vários cenários de desenvolvimento, mas você pode descobrir alguns casos em que eles não fornecem funcionalidade necessária. Nesses casos, você pode estender o sistema de projeto do SharePoint.  
  
## <a name="overview-of-the-sharepoint-project-system"></a>Visão geral do sistema de projeto do SharePoint  
 O sistema de projeto do SharePoint baseia-se o componente fundamental de *itens de projeto do SharePoint*. Um item de projeto do SharePoint representa uma única personalização do SharePoint, como uma definição de lista, uma Web Part ou um tipo de conteúdo.  
  
 Um projeto do SharePoint é um projeto do Visual Studio que inclui um ou mais itens de projeto do SharePoint. Projetos SharePoint também contêm componentes adicionais que definem como os itens de projeto são agrupados em recursos e pacotes de implantação.  
  
 Para obter mais informações sobre o conteúdo de itens de projeto do SharePoint e projetos do SharePoint, consulte [criando modelos de Item e modelos de projeto do SharePoint para itens de projeto](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
## <a name="how-to-extend-the-sharepoint-project-system"></a>Como estender o sistema de projeto do SharePoint  
 Você pode estender o sistema de projeto do SharePoint das seguintes maneiras:  
  
-   Definir seus próprios tipos de item de projeto do SharePoint e associá-los a novos modelos de item ou modelos de projeto no Visual Studio. Por exemplo, você pode definir um tipo de item de projeto do SharePoint para criar uma ação personalizada ou um campo. Para obter mais informações, consulte [definindo tipos de Item de projeto do SharePoint de personalizado](../sharepoint/defining-custom-sharepoint-project-item-types.md).  
  
-   Estenda os tipos de item de projeto do SharePoint que já estão instalados no Visual Studio. Por exemplo, você pode adicionar um item de menu de atalho a um item de projeto no **Solution Explorer** e personalizar o item de projeto quando um desenvolvedor escolhe o item de menu. Para obter mais informações, consulte [estendendo itens de projeto do SharePoint](../sharepoint/extending-sharepoint-project-items.md).  
  
-   Estenda a projetos do SharePoint. Por exemplo, você pode adicionar manipuladores de eventos para executar tarefas específicas quando itens são adicionados ou removidos de projetos do SharePoint. Para obter mais informações, consulte [estendendo projetos do SharePoint](../sharepoint/extending-sharepoint-projects.md).  
  
-   Estenda o comportamento de empacotamento e implantação de itens de projeto do SharePoint e projetos do SharePoint. Por exemplo, você pode criar suas próprias etapas de implantação a ser executada quando você implanta ou cancelar um projeto, ou você pode executar tarefas personalizadas adicionais ao Visual Studio executa determinadas etapas de implantação. Para obter mais informações, consulte [estendendo SharePoint empacotamento e implantação](../sharepoint/extending-sharepoint-packaging-and-deployment.md).  
  
## <a name="common-development-tasks"></a>Tarefas comuns de desenvolvimento  
 Você pode executar as seguintes tarefas comuns nas extensões do sistema de projeto do SharePoint:  
  
-   Salve dados de cadeia de caracteres personalizada com itens de projeto e em vários tipos diferentes de arquivos de projeto. Para obter mais informações, consulte [salvando dados em extensões do sistema de projeto do SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
-   Converter um objeto no sistema de projeto do SharePoint para um objeto correspondente no modelo de objeto de automação do Visual Studio ou modelo de objeto de integração, ou vice-versa. Para obter mais informações, consulte [converter entre SharePoint sistema de tipos de projeto e outros tipos de projeto Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).  
  
## <a name="see-also"></a>Consulte também  
 [Definindo tipos de Item de projeto do SharePoint personalizado](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Estendendo itens de projeto do SharePoint](../sharepoint/extending-sharepoint-project-items.md)   
 [Estendendo projetos SharePoint](../sharepoint/extending-sharepoint-projects.md)   
 [Estendendo empacotamento do SharePoint e implantação](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [Salvando dados em extensões do sistema de projeto do SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)   
 [Converter entre tipos de sistema de projeto do SharePoint e outros tipos de projeto do Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)   
 [Estendendo as ferramentas do SharePoint no Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)   
 [Conceitos e funcionalidades de programação para extensões de Ferramentas do SharePoint](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)  
  
  