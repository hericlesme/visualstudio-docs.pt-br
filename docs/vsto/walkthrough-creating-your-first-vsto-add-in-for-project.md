---
title: 'Passo a passo: Criando seu primeiro suplemento VSTO para Project | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], creating your first project
- Office development in Visual Studio, creating your first project
- Project [Office development in Visual Studio], creating your first project
- add-ins [Office development in Visual Studio], creating your first project
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 3572f07a9bb0e3fc9a38ec55ae260e19dd671620
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-creating-your-first-vsto-add-in-for-project"></a>Passo a passo: Criando seu primeiro suplemento VSTO para Project
  Este passo a passo mostra como criar um suplemento do VSTO para o Microsoft Office Project. Os recursos que você criar este tipo de solução estão disponíveis para o aplicativo em si, independentemente de qual projeto estiver aberto. Para obter mais informações, consulte [visão geral de desenvolvimento de soluções do Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
 [!INCLUDE[appliesto_projallapp](../vsto/includes/appliesto-projallapp-md.md)]  
  
 Esta explicação passo a passo ilustra as seguintes tarefas:  
  
-   Criando um projeto de suplemento do VSTO do projeto.  
  
-   Escrevendo código que usa o modelo de objeto do projeto para adicionar uma tarefa para um novo projeto.  
  
-   Criar e executar o projeto para testá-lo.  
  
-   A limpeza do projeto concluído para que o suplemento do VSTO não seja executado automaticamente no computador de desenvolvimento.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Você precisa dos seguintes componentes para concluir esta instrução passo a passo:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Project_15_short](../vsto/includes/project-15-short-md.md)] ou [!INCLUDE[Project_14_short](../vsto/includes/project-14-short-md.md)].  
  
## <a name="creating-the-project"></a>Criando o Projeto  
  
#### <a name="to-create-a-new-project-in-visual-studio"></a>Para criar um novo projeto no Visual Studio  
  
1.  Inicie o [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  No menu **Arquivo**, aponte para **Novo** e clique em **Projeto**.  
  
3.  No painel de modelos, expanda **Visual C#** ou **Visual Basic**e, em seguida, expanda **Office/SharePoint**.  
  
4.  Em expandidos **Office/SharePoint** nó, selecione o **suplementos do Office** nó.  
  
5.  Na lista de modelos de projeto, selecione **suplemento Project 2010** ou **suplemento do projeto 2013**.  
  
6.  No **nome** , digite **FirstProjectAddIn**.  
  
7.  Clique em **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] cria o **FirstProjectAddIn** projeto e abrirá o **ThisAddIn** arquivo de código no editor.  
  
## <a name="writing-code-that-adds-a-new-task-to-a-project"></a>Escrevendo código que adiciona uma nova tarefa a um projeto  
 Em seguida, adicione código ao arquivo de código ThisAddIn. O novo código usa o modelo de objeto do projeto para adicionar uma nova tarefa a um projeto. Por padrão, o arquivo de código da classe ThisAddIn contém o seguinte código gerado:  
  
-   Uma definição parcial do `ThisAddIn` classe. Essa classe fornece um ponto de entrada para o seu código e fornece acesso ao modelo de objeto do projeto. Para obter mais informações, consulte [Programando a validação](../vsto/programming-vsto-add-ins.md). O restante do `ThisAddIn` classe é definida em um arquivo de código oculto que você não deve modificar.  
  
-   O `ThisAddIn_Startup` e `ThisAddIn_Shutdown` manipuladores de eventos. Esses manipuladores de eventos são chamados quando o projeto carrega e descarrega o suplemento do VSTO. Use esses manipuladores de eventos para inicializar o suplemento do VSTO quando ele é carregado e para limpar os recursos usados pelo seu suplemento do VSTO quando ela é descarregada. Para obter mais informações, consulte [eventos em projetos do Office](../vsto/events-in-office-projects.md).  
  
#### <a name="to-add-a-task-to-a-new-project"></a>Para adicionar uma tarefa para um novo projeto  
  
