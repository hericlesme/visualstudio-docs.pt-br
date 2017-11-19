---
title: "Passo a passo: Coletando dados usando um formulário do Windows | Microsoft Docs"
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
- data [Office development in Visual Studio], Windows Forms
- Windows Forms [Office development in Visual Studio], collecting data
- forms [Office development in Visual Studio], walkthroughs
- worksheets [Office development in Visual Studio], collecting data
ms.assetid: 40e87f7f-cfbb-4761-bf1b-d042f45f4f09
caps.latest.revision: "54"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 32156e4d2c9e8e5f809a4de64478667e7133aeb1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-collecting-data-using-a-windows-form"></a>Instruções passo a passo: coletando dados usando um Windows Form
  Este passo a passo demonstra como abrir um formulário do Windows de uma personalização no nível do documento para o Microsoft Office Excel, coletar informações do usuário e gravar informações em uma célula de planilha.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Embora este passo a passo usa um projeto no nível do documento para Excel, especificamente, os conceitos demonstrados pelo passo a passo sejam aplicam a outros projetos do Office.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Você precisa dos seguintes componentes para concluir esta instrução passo a passo:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] ou [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
> [!NOTE]  
>  Seu computador pode mostrar diferentes nomes ou locais para alguns dos elementos de interface do usuário do Visual Studio nas instruções a seguir. A edição do Visual Studio que você possui e as configurações que você usa determinam esses elementos. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="creating-a-new-project"></a>Criando um novo projeto  
 A primeira etapa é criar um projeto de pasta de trabalho do Excel.  
  
#### <a name="to-create-a-new-project"></a>Para criar um novo projeto  
  
1.  Criar um projeto de pasta de trabalho do Excel com o nome **WinFormInput**e selecione **criar um novo documento** no assistente. Para obter mais informações, consulte [como: criar projetos do Office no Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio abre a nova pasta de trabalho do Excel no designer e adiciona o **WinFormInput** projeto **Gerenciador de soluções**.  
  
## <a name="adding-a-namedrange-control-to-the-worksheet"></a>Adicionar um controle NamedRange a planilha  
  
#### <a name="to-add-a-named-range-to-sheet1"></a>Para adicionar um intervalo nomeado para Sheet1  
  
1.  Selecione a célula **A1** em `Sheet1`.  
  
2.  No **nome** , digite **formInput**.  
  
     O **nome** caixa está localizada à esquerda da barra de fórmulas acima coluna **um** da planilha.  
  
3.  Pressione ENTER.  
  
     Um <xref:Microsoft.Office.Tools.Excel.NamedRange> controle é adicionado à célula **A1**. Não há nenhuma indicação visível na planilha, mas **formInput** aparece no **nome** caixa (logo acima da planilha no lado esquerdo) e no **propriedades** janela quando célula **A1** está selecionado.  
  
## <a name="adding-a-windows-form-to-the-project"></a>Adicionar um formulário do Windows para o projeto  
 Crie um formulário do Windows para solicitar informações do usuário.  
  
#### <a name="to-add-a-windows-form"></a>Para adicionar um formulário do Windows  
  
1.  Selecione o projeto **WinFormInput** na **Gerenciador de soluções**.  
  
2.  Sobre o **projeto** menu, clique em **Adicionar formulário do Windows**.  
  
3.  Nomeie o formulário **GetInputString.vb** ou **GetInputString.cs**e, em seguida, clique em **adicionar**.  
  
     O novo formulário é aberto no designer.  
  
4.  Adicionar um <xref:System.Windows.Forms.TextBox> e uma <xref:System.Windows.Forms.Button> ao formulário.  
  
5.  Selecione o botão, localize a propriedade **texto** no **propriedades** janela e altere o texto para **Okey**.  
  
 Em seguida, adicione código para `ThisWorkbook.vb` ou `ThisWorkbook.cs` para coletar as informações do usuário.  
  
## <a name="displaying-the-windows-form-and-collecting-information"></a>Exibindo o formulário do Windows e a coleta de informações  
 Criar uma instância do `GetInputString` formulário do Windows e exibi-lo e, em seguida, gravar as informações do usuário em uma célula na planilha.  
  
#### <a name="to-display-the-form-and-collect-information"></a>Para exibir o formulário e colete informações  
  
1.  Clique com botão direito **ThisWorkbook** ou **ThisWorkbook.cs** na **Solution Explorer**e, em seguida, clique em **Exibir código**.  
  
2.  No <xref:Microsoft.Office.Tools.Excel.Workbook.Open> manipulador de eventos do `ThisWorkbook`, adicione o seguinte código para declarar uma variável para o formulário `GetInputString` e, em seguida, exibir o formulário.  
  
    > [!NOTE]  
    >  Em c#, você deve adicionar um manipulador de eventos conforme o <xref:Microsoft.Office.Tools.Excel.Workbook.Startup> evento abaixo. Para obter informações sobre como criar manipuladores de eventos, consulte [como: criar manipuladores de eventos em projetos do Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreProgrammingCollectingData#1](../vsto/codesnippet/CSharp/WinFormInputCS/ThisWorkbook.cs#1)]
     [!code-vb[Trin_VstcoreProgrammingCollectingData#1](../vsto/codesnippet/VisualBasic/WinFormInput/ThisWorkbook.vb#1)]  
  
3.  Criar um método chamado `WriteStringToCell` que escreve o texto para um intervalo nomeado. Este método é chamado do formulário e a entrada do usuário é passada para o <xref:Microsoft.Office.Tools.Excel.NamedRange> controle, `formInput`, na célula **A1**.  
  
     [!code-csharp[Trin_VstcoreProgrammingCollectingData#2](../vsto/codesnippet/CSharp/WinFormInputCS/ThisWorkbook.cs#2)]
     [!code-vb[Trin_VstcoreProgrammingCollectingData#2](../vsto/codesnippet/VisualBasic/WinFormInput/ThisWorkbook.vb#2)]  
  
 Em seguida, adicione código ao formulário para lidar com o clique do botão eventos.  
  
## <a name="sending-information-to-the-worksheet"></a>Enviar informações à planilha  
  
#### <a name="to-send-information-to-the-worksheet"></a>Para enviar informações para a planilha  
  
1.  Clique com botão direito **GetInputString** na **Solution Explorer**e, em seguida, clique em **Designer de exibição**.  
  
2.  Clique duas vezes no botão para abrir o arquivo de código com o botão <xref:System.Windows.Forms.Control.Click> adicionado do manipulador de eventos.  
  
3.  Adicione código para o manipulador de eventos para obter a entrada da caixa de texto, enviá-lo para a função `WriteStringToCell`e, em seguida, feche o formulário.  
  
     [!code-csharp[Trin_VstcoreProgrammingCollectingData#3](../vsto/codesnippet/CSharp/WinFormInputCS/GetInputString.cs#3)]
     [!code-vb[Trin_VstcoreProgrammingCollectingData#3](../vsto/codesnippet/VisualBasic/WinFormInput/GetInputString.vb#3)]  
  
## <a name="testing"></a>Testes  
 Agora você pode executar o projeto. O formulário do Windows é exibida e a entrada aparece na planilha.  
  
#### <a name="to-test-your-workbook"></a>Para testar a sua pasta de trabalho  
  
1.  Pressione F5 para executar o projeto.  
  
2.  Confirme que o formulário do Windows é exibida.  
  
3.  Tipo **Hello World** na caixa de texto e depois clique em **Okey**.  
  
4.  Confirme se **Hello World** aparece na célula **A1** da planilha.  
  
## <a name="next-steps"></a>Próximas etapas  
 Este passo a passo mostra os fundamentos da exibição de um formulário do Windows e passando dados em uma planilha. Outras tarefas que você pode desejar executar:  
  
-   Use controles de formulários do Windows em uma pasta de trabalho do Excel ou um documento do Word. Para obter mais informações, consulte [controles dos Windows Forms na visão geral de documentos do Office](../vsto/windows-forms-controls-on-office-documents-overview.md).  
  
-   Modificar a interface do usuário de um aplicativo do Microsoft Office de uma personalização no nível do documento ou um suplemento do VSTO. Para obter mais informações, consulte [personalização da interface do usuário do Office](../vsto/office-ui-customization.md).  
  
## <a name="see-also"></a>Consulte também  
 [Desenvolvendo soluções do Office](../vsto/developing-office-solutions.md)   
 [Escrevendo código em soluções do Office](../vsto/writing-code-in-office-solutions.md)   
 [Suplementos de programação para o VSTO](../vsto/programming-vsto-add-ins.md)   
 [Personalizações no nível do documento da programação](../vsto/programming-document-level-customizations.md)   
 [Explicações passo a passo usando o Word](../vsto/walkthroughs-using-word.md)   
 [Instruções passo a passo para usar o Excel](../vsto/walkthroughs-using-excel.md)  
  
  