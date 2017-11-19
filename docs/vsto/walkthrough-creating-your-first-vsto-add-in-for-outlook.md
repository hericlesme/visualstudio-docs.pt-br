---
title: 'Passo a passo: Criando seu primeiro suplemento VSTO para Outlook | Microsoft Docs'
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
- application-level add-ins [Office development in Visual Studio], creating your first project
- Office development in Visual Studio, creating your first project
- add-ins [Office development in Visual Studio], creating your first project
- Outlook [Office development in Visual Studio], creating your first project
ms.assetid: 2c5c5d75-27ee-471f-9328-58f0cf05b2b7
caps.latest.revision: "28"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 514e6e0f52867b586135050d555508caec8cb6e6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-creating-your-first-vsto-add-in-for-outlook"></a>Passo a passo: criando seu primeiro suplemento VSTO para Outlook
  Este passo a passo mostra como criar um suplemento do VSTO para o Microsoft Office Outlook. Os recursos que você criar este tipo de solução estão disponíveis para o aplicativo em si, independentemente de qual item do Outlook estiver aberto. Para obter mais informações, consulte [visão geral de desenvolvimento de soluções do Office &#40; VSTO &#41; ](../vsto/office-solutions-development-overview-vsto.md).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
 Esta explicação passo a passo ilustra as seguintes tarefas:  
  
-   Criando um projeto de suplemento do Outlook VSTO para Outlook.  
  
-   Escrevendo código que usa o modelo de objeto do Outlook para adicionar texto de assunto e corpo de uma nova mensagem de email.  
  
-   Criar e executar o projeto para testá-lo.  
  
-   A limpeza do projeto concluído para que o suplemento do VSTO não seja executado automaticamente no computador de desenvolvimento.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Você precisa dos seguintes componentes para concluir esta instrução passo a passo:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Outlook  
  
## <a name="creating-the-project"></a>Criando o Projeto  
  
#### <a name="to-create-a-new-outlook-project-in-visual-studio"></a>Para criar um novo projeto do Outlook no Visual Studio  
  
1.  Inicie o [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  No menu **Arquivo**, aponte para **Novo** e clique em **Projeto**.  
  
3.  No painel de modelos, expanda **Visual C#** ou **Visual Basic**e, em seguida, expanda **Office/SharePoint**.  
  
4.  Em expandidos **Office/SharePoint** nó, selecione o **suplementos do Office** nó.  
  
5.  Na lista de modelos de projeto, escolha um projeto de suplemento do VSTO do Outlook.  
  
6.  No **nome** , digite **FirstOutlookAddIn**.  
  
7.  Clique em **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]cria o **FirstOutlookAddIn** projeto e abrirá o **ThisAddIn** arquivo de código no editor.  
  
## <a name="writing-code-that-adds-text-to-each-new-mail-message"></a>Escrevendo código que adiciona o texto para cada nova mensagem de email  
 Em seguida, adicione código ao arquivo de código ThisAddIn. O novo código usa o modelo de objeto do Outlook para adicionar texto para cada nova mensagem de email. Por padrão, o arquivo de código da classe ThisAddIn contém o seguinte código gerado:  
  
-   Uma definição parcial do `ThisAddIn` classe. Essa classe fornece um ponto de entrada para o seu código e fornece acesso ao modelo de objeto do Outlook. Para obter mais informações, consulte [Programando suplementos do VSTO](../vsto/programming-vsto-add-ins.md). O restante do `ThisAddIn` classe é definida em um arquivo de código oculto que você não deve modificar.  
  
-   O `ThisAddIn_Startup` e `ThisAddIn_Shutdown` manipuladores de eventos. Esses manipuladores de eventos são chamados quando o Outlook carrega e descarrega o suplemento do VSTO. Use esses manipuladores de eventos para inicializar o suplemento do VSTO quando ele é carregado e para limpar os recursos usados pelo seu suplemento do VSTO quando ela é descarregada. Para obter mais informações, consulte [eventos em projetos do Office](../vsto/events-in-office-projects.md).  
  
#### <a name="to-add-text-to-the-subject-and-body-of-each-new-mail-message"></a>Para adicionar texto para o assunto e corpo de cada nova mensagem de email  
  
1.  No arquivo de código classe ThisAddIn, declare um campo chamado `inspectors` no `ThisAddIn` classe. O `inspectors` campo mantém uma referência para a coleção de janelas do Inspetor na instância atual do Outlook. Essa referência impede que o coletor de lixo liberar a memória que contém o manipulador de eventos para o <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> evento.  
  
     [!code-vb[Trin_OutlookAddInTutorial#1](../vsto/codesnippet/VisualBasic/Trin_OutlookAddInTutorial/ThisAddIn.vb#1)]
     [!code-csharp[Trin_OutlookAddInTutorial#1](../vsto/codesnippet/CSharp/Trin_OutlookAddInTutorial/ThisAddIn.cs#1)]  
  
2.  Substitua o `ThisAddIn_Startup` método com o código a seguir. Esse código anexa um manipulador de eventos para o <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> evento.  
  
     [!code-vb[Trin_OutlookAddInTutorial#2](../vsto/codesnippet/VisualBasic/Trin_OutlookAddInTutorial/ThisAddIn.vb#2)]
     [!code-csharp[Trin_OutlookAddInTutorial#2](../vsto/codesnippet/CSharp/Trin_OutlookAddInTutorial/ThisAddIn.cs#2)]  
  
3.  No arquivo de código classe ThisAddIn, adicione o seguinte código para o `ThisAddIn` classe. Esse código define um manipulador de eventos para o <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> evento.  
  
     Quando o usuário cria uma nova mensagem de email, esse manipulador de eventos adiciona texto para a linha de assunto e corpo da mensagem.  
  
     [!code-vb[Trin_OutlookAddInTutorial#3](../vsto/codesnippet/VisualBasic/Trin_OutlookAddInTutorial/ThisAddIn.vb#3)]
     [!code-csharp[Trin_OutlookAddInTutorial#3](../vsto/codesnippet/CSharp/Trin_OutlookAddInTutorial/ThisAddIn.cs#3)]  
  
 Para modificar cada nova mensagem de email, os exemplos de código anterior usam os seguintes objetos:  
  
-   O `Application` campo o `ThisAddIn` classe. O `Application` campo retorna um <xref:Microsoft.Office.Interop.Outlook.Application> objeto que representa a instância atual do Outlook.  
  
-   O `Inspector` parâmetro do manipulador de eventos para o <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> evento. O `Inspector` parâmetro é um <xref:Microsoft.Office.Interop.Outlook.Inspector> objeto que representa a janela do Inspetor da nova mensagem de email. Para obter mais informações, consulte [soluções do Outlook](../vsto/outlook-solutions.md).  
  
## <a name="testing-the-project"></a>O projeto de teste  
 Quando você compilar e executa o projeto, verifique se o texto aparece na linha de assunto e corpo de uma nova mensagem de email.  
  
#### <a name="to-test-the-project"></a>Para testar o projeto  
  
1.  Pressione **F5** para compilar e executar seu projeto.  
  
     Quando você compila o projeto, o código é compilado em um assembly que está incluído na pasta de saída de compilação do projeto. O Visual Studio também cria um conjunto de entradas do registro que permitem que o Outlook descobrir e carregar o suplemento do VSTO, e ele define as configurações de segurança no computador de desenvolvimento para habilitar o suplemento do VSTO executar. Para obter mais informações, consulte [Office criar processo de visão geral da solução](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md).  
  
2.  No Outlook, crie uma nova mensagem de email.  
  
3.  Verifique se o texto a seguir é adicionado para a linha de assunto e o corpo da mensagem.  
  
     **Este texto foi adicionado por meio de código.**  
  
4.  Feche o Outlook.  
  
## <a name="cleaning-up-the-project"></a>O projeto de limpeza  
 Quando você terminar de desenvolvimento de um projeto, remova o suplemento do VSTO assembly, entradas do registro e as configurações de segurança do seu computador de desenvolvimento. Caso contrário, o suplemento do VSTO será executado toda vez que você abrir o Outlook no computador de desenvolvimento.  
  
#### <a name="to-clean-up-your-project"></a>Para limpar seu projeto  
  
1.  No Visual Studio, no **criar** menu, clique em **limpar solução**.  
  
## <a name="next-steps"></a>Próximas etapas  
 Agora que você criou um básico do VSTO suplemento para Outlook, você pode aprender mais sobre como desenvolver um suplemento do VSTO com estes tópicos:  
  
-   Tarefas de programação gerais que você pode executar usando os suplementos do VSTO para Outlook. Para obter mais informações, consulte [Programando suplementos do VSTO](../vsto/programming-vsto-add-ins.md).  
  
-   Usando o modelo de objeto do Outlook. Para obter mais informações, consulte [soluções do Outlook](../vsto/outlook-solutions.md).  
  
-   Personalizando a interface do usuário do Outlook, por exemplo, adicionando uma guia à faixa de opções ou criar seu próprio painel de tarefas personalizadas. Para obter mais informações, consulte [personalização da interface do usuário do Office](../vsto/office-ui-customization.md).  
  
-   Compilar e depurar o suplemento do VSTO para Outlook. Para obter mais informações, consulte [criando soluções do Office](../vsto/building-office-solutions.md).  
  
-   Implantação de suplementos do VSTO para Outlook. Para obter mais informações, consulte [implantar uma solução Office](../vsto/deploying-an-office-solution.md).  
  
## <a name="see-also"></a>Consulte também  
 [Suplementos de programação para o VSTO](../vsto/programming-vsto-add-ins.md)   
 [Soluções do Outlook](../vsto/outlook-solutions.md)   
 [Personalização da interface do usuário do Office](../vsto/office-ui-customization.md)   
 [Criando soluções do Office](../vsto/building-office-solutions.md)   
 [Implantando uma solução do Office](../vsto/deploying-an-office-solution.md)   
 [Visão geral dos modelos do Office Project](../vsto/office-project-templates-overview.md)  
  
  