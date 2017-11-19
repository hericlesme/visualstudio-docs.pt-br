---
title: "Passo a passo: Exibindo texto em uma caixa de texto em uma planilha usando um botão | Microsoft Docs"
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
- text [Office development in Visual Studio], displaying worksheets
- worksheets, displaying text
- text boxes, displaying text in worksheets
- text [Office development in Visual Studio], text boxes
ms.assetid: 59b73159-aab7-4f61-9ace-1723c18d78d6
caps.latest.revision: "56"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1b95eb6eeb5f8615f8f471ad33139afa49d5633f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button"></a>Instruções passo a passo: exibindo texto em uma caixa de texto em uma planilha usando um botão
  Este passo a passo mostra os fundamentos de como usar os botões e caixas de texto em planilhas do Microsoft Office Excel e como criar projetos do Excel usando ferramentas de desenvolvimento do Office no Visual Studio. Para ver o resultado como um exemplo completo, consulte o exemplo de controles do Excel em [amostras de desenvolvimento do Office e explicações passo a passo](../vsto/office-development-samples-and-walkthroughs.md).  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Durante este passo a passo, você aprenderá a:  
  
-   Adicione controles a uma planilha.  
  
-   Preencha uma caixa de texto quando um botão é clicado.  
  
-   Seu projeto de teste.  
  
> [!NOTE]  
>  Seu computador pode mostrar diferentes nomes ou locais para alguns dos elementos de interface do usuário do Visual Studio nas instruções a seguir. A edição do Visual Studio que você possui e as configurações que você usa determinam esses elementos. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Você precisa dos seguintes componentes para concluir esta instrução passo a passo:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] ou [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
## <a name="creating-the-project"></a>Criando o Projeto  
 Nesta etapa, você criará um projeto de pasta de trabalho do Excel usando o Visual Studio.  
  
#### <a name="to-create-a-new-project"></a>Para criar um novo projeto  
  
1.  Criar um projeto de pasta de trabalho do Excel com o nome **meu botão do Excel**. Verifique se **criar um novo documento** está selecionado. Para obter mais informações, consulte [como: criar projetos do Office no Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio abre a nova pasta de trabalho do Excel no designer e adiciona o **meu botão do Excel** projeto **Gerenciador de soluções**.  
  
## <a name="adding-controls-to-the-worksheet"></a>Adicionando controles a planilha  
 Para este passo a passo, você precisará de um botão e uma caixa de texto na primeira planilha.  
  
#### <a name="to-add-a-button-and-a-text-box"></a>Para adicionar um botão e uma caixa de texto  
  
1.  Verifique o **Button.xlsx de Excel Meus** pasta de trabalho é aberta no designer do Visual Studio, com `Sheet1` exibida.  
  
2.  Do **controles comuns** guia da caixa de ferramentas, arraste um <xref:Microsoft.Office.Tools.Excel.Controls.TextBox> para `Sheet1`.  
  
3.  Do **exibição** menu, selecione **janela propriedades**.  
  
4.  Certifique-se de que **TextBox1** está visível no **propriedades** caixa de lista suspensa da janela e altere o **nome** propriedade da caixa de texto para **texto exibido**.  
  
5.  Arraste um **botão** controle para `Sheet1` e altere as propriedades a seguir:  
  
    |Propriedade|Valor|  
    |--------------|-----------|  
    |**Nome**|**insertText**|  
    |**Texto**|**Inserir texto**|  
  
 Agora, escreva o código para ser executado quando o botão é clicado.  
  
## <a name="populating-the-text-box-when-the-button-is-clicked"></a>Preenchendo a caixa de texto quando o botão é clicado  
 Cada vez que o usuário clica no botão **Olá, mundo!** é anexado à caixa de texto.  
  
#### <a name="to-write-to-the-text-box-when-the-button-is-clicked"></a>Para gravar na caixa de texto quando o botão é clicado  
  
1.  Em **Solution Explorer**, clique com botão direito **Planilha1**e, em seguida, clique em **Exibir código** no menu de atalho.  
  
2.  Adicione o seguinte código para o <xref:System.Windows.Forms.Control.Click> manipulador de eventos do botão:  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#11](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#11)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#11](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#11)]  
  
3.  Em c#, você deve adicionar um manipulador de eventos para o <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> evento conforme mostrado abaixo. Para obter informações sobre como criar manipuladores de eventos, consulte [como: criar manipuladores de eventos em projetos do Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#12](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#12)]  
  
## <a name="testing-the-application"></a>Testando o aplicativo  
 Agora você pode testar sua pasta de trabalho para certificar-se de que a mensagem **Olá, mundo!** aparece na caixa de texto quando você clicar no botão.  
  
#### <a name="to-test-your-workbook"></a>Para testar a sua pasta de trabalho  
  
1.  Pressione F5 para executar o projeto.  
  
2.  Clique no botão.  
  
3.  Confirme se **Hello World!** é exibida na caixa de texto.  
  
## <a name="next-steps"></a>Próximas etapas  
 Este passo a passo mostra os fundamentos de como usar os botões e caixas de texto em planilhas do Excel. Estas são algumas tarefas que podem vir a seguir:  
  
-   Implantar o projeto. Para obter mais informações, consulte [implantar uma solução Office](../vsto/deploying-an-office-solution.md).  
  
-   Usando as caixas de seleção para alterar a formatação. Para obter mais informações, consulte [passo a passo: alterando planilha formatação usando controles CheckBox](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md).  
  
## <a name="see-also"></a>Consulte também  
 [Como: adicionar controles a documentos do Office do Windows Forms](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [Explicações passo a passo usando o Excel](../vsto/walkthroughs-using-excel.md)   
 [Limitações de controles do Windows Forms em documentos do Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  
  