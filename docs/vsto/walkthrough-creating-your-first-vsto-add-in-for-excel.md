---
title: 'Passo a passo: Criando seu primeiro suplemento VSTO para Excel | Microsoft Docs'
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
- Excel [Office development in Visual Studio], creating your first project
ms.assetid: a855e2be-3ecf-4112-a7f5-ec0f7fad3b5f
caps.latest.revision: "33"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3d22d5b80186bf3117980cd8059ac9431bac5522
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-creating-your-first-vsto-add-in-for-excel"></a>Passo a passo: criando o primeiro suplemento do VSTO para Excel
  Este passo a passo introdutório mostra como criar um suplemento de nível de aplicativo para o Microsoft Office Excel. Os recursos que você criar este tipo de solução estão disponíveis para o aplicativo em si, independentemente de quais pastas de trabalho estão abertas.  
  
 [!INCLUDE[appliesto_xlallapp](../vsto/includes/appliesto-xlallapp-md.md)]  
  
 Esta explicação passo a passo ilustra as seguintes tarefas:  
  
-   Criando um projeto de suplemento do Excel VSTO para Excel.  
  
-   Escrevendo código que usa o modelo de objeto do Excel para adicionar texto a uma pasta de trabalho quando ele for salvo.  
  
-   Criar e executar o projeto para testá-lo.  
  
