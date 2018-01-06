---
title: Modelos de Item de projeto do SharePoint e do projeto | Microsoft Docs
ms.custom: 
ms.date: 02/22/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.SharePointTools.SPE.FirstWizardPage
- VS.SharePointTools.SPE.ListInstance
- VS.SharePointTools.SPE.ListDefinition
- VS.SharePointTools.SPE.ListDefFromContentType
- VS.SharePointTools.SPE.ContentType
- SPE.Wizard
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, project and project item templates
- SharePoint development in Visual Studio, templates
ms.assetid: 54a7576f-d3f9-475d-8ed7-b675ad21cb53
caps.latest.revision: "41"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: dc29b307f6459e3a5841ae1dd1c60ae9ab9ed152
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="sharepoint-project-and-project-item-templates"></a>SharePoint Modelos de projeto e de item de projeto
  As seções a seguir descrevem o projeto do SharePoint disponível e modelos de projeto item e como eles são usados. 
  
##  <a name="project-and-project-item-templates-overview"></a>Projeto e visão geral de modelos de Item de projeto  
 Quando você cria um novo projeto do SharePoint no Visual Studio, um projeto do SharePoint é adicionado à solução junto com todos os itens de projeto necessários para esse tipo de projeto. Por exemplo, se você criar um projeto de Web Part do Silverlight, Visual Studio cria uma solução que contém um item de projeto do Visual Web Part e um item de projeto de aplicativo do Silverlight juntamente com todos os arquivos necessários para os itens de projeto. Modelos de item de projeto são usados para adicionar itens de projeto a um projeto existente do SharePoint, como a adição de um receptor de eventos, a coluna de site ou a lista.  
  
 Para obter informações sobre conceitos básicos do SharePoint, consulte [blocos de construção do SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=179404). Usuários avançados podem criar modelos de item de projeto e projeto personalizados. Para obter mais informações, consulte [estendendo o sistema de projeto do SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).  
  
##  <a name="project-templates"></a>Modelos de projeto  
 A seguir está uma lista de modelos de projeto do SharePoint. Para exibir os modelos de projeto do SharePoint no Visual Studio, no **novo projeto** caixa de diálogo caixa, expanda o **SharePoint** nó sob o **Visual C#** ou  **Visual Basic**e, em seguida, escolha **2010**.  
  
### <a name="sharepoint-2010-project"></a>Projeto do SharePoint 2010  
 O conteúdo de um *projeto do SharePoint 2010* são incluídos em cada modelo de projeto do SharePoint. Contém um projeto do SharePoint 2010:  
  
-   Um arquivo de projeto.  
  
-   Uma página de propriedades do projeto.  
  
-   Um **referências** pasta listando todas as referências de assembly no projeto.  
  
-   Um **recursos** pasta que contém um arquivo de configuração .feature, usado para implantar os recursos do servidor do SharePoint.  
  
-   Um **pacote** pasta que contém um arquivo de pacote, usado para implantar a solução do SharePoint.  
  
-   Um arquivo de key.snk (chave de nome forte) que é usado para assinar o assembly com um nome forte, para segurança aprimorada.  
  
### <a name="sharepoint-2010-silverlight-web-part"></a>Web Part do Silverlight do SharePoint 2010  
 *Web Part do SharePoint 2010 do Silverlight* projetos permitem que você criar web parts do SharePoint que exibem os aplicativos Silverlight. Quando você cria este projeto, você pode especificar se deseja adicionar um novo aplicativo Silverlight para ele ou fazer referência a um existente. Para obter mais informações, consulte [criando Web Parts para SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md) e [passo a passo: Criando um Web Part do Silverlight que exibe OData para SharePoint](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md).  
  
