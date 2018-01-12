---
title: 'Passo a passo: Criando seu primeiro suplemento VSTO para PowerPoint | Microsoft Docs'
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
- PowerPoint [Office development in Visual Studio], creating your first project
- add-ins [Office development in Visual Studio], creating your first project
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: eec0f2eaf7cc415e026a8427f7a881cd7ed15160
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-creating-your-first-vsto-add-in-for-powerpoint"></a>Passo a passo: criando o seu primeiro suplemento VSTO para o PowerPoint
  Este passo a passo mostra como criar um suplemento do VSTO para o Microsoft Office PowerPoint. Os recursos que você criar este tipo de solução estão disponíveis para o aplicativo em si, independentemente de qual apresentações estão abertas. Para obter mais informações, consulte [visão geral de desenvolvimento de soluções do Office &#40; VSTO &#41; ](../vsto/office-solutions-development-overview-vsto.md).  
  
 [!INCLUDE[appliesto_pptallapp](../vsto/includes/appliesto-pptallapp-md.md)]  
  
 Esta explicação passo a passo ilustra as seguintes tarefas:  
  
-   Criando um projeto de suplemento do PowerPoint VSTO para PowerPoint.  
  
-   Escrevendo código que usa o modelo de objeto do PowerPoint para adicionar uma caixa de texto para cada novo slide.  
  
-   Criar e executar o projeto para testá-lo.  
  
-   Limpando o projeto para que o suplemento do VSTO não seja executado automaticamente no computador de desenvolvimento.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Você precisa dos seguintes componentes para concluir esta instrução passo a passo:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   PowerPoint  
  
## <a name="creating-the-project"></a>Criando o Projeto  
  
#### <a name="to-create-a-new-project"></a>Para criar um novo projeto  
  
1.  Inicie o [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  No menu **Arquivo**, aponte para **Novo** e clique em **Projeto**.  
  
3.  No painel de modelos, expanda **Visual C#** ou **Visual Basic**e, em seguida, expanda **Office/SharePoint**.  
  
4.  Em expandidos **Office/SharePoint** nó, selecione o **suplementos do Office** nó.  
  
5.  Na lista de modelos de projeto, selecione um projeto de suplemento do VSTO do PowerPoint.  
  
6.  No **nome** , digite **FirstPowerPointAddIn**.  
  
7.  Clique em **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]cria o **FirstPowerPointAddIn** projeto e abrirá o **ThisAddIn** arquivo de código no editor.  
  
## <a name="writing-code-that-adds-text-to-each-new-slide"></a>Escrevendo código que adiciona o texto para cada novo Slide  
 Em seguida, adicione código ao arquivo de código ThisAddIn. O novo código usa o modelo de objeto do PowerPoint para adicionar uma caixa de texto para cada novo slide. Por padrão, o arquivo de código da classe ThisAddIn contém o seguinte código gerado:  
  
-   Uma definição parcial do `ThisAddIn` classe. Essa classe fornece um ponto de entrada para o seu código e fornece acesso ao modelo de objeto do PowerPoint. Para obter mais informações, consulte [Programando suplementos do VSTO](../vsto/programming-vsto-add-ins.md). O restante do `ThisAddIn` classe é definida em um arquivo de código oculto que você não deve modificar.  
  
-   O `ThisAddIn_Startup` e `ThisAddIn_Shutdown` manipuladores de eventos. Esses manipuladores de eventos são chamados quando o PowerPoint carrega e descarrega o suplemento do VSTO. Use esses manipuladores de eventos para inicializar o suplemento do VSTO quando ele é carregado e para limpar os recursos usados pelo seu suplemento do VSTO quando ela é descarregada. Para obter mais informações, consulte [eventos em projetos do Office](../vsto/events-in-office-projects.md).  
  
#### <a name="to-add-a-text-box-to-each-new-slide"></a>Para adicionar uma caixa de texto para cada novo slide  
  
1.  No arquivo de código classe ThisAddIn, adicione o seguinte código para o `ThisAddIn` classe. Esse código define um manipulador de eventos para o <xref:Microsoft.Office.Interop.PowerPoint.EApplication_Event.PresentationNewSlide> evento o <xref:Microsoft.Office.Interop.PowerPoint.Application> objeto.  
  
     Quando o usuário adiciona um novo slide à apresentação ativa, esse manipulador de eventos adiciona uma caixa de texto à parte superior do novo slide, e ele adiciona um texto à caixa de texto.  
  
     [!code-vb[Trin_PowerPointAddInTutorial#1](../vsto/codesnippet/VisualBasic/Trin_PowerPointAddInTutorial/ThisAddIn.vb#1)]
     [!code-csharp[Trin_PowerPointAddInTutorial#1](../vsto/codesnippet/CSharp/Trin_PowerPointAddInTutorial/ThisAddIn.cs#1)]  
  
2.  Se você estiver usando c#, adicione o seguinte código para o `ThisAddIn_Startup` manipulador de eventos. Esse código é necessária para conectar o `Application_PresentationNewSlide` manipulador de eventos com o <xref:Microsoft.Office.Interop.PowerPoint.EApplication_Event.PresentationNewSlide> evento.  
  
     [!code-csharp[Trin_PowerPointAddInTutorial#2](../vsto/codesnippet/CSharp/Trin_PowerPointAddInTutorial/ThisAddIn.cs#2)]  
  
 Para modificar cada novo slide, os exemplos de código anterior usam os seguintes objetos:  
  
-   O `Application` campo o `ThisAddIn` classe. O `Application` campo retorna um <xref:Microsoft.Office.Interop.PowerPoint.Application> objeto que representa a instância atual do PowerPoint.  
  
-   O `Sld` parâmetro do manipulador de eventos para o <xref:Microsoft.Office.Interop.PowerPoint.EApplication_Event.PresentationNewSlide> evento. O `Sld` parâmetro é um <xref:Microsoft.Office.Interop.PowerPoint.Slide> objeto que representa o novo slide. Para obter mais informações, consulte [soluções PowerPoint](../vsto/powerpoint-solutions.md).  
  
## <a name="testing-the-project"></a>O projeto de teste  
 Quando você compilar e executa o projeto, verifique se a caixa de texto aparece em novos slides que você adicionar a uma apresentação.  
  
#### <a name="to-test-the-project"></a>Para testar o projeto  
  
1.  Pressione **F5** para compilar e executar seu projeto.  
  
     Quando você compila o projeto, o código é compilado em um assembly que é colocado na pasta de saída de compilação do projeto. O Visual Studio também cria um conjunto de entradas do registro que permitem o PowerPoint descobrir e carregar o suplemento do VSTO, e ele define as configurações de segurança no computador de desenvolvimento para habilitar o suplemento do VSTO executar. Para obter mais informações, consulte [criando soluções do Office](../vsto/building-office-solutions.md).  
  
2.  No PowerPoint, adicione um novo slide à apresentação ativa.  
  
3.  Verifique se o texto a seguir é adicionado a uma nova caixa de texto na parte superior do slide.  
  
     **Este texto foi adicionado por meio de código.**  
  
4.  Feche o PowerPoint.  
  
## <a name="cleaning-up-the-project"></a>O projeto de limpeza  
 Quando você terminar de desenvolvimento de um projeto, remova o suplemento do VSTO assembly, entradas do registro e as configurações de segurança do seu computador de desenvolvimento. Caso contrário, o suplemento do VSTO será executado toda vez que abrir o PowerPoint no computador de desenvolvimento.  
  
#### <a name="to-clean-up-your-project"></a>Para limpar seu projeto  
  
1.  No Visual Studio, no **criar** menu, clique em **limpar solução**.  
  
## <a name="next-steps"></a>Próximas etapas  
 Agora que você criou um Add-in básico do VSTO para PowerPoint, você pode aprender mais sobre como desenvolver um suplemento do VSTO com estes tópicos:  
  
-   Tarefas de programação gerais que você pode executar nos suplementos do VSTO para PowerPoint. Para obter mais informações, consulte [Programando suplementos do VSTO](../vsto/programming-vsto-add-ins.md).  
  
-   Usando o modelo de objeto do PowerPoint. Para obter mais informações, consulte [soluções PowerPoint](../vsto/powerpoint-solutions.md).  
  
-   Personalizando a interface do usuário do PowerPoint, por exemplo, adicionando uma guia à faixa de opções ou criar seu próprio painel de tarefas personalizadas. Para obter mais informações, consulte [personalização da interface do usuário do Office](../vsto/office-ui-customization.md).  
  
-   Compilando e depurando suplementos do VSTO para PowerPoint. Para obter mais informações, consulte [criando soluções do Office](../vsto/building-office-solutions.md).  
  
-   Implantação de suplementos do VSTO para PowerPoint. Para obter mais informações, consulte [implantar uma solução Office](../vsto/deploying-an-office-solution.md).  
  
## <a name="see-also"></a>Consulte também  
 [Suplementos de programação para o VSTO](../vsto/programming-vsto-add-ins.md)   
 [Soluções PowerPoint](../vsto/powerpoint-solutions.md)   
 [Personalização da interface do usuário do Office](../vsto/office-ui-customization.md)   
 [Criando soluções do Office](../vsto/building-office-solutions.md)   
 [Implantando uma solução do Office](../vsto/deploying-an-office-solution.md)   
 [Visão geral dos modelos do Office Project](../vsto/office-project-templates-overview.md)  
  
  