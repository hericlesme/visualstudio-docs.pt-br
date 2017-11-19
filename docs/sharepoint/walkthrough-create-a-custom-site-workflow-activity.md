---
title: 'Passo a passo: Criar uma atividade de fluxo de trabalho de um Site personalizado | Microsoft Docs'
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
- custom workflow activities [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, custom workflow activities
- site workflows [SharePoint development in Visual Studio]
- workflow activities [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, site workflows
ms.assetid: 8219a779-c27b-4186-92c9-5bda03328aa9
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6d3579c3d537dc13723cbe285b454b24d079fe1f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-create-a-custom-site-workflow-activity"></a>Instruções passo a passo: criar uma atividade personalizada de fluxo de trabalho do local
  Este passo a passo demonstra como criar uma atividade personalizada para um fluxo de trabalho de nível de site usando [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. (Fluxos de trabalho de nível de site se aplicam ao site inteiro, não apenas em uma lista no site.) A atividade personalizada cria um lista de avisos de backup e, em seguida, copia o conteúdo da lista de anúncios.  
  
 Este passo a passo demonstra as seguintes tarefas:  
  
-   Criando um fluxo de trabalho de nível de site.  
  
-   Criar uma atividade de fluxo de trabalho personalizado.  
  
-   Criando e excluindo uma lista do SharePoint.  
  
-   Copiar os itens de uma lista para outra.  
  
-   Exibindo uma lista na barra Início rápido.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Você precisa dos seguintes componentes para concluir esta instrução passo a passo:  
  
-   Edições do [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] e do SharePoint. Para obter mais informações, consulte [requisitos para desenvolver soluções do SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio.  
  
## <a name="creating-a-site-workflow-custom-activity-project"></a>Criando um projeto de atividade personalizada de fluxo de trabalho do Site  
 Primeiro, crie um projeto para manter e testar a atividade de fluxo de trabalho personalizado.  
  
#### <a name="to-create-a-site-workflow-custom-activity-project"></a>Para criar um projeto de atividade personalizada de fluxo de trabalho do site  
  
1.  Na barra de menus, escolha **arquivo**, **novo**, **projeto** para exibir o **novo projeto** caixa de diálogo.  
  
2.  Expanda o **SharePoint** nó sob o **Visual C#** ou **Visual Basic**e, em seguida, escolha o **2010** nó.  
  
3.  No **modelos** painel, escolha o **projeto do SharePoint 2010** modelo.  
  
4.  No **nome** , digite **AnnouncementBackup**e, em seguida, escolha o **Okey** botão.  
  
     O **Assistente de personalização do SharePoint** é exibida.  
  
5.  No **especificar o nível de site e segurança de depuração** página, escolha o **implantar como uma solução de farm** botão de opção e, em seguida, escolha o **concluir** botão para aceitar o site padrão e o nível de confiança.  
  
     Esta etapa define o nível de confiança para a solução como solução de farm, a única opção disponível para projetos de fluxo de trabalho.  
  
6.  Em **Solution Explorer**, escolha o nó do projeto e, em seguida, na barra de menus, escolha **projeto**, **Adicionar Novo Item**.  
  
7.  Em um **Visual C#** ou **Visual Basic**, expanda o **SharePoint** nó e, em seguida, escolha o **2010** nó.  
  
8.  No **modelos** painel, escolha o **o fluxo de trabalho sequencial (somente solução de Farm)** modelo e, em seguida, escolha o **adicionar** botão.  
  
     O **Assistente de personalização do SharePoint** é exibida.  
  
9. Sobre o **especifique o nome do fluxo de trabalho para depuração** página, aceite o nome padrão (AnnouncementBackup - Workflow1). Altere o tipo de modelo de fluxo de trabalho para **fluxo de trabalho do Site**e, em seguida, escolha o **próximo** botão.  
  
10. Escolha o **concluir** botão para aceitar as configurações padrão restantes.  
  
## <a name="adding-a-custom-workflow-activity-class"></a>Adicionando uma classe de atividade de fluxo de trabalho personalizado  
 Em seguida, adicione uma classe para o projeto contém o código para a atividade de fluxo de trabalho personalizado.  
  
#### <a name="to-add-a-custom-workflow-activity-class"></a>Para adicionar uma classe de atividade de fluxo de trabalho personalizado  
  
1.  Na barra de menus, escolha **projeto**, **Adicionar Novo Item** para exibir o **Adicionar Novo Item** caixa de diálogo.  
  
2.  No **modelos instalados** exibição de árvore, escolha o **código** nó e, em seguida, escolha o **classe** modelo na lista de modelos de item de projeto. Use o nome padrão Class1. Escolha o botão **Adicionar**.  
  
3.  Substitua todo o código em Class1 com o seguinte:  
  
     [!code-csharp[SP_AnnBackup#1](../sharepoint/codesnippet/CSharp/announcementbackup/class1.cs#1)]
     [!code-vb[SP_AnnBackup#1](../sharepoint/codesnippet/VisualBasic/announcementbackupvb/class1.vb#1)]  
  
4.  Salve o projeto e, em seguida, na barra de menus, escolha **criar**, **compilar solução**.  
  
     Class1 aparece como uma ação personalizada no **caixa de ferramentas** no **AnnouncementBackup componentes** guia.  
  
## <a name="adding-the-custom-activity-to-the-site-workflow"></a>Adicionando a atividade personalizada para o fluxo de trabalho do Site  
 Em seguida, adicione uma atividade ao fluxo de trabalho para conter o código personalizado.  
  
#### <a name="to-add-a-custom-activity-to-the-site-workflow"></a>Para adicionar uma atividade personalizada para o site de fluxo de trabalho  
  
1.  Abra Workflow1 no designer de fluxo de trabalho no modo de design.  
  
2.  Arraste Class1 do **caixa de ferramentas** para que ele apareça sob o `onWorkflowActivated1` atividade ou abrir o menu de atalho para Class1, escolha **cópia**, abra o menu de atalho para a linha no `onWorkflowActivated1` atividade e, em seguida, escolha **colar**.  
  
3.  Salvar o projeto.  
  
## <a name="testing-the-site-workflow-custom-activity"></a>Testando a atividade personalizada de fluxo de trabalho do Site  
 Em seguida, execute o projeto e iniciar o fluxo de trabalho do site. A atividade personalizada cria uma lista de anúncios de backup e copia o conteúdo da lista de avisos atual. O código também verifica se uma lista de backup já existe antes de criar um. Se já existir uma lista de backup, ele será excluído. O código também adiciona um link para a nova lista na barra de início rápido do site do SharePoint.  
  
#### <a name="to-test-the-site-workflow-custom-activity"></a>Para testar a atividade personalizada de fluxo de trabalho do site  
  
1.  Escolha a tecla F5 para executar o projeto e implantá-lo no SharePoint.  
  
2.  Na barra de início rápido, escolha o **lista** link para exibir todas as listas que estão disponíveis no site do SharePoint. Observe que há apenas uma lista de anúncios chamado de **anúncios**.  
  
3.  Na parte superior da página da Web do SharePoint, escolha o **fluxos de trabalho do Site** link.  
  
4.  Em uma seção de fluxo de trabalho novo início, escolha o **AnnouncementBackup - Workflow1** link. Isso inicia o fluxo de trabalho do site e executa o código na ação personalizada.  
  
5.  Na barra de início rápido, escolha o **Backup anúncios** link. Observe que todos os anúncios que estão contidos no **anúncios** lista foram copiados para essa nova lista.  
  
## <a name="see-also"></a>Consulte também  
 [Como: criar um receptor de evento](../sharepoint/how-to-create-an-event-receiver.md)   
 [Desenvolvendo soluções do SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
  