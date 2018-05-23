---
title: Introdução à programação de suplementos do VSTO
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VST.ProjectItem.Outlook
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], getting started
- add-ins [Office development in Visual Studio], getting started
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7249c3971c8008f70b9e5add79adddde17fe6a82
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/22/2018
---
# <a name="get-started-programming-vsto-add-ins"></a>Introdução à programação de suplementos do VSTO
  Você pode usar os suplementos do VSTO para automatizar os aplicativos do Microsoft Office, estender os recursos do aplicativo e personalizar a interface do usuário (IU) do aplicativo. Para obter informações sobre como suplementos do VSTO em comparação com outros tipos de soluções do Office que você pode criar usando o Visual Studio, consulte [visão geral de desenvolvimento de soluções do Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
## <a name="create-vsto-add-in-projects"></a>Criar projetos de suplemento do VSTO  
 Criar projetos de suplemento do VSTO usando um dos modelos de projeto do suplemento do VSTO no **novo projeto** caixa de diálogo. Esses modelos incluem referências de assembly necessárias e os arquivos de projeto. Visual Studio fornece modelos de projeto de suplemento do VSTO para a maioria dos aplicativos do Office.  
  
 Para obter mais informações sobre como criar um projeto de suplemento do VSTO, consulte [como: projetos do Office criar no Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md). Para obter mais informações sobre os modelos de projeto, consulte [visão geral de modelos de projeto do Office](../vsto/office-project-templates-overview.md).  
  
## <a name="develop-vsto-add-in-projects"></a>Desenvolver projetos de suplemento do VSTO  
 Quando você cria um projeto de suplemento do VSTO, Visual Studio cria automaticamente um *ThisAddIn* (em [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]) ou *ThisAddIn.cs* (em c#) o arquivo de código. Este arquivo contém o `ThisAddIn` classe, que fornece a base para o suplemento do VSTO. Você pode usar os membros dessa classe para executar código quando o suplemento do VSTO é carregado ou descarregado, para acessar o modelo de objeto do aplicativo host e para estender os recursos do aplicativo. Para obter mais informações, consulte [programa suplementos do VSTO](../vsto/programming-vsto-add-ins.md).  
  
## <a name="automate-applications-by-using-the-object-models"></a>Automatizar aplicativos usando os modelos de objeto  
 Os modelos de objeto dos aplicativos do Microsoft Office expõem vários tipos que você pode programar em um suplemento do VSTO. Você pode usar esses tipos para automatizar o aplicativo. Por exemplo, você pode criar e enviar uma mensagem de email no Outlook programaticamente, ou você pode abrir um documento e adicionar o conteúdo no Word. Para obter mais informações sobre como acessar o modelo de objeto do aplicativo de host no código, consulte [programa suplementos do VSTO](../vsto/programming-vsto-add-ins.md).  
  
 Para obter mais informações sobre os modelos de objeto de aplicativos específicos do Microsoft Office, consulte os tópicos a seguir:  
  
-   [Visão geral do modelo de objeto do Excel](../vsto/excel-object-model-overview.md)  
  
-   [Visão geral do modelo de objeto do Word](../vsto/word-object-model-overview.md)  
  
-   [Visão geral de modelo de objeto do Outlook](../vsto/outlook-object-model-overview.md)  
  
-   [Soluções InfoPath](../vsto/infopath-solutions.md)  
  
-   [Soluções PowerPoint](../vsto/powerpoint-solutions.md)  
  
-   [Soluções de projeto](../vsto/project-solutions.md)  
  
-   [Visão geral do modelo de objeto do Visio](../vsto/visio-object-model-overview.md)  
  
## <a name="customize-the-user-interface-of-applications"></a>Personalizar a interface do usuário de aplicativos  
 Há várias maneiras diferentes de personalizar a interface do usuário do aplicativo host usando um suplemento do VSTO:  
  
-   Para Excel e Word, você pode adicionar controles gerenciados a documentos. Para obter mais informações, consulte [documentos de estender o Word e pastas de trabalho do Excel no suplemento do VSTO em tempo de execução](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
-   Se o aplicativo dá suporte a ele, você pode personalizar a faixa de opções. Para obter mais informações, consulte [visão geral da faixa de opções](../vsto/ribbon-overview.md).  
  
-   Se o aplicativo dá suporte a ele, você pode criar um painel tarefa personalizada. Para obter mais informações, consulte [painéis de tarefas personalizados](../vsto/custom-task-panes.md).  
  
-   Para o Outlook, você pode criar uma região de formulário personalizado. Para obter mais informações, consulte [regiões de formulário do Outlook criar](../vsto/creating-outlook-form-regions.md).  
  
-   Para todos os aplicativos do Microsoft Office, você pode exibir os formulários do Windows no seu suplemento do VSTO.  
  
 Para obter mais informações sobre como personalizar os aplicativos de interface do usuário do Microsoft Office, consulte [personalização da interface do usuário do Office](../vsto/office-ui-customization.md).  
  
## <a name="next-steps"></a>Próximas etapas  
 Para saber como criar suplementos do VSTO, consulte as instruções a seguir:  
  
-   [Passo a passo: Criar seu primeiro VSTO suplemento para Excel](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)  
  
-   [Passo a passo: Criar seu primeiro VSTO suplemento para Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)  
  
-   [Passo a passo: Criar o primeiro Add-in do VSTO para PowerPoint](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)  
  
-   [Passo a passo: Criar o primeiro VSTO Add-in do projeto](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)  
  
-   [Passo a passo: Criar o primeiro Add-in do VSTO para Word](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)  
  
 Essas orientações apresentam as ferramentas de desenvolvimento do Office no Visual Studio e o modelo de programação para suplementos do VSTO.  
  
 Para obter uma lista de tópicos que mostram algumas das tarefas comuns em projetos do Office, consulte [tarefas comuns na programação do Office](../vsto/common-tasks-in-office-programming.md).  
  
## <a name="see-also"></a>Consulte também  
 [Como: criar projetos do Office no Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Introdução &#40;desenvolvimento do Office no Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Escrever código em soluções do Office](../vsto/writing-code-in-office-solutions.md)   
 [Arquitetura de suplementos do VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Programa de suplementos do VSTO](../vsto/programming-vsto-add-ins.md)  
  
  