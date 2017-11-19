---
title: "Passo a passo: Alterando a formatação da planilha usando controles CheckBox | Microsoft Docs"
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
- worksheets, changing formatting using managed controls
- worksheets, check box controls
- controls [Office development in Visual Studio], adding to worksheets
ms.assetid: 4be79613-50a0-428e-9816-aadbc098272a
caps.latest.revision: "70"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7f10b0ed77dc9d5f97b6fc2fc4f218c86dafee41
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-changing-worksheet-formatting-using-checkbox-controls"></a>Instruções passo a passo: alterando a formatação da planilha usando controles CheckBox
  Este passo a passo mostra os fundamentos de como usar caixas de seleção em uma planilha do Microsoft Office Excel para alterar a formatação. Você usará ferramentas de desenvolvimento do Office no Visual Studio para criar e adicionar código ao seu projeto. Para ver o resultado como um exemplo completo, consulte o exemplo de controles do Excel em [amostras de desenvolvimento do Office e explicações passo a passo](../vsto/office-development-samples-and-walkthroughs.md).  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Durante este passo a passo, você aprenderá a:  
  
-   Adicione texto e controles a uma planilha.  
  
-   Formate o texto quando uma opção é selecionada.  
  
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
  
1.  Criar um projeto de pasta de trabalho do Excel com o nome **formatação do Excel meu**. Verifique se **criar um novo documento** está selecionado. Para obter mais informações, consulte [como: criar projetos do Office no Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio abre a nova pasta de trabalho do Excel no designer e adiciona o **formatação do Excel Meus** projeto **Gerenciador de soluções**.  
  
## <a name="adding-text-and-controls-to-the-worksheet"></a>Adicionando texto e controles à planilha  
 Para este passo a passo, você precisará de três <xref:Microsoft.Office.Tools.Excel.Controls.CheckBox> controles e texto em uma <xref:Microsoft.Office.Tools.Excel.NamedRange> controle.  
  
#### <a name="to-add-three-check-boxes"></a>Para adicionar três caixas de seleção  
  
1.  Verifique se a pasta de trabalho é aberta no designer do Visual Studio e que `Sheet1` está aberto.  
  
2.  Do **controles comuns** guia do **caixa de ferramentas**, arraste um <xref:Microsoft.Office.Tools.Excel.Controls.CheckBox> controle para ou próximo a célula **B2** na **Planilha1**.  
  
3.  Do **exibição** menu, selecione **propriedades** janela.  
  
4.  Certifique-se de que **Checkbox1** está visível na caixa de listagem de nome do objeto do **propriedades** janela e alterar as seguintes propriedades:  
  
    |Propriedade|Valor|  
    |--------------|-----------|  
    |**Nome**|**applyBoldFont**|  
    |**Texto**|**Negrito**|  
  
5.  Arraste uma segunda caixa de seleção em ou próximo a célula **B4** e alterar as seguintes propriedades:  
  
    |Propriedade|Valor|  
    |--------------|-----------|  
    |**Nome**|**applyItalicFont**|  
    |**Texto**|**Itálico**|  
  
6.  Arraste uma caixa de seleção terceira sobre ou próximo a célula **B6** e alterar as seguintes propriedades:  
  
    |Propriedade|Valor|  
    |--------------|-----------|  
    |**Nome**|**applyUnderlineFont**|  
    |**Texto**|**Sublinhado**|  
  
7.  Selecione todos os controles de caixa de seleção três mantendo a tecla CTRL.  
  
8.  No grupo Organizar da guia formato no Excel, clique em **alinhar**e, em seguida, clique em **Alinhar à esquerda**.  
  
     Os controles de caixa de seleção três são alinhados à esquerda, na posição do primeiro controle selecionado.  
  
     Você será, em seguida, arraste um <xref:Microsoft.Office.Tools.Excel.NamedRange> controle à planilha.  
  
    > [!NOTE]  
    >  Você também pode adicionar o <xref:Microsoft.Office.Tools.Excel.NamedRange> controle digitando **textFont** para o **nome** caixa.  
  
#### <a name="to-add-text-to-a-namedrange-control"></a>Para adicionar texto a um controle NamedRange  
  
1.  Do **Excel controles** guia da caixa de ferramentas, arraste um <xref:Microsoft.Office.Tools.Excel.NamedRange> controle a célula **B9**.  
  
2.  Verifique **$B$ 9** aparece na caixa de texto editável e que a célula **B9** está selecionado. Se não estiver, clique na célula **B9** para selecioná-la.  
  
3.  Clique em **OK**.  
  
4.  Célula **B9** torna-se um intervalo nomeado `NamedRange1`.  
  
     Não há nenhuma indicação visível na planilha, mas `NamedRange1` aparece no **caixa nome** (logo acima da planilha no lado esquerdo) quando a célula **B9** está selecionado.  
  
5.  Certifique-se de que **NamedRange1** está visível na caixa de listagem de nome do objeto do **propriedades** janela e alterar as seguintes propriedades:  
  
    |Propriedade|Valor|  
    |--------------|-----------|  
    |**Nome**|**textFont**|  
    |**Value2**|**Clique em uma caixa de seleção para alterar a formatação de texto.**|  
  
 Em seguida, escreva o código para formatar o texto quando uma opção é selecionada.  
  
## <a name="formatting-the-text-when-an-option-is-selected"></a>O texto quando um a opção de formatação está selecionada  
 Nesta seção, você escreverá código para que quando o usuário seleciona uma opção de formatação, o formato do texto na planilha é alterado.  
  
#### <a name="to-change-formatting-when-a-check-box-is-selected"></a>Para alterar a formatação quando uma caixa de seleção está selecionada  
  
1.  Clique com botão direito **Planilha1**e, em seguida, clique em **Exibir código** no menu de atalho.  
  
2.  Adicione o seguinte código para o <xref:System.Windows.Forms.Control.Click> manipulador de eventos do `applyBoldFont` caixa de seleção:  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#7](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#7)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#7](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#7)]  
  
3.  Adicione o seguinte código para o <xref:System.Windows.Forms.Control.Click> manipulador de eventos do `applyItalicFont` caixa de seleção:  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#8](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#8)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#8](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#8)]  
  
4.  Adicione o seguinte código para o <xref:System.Windows.Forms.Control.Click> manipulador de eventos do `applyUnderlineFont` caixa de seleção:  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#9](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#9)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#9)]  
  
5.  Em c#, você deve adicionar manipuladores de eventos para as caixas de seleção para o <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> evento conforme mostrado abaixo. Para obter informações sobre como criar manipuladores de eventos, consulte [como: criar manipuladores de eventos em projetos do Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#10)]  
  
## <a name="testing-the-application"></a>Testando o aplicativo  
 Agora você pode testar sua pasta de trabalho para certificar-se de que o texto está formatado corretamente quando você marca ou desmarca uma caixa de seleção.  
  
#### <a name="to-test-your-workbook"></a>Para testar a sua pasta de trabalho  
  
1.  Pressione F5 para executar o projeto.  
  
2.  Marque ou desmarque uma caixa de seleção.  
  
3.  Confirme que o texto está formatado corretamente.  
  
## <a name="next-steps"></a>Próximas etapas  
 Este passo a passo mostra os fundamentos de como usar caixas de seleção e formatação de texto em planilhas do Excel. Estas são algumas tarefas que podem vir a seguir:  
  
-   Implantar o projeto. Para obter mais informações, consulte [implantar uma solução Office pelo ClickOnce usando](../vsto/deploying-an-office-solution-by-using-clickonce.md).  
  
-   Usar um botão para preencher uma caixa de texto. Para obter mais informações, consulte [passo a passo: exibindo texto em uma caixa de texto em uma planilha usando um botão](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md).  
  
## <a name="see-also"></a>Consulte também  
 [Explicações passo a passo usando o Excel](../vsto/walkthroughs-using-excel.md)   
 [Controle NamedRange](../vsto/namedrange-control.md)   
 [Limitações de controles do Windows Forms em documentos do Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  
  