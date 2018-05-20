---
title: 'Passo a passo: Alterar a formatação do documento usando controles CheckBox'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word documents, changing formatting using controls
- documents [Office development in Visual Studio], formatting
- check boxes, Word documents
- documents [Office development in Visual Studio], check box controls
- controls [Office development in Visual Studio], adding to documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 459253c6a84add4fcca68565d5bf082dc0931f22
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
---
# <a name="walkthrough-change-document-formatting-using-checkbox-controls"></a>Passo a passo: Alterar a formatação do documento usando controles CheckBox
  Este passo a passo demonstra como usar controles de formulários do Windows em uma personalização no nível do documento para o Microsoft Office Word para alterar a formatação de texto.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Esta explicação passo a passo ilustra as seguintes tarefas:  
  
-   Adicionando texto e o controle para o documento em um projeto no nível do documento em tempo de design.  
  
-   Formatando o texto quando uma opção é selecionada.  
  
 Para ver o resultado como um exemplo completo, consulte o exemplo de controles do Word em [amostras de desenvolvimento do Office e explicações passo a passo](../vsto/office-development-samples-and-walkthroughs.md).  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Você precisa dos seguintes componentes para concluir esta instrução passo a passo:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] ou [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].  
  
## <a name="create-the-project"></a>Criar o projeto  
 A primeira etapa é criar um projeto de Documento do Word.  
  
### <a name="create-a-new-project"></a>Criar um novo projeto  
  
1.  Criar um projeto de documento do Word com o nome **formatação do Word meu**. No assistente, selecione **criar um novo documento**.  
  
     Para obter mais informações, consulte [como: projetos do Office criar no Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio abre o novo documento do Word no designer e adiciona o **formatação do Word Meus** projeto **Gerenciador de soluções**.  
  
## <a name="add-text-and-controls-to-the-word-document"></a>Adicionar texto e controles para o documento do Word  
 Para este passo a passo, adicione três caixas de seleção e algum texto em uma <xref:Microsoft.Office.Tools.Word.Bookmark> controle para o documento do Word. As caixas de seleção apresentará opções para o usuário para a formatação de texto.  
  
### <a name="add-three-check-boxes"></a>Adicionar três caixas de seleção  
  
1.  Verifique se o documento é aberto no designer do Visual Studio.  
  
2.  Do **controles comuns** guia do **caixa de ferramentas**, arraste a primeira <xref:Microsoft.Office.Tools.Word.Controls.CheckBox> controle o documento.  
  
3.  No **propriedades** janela, altere as propriedades a seguir.  
  
    |Propriedade|Valor|  
    |--------------|-----------|  
    |**Nome**|**applyBoldFont**|  
    |**Texto**|**Negrito**|  
  
4.  Pressione **Enter** para mover o ponto de inserção abaixo a caixa de seleção.  
  
5.  Adicionar uma segunda caixa de seleção para o documento abaixo o `ApplyBoldFont` caixa de seleção e altere as propriedades a seguir.  
  
    |Propriedade|Valor|  
    |--------------|-----------|  
    |**Nome**|**applyItalicFont**|  
    |**Texto**|**Itálico**|  
  
6.  Pressione **Enter** para mover o ponto de inserção abaixo a segunda caixa de seleção.  
  
7.  Adicionar uma terceira caixa de seleção para o documento abaixo o `ApplyItalicFont` caixa de seleção e altere as propriedades a seguir.  
  
    |Propriedade|Valor|  
    |--------------|-----------|  
    |**Nome**|**applyUnderlineFont**|  
    |**Texto**|**sublinhado**|  
  
### <a name="add-text-and-a-bookmark-control"></a>Adicionar texto e um controle de indicador  
  
1.  Mover o ponto de inserção abaixo dos controles da caixa de seleção e digite o seguinte texto:  
  
     **Clique em uma caixa de seleção para alterar a formatação de texto.**  
  
2.  Do **controles Word** guia do **caixa de ferramentas**, arraste um <xref:Microsoft.Office.Tools.Word.Bookmark> controle o documento.  
  
     O **adicionar controle do indicador** caixa de diálogo é exibida.  
  
3.  Selecione o texto que você adicionou ao documento e clique em **Okey**.  
  
     Um <xref:Microsoft.Office.Tools.Word.Bookmark> controle chamado **Bookmark1** é adicionada ao texto selecionado no documento.  
  
4.  No **propriedades** janela, altere o valor da **(nome)** propriedade **fontText.**  
  
 Em seguida, escreva o código para formatar o texto quando uma caixa de seleção é marcada ou desmarcada.  
  
## <a name="format-the-text-when-a-check-box-is-checked-or-cleared"></a>Formatar o texto quando uma caixa de seleção é marcada ou desmarcada  
 Quando o usuário seleciona uma opção de formatação, altere o formato do texto do documento.  
  
### <a name="change-formatting-when-a-check-box-is-selected"></a>Alterar a formatação quando uma caixa de seleção está selecionada  
  
1.  Clique com botão direito `ThisDocument` na **Solution Explorer**e, em seguida, clique em **Exibir código** no menu de atalho.  
  
2.  Para c# somente, adicione as seguintes constantes para o **ThisDocument** classe.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#2](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#2)]  
  
3.  Adicione o seguinte código para o <xref:System.Windows.Forms.Control.Click> manipulador de eventos do `applyBoldFont` caixa de seleção.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsWord#3](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#3)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#3](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#3)]  
  
4.  Adicione o seguinte código para o <xref:System.Windows.Forms.Control.Click> manipulador de eventos do `applyItalicFont` caixa de seleção.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsWord#4](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#4)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#4](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#4)]  
  
5.  Adicione o seguinte código para o <xref:System.Windows.Forms.Control.Click> manipulador de eventos do `applyUnderlineFont` caixa de seleção.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsWord#5](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#5)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#5](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#5)]  
  
6.  Em c#, você deve adicionar manipuladores de eventos para as caixas de texto para o <xref:Microsoft.Office.Tools.Word.Document.Startup> evento. Para obter informações sobre como criar manipuladores de eventos, consulte [como: criar manipuladores de eventos em projetos do Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#6](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#6)]  
  
## <a name="test-the-application"></a>Testar o aplicativo  
 Agora você pode testar o documento para verificar se o texto está formatado corretamente quando você marca ou desmarca uma caixa de seleção.  
  
### <a name="test-your-document"></a>Teste seu documento  
  
1.  Pressione **F5** para executar o projeto.  
  
2.  Marque ou desmarque uma caixa de seleção.  
  
3.  Confirme que o texto está formatado corretamente.  
  
## <a name="next-steps"></a>Próximas etapas  
 Este passo a passo mostra as Noções básicas de usando caixas de seleção e alterar programaticamente o texto de formatação em documentos do Word. Estas são algumas tarefas que podem vir a seguir:  
  
-   Use um botão para preencher uma caixa de texto. Para obter mais informações, consulte [passo a passo: exibir texto em uma caixa de texto em um documento usando um botão](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button.md).  
  
-   Usando botões de opção para selecionar estilos de gráfico. Para obter mais informações, consulte [passo a passo: atualizar um gráfico em um documento usando botões de opção](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md).  
  

## <a name="see-also"></a>Consulte também  
 [Explicações passo a passo usando o Word](../vsto/walkthroughs-using-word.md)   
 [Explicações passo a passo e exemplos de desenvolvimento do office](../vsto/office-development-samples-and-walkthroughs.md)   
 [Controle NamedRange](../vsto/namedrange-control.md)   
 [Limitações de controles de Windows Forms em documentos do Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  
  