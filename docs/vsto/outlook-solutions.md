---
title: "Soluções do Outlook | Microsoft Docs"
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
- solutions [Office development in Visual Studio], Outlook
- Office projects [Office development in Visual Studio], Outlook
- Office solutions [Office development in Visual Studio], Outlook
- templates [Office development in Visual Studio], Outlook
- projects [Office development in Visual Studio], Outlook
- Outlook [Office development in Visual Studio]
- e-mail [Office development in Visual Studio], Outlook solutions
ms.assetid: 2ae3cd9c-bf31-4efa-8b18-b6b1c34a8d93
caps.latest.revision: "27"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 3692e6b224297175d8466a993b0dc16cc7827294
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="outlook-solutions"></a>Soluções do Outlook
  O Visual Studio fornece modelos de projeto, que você pode usar para criar suplementos do VSTO para o Microsoft Office Outlook. Você pode usar os suplementos do VSTO para automatizar o Outlook, estender os recursos do Outlook ou personalizar a interface de usuário (UI) do Outlook. Para obter mais informações sobre os suplementos do VSTO, consulte [suplementos da arquitetura do VSTO](../vsto/architecture-of-vsto-add-ins.md).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
> [!NOTE]  
>  Interessado em desenvolvimento de soluções que estendem a experiência do Office em [várias plataformas](https://dev.office.com/add-in-availability)? Confira a nova [modelo de suplementos do Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Suplementos do Office têm uma superfície pequena em comparação com suplementos do VSTO e soluções, e você pode criá-los usando quase qualquer tecnologia, como JavaScript, HTML5, CSS3 e XML de programação da web.  
  
## <a name="creating-an-outlook-vsto-add-in-project"></a>Criando um projeto de suplemento do VSTO Outlook  
 Criar projetos do Outlook usando o **do suplemento do Outlook** modelo de projeto no **novo projeto** caixa de diálogo. Esse modelo inclui referências de assembly necessárias e os arquivos de projeto.  
  
 Para obter mais informações sobre como criar um projeto de suplemento do VSTO, consulte [como: criar projetos do Office no Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md). Para obter mais informações sobre os modelos de projeto, consulte [visão geral de modelos de projeto do Office](../vsto/office-project-templates-overview.md).  
  
## <a name="outlook-vsto-add-in-programming-model"></a>Outlook VSTO adicionar no modelo de programação  
 Quando você cria um projeto de suplemento do VSTO do Outlook, o Visual Studio gera uma classe chamada `ThisAddIn`, que é a base da sua solução. Essa classe fornece um ponto de partida para escrever seu código e também expõe o modelo de objeto do Outlook para o suplemento do VSTO.  
  
 Para obter mais informações sobre o `ThisAddIn` classe e outros recursos que você pode usar um VSTO Add-in, consulte [Programando suplementos do VSTO](../vsto/programming-vsto-add-ins.md).  
  
## <a name="automating-outlook-by-using-the-outlook-object-model"></a>Automatizando o Outlook usando o modelo de objeto do Outlook  
 O modelo de objeto do Outlook expõe vários tipos que você pode usar para automatizar o Outlook. Esses tipos permitem que você escreva código para realizar tarefas comuns:  
  
-   Criar e enviar mensagens de email programaticamente.  
  
-   Envie novas solicitações de reunião.  
  
-   Procurar por itens em pastas do Outlook.  
  
 Para obter mais informações, consulte [visão geral de modelo de objeto do Outlook](../vsto/outlook-object-model-overview.md).  
  
## <a name="customizing-the-user-interface-of-an-outlook-application"></a>Personalizando a Interface do usuário de um aplicativo do Outlook  
  
|Tarefa|Para obter mais informações|  
|----------|--------------------------|  
|Adicione guias personalizadas para a faixa de opções de um inspetor do Outlook.|[Visão geral da faixa de opções](../vsto/ribbon-overview.md)|  
|Adicione grupos personalizados a uma guia interna em um inspetor do Outlook.|[Como personalizar uma guia interna](../vsto/how-to-customize-a-built-in-tab.md)|  
|Adicionar um painel tarefa personalizada que aparece em um inspetor do Outlook|[Painéis de tarefas personalizados](../vsto/custom-task-panes.md).|  
|Adicione uma região de formulário que estende ou substitui formulários existentes do Outlook.|[Criando regiões de formulário do Outlook](../vsto/creating-outlook-form-regions.md)|  
  
 Para obter mais informações sobre como personalizar a interface do usuário do Outlook e outros aplicativos do Microsoft Office, consulte [personalização da interface do usuário do Office](../vsto/office-ui-customization.md).  
  
## <a name="related-topics"></a>Tópicos relacionados  
  
|Título|Descrição|  
|-----------|-----------------|  
|[Visão geral do modelo de objeto do Outlook](../vsto/outlook-object-model-overview.md)|Fornece uma visão geral dos objetos que são fornecidos pelo modelo de objeto do Outlook.|  
|[Criando regiões de formulário do Outlook](../vsto/creating-outlook-form-regions.md)|Explica as ferramentas fornecidas pelo Visual Studio que tornam mais fácil para você criar, desenvolver e depurar regiões de formulário.|  
|[Passo a passo: criando seu primeiro suplemento VSTO para Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)|Mostra como criar um suplemento do VSTO para o Microsoft Office Outlook.|  
|[Outlook 2010 no desenvolvimento do Office](http://go.microsoft.com/fwlink/?LinkId=199013)|A área da biblioteca do MSDN, onde você pode encontrar artigos e documentação de referência sobre o desenvolvimento de soluções do Outlook (não específicas ao desenvolvimento do Office usando o Visual Studio).|  
  
  