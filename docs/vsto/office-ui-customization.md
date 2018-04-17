---
title: Personalização da interface do usuário do Office | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- menus [Office development in Visual Studio], customizing
- actions panes [Office development in Visual Studio], creating
- WPF [Office development in Visual Studio]
- toolbars [Office development in Visual Studio], customizing
- Office applications [Office development in Visual Studio], UI customization
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9a35ca6a868aa1fff2a4bd4bfbd3ec466d5a2107
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="office-ui-customization"></a>Personalização da interface do usuário do Office
  Você pode personalizar a interface do usuário (UI) de aplicativos do Microsoft Office usando as ferramentas de desenvolvedor do Office no Visual Studio. Este tópico descreve os recursos de interface do usuário que você pode personalizar as seções a seguir:  
  
-   [Comparação de recursos de interface do usuário](#Comparison)  
  
-   [Painéis de ações e painéis de tarefas personalizados](#Actions)  
  
-   [Interface do usuário personalizada](#Ribbon)  
  
-   [Modo de exibição Backstage](#Backstage)  
  
-   [Regiões de formulário do Outlook](#FormRegion)  
  
-   [Controles em documentos](#Controls)  
  
-   [Menus de atalho](#Shortcut)  
  
##  <a name="Comparison"></a> Comparação de recursos de interface do usuário  
 A tabela a seguir compara os principais recursos de interface do usuário que você pode personalizar em projetos do Microsoft Office.  
  
|Recurso|Tipos de projeto com suporte|Aplicativos do Microsoft Office com suporte|  
|-------------|-----------------------------|---------------------------------------------|  
|Painel Ações|Personalizações no nível de documento|Excel<br /><br /> Palavra|  
|Painéis de tarefas personalizados|Suplementos do VSTO|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)]<br /><br /> [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)]<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Palavra<br /><br /> Excel|  
|Interface do usuário personalizada|Personalizações no nível de documento<br /><br /> Suplementos do VSTO|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)]<br /><br /> [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)]<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Projeto<br /><br /> Palavra<br /><br /> Visio|  
|Modo de exibição Backstage|Personalizações no nível de documento<br /><br /> Suplementos do VSTO|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)].<br /><br /> [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)]<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Projeto<br /><br /> Palavra<br /><br /> Visio|  
|Regiões de formulário do Outlook|Suplementos do VSTO|Outlook|  
|Controles em documentos|Personalizações no nível de documento<br /><br /> Suplementos do VSTO|Excel<br /><br /> Palavra|  
|Menus de atalho|Personalizações no nível de documento<br /><br /> Suplementos do VSTO|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)]<br /><br /> [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)]<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Projeto<br /><br /> Palavra<br /><br /> Visio<br /><br /> Excel|  
  
##  <a name="Actions"></a> Painéis de ações e painéis de tarefas personalizados  
 Painéis de tarefas estão os painéis de interface do usuário que são normalmente encaixados em um dos lados de uma janela em um aplicativo do Microsoft Office. Quase todos os aplicativos do Microsoft Office incluem painéis de tarefas internas. Um exemplo de um painel de tarefas é o painel de tarefas Ajuda no Word.  
  
 As ferramentas de desenvolvimento do Office no Visual Studio fornecem duas maneiras diferentes de personalizar os painéis de tarefas:  
  
-   Você pode adicionar um painel de ações para uma personalização no nível do documento. Por padrão, o painel de ações é exibido no lado direito do aplicativo, à direita do documento. No entanto, o painel de ações, também pode ser exibido para a esquerda, superior ou inferior do documento.  
  
-   Você pode adicionar um painel tarefa personalizada para um suplemento do VSTO. Os usuários podem encaixar painéis de tarefas personalizados para diferentes lados da janela do aplicativo ou pode arrastar painéis de tarefas personalizados para qualquer local na janela.  
  
 Painéis de ações e painéis de tarefas personalizados fornecem funcionalidade hospedando uma variedade de controles para ajudar os usuários a executar tarefas como entrada de dados. Em comparação com um grupo de faixa de opções, painéis de ações e painéis de tarefas personalizados fornecem uma área maior para incluir o texto e controles.  
  
 Para obter mais informações sobre painéis de ações, consulte [visão geral do painel de ações](../vsto/actions-pane-overview.md). Para obter mais informações sobre painéis de tarefas personalizados, consulte [painéis de tarefas personalizados](../vsto/custom-task-panes.md).  
  
##  <a name="Ribbon"></a> Interface do usuário personalizada  
 Você pode personalizar a interface do usuário para expor a funcionalidade que você adicionar a aplicativos do Office. A faixa de opções é uma maneira de organizar os comandos relacionados (na forma de controles) para que eles são mais fáceis de localizar. Você pode criar seus próprios guias da faixa de opções e grupos para fornecer aos usuários acesso à funcionalidade que você fornece em sua solução. A maioria dos recursos que foram acessados usando os menus e barras de ferramentas em versões anteriores do Microsoft Office system agora pode ser acessada usando a faixa de opções.  
  
 Para obter mais informações, consulte [visão geral da faixa de opções](../vsto/ribbon-overview.md).  
  
