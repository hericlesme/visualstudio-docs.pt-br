---
title: "Usando controles WPF em soluções do Office | Microsoft Docs"
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
helpviewer_keywords: WPF [Office development in Visual Studio]
ms.assetid: 305a212b-0a95-40ad-87aa-22896fe80a04
caps.latest.revision: "25"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 9cbb87017b910accae5ebc63b648691c50f88476
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="using-wpf-controls-in-office-solutions"></a>Usando controles WPF em soluções do Office
  Embora soluções criadas usando as ferramentas de desenvolvimento do Office no Visual Studio são projetadas para trabalhar com diretamente com controles de formulários do Windows, você também pode usar controles WPF em suas soluções. Windows Presentation Foundation (WPF) é uma alternativa para formulários do Windows para a criação de interfaces do usuário. WPF usa uma linguagem de marcação chamada Extensible Application marcação idioma (XAML) para fornecer novas técnicas para a incorporação de documentos, mídia e interface do usuário. Para obter mais informações, consulte [Introdução ao WPF no Visual Studio 2015](/dotnet/framework/wpf/getting-started/introduction-to-wpf-in-vs).  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Qualquer elemento de interface do usuário que pode hospedar controles de formulários do Windows em uma solução do Office também pode hospedar controles do WPF. Isso inclui os seguintes elementos:  
  
-   Documentos e planilhas em personalizações no nível do documento.  
  
-   Painéis de ações em personalizações no nível do documento.  
  
-   Painéis de tarefas personalizados nos suplementos do VSTO.  
  
-   Regiões de formulário no suplemento do VSTO para Outlook.  
  
## <a name="adding-wpf-controls-to-office-projects-at-design-time"></a>Adicionando controles WPF a projetos do Office em tempo de Design  
 É possível adicionar controles WPF diretamente a elementos de interface do usuário em soluções do Office. Em vez disso, adicione um **controle de usuário (WPF)** item ao seu projeto e usá-la como superfície de design para controles do WPF. Em seguida, adicione o controle de usuário do WPF a um elemento de interface do usuário em seu projeto.  
  
#### <a name="to-add-wpf-controls-to-an-actions-pane-custom-task-pane-or-form-region"></a>Para adicionar controles WPF a um painel de ações, painel de tarefas personalizado ou região de formulário  
  
1.  Abra um projeto para o qual você deseja adicionar um painel tarefa personalizada, um painel de ações ou uma região de formulário.  
  
2.  Adicionar um **controle de usuário (WPF)** item ao seu projeto.  
  
3.  Do **caixa de ferramentas**, adicionar controles WPF para a superfície de design de controle de usuário do WPF.  
  
     Por padrão, quando o designer de controle de usuário WPF é aberto, o **caixa de ferramentas** contém controles do WPF.  
  
4.  Compile o projeto.  
  
5.  Adicione um painel Ações, a região de formulário ou o painel de tarefas personalizado ao seu projeto:  
  
    -   Para regiões de formulário, adicione um **região de formulário do Outlook** item ao projeto. Para obter mais informações, consulte [como: adicionar uma região de formulário a um projeto de suplemento do Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).  
  
    -   Painéis de ações, adicione um **controle do painel Ações** ou **controle de usuário** item ao projeto. Para obter mais informações, consulte [como: adicionar um painel de ações a documentos do Word ou pastas de trabalho do Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md) e [como: adicionar um painel de ações a documentos do Word ou pastas de trabalho do Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md).  
  
    -   Painéis de tarefas personalizados, adicione um **controle de usuário** item ao projeto. Para obter mais informações, consulte [como: adicionar um painel de tarefas personalizado a um aplicativo](../vsto/how-to-add-a-custom-task-pane-to-an-application.md).  
  
6.  Do *ProjectName* **controles de usuário do WPF** guia do **caixa de ferramentas**, arraste o controle de usuário do WPF do Designer para o painel Ações, região de formulário ou painel de tarefas personalizado.  
  
     Visual Studio cria automaticamente um <xref:System.Windows.Forms.Integration.ElementHost> objeto que hospeda o controle de usuário do WPF no elemento de interface do usuário.  
  
7.  Recompile o projeto.  
  
#### <a name="to-add-wpf-controls-to-a-document-or-worksheet-in-a-document-level-project"></a>Para adicionar controles WPF a um documento ou a planilha em um projeto no nível de documento  
  
1.  Abra um projeto de nível de documento do Word ou Excel.  
  
