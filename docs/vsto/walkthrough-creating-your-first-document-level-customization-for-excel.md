---
title: "Passo a passo: Criando a primeira personalização no nível do documento para Excel | Microsoft Docs"
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
- Office development in Visual Studio, creating your first project
- Excel [Office development in Visual Studio], creating your first project
- document-level customizations [Office development in Visual Studio], creating your first project
ms.assetid: 785d3b86-5ed5-4e0d-b5ee-896b6b1330ac
caps.latest.revision: "28"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 93b9fdad9fc0224c34835457f76140a0df5612b9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-creating-your-first-document-level-customization-for-excel"></a>Instruções passo a passo: criando a primeira personalização no nível do documento para Excel
  Este passo a passo introdutório mostra como criar uma personalização no nível do documento para o Microsoft Office Excel. Os recursos que você criar este tipo de solução estão disponíveis somente quando uma determinada pasta de trabalho é aberta. Você não pode usar uma personalização no nível do documento para fazer alterações no nível de aplicativo, por exemplo, exibindo uma nova guia de faixa de opções quando qualquer pasta de trabalho é aberta.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Esta explicação passo a passo ilustra as seguintes tarefas:  
  
-   Criando um projeto de pasta de trabalho do Excel.  
  
-   Adicionando texto em uma planilha que está hospedada no designer do Visual Studio.  
  
-   Escrevendo código que usa o modelo de objeto do Excel para adicionar texto à planilha personalizada quando ele é aberto.  
  
-   Criar e executar o projeto para testá-lo.  
  