### <a name="sharepoint-2010-visual-web-part"></a>Web Part Visual do SharePoint 2010  
 Um *Visual Web Part do SharePoint 2010* projeto inclui um arquivo de definição de Elements, um **Web Part** item e um **controle de usuário** item. Você pode criar a aparência do visual web part arrastando ou copiando os controles de ferramentas do Visual Studio para a superfície do controle de usuário. Para obter mais informações, consulte [como: criar uma Web Part do SharePoint usando um Designer](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md) e [blocos de construção: Web Parts](http://go.microsoft.com/fwlink/?LinkId=179438).  
  
### <a name="import-sharepoint-2010-solution-package"></a>Importar Pacote de Soluções do SharePoint 2010  
 *Importar o pacote de solução do SharePoint 2010* projetos permitem que você importe todo ou parte de um site existente do SharePoint 2010, exportado para um arquivo de solução (. wsp) do SharePoint, no Visual Studio. Uma vez importado para o Visual Studio, você pode personalizar seus itens e reimplantá-los. Para obter mais informações, consulte [importar itens de um Site do SharePoint existente](../sharepoint/importing-items-from-an-existing-sharepoint-site.md).  
  
### <a name="import-reusable-sharepoint-2010-workflow"></a>Importar Fluxo de Trabalho Reutilizável do SharePoint 2010  
 *Importar fluxo de trabalho reutilizável do SharePoint 2010* projetos permitem que você importe um fluxo de trabalho reutilizável, declarativo criado no SharePoint Designer 2010 para o Visual Studio. O fluxo de trabalho é exportado do site do SharePoint como um arquivo. wsp. Uma vez importado para o Visual Studio, pode personalizá-lo, adicione código para ele e, em seguida, implantá-lo em um site do SharePoint. Para obter mais informações, consulte [passo a passo: importar um fluxo de trabalho do SharePoint Designer reutilizável no Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md).  
  
##  <a name="project-item-templates"></a>Modelos de Item de projeto  
 A seguir está uma lista de modelos de item de projeto do SharePoint. Modelos de item de projeto Adicionar arquivos à solução do SharePoint para dar suporte à funcionalidade do SharePoint como colunas de sites, listas e tipos de conteúdo. Por exemplo, a adição de uma coluna de site para sua solução adiciona um projeto de coluna de site que contém um arquivo de definição de Elements. Adicionar uma web part visual adiciona um projeto do visual web part à sua solução que contém um arquivo Elements, um item de controle de usuário e um item do visual web part.  
  
 Para exibir os modelos de item de projeto do SharePoint, em **Solution Explorer**, abra o menu de atalho para um projeto do SharePoint e, em seguida, escolha **adicionar**, **Novo Item**. Expanda o **SharePoint** nó sob o **Visual C#** ou **Visual Basic**e, em seguida, escolha **2010**.  
  
### <a name="application-page-farm-solution-only"></a>Página de aplicativo (somente solução de Farm)  
 Um **página de aplicativo (solução de Farm somente)** item permite que você crie um [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] página da web para um site do SharePoint. Páginas de aplicativos podem ser usadas apenas em soluções de farm. Você pode adicionar esse item de projeto somente a soluções de farm. Para obter mais informações, consulte [como: criar uma página de aplicativo](../sharepoint/how-to-create-an-application-page.md) e [layouts de aplicativo tipo de página](http://go.microsoft.com/fwlink/?LinkId=179434).  
  
### <a name="business-data-connectivity-model-farm-solution-only"></a>Modelo de conectividade de dados corporativos (somente solução de Farm)  
 Um **modelo de conectividade de dados corporativos (solução de Farm somente)** item permite integrar dados corporativos do SharePoint. Dados de negócios podem vir de aplicativos de servidor de back-end, como [!INCLUDE[ssNoVersion](../sharepoint/includes/ssnoversion-md.md)], Siebel e Service Advertising Protocol (SAP). Modelos de conectividade de dados de negócios podem ser usados apenas em soluções de farm. Você pode adicionar esse item de projeto somente a soluções de farm. Para obter mais informações, consulte [como: criar um modelo BDC](../sharepoint/how-to-create-a-bdc-model.md), [como: usar um arquivo de recurso para especificar nomes localizados, propriedades e permissões](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md), e [Novidades: conectividade de negócios Serviços](http://go.microsoft.com/fwlink/?LinkId=179411).  
  
### <a name="content-type"></a>Tipo de Conteúdo  
 *Tipo de conteúdo* itens permitem criar tipos de conteúdo personalizados com base em um tipo de conteúdo (base) existente como um documento, anúncio ou uma tarefa. Um tipo de conteúdo personalizado fornece os mesmos atributos e campos como o tipo de conteúdo base junto com qualquer coluna de site (campos) que você definir. Por exemplo, você pode criar um tipo de conteúdo de contato personalizado com base no tipo de base entre em contato com conteúdo que é fornecido no SharePoint. Você pode personalizar o tipo de conteúdo, alterar as colunas de site existente ou adicionar mais colunas de site para aqueles que já está incluídos no tipo de conteúdo base.  
  
> [!NOTE]  
>  Devido a uma limitação do SharePoint, você não pode criar um tipo de conteúdo de solução do farm com base em um tipo de conteúdo da solução em área restrita.  
  
 Para obter mais informações, consulte [passo a passo: criar uma coluna de Site, o tipo de conteúdo e a lista do SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) e [blocos de construção: tipo de conteúdo](http://go.microsoft.com/fwlink/?LinkId=179413).  
  
### <a name="empty-element"></a>Elemento vazio  
 *Elementos vazios* geralmente são usadas para definir itens de projeto do SharePoint que não têm um projeto ou o modelo de item de projeto no Visual Studio. Quando você adiciona um elemento vazio ao seu projeto, um nó denominado EmptyElement [x](where [x] is a unique number\) is created. EmptyElement [x] contém um único arquivo chamado elements. Use [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] instruções para definir os elementos desejados no Elements.  
  
### <a name="event-receiver"></a>Receptor de evento  
 *Receptores de evento* tratar eventos para itens no site do SharePoint, como quando um item é adicionado a uma lista, quando um item da web for excluído, ou quando um fluxo de trabalho foi iniciado. O modelo de item de projeto de receptor de evento permite que você manipule  
  
-   Lista de eventos  
  
-   Eventos de item de lista  
  
-   Eventos de email da lista  
  
-   Eventos da Web  
  
-   Eventos de fluxo de trabalho de lista  
  
 O item de projeto do receptor de eventos cria um **receptor de evento** pasta com um arquivo de classe única que contém manipuladores de eventos para todos os eventos de você especificou quando criou o projeto no **personalização do SharePoint Assistente de**. Classe receptora do evento pode tratar eventos que ocorrem no site do SharePoint quando itens como arquivos, campos, itens, listas, anexos, web parts e fluxos de trabalho são adicionados, atualizados, excluídos ou removidos. Para obter mais informações, consulte [como: criar um receptor de evento](../sharepoint/how-to-create-an-event-receiver.md) e [blocos de construção: manipulação de eventos](http://go.microsoft.com/fwlink/?LinkId=179416).  
  
### <a name="list"></a>Lista  
 Uma lista é uma instância de uma reutilizável SharePoint lista definição base, como um calendário ou uma lista de tarefas. Depois de adicionar uma lista para sua solução, o Designer de lista permite que você adicionar colunas de site na lista e criar colunas de lista personalizada. Isso inclui colunas de tipos de conteúdo do site. Você pode especificar o *exibição* para a lista, que determina as colunas que aparecerão na lista. Para obter mais informações, consulte [passo a passo: criar uma coluna de Site, o tipo de conteúdo e a lista do SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) e [blocos de construção: listas e bibliotecas de documentos](http://go.microsoft.com/fwlink/?LinkId=179421).  
  
### <a name="module"></a>Módulo  
 *Módulos* (não deve ser confundido com [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] módulos) contém arquivos que você deseja implantar no servidor do SharePoint, como imagens ou anotações. O item de projeto de módulo contém um **módulo** nó. O nó de módulo contém dois modelos de item de projeto: um arquivo de definição de XML, que atua como um manifesto do módulo, e um arquivo txt, um arquivo de espaço reservado. Para obter mais informações, consulte [usando módulos para incluir arquivos na solução](../sharepoint/using-modules-to-include-files-in-the-solution.md) e [módulos](http://go.microsoft.com/fwlink/?LinkId=179425).  
  
### <a name="sequential-workflow-farm-solution-only"></a>O fluxo de trabalho sequencial (somente solução de Farm)  
 Um *fluxo de trabalho sequencial* é uma série de etapas de lógica de negócios, executadas em sequência, até que a última etapa é concluída. Fluxos de trabalho sequenciais são usados para gerenciar processos que envolvem itens do SharePoint, como listas e documentos. Você pode criar fluxos de trabalho de nível de site (globais) ou (locais) no nível da lista de fluxos de trabalho, e você pode selecionar se um fluxo de trabalho é iniciado automaticamente ou manualmente. Este item de projeto pode ser usado apenas em soluções de farm. Você pode adicionar esse item de projeto somente a soluções de farm. Para obter mais informações, consulte [criar soluções de fluxo de trabalho do SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md), [fluxos de trabalho no SharePoint Server 2010](http://go.microsoft.com/fwlink/?LinkId=260555), e [Novidades: aprimoramentos de fluxo de trabalho](http://go.microsoft.com/fwlink/?LinkId=179418).  
  
### <a name="silverlight-web-part"></a>Web Part do Silverlight  
 *Web part do Silverlight* itens de projeto permitem que você criar web parts do SharePoint que exibem os aplicativos Silverlight. Quando você adiciona este item de projeto para sua solução, você pode escolher se deseja adicionar um novo aplicativo Silverlight ou fazer referência a um existente mais tarde. Para obter mais informações, consulte [criando Web Parts para SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md) e [passo a passo: Criando um Web Part do Silverlight que exibe OData para SharePoint](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md).  
  
### <a name="site-column"></a>Coluna de site  
 Um *coluna site*, também conhecido como um *campo*, é um dos elementos mais básicos, você pode adicionar a um projeto do SharePoint. Uma coluna de site representa um tipo de dados, como um número de telefone, um comentário de texto ou o nome da cidade de um contato em uma lista de contatos. Para obter mais informações, consulte [criar colunas de Site, tipos de conteúdo e listas do SharePoint](../sharepoint/creating-site-columns-content-types-and-lists-for-sharepoint.md) e [colunas](http://go.microsoft.com/fwlink/?LinkId=226840).  
  
### <a name="site-definition-farm-solution-only"></a>Definição de site (somente solução de Farm)  
 *Definição de site* itens de projeto contém uma pasta de definição de site que inclui os seguintes arquivos:  
  
-   Uma padrão página. aspx, usada como a página da web padrão para o site.  
  
-   Um arquivo de onet.xml que define os componentes do site.  
  
-   Um arquivo xml webtemp que especifica as configurações de definição de site que aparecem no **seleção de modelo** seção o **novo Site do SharePoint** página.  
  
 Depois de adicionar uma definição de site, você deve adicionar código e os arquivos para apresentar a funcionalidade. Este item de projeto pode ser usado apenas em soluções de farm. Você pode adicionar esse item de projeto somente a soluções de farm. Para obter mais informações, consulte [criar definições de Site do SharePoint](../sharepoint/creating-site-definitions-for-sharepoint.md) e [configurações e definições de Site](http://go.microsoft.com/fwlink/?LinkId=260554).  
  
### <a name="state-machine-workflow-farm-solution-only"></a>Fluxo de trabalho de máquina de estado (somente solução de Farm)  
 Um *fluxo de trabalho de máquina de estado* é um conjunto de estados de lógica de negócios, transições e ações. As etapas em um fluxo de trabalho de máquina de estado não são executadas em sequência; em vez disso, eles são acionados por estados e ações. Como um fluxo de trabalho sequencial, fluxos de trabalho de máquina de estado são associados a itens do SharePoint, como listas e documentos. Uma vez, você pode criar fluxos de trabalho de nível de site (globais) ou (locais) no nível da lista de fluxos de trabalho. Você também pode selecionar se um fluxo de trabalho é iniciado automaticamente ou manualmente. Este item de projeto pode ser usado apenas em soluções de farm. Você pode adicionar esse item de projeto somente a soluções de farm. Para obter mais informações, consulte [criar soluções de fluxo de trabalho do SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md), [fluxos de trabalho no SharePoint Server 2010](http://go.microsoft.com/fwlink/?LinkId=260555), e [Novidades: aprimoramentos de fluxo de trabalho](http://go.microsoft.com/fwlink/?LinkId=179418).  
  
### <a name="user-control-farm-solution-only"></a>Controle de usuário (somente solução de Farm)  
 Um *controle de usuário* é um controle personalizado, reutilizável para o qual você pode adicionar outros controles do ASP.NET e do SharePoint. O controle de usuário pode ser adicionado a páginas de aplicativos e web parts que são executados no SharePoint. Este item de projeto pode ser usado apenas em soluções de farm. Você pode adicionar esse item de projeto somente a soluções de farm. Para obter mais informações, consulte [criação de controles de reutilizáveis para Web Parts ou páginas de aplicativo](http://go.microsoft.com/fwlink/?LinkId=226841).  
  
### <a name="visual-web-part"></a>Web Part Visual  
 Um *web part visual* item de projeto inclui um arquivo de definição de Elements, um **Web Part** item e um **controle de usuário** item. Você pode criar a aparência do visual web part arrastando ou copiando os controles de ferramentas do Visual Studio para a superfície do controle de usuário. Para obter mais informações, consulte [como: criar uma Web Part do SharePoint usando um Designer](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md) e [blocos de construção: Web Parts](http://go.microsoft.com/fwlink/?LinkId=179438).  
  
### <a name="web-part"></a>Web Part  
 Um *da web part* é um controle de servidor que é executado dentro de um tipo especial de página chamada uma página de Web Part. Eles são os blocos de construção de páginas que aparecem em um site do SharePoint. O item de web part fornece os arquivos que permitem a criação de uma web part para um site do SharePoint. Para obter mais informações, consulte [como: criar uma Web Part do SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md) e [blocos de construção: Web Parts](http://go.microsoft.com/fwlink/?LinkId=179438).  
  
## <a name="see-also"></a>Consulte também  
 [Desenvolver soluções do SharePoint](../sharepoint/developing-sharepoint-solutions.md)   
 [Produtos e tecnologias SharePoint](http://go.microsoft.com/fwlink/?LinkId=178818)  
  
  
