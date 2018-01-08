---
title: Integrando dados corporativos ao SharePoint | Microsoft Docs
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
- Business Data Connectivity service [SharePoint development in Visual Studio], business data
- BDC [SharePoint development in Visual Studio], aggregating data
- BDC [SharePoint development in Visual Studio], business data
- Business Data Connectivity service [SharePoint development in Visual Studio], aggregating data
- BDC [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], data
- BDC [SharePoint development in Visual Studio], data
ms.assetid: e092e3d6-2c5f-4060-ae86-d37db8967559
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 4cacdbb314130fa45b5aa3820abbbffbcbc6c0bf
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="integrating-business-data-into-sharepoint"></a>Integrando dados corporativos ao SharePoint
  Você pode integrar dados corporativos do SharePoint. Dados de negócios podem vir de aplicativos de servidor de back-end, como [!INCLUDE[TLA#tla_sqlsvr](../sharepoint/includes/tlasharptla-sqlsvr-md.md)], Siebel e SAP, ou um serviço Web. Os usuários podem exibir, adicionar, atualizar ou excluir dados de negócios usando listas externas ou Web Parts de dados de negócios no SharePoint.  Usuários também podem acessar esses dados offline em um aplicativo do Microsoft Office, como o Microsoft Outlook. Para obter mais informações, consulte [onde pode você mostrar dados externos](http://go.microsoft.com/fwlink/?LinkId=169295).  
  
 Para integrar dados do SharePoint, crie um modelo para o serviço de conectividade de dados de negócios (BDC). O serviço BDC é um aplicativo no SharePoint que armazena informações sobre dados em aplicativos de negócios. Para obter mais informações, consulte [serviço conectividade de dados de negócios (BDC)](http://go.microsoft.com/fwlink/?LinkID=169276).  
  
## <a name="models-in-visual-studio"></a>Modelos do Visual Studio  
 Modelos do Visual Studio permitem que você escrever código personalizado para recuperar e atualizar dados de fontes de dados de back-end. Você também pode agregar dados de várias fontes de dados. Por exemplo, você pode exibir uma lista de clientes que contém dados de um [!INCLUDE[ssNoVersion](../sharepoint/includes/ssnoversion-md.md)] banco de dados e um serviço Web.  
  
 Você também pode importar modelos que já foram implantados no SharePoint. Depois de importar um modelo, você pode adicionar código personalizado ou usar apenas o Visual Studio para empacotar e implantar o modelo em vários farms de servidores do SharePoint. Para obter mais informações, consulte [criando um modelo de conectividade de dados corporativos](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
## <a name="designing-a-model-in-visual-studio"></a>Criar um modelo no Visual Studio  
 Você pode criar um modelo usando um designer e várias janelas de ferramenta. Ao projetar o modelo, o Visual Studio gera o modelo XML. Para obter mais informações, consulte [visão geral de ferramentas de Design de modelo BDC](../sharepoint/bdc-model-design-tools-overview.md).  
  
 Um modelo contém entidades e métodos.  
  
### <a name="entities"></a>Entidades  
 Uma entidade descreve uma coleção de campos. Por exemplo, uma entidade pode representar uma tabela em um banco de dados. Uma entidade é exibido como um tipo de conteúdo externo no SharePoint. Para obter mais informações sobre tipos de conteúdo externos, consulte [quais são os tipos de conteúdo externos?](http://go.microsoft.com/fwlink/?LinkId=169293)  
  
### <a name="methods"></a>Métodos  
 Um método permite que os consumidores de um tipo de conteúdo externo para executar uma ação nos campos de uma entidade. Por exemplo, um método Updater pode permitem aos usuários alterar o endereço e a data de um cliente de origem onde `Address` e `BirthDate` são campos do `Customer` entidade.  
  
 O Visual Studio gera um arquivo de código de serviço para cada entidade em seu modelo. Quando você adiciona um método para seu modelo, o Visual Studio gera um método correspondente no arquivo de código de serviço. Adicione código para cada método para executar a tarefa apropriada. Por exemplo, se você adicionar um método Creator para o modelo, o Visual Studio gera um método Creator em seu arquivo de código de serviço. Esse método é chamado pelo serviço BDC quando um usuário clica o **Novo Item** botão em uma lista com base no modelo. Portanto, adicione código ao método criador que adiciona novos dados a uma fonte de dados. Para obter mais informações, consulte [criando um modelo de conectividade de dados corporativos](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
## <a name="related-topics"></a>Tópicos relacionados  
  
|Título|Descrição|  
|-----------|-----------------|  
|[Criando um modelo de Conectividade de Dados Corporativos](../sharepoint/creating-a-business-data-connectivity-model.md)|Mostra como criar um novo modelo ou importar um modelo que você exportar do SharePoint.|  
|[Designando um modelo de Conectividade de Dados Corporativos](../sharepoint/designing-a-business-data-connectivity-model.md)|Explica como criar os elementos de um modelo usando ferramentas de design do Visual Studio.|  
|[Quando usar o SharePoint Designer vs. Soluções do Visual Studio ao construir usando BCS](http://go.microsoft.com/fwlink/?LinkID=183448)|Ajuda a decidir se deseja usar o Visual Studio ou usar o SharePoint Designer para criar um modelo para o catálogo de dados corporativos.|  
  
  