1.  No arquivo de código classe ThisAddIn, adicione o seguinte código para o `ThisAddIn` classe. Esse código define um manipulador de eventos para o evento NewProject da classe Microsoft.Office.Interop.MSProject.Application.  
  
     Quando o usuário cria um novo projeto, esse manipulador de eventos adiciona uma tarefa para o projeto.  
  
     [!code-vb[Trin_ProjectAddInTutorial#1](../vsto/codesnippet/VisualBasic/Trin_ProjectAddInTutorial/ThisAddIn.vb#1)]
     [!code-csharp[Trin_ProjectAddInTutorial#1](../vsto/codesnippet/CSharp/Trin_ProjectAddInTutorial/ThisAddIn.cs#1)]  
  
 Para modificar o projeto, este exemplo de código usa os seguintes objetos:  
  
-   O `Application` campo o `ThisAddIn` classe. O `Application` campo retorna um objeto Microsoft.Office.Interop.MSProject.Application, que representa a instância atual do projeto.  
  
-   O `pj` parâmetro do manipulador de eventos para o evento NewProject. O `pj` parâmetro é um objeto Microsoft.Office.Interop.MSProject.Project, que representa o projeto. Para obter mais informações, consulte [soluções de projeto](../vsto/project-solutions.md).  
  
1.  Se você estiver usando c#, adicione o seguinte código para o `ThisAddIn_Startup` manipulador de eventos. Esse código se conecta a `Application_Newproject` manipulador de eventos com o evento NewProject.  
  
     [!code-csharp[Trin_ProjectAddInTutorial#2](../vsto/codesnippet/CSharp/Trin_ProjectAddInTutorial/ThisAddIn.cs#2)]  
  
-  
  
## <a name="testing-the-project"></a>O projeto de teste  
 Quando você compilar e executa o projeto, verifique se a nova tarefa aparece no novo projeto resultante.  
  
#### <a name="to-test-the-project"></a>Para testar o projeto  
  
1.  Pressione **F5** para compilar e executar seu projeto. Microsoft Project inicia e abre automaticamente um novo projeto em branco.  
  
     Quando você compila o projeto, o código é compilado em um assembly que está incluído na pasta de saída de compilação do projeto. O Visual Studio também cria um conjunto de entradas do registro que permitem que o projeto descobrir e carregar o suplemento do VSTO, e ele define as configurações de segurança no computador de desenvolvimento para habilitar o suplemento do VSTO executar. Para obter mais informações, consulte [Office criar processo de visão geral da solução](http://msdn.microsoft.com/en-us/a9d12e4f-c9ea-4a62-a841-c42b91f831ee).  
  
2.  Verifique se que uma nova tarefa é adicionada ao projeto em branco.  
  
3.  Verifique se o texto a seguir aparece no **nome da tarefa** campo da tarefa.  
  
     **Este texto foi adicionado por meio de código.**  
  
4.  Feche o Microsoft Project.  
  
## <a name="cleaning-up-the-project"></a>O projeto de limpeza  
 Quando você terminar de desenvolvimento de um projeto, remova o suplemento do VSTO assembly, entradas do registro e as configurações de segurança do seu computador de desenvolvimento. Caso contrário, o suplemento do VSTO será executado sempre que você abrir o Microsoft Project no computador de desenvolvimento.  
  
#### <a name="to-clean-up-your-project"></a>Para limpar seu projeto  
  
1.  No Visual Studio, no **criar** menu, clique em **limpar solução**.  
  
## <a name="next-steps"></a>Próximas etapas  
 Agora que você criou um básico do VSTO suplemento para o projeto, você pode aprender mais sobre como desenvolver um suplemento do VSTO com estes tópicos:  
  
-   Tarefas gerais de programação que você pode executar no suplemento do VSTO para o projeto: [Programando suplementos do VSTO](../vsto/programming-vsto-add-ins.md).  
  
-   Usando o modelo de objeto do projeto: [soluções de projeto](../vsto/project-solutions.md).  
  
-   Compilar e depurar o suplemento do VSTO para o projeto: [criando soluções do Office](../vsto/building-office-solutions.md).  
  
-   Implantação de suplementos do VSTO para Project: [implantar uma solução Office](../vsto/deploying-an-office-solution.md).  
  
## <a name="see-also"></a>Consulte também  
 [Suplementos de programação para o VSTO](../vsto/programming-vsto-add-ins.md)   
 [Soluções de projeto](../vsto/project-solutions.md)   
 [Criando soluções do Office](../vsto/building-office-solutions.md)   
 [Implantando uma solução do Office](../vsto/deploying-an-office-solution.md)   
 [Visão geral dos modelos do Office Project](../vsto/office-project-templates-overview.md)  
  
  