2.  Adicionar um **controle de usuário (WPF)** item ao seu projeto.  
  
3.  Do **caixa de ferramentas**, adicionar controles WPF para a superfície de design de controle de usuário do WPF.  
  
4.  Compile o projeto.  
  
5.  Adicionar um **controle de usuário** item (ou seja, um controle de usuário de formulários do Windows) para o projeto.  
  
6.  Abra o designer para o controle de usuário do Windows Forms.  
  
7.  Do *ProjectName* **controles de usuário do WPF** guia do **caixa de ferramentas**, arraste o controle de usuário do WPF para o designer.  
  
     Visual Studio cria automaticamente um <xref:System.Windows.Forms.Integration.ElementHost> objeto que hospeda o controle de usuário do WPF no controle de usuário de formulários do Windows.  
  
8.  Escreva código que adiciona programaticamente o controle de usuário do Windows Forms para o documento ou a pasta de trabalho. Para obter mais informações, consulte [adicionando controles a documentos do Office em tempo de execução](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
    > [!NOTE]  
    >  Você não pode arrastar o controle de usuário do Windows Forms para o documento ou a planilha no designer.  
  
9. Recompile o projeto.  
  
## <a name="hosting-wpf-controls-by-using-the-elementhost-class"></a>Hospedando controles WPF usando a classe ElementHost  
 Visual Studio fornece recursos que ajudam você a usar controles de formulários do Windows em suas soluções do Office, mas ele não fornece recursos semelhantes para controles do WPF. Por exemplo, você pode adicionar controles de Windows Forms a documentos e planilhas em tempo de design arrastando controles do **caixa de ferramentas**, ou em tempo de execução usando métodos auxiliares. No entanto, essas ferramentas não estão disponíveis para controles do WPF.  
  
 Uso de controles WPF a <xref:System.Windows.Forms.Integration.ElementHost> classe como uma camada de integração entre um controle de formulários do Windows ou o formulário e os controles do WPF. Quando você adicionar controles WPF à sua solução em tempo de design, o Visual Studio gera automaticamente um <xref:System.Windows.Forms.Integration.ElementHost> objeto para você.  
  
## <a name="wpf-resources"></a>Recursos do WPF  
 Para obter mais informações sobre a arquitetura e os problemas de design para hospedar controles WPF em formulários e controles de formulários do Windows, consulte os tópicos a seguir:  
  
-   [Windows Forms e arquitetura de entrada da interoperabilidade do WPF](/dotnet/framework/wpf/advanced/windows-forms-and-wpf-interoperability-input-architecture)  
  
-   [Windows Forms e mapeamento de propriedade do WPF](/dotnet/framework/wpf/advanced/windows-forms-and-wpf-property-mapping)  
  
-   [Interoperação do WPF e do Windows Forms](/dotnet/framework/wpf/advanced/wpf-and-windows-forms-interoperation)  
  
-   [Controles dos Windows Forms e controles WPF equivalentes](/dotnet/framework/wpf/advanced/windows-forms-controls-and-equivalent-wpf-controls)  
  
 Para obter mais informações sobre como adicionar controles WPF a formulários no Visual Studio e controles de formulários do Windows em tempo de design, consulte os tópicos a seguir:  
  
-   [Instruções passo a passo: criando novo conteúdo WPF no Windows Forms no tempo de design](/dotnet/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time)  
  
-   [Instruções passo a passo: organizando conteúdo WPF no Windows Forms no tempo de design](/dotnet/framework/winforms/advanced/walkthrough-arranging-wpf-content-on-windows-forms-at-design-time)  
  
-   [Instruções passo a passo: estilos de conteúdo WPF](/dotnet/framework/winforms/advanced/walkthrough-styling-wpf-content)  
  
## <a name="see-also"></a>Consulte também  
 [Personalização da interface do usuário do Office](../vsto/office-ui-customization.md)   
 [Controles em Visão geral de documentos do Office do Windows Forms](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Visão geral do painel de ações](../vsto/actions-pane-overview.md)   
 [Painéis de tarefas personalizados](../vsto/custom-task-panes.md)   
 [Criando regiões de formulário do Outlook](../vsto/creating-outlook-form-regions.md)   
 [Como: adicionar um painel de ações a documentos do Word ou pastas de trabalho do Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [Como: adicionar um painel de ações a documentos do Word ou pastas de trabalho do Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [Como: adicionar um painel tarefa personalizada a um aplicativo](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)   
 [Como adicionar uma região do formulário a um projeto de suplemento do Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)  
  
  