---
title: Estendendo as ferramentas do SharePoint no Visual Studio | Microsoft Docs
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
- extensibility [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, extending tools
ms.assetid: 084cf4bf-aaba-4277-8032-448f2cb2a124
caps.latest.revision: "39"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 3c18f4097fb9f718f4ec2fc9c4683e599d38b74a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="extending-the-sharepoint-tools-in-visual-studio"></a>Estendendo as ferramentas do SharePoint no Visual Studio
  Ferramentas do SharePoint no Visual Studio atendem aos requisitos de muitos cenários de desenvolvimento de aplicativos. No entanto, talvez você descubra que os casos em que eles não fornecem a funcionalidade que você ou outros desenvolvedores exigem. Nesses casos, você pode estender as ferramentas do SharePoint para criar a funcionalidade que você precisa.  
  
## <a name="how-to-extend-the-sharepoint-tools"></a>Como estender as ferramentas do SharePoint  
 Você pode estender o sistema de projeto do SharePoint e o **conexões do SharePoint** nó o **Server Explorer** janela.  
  
### <a name="extending-the-sharepoint-project-system"></a>Estendendo o sistema de projeto do SharePoint  
 Visual Studio inclui um conjunto de modelos de projeto e modelos de item que você pode usar para criar soluções do SharePoint. Por exemplo, há modelos para receptores de evento, as definições de lista, fluxos de trabalho e Web Parts. No entanto, você também pode definir seus próprios tipos de itens de projeto do SharePoint para criar componentes do SharePoint, como campos ou ações personalizadas. Você também pode criar extensões para tipos de item de projeto do SharePoint que já estão instalados no Visual Studio, e você pode criar extensões para projetos do SharePoint.  
  
 Para obter mais informações, consulte [estendendo o sistema de projeto do SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).  
  
### <a name="extending-the-sharepoint-connections-node-in-server-explorer"></a>Estendendo o nó Conexões do SharePoint no Gerenciador de Servidores  
 No Visual Studio, você pode usar o **conexões do SharePoint** nó o**Server Explorer** janela para exibir muitos dos componentes de um ou mais sites locais do SharePoint em uma exibição de árvore hierárquica. Você também pode estender o **conexões do SharePoint** nó das seguintes maneiras:  
  
-   Adicionando seus próprios nós. Isso é útil se você deseja exibir os componentes de sites do SharePoint que não são exibidas por padrão.  
  
-   Estendendo nós existentes. Por exemplo, você pode adicionar um novo nó filho em um nó existente, ou você pode adicionar um item de menu de atalho a um nó e executar tarefas quando um desenvolvedor clica no item de menu.  
  
 Para obter mais informações, consulte [estendendo o nó de conexões do SharePoint no Gerenciador de servidores](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).  
  
## <a name="development-computer-requirements"></a>Requisitos do computador de desenvolvimento  
 Para criar extensões para ferramentas do SharePoint, seu computador de desenvolvimento deve atender os mesmos requisitos para a criação de soluções do SharePoint no Visual Studio. Para obter mais informações, consulte [requisitos para desenvolver soluções do SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
 Também é recomendável que você instale o [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]. O SDK inclui modelos de projeto e as ferramentas que você pode usar para estender o Visual Studio. Em particular, o SDK inclui um modelo de projeto, que você pode usar para criar facilmente um pacote de extensão de Visual Studio (VSIX). Pacotes VSIX são a melhor maneira de implantar as extensões do Visual Studio no Visual Studio. Todas as extensões de ferramentas do SharePoint devem ser implantadas por meio de pacotes VSIX. Todas as orientações nesta documentação pressupõem que você tenha o [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)] instalado.  
  
 Para instalar o SDK do Visual Studio, consulte [instalar o SDK do Visual Studio](../extensibility/installing-the-visual-studio-sdk.md). Para obter mais informações sobre as extensões do Visual Studio, consulte [começando a desenvolver extensões do Visual Studio](../extensibility/starting-to-develop-visual-studio-extensions.md).  
  
## <a name="see-also"></a>Consulte também  
 [Extensões de ferramentas de visão geral do modelo de programação do SharePoint](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)   
 [Estendendo o sistema de projeto do SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)   
 [Estendendo o nó de conexões do SharePoint no Gerenciador de servidores](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Conceitos de programação e recursos para extensões de ferramentas do SharePoint](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)   
 [Referência &#40; Extensibilidade de ferramentas do SharePoint &#41;](../sharepoint/reference-sharepoint-tools-extensibility.md)   
 [Depurando extensões para ferramentas do SharePoint no Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)   
 [Implantando extensões para as Ferramentas do SharePoint no Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)  
  
  