-   A limpeza do projeto concluído para que o suplemento do VSTO não seja executado automaticamente no computador de desenvolvimento.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Você precisa dos seguintes componentes para concluir esta instrução passo a passo:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] ou [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
## <a name="creating-the-project"></a>Criando o Projeto  
  
#### <a name="to-create-a-new-excel-vsto-add-in-project-in-visual-studio"></a>Para criar um novo projeto de suplemento do VSTO do Excel no Visual Studio  
  
1.  Inicie o [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  No menu **Arquivo**, aponte para **Novo** e clique em **Projeto**.  
  
3.  No painel de modelos, expanda **Visual C#** ou **Visual Basic**e, em seguida, expanda **Office/SharePoint**.  
  
4.  Em expandidos **Office/SharePoint** nó, selecione o **suplementos do Office** nó.  
  
5.  Na lista de modelos de projeto, selecione **suplemento do Excel 2010** ou **suplemento do Excel 2013**.  
  
6.  No **nome** , digite **FirstExcelAddIn**.  
  
7.  Clique em **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]cria o **FirstExcelAddIn** do projeto e abre o arquivo de código da classe ThisAddIn no editor.  
  
## <a name="writing-code-to-add-text-to-the-saved-workbook"></a>Escrevendo código para adicionar texto para a pasta de trabalho salva  
 Em seguida, adicione código ao arquivo de código ThisAddIn. O novo código usa o modelo de objeto do Excel para inserir texto clichê na primeira linha da planilha ativa. A planilha ativa é a planilha é aberta quando o usuário salva a pasta de trabalho. Por padrão, o arquivo de código da classe ThisAddIn contém o seguinte código gerado:  
  
-   Uma definição parcial do `ThisAddIn` classe. Essa classe fornece um ponto de entrada para o seu código e fornece acesso ao modelo de objeto do Excel. Para obter mais informações, consulte [Programando suplementos do VSTO](../vsto/programming-vsto-add-ins.md). O restante do `ThisAddIn` classe é definida em um arquivo de código oculto que você não deve modificar.  
  
-   O `ThisAddIn_Startup` e `ThisAddIn_Shutdown` manipuladores de eventos. Esses manipuladores de eventos são chamados quando o Excel carrega e descarrega o suplemento do VSTO. Use esses manipuladores de eventos para inicializar o suplemento do VSTO quando ele é carregado e para limpar os recursos usados pelo seu suplemento quando ele é descarregado. Para obter mais informações, consulte [eventos em projetos do Office](../vsto/events-in-office-projects.md).  
  
#### <a name="to-add-a-line-of-text-to-the-saved-workbook"></a>Para adicionar uma linha de texto para a pasta de trabalho salva  
  
1.  No arquivo de código classe ThisAddIn, adicione o seguinte código para o `ThisAddIn` classe. O novo código define um manipulador de eventos para o <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave> evento, que é gerado quando uma pasta de trabalho é salvo.  
  
     Quando o usuário salva uma pasta de trabalho, o manipulador de eventos adiciona novo texto no início da planilha ativa.  
  
     [!code-vb[Trin_ExcelAddInTutorial#1](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInTutorial/ThisAddIn.vb#1)]
     [!code-csharp[Trin_ExcelAddInTutorial#1](../vsto/codesnippet/CSharp/Trin_ExcelAddInTutorial/ThisAddIn.cs#1)]  
  
2.  Se você estiver usando c#, adicione o seguinte código necessário para o `ThisAddIn_Startup` manipulador de eventos. Esse código é usado para conectar-se a `Application_WorkbookBeforeSave` manipulador de eventos com o <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave> evento.  
  
     [!code-csharp[Trin_ExcelAddInTutorial#2](../vsto/codesnippet/CSharp/Trin_ExcelAddInTutorial/ThisAddIn.cs#2)]  
  
 Para modificar a pasta de trabalho quando ele for salvo, os exemplos de código anterior usam os seguintes objetos:  
  
-   O `Application` campo o `ThisAddIn` classe. O `Application` campo retorna um <xref:Microsoft.Office.Interop.Excel.Application> objeto que representa a instância atual do Excel.  
  
-   O `Wb` parâmetro do manipulador de eventos para o <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave> evento. O `Wb` parâmetro é um <xref:Microsoft.Office.Interop.Excel.Workbook> objeto que representa a pasta de trabalho salva. Para obter mais informações, consulte [visão geral do modelo de objeto do Excel](../vsto/excel-object-model-overview.md).  
  
## <a name="testing-the-project"></a>O projeto de teste  
  
#### <a name="to-test-the-project"></a>Para testar o projeto  
  
1.  Pressione **F5** para compilar e executar seu projeto.  
  
     Quando você compila o projeto, o código é compilado em um assembly que está incluído na pasta de saída de compilação do projeto. O Visual Studio também cria um conjunto de entradas do registro que permitem que o Excel descobrir e carregar o suplemento do VSTO, e ele define as configurações de segurança no computador de desenvolvimento para habilitar o suplemento do VSTO executar. Para obter mais informações, consulte [criando soluções do Office](../vsto/building-office-solutions.md).  
  
2.  No Excel, salve a pasta de trabalho.  
  
3.  Verifique se o texto a seguir é adicionado à pasta de trabalho.  
  
     **Este texto foi adicionado por meio de código.**  
  
4.  Feche o Excel.  
  
## <a name="cleaning-up-the-project"></a>O projeto de limpeza  
 Quando você terminar de desenvolvimento de um projeto, remova o suplemento do VSTO assembly, entradas do registro e as configurações de segurança do seu computador de desenvolvimento. Caso contrário, o suplemento do VSTO continuará a executar toda vez que você abrir o Excel no computador de desenvolvimento.  
  
#### <a name="to-clean-up-the-completed-project-on-your-development-computer"></a>Para limpar o projeto concluído no computador de desenvolvimento  
  
1.  No Visual Studio, no **criar** menu, clique em **limpar solução**.  
  
## <a name="next-steps"></a>Próximas etapas  
 Agora que você criou um básico do VSTO suplemento para Excel, você pode aprender mais sobre como desenvolver um suplemento do VSTO com estes tópicos:  
  
-   Tarefas gerais de programação que você pode executar nos suplementos do VSTO: [Programando suplementos do VSTO](../vsto/programming-vsto-add-ins.md).  
  
-   Tarefas de programação que são específicas para suplementos VSTO do Excel: [soluções do Excel](../vsto/excel-solutions.md).  
  
-   Usando o modelo de objeto do Excel: [visão geral do modelo de objeto do Excel](../vsto/excel-object-model-overview.md).  
  
-   Personalizando a interface do usuário (IU) do Excel, por exemplo, por adicionar uma guia a faixa de opções ou criar seu próprio painel de tarefas personalizado: [personalização da interface do usuário do Office](../vsto/office-ui-customization.md).  
  
-   Compilando e depurando de suplementos do VSTO para Excel: [criando soluções do Office](../vsto/building-office-solutions.md).  
  
-   Implantação de suplementos do VSTO para Excel: [implantar uma solução Office](../vsto/deploying-an-office-solution.md).  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral sobre o desenvolvimento de soluções do Office &#40; VSTO &#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Soluções do Excel](../vsto/excel-solutions.md)   
 [Suplementos de programação para o VSTO](../vsto/programming-vsto-add-ins.md)   
 [Visão geral do modelo de objeto do Excel](../vsto/excel-object-model-overview.md)   
 [Personalização da interface do usuário do Office](../vsto/office-ui-customization.md)   
 [Criando soluções do Office](../vsto/building-office-solutions.md)   
 [Implantando uma solução do Office](../vsto/deploying-an-office-solution.md)   
 [Visão geral dos modelos do Office Project](../vsto/office-project-templates-overview.md)  
  
  