##  <a name="Backstage"></a> Modo de exibição Backstage  
 Em aplicativos do Office, clique o **arquivo** guia abre o modo de exibição Backstage. O modo de exibição Backstage fornece uma interface do usuário que combina as ações e tarefas de nível de arquivo e substitui a funcionalidade semelhante disponível no botão Microsoft Office no sistema Microsoft Office 2007. O modo de exibição Backstage é totalmente extensível por meio de XML.  
  
 O Visual Studio não fornece um designer ou APIs para personalizar o modo de exibição Backstage. No entanto, se você adicionar um **da faixa de opções (XML)** item ao seu projeto do Office, você pode adicionar o XML para o arquivo XML da faixa de opções para personalizar o modo de exibição Backstage. Para obter mais informações sobre **da faixa de opções (XML)** itens, consulte [XML da faixa de opções](../vsto/ribbon-xml.md).  
  
 Para obter mais informações sobre como personalizar o modo de exibição Backstage, consulte [introdução para o modo de exibição do Office 2010 Backstage para desenvolvedores](http://go.microsoft.com/fwlink/?LinkId=182189) e [personalizar a exibição do Office 2010 Backstage para desenvolvedores](http://go.microsoft.com/fwlink/?LinkId=182188).  
  
##  <a name="FormRegion"></a> Regiões de formulário do Outlook  
 Use regiões de formulário para adicionar funcionalidade personalizada aos formulários padrão do Microsoft Office Outlook. Você pode criar regiões de formulário que estendem qualquer formulário existente com os campos adicionais ou controles. Se você criar uma nova região de formulário usando as ferramentas de desenvolvimento do Office no Visual Studio, você pode usar somente os controles de formulários do Windows na região de formulário. Se você importar uma região de formulário projetada no Outlook, você pode usar somente os controles do Outlook nativo.  
  
 Você pode criar regiões de formulário que ocupam diferentes áreas da interface do usuário do Outlook. Por exemplo, regiões de formulário adjacentes são exibidos na parte inferior da primeira página de um formulário, e cada região de formulário adjacente é recolhido. Você também pode adicionar uma região de formulário separado que é exibido como uma página de forma mais completa e que podem aparecer em qualquer formato padrão existente ou um formulário personalizado.  
  
 Para obter mais informações, consulte [criar regiões de formulário do Outlook](../vsto/creating-outlook-form-regions.md).  
  
##  <a name="Controls"></a> Controles em documentos  
 Você pode adicionar uma variedade de controles a documentos do Word e planilhas do Excel. Por exemplo, você talvez queira adicionar um controle de seletor de data para um documento para que o usuário possa inserir datas em um formato padrão ou colocar um botão em uma planilha para enviar dados para um banco de dados.  
  
 Ao desenvolver projetos no nível de documento para Excel ou Word, você pode usar o designer do Visual Studio para adicionar controles para o documento ou a pasta de trabalho em seu projeto em tempo de design, ou você pode adicionar programaticamente os controles em tempo de execução. Quando você desenvolver projetos de suplemento do VSTO para Excel ou Word, você pode adicionar programaticamente controles para qualquer documento aberto ou a pasta de trabalho em tempo de execução.  
  
 Para obter mais informações, consulte [itens de Host e visão geral dos controles de Host](../vsto/host-items-and-host-controls-overview.md) e [controles dos Windows Forms na visão geral de documentos do Office](../vsto/windows-forms-controls-on-office-documents-overview.md).  
  
##  <a name="Shortcut"></a> Menus de atalho  
 Um menu de atalho aparece quando você clica em um documento ou uma janela de aplicativo. Você pode definir um menu de atalho aparecem após um evento, como quando um usuário clica um documento, a pasta de trabalho ou o controle de host. Você pode adicionar um número de comandos de menu diferente ou controles para um menu de atalho. Crie menus de atalho por meio de XML. Se você adicionar um **da faixa de opções (XML)** item ao seu projeto do Office, você pode adicionar o XML para o arquivo XML da faixa de opções para criar menus de atalho. Para obter mais informações sobre como usar XML para criar menus de atalho, consulte [como: adicionar comandos a Menus de atalho](../vsto/how-to-add-commands-to-shortcut-menus.md).  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral da faixa de opções](../vsto/ribbon-overview.md)   
 [Controles em Visão geral de documentos do Office do Windows Forms](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Visão geral do painel de ações](../vsto/actions-pane-overview.md)   
 [Criando regiões de formulário do Outlook](../vsto/creating-outlook-form-regions.md)   
 [Painéis de tarefas personalizados](../vsto/custom-task-panes.md)   
 [Usando controles WPF em soluções do Office](../vsto/using-wpf-controls-in-office-solutions.md)   
 [Como: exibir a guia Desenvolvedor na faixa de opções](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)   
 [Como: Mostrar erros de Interface do usuário do suplemento](../vsto/how-to-show-add-in-user-interface-errors.md)   
 [Instruções passo a passo: coletando dados usando um Formulário do Windows](../vsto/walkthrough-collecting-data-using-a-windows-form.md)  
  
  