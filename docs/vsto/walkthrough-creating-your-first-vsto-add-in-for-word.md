---
title: 'Passo a passo: Criando seu primeiro suplemento VSTO para Word | Microsoft Docs'
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
- Word [Office development in Visual Studio], creating your first project
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 3452bd5e550ab724dc6c236515579869814a9237
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-creating-your-first-vsto-add-in-for-word"></a>Passo a passo: criando o seu primeiro suplemento VSTO para o Word
  Este passo a passo introdutório mostra como criar um suplemento do VSTO para o Microsoft Office Word. Os recursos que você criar este tipo de solução estão disponíveis para o aplicativo em si, independentemente de qual documentos estiverem abertos.  
  
 [!INCLUDE[appliesto_wdallapp](../vsto/includes/appliesto-wdallapp-md.md)]  
  
 Esta explicação passo a passo ilustra as seguintes tarefas:  
  
-   Criando um projeto de suplemento do VSTO do Word.  
  
-   Escrevendo código que usa o modelo de objeto do Word para adicionar texto a um documento quando ele for salvo.  
  
-   Criar e executar o projeto para testá-lo.  
  
-   A limpeza do projeto concluído para que o suplemento do VSTO não seja executado automaticamente no computador de desenvolvimento.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Você precisa dos seguintes componentes para concluir esta instrução passo a passo:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word  
  
## <a name="creating-the-project"></a>Criando o Projeto  
  
#### <a name="to-create-a-new-word-vsto-add-in-project-in-visual-studio"></a>Para criar um novo projeto de suplemento do VSTO Word no Visual Studio  
  
1.  Inicie o [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  No menu **Arquivo**, aponte para **Novo** e clique em **Projeto**.  
  
3.  No painel de modelos, expanda **Visual C#** ou **Visual Basic**e, em seguida, expanda **Office/SharePoint**.  
  
4.  Em expandidos **Office/SharePoint** nó, selecione o **suplementos do Office** nó.  
  
5.  Na lista de modelos de projeto, selecione um projeto de suplemento do VSTO do Word.  
  
6.  No **nome** , digite **FirstWordAddIn**.  
  
7.  Clique em **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]cria o **FirstWordAddIn** do projeto e abre o arquivo de código da classe ThisAddIn no editor.  
  
## <a name="writing-code-to-add-text-to-the-saved-document"></a>Escrevendo código para adicionar texto ao documento salvo  
 Em seguida, adicione código ao arquivo de código ThisAddIn. O novo código usa o modelo de objeto do Word para adicionar texto clichê para cada documento salvo. Por padrão, o arquivo de código da classe ThisAddIn contém o seguinte código gerado:  
  
-   Uma definição parcial do `ThisAddIn` classe. Essa classe fornece um ponto de entrada para o seu código e fornece acesso ao modelo de objeto do Word. Para obter mais informações, consulte [Programando suplementos do VSTO](../vsto/programming-vsto-add-ins.md). O restante do `ThisAddIn` classe é definida em um arquivo de código oculto que você não deve modificar.  
  
-   O `ThisAddIn_Startup` e `ThisAddIn_Shutdown` manipuladores de eventos. Esses manipuladores de eventos são chamados quando o Word carrega e descarrega o suplemento do VSTO. Use esses manipuladores de eventos para inicializar o suplemento do VSTO quando ele é carregado e para limpar os recursos usados pelo seu suplemento do VSTO quando ela é descarregada. Para obter mais informações, consulte [eventos em projetos do Office](../vsto/events-in-office-projects.md).  
  
#### <a name="to-add-a-paragraph-of-text-to-the-saved-document"></a>Para adicionar um parágrafo de texto para o documento salvo  
  