-   A limpeza do projeto concluído para remover arquivos de compilação desnecessários e configurações de segurança de seu computador de desenvolvimento.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Você precisa dos seguintes componentes para concluir esta instrução passo a passo:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] ou [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
## <a name="creating-the-project"></a>Criando o Projeto  
  
#### <a name="to-create-a-new-excel-workbook-project-in-visual-studio"></a>Para criar um novo projeto de pasta de trabalho do Excel no Visual Studio  
  
1.  Inicie o [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  No menu **Arquivo**, aponte para **Novo** e clique em **Projeto**.  
  
3.  No painel de modelos, expanda **Visual C#** ou **Visual Basic**e, em seguida, expanda **Office/SharePoint**.  
  
4.  Em expandidos **Office/SharePoint** nó, selecione o **suplementos do Office** nó.  
  
5.  Na lista de modelos de projeto, escolha um projeto de suplemento do VSTO do Excel.  
  
6.  No **nome** , digite **FirstWorkbookCustomization**.  
  
7.  Clique em **OK**.  
  
     O **Visual Studio Tools para Office Project Wizard** é aberto.  
  
8.  Selecione **criar um novo documento**e clique em **Okey**.  
  
    -   [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]cria o **FirstWorkbookCustomization** do projeto e adiciona os seguintes arquivos ao projeto.  
  
    -   *FirstWorkbookCustomization*. xlsx - representa a pasta de trabalho do Excel no projeto. Contém todas as planilhas e gráficos.  
  
    -   Planilha1 (arquivo. vb para o arquivo. cs para Visual c# ou Visual Basic) - uma planilha que fornece a superfície de design e o código para a primeira planilha na pasta de trabalho. Para obter mais informações, consulte [Item de Host de planilha](../vsto/worksheet-host-item.md).  
  
    -   Planilha2 (arquivo. vb para o arquivo. cs para Visual c# ou Visual Basic) - uma planilha que fornece a superfície de design e o código para a segunda planilha na pasta de trabalho.  
  
    -   Sheet3 (arquivo. vb para o arquivo. cs para Visual c# ou Visual Basic) - uma planilha que fornece a superfície de design e o código para a terceira planilha na pasta de trabalho.  
  
    -   ThisWorkbook (arquivo. vb para o Visual Basic) ou arquivo. cs para Visual c# - contém a superfície de design e o código para personalizações no nível de pasta de trabalho. Para obter mais informações, consulte [Item de Host de pasta de trabalho](../vsto/workbook-host-item.md).  
  
     O arquivo de código Planilha1 é aberto automaticamente no designer.  
  
## <a name="closing-and-reopening-worksheets-in-the-designer"></a>Fechar e reabrir planilhas no Designer  
 Se você deliberadamente ou acidentalmente fechar uma pasta de trabalho ou em uma planilha no designer enquanto você estiver desenvolvendo seu projeto, você poderá reabri-lo.  
  
#### <a name="to-close-and-reopen-a-worksheet-in-the-designer"></a>Fechar e reabrir uma planilha no designer  
  
1.  Feche a pasta de trabalho clicando o **fechar** botão (X) para a janela do designer.  
  
2.  Em **Solution Explorer**, com o botão direito do **Planilha1** arquivo de código e, em seguida, clique em **Designer de exibição**.  
  
     \- ou -  
  
     Em **Solution Explorer**, clique duas vezes o **Planilha1** arquivo de código.  
  
## <a name="adding-text-to-a-worksheet-in-the-designer"></a>Adicionando texto em uma planilha no Designer  
 Você pode criar a interface do usuário (UI) de sua personalização modificando a planilha que está aberta no designer. Por exemplo, adicionar texto às células, aplicar fórmulas ou adicionar controles do Excel. Para obter mais informações sobre como usar o designer, consulte [projetos do Office no ambiente do Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).  
  
#### <a name="to-add-text-to-a-worksheet-by-using-the-designer"></a>Para adicionar texto a uma planilha usando o designer  
  
1.  Na planilha que está aberta no designer, selecione a célula **A1**e, em seguida, digite o texto a seguir.  
  
     **Este texto foi adicionado usando o designer.**  
  
> [!WARNING]  
>  Se você adicionar essa linha de texto para a célula **A2**, ele será substituído por outro código neste exemplo.  
  
## <a name="adding-text-to-a-worksheet-programmatically"></a>Adicionando texto em uma planilha programaticamente  
 Em seguida, adicione código ao arquivo de código Planilha1. O novo código usa o modelo de objeto do Excel para adicionar uma segunda linha de texto para a pasta de trabalho. Por padrão, o arquivo de código Sheet1 contém o seguinte código gerado:  
  
-   Uma definição parcial do `Sheet1` classe que representa o modelo de programação da planilha e fornece acesso ao modelo de objeto do Excel. Para obter mais informações, [Item de Host de planilha](../vsto/worksheet-host-item.md) e [visão geral de modelo de objeto do Word](../vsto/word-object-model-overview.md). O restante do `Sheet1` classe é definida em um arquivo de código oculto que você não deve modificar.  
  
-   O `Sheet1_Startup` e `Sheet1_Shutdown` manipuladores de eventos. Esses manipuladores de eventos são chamados quando o Excel carrega e descarrega a personalização. Use esses manipuladores de eventos para inicializar a personalização quando ele é carregado e para limpar os recursos usados pela sua personalização quando ela é descarregada. Para obter mais informações, consulte [eventos em projetos do Office](../vsto/events-in-office-projects.md).  
  
#### <a name="to-add-a-second-line-of-text-to-the-worksheet-by-using-code"></a>Para adicionar uma segunda linha de texto à planilha usando código  
  
1.  Em **Solution Explorer**, clique com botão direito **Planilha1**e, em seguida, clique em **Exibir código**.  
  
     O arquivo de código é aberto no Visual Studio.  
  
2.  Substitua o `Sheet1_Startup` manipulador de eventos com o código a seguir. Quando Sheet1 é aberto, esse código adiciona uma segunda linha de texto à planilha.  
  
     [!code-csharp[Trin_ExcelWorkbookTutorial#1](../vsto/codesnippet/CSharp/Trin_ExcelWorkbookTutorial/Sheet1.cs#1)]
     [!code-vb[Trin_ExcelWorkbookTutorial#1](../vsto/codesnippet/VisualBasic/Trin_ExcelWorkbookTutorial/Sheet1.vb#1)]  
  
## <a name="testing-the-project"></a>O projeto de teste  
  
#### <a name="to-test-your-workbook"></a>Para testar a sua pasta de trabalho  
  
1.  Pressione **F5** para compilar e executar seu projeto.  
  
     Quando você compila o projeto, o código é compilado em um assembly que está associado com a pasta de trabalho. O Visual Studio coloca uma cópia da pasta de trabalho e o assembly na pasta de saída de compilação do projeto, e ele configura as configurações de segurança no computador de desenvolvimento para habilitar a personalização executar. Para obter mais informações, consulte [criando soluções do Office](../vsto/building-office-solutions.md).  
  
2.  Na pasta de trabalho, verifique se que você vê o seguinte texto.  
  
     **Este texto foi adicionado usando o designer.**  
  
     **Este texto foi adicionado por meio de código.**  
  
3.  Feche a pasta de trabalho.  
  
## <a name="cleaning-up-the-project"></a>O projeto de limpeza  
 Quando você terminar de desenvolvimento de um projeto, você deve remover os arquivos na pasta de saída de compilação e as configurações de segurança criadas pelo processo de compilação.  
  
#### <a name="to-clean-up-the-completed-project-on-your-development-computer"></a>Para limpar o projeto concluído no computador de desenvolvimento  
  
1.  No Visual Studio, no **criar** menu, clique em **limpar solução**.  
  
## <a name="next-steps"></a>Próximas etapas  
 Agora que você criou uma personalização básica de nível de documento para Excel, você pode aprender mais sobre como desenvolver personalizações destes tópicos:  
  
-   Tarefas gerais de programação que você pode executar em personalizações no nível do documento: [personalizações de programação de nível de documento](../vsto/programming-document-level-customizations.md).  
  
-   Tarefas de programação que são específicas para personalizações no nível de documento para Excel: [soluções do Excel](../vsto/excel-solutions.md).  
  
-   Usando o modelo de objeto do Excel: [visão geral do modelo de objeto do Excel](../vsto/excel-object-model-overview.md).  
  
-   Personalizando a interface do usuário do Excel, por exemplo, por adicionar uma guia a faixa de opções ou criar seu próprio painel de ações: [personalização da interface do usuário do Office](../vsto/office-ui-customization.md).  
  
-   Usando objetos estendidos do Excel fornecidos pelas ferramentas de desenvolvimento do Office no Visual Studio para executar tarefas que não são possíveis por meio do modelo de objeto do Excel (por exemplo, hospedagem de controles gerenciados em documentos e associando controles do Excel a dados usando o Windows Forms modelo de associação de dados): [automatizando o Excel usando objetos estendidos](../vsto/automating-excel-by-using-extended-objects.md).  
  
-   Compilar e depurar personalizações no nível de documento para Excel: [criando soluções do Office](../vsto/building-office-solutions.md).  
  
-   Implantando as personalizações no nível de documento para Excel: [implantar uma solução Office](../vsto/deploying-an-office-solution.md).  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral sobre o desenvolvimento de soluções do Office &#40; VSTO &#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Soluções do Excel](../vsto/excel-solutions.md)   
 [Personalizações no nível do documento da programação](../vsto/programming-document-level-customizations.md)   
 [Visão geral do modelo de objeto do Excel](../vsto/excel-object-model-overview.md)   
 [Automatizando o Excel usando objetos estendidos](../vsto/automating-excel-by-using-extended-objects.md)   
 [Personalização da interface do usuário do Office](../vsto/office-ui-customization.md)   
 [Criando soluções do Office](../vsto/building-office-solutions.md)   
 [Implantando uma solução do Office](../vsto/deploying-an-office-solution.md)   
 [Visão geral dos modelos do Office Project](../vsto/office-project-templates-overview.md)  
  
  