1.  No arquivo de código classe ThisAddIn, adicione o seguinte código para o `ThisAddIn` classe. O novo código define um manipulador de eventos para o <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> evento, que é gerado quando um documento é salvo.  
  
     Quando o usuário salva um documento, o manipulador de eventos adiciona novo texto no início do documento.  
  
     [!code-vb[Trin_WordAddInTutorial#1](../vsto/codesnippet/VisualBasic/FirstWordAddIn/ThisAddIn.vb#1)]
     [!code-csharp[Trin_WordAddInTutorial#1](../vsto/codesnippet/CSharp/FirstWordAddIn/ThisAddIn.cs#1)]  
  
    > [!NOTE]  
    >  Esse código usa um valor de índice de 1 para acessar o primeiro parágrafo de <xref:Microsoft.Office.Interop.Word._Document.Paragraphs%2A> coleção. Embora o Visual Basic e Visual c# usam conjuntos baseados em 0, os limites inferiores da matriz da maioria das coleções no modelo de objeto do Word é 1. Para obter mais informações, consulte [escrevendo código em soluções do Office](../vsto/writing-code-in-office-solutions.md).  
  
2.  Se você estiver usando c#, adicione o seguinte código necessário para o `ThisAddIn_Startup` manipulador de eventos. Esse código é usado para conectar-se a `Application_DocumentBeforeSave` manipulador de eventos com o <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> evento.  
  
     [!code-csharp[Trin_WordAddInTutorial#2](../vsto/codesnippet/CSharp/FirstWordAddIn/ThisAddIn.cs#2)]  
  
 Para modificar o documento quando ele for salvo, os exemplos de código anterior usam os seguintes objetos:  
  
-   O `Application` campo o `ThisAddIn` classe. O `Application` campo retorna um <xref:Microsoft.Office.Interop.Word.Application> objeto que representa a instância atual do Word.  
  
-   O `Doc` parâmetro do manipulador de eventos para o <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> evento. O `Doc` parâmetro é um <xref:Microsoft.Office.Interop.Word.Document> objeto que representa o documento salvo. Para obter mais informações, consulte [visão geral de modelo de objeto do Word](../vsto/word-object-model-overview.md).  
  
## <a name="testing-the-project"></a>O projeto de teste  
  
#### <a name="to-test-the-project"></a>Para testar o projeto  
  
1.  Pressione **F5** para compilar e executar seu projeto.  
  
     Quando você compila o projeto, o código é compilado em um assembly que está incluído na pasta de saída de compilação do projeto. O Visual Studio também cria um conjunto de entradas do registro que permitem que o Word descobrir e carregar o suplemento do VSTO, e ele define as configurações de segurança no computador de desenvolvimento para habilitar o suplemento do VSTO executar. Para obter mais informações, consulte [criando soluções do Office](../vsto/building-office-solutions.md).  
  
2.  No Word, salve o documento ativo.  
  
3.  Verifique se o texto a seguir é adicionado ao documento.  
  
     **Este texto foi adicionado por meio de código.**  
  
4.  Feche o Word.  
  
## <a name="cleaning-up-the-project"></a>O projeto de limpeza  
 Quando você terminar de desenvolvimento de um projeto, remova o suplemento do VSTO assembly, entradas do registro e as configurações de segurança do seu computador de desenvolvimento. Caso contrário, o suplemento do VSTO continuará a executar toda vez que você abra o Word no computador de desenvolvimento.  
  
#### <a name="to-clean-up-the-completed-project-on-your-development-computer"></a>Para limpar o projeto concluído no computador de desenvolvimento  
  
1.  No Visual Studio, no **criar** menu, clique em **limpar solução**.  
  
## <a name="next-steps"></a>Próximas etapas  
 Agora que você criou um Add-in básico do VSTO para Word, você pode aprender mais sobre como desenvolver um suplemento do VSTO com estes tópicos:  
  
-   Tarefas gerais de programação que você pode executar nos suplementos do VSTO: [Programando suplementos do VSTO](../vsto/programming-vsto-add-ins.md).  
  
-   Tarefas de programação que são específicas para suplementos VSTO Word: [soluções do Word](../vsto/word-solutions.md).  
  
-   Usando o modelo de objeto do Word: [visão geral de modelo de objeto do Word](../vsto/word-object-model-overview.md).  
  
-   Personalizando a interface do usuário do Word, por exemplo, por adicionar uma guia a faixa de opções ou criar seu próprio painel de tarefas personalizado: [personalização da interface do usuário do Office](../vsto/office-ui-customization.md).  
  
-   Compilando e depurando de suplementos do VSTO para Word: [criando soluções do Office](../vsto/building-office-solutions.md).  
  
-   Implantação de suplementos do VSTO para Word: [implantar uma solução Office](../vsto/deploying-an-office-solution.md).  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral sobre o desenvolvimento de soluções do Office &#40; VSTO &#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Soluções do Word](../vsto/word-solutions.md)   
 [Suplementos de programação para o VSTO](../vsto/programming-vsto-add-ins.md)   
 [Visão geral do modelo de objeto do Word](../vsto/word-object-model-overview.md)   
 [Personalização da interface do usuário do Office](../vsto/office-ui-customization.md)   
 [Criando soluções do Office](../vsto/building-office-solutions.md)   
 [Implantando uma solução do Office](../vsto/deploying-an-office-solution.md)   
 [Visão geral dos modelos do Office Project](../vsto/office-project-templates-overview.md)  
  
  