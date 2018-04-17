---
title: 'Passo a passo: Adicionando controles a um documento em tempo de execução em um suplemento do VSTO | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- add-ins [Office development in Visual Studio], adding controls
- application-level add-ins [Office development in Visual Studio], adding controls
- controls [Office development in Visual Studio], adding to documents at run time
- documents [Office development in Visual Studio], adding controls at run time
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1f26a60bdbd0db2464a8ac479b7534fb63f18cea
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-adding-controls-to-a-document-at-run-time-in-a-vsto-add-in"></a>Passo a passo: Adicionando controles a um documento em tempo de execução em um suplemento do VSTO
  É possível adicionar controles para qualquer documento do Microsoft Office Word aberto usando um suplemento do VSTO. Este passo a passo demonstra como usar a faixa de opções para habilitar usuários adicionar um <xref:Microsoft.Office.Tools.Word.Controls.Button> ou <xref:Microsoft.Office.Tools.Word.RichTextContentControl> para um documento.  
  
 **Aplica-se a:** as informações neste tópico se aplicam a projetos de suplemento do VSTO para Word 2010. Para obter mais informações, consulte [recursos disponibilizados pelo aplicativo do Office e pelo tipo de projeto](../vsto/features-available-by-office-application-and-project-type.md).  
  
 Esta explicação passo a passo ilustra as seguintes tarefas:  
  
-   Criar um novo projeto de suplemento do VSTO do Word.  
  
-   Fornecendo uma interface do usuário (UI) para adicionar controles ao documento.  
  
-   Adicionando controles para o documento em tempo de execução.  
  
-   Removendo controles do documento.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Você precisa dos seguintes componentes para concluir esta instrução passo a passo:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] ou [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].  
  
## <a name="creating-a-new-word-add-in-project"></a>Criando um projeto novo do suplemento do Word  
 Comece criando um projeto de suplemento do VSTO do Word.  
  
#### <a name="to-create-a-new-word-vsto-add-in-project"></a>Para criar um novo projeto de suplemento do VSTO do Word  
  
1.  Criar um projeto de suplemento do VSTO para Word com o nome **WordDynamicControls**. Para obter mais informações, consulte [como: criar projetos do Office no Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  Adicione uma referência para o **Microsoft.Office.Tools.Word.v4.0.Utilities.dll** assembly. Essa referência é necessária para adicionar programaticamente um controle de formulários do Windows para o documento mais tarde neste passo a passo.  
  
## <a name="providing-a-ui-to-add-controls-to-a-document"></a>Fornece uma interface do usuário para adicionar controles a um documento  
 Adicione uma guia da faixa de opções no Word. Os usuários podem selecionar caixas de seleção na guia para adicionar controles a um documento.  
  
#### <a name="to-provide-a-ui-to-add-controls-to-a-document"></a>Para fornecer uma interface do usuário para adicionar controles a um documento  
  
1.  No menu **Projeto**, clique em **Adicionar Novo Item**.  
  
2.  No **Adicionar Novo Item** caixa de diálogo, selecione **faixa de opções (Visual Designer)**.  
  
3.  Alterar o nome da nova faixa de opções para **MyRibbon**e clique em **adicionar**.  
  
     O **MyRibbon.cs** ou **MyRibbon.vb** arquivo é aberto no Designer de faixa de opções e exibe um guia padrão e o grupo.  
  
4.  No Designer de faixa de opções, clique o **group1** grupo.  
  
5.  No **propriedades** janela, altere o **rótulo** propriedade **group1** para **adicionar controles**.  
  
6.  Do **controles de faixa de opções do Office** guia do **caixa de ferramentas**, arraste um **caixa de seleção** controle para **group1**.  
  
7.  Clique em **CheckBox1** para selecioná-la.  
  
8.  No **propriedades** janela, altere as propriedades a seguir.  
  
    |Propriedade|Valor|  
    |--------------|-----------|  
    |**Nome**|**addButtonCheckBox**|  
    |**Rótulo**|**Botão Adicionar**|  
  
9. Adicionar uma segunda caixa de seleção para **group1**e, em seguida, altere as propriedades a seguir.  
  
    |Propriedade|Valor|  
    |--------------|-----------|  
    |**Nome**|**addRichTextCheckBox**|  
    |**Rótulo**|**Adicionar controle Rich Text**|  
  
10. No Designer de faixa de opções, clique duas vezes em **botão Adicionar**.  
  
     O <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> manipulador de eventos do **botão Adicionar** caixa de seleção é aberto no Editor de códigos.  
  
11. Volte para o Designer de faixa de opções e clique duas vezes em **adicionar controle de Rich Text**.  
  
     O <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> manipulador de eventos do **adicionar controle de Rich Text** caixa de seleção é aberto no Editor de códigos.  
  
 Posteriormente neste passo a passo, você adicionará código para esses manipuladores de eventos para adicionar e remover controles no documento ativo.  
  
## <a name="adding-and-removing-controls-on-the-active-document"></a>Adicionando e removendo controles no documento ativo  
 No código de suplemento do VSTO, você deve converter o documento ativo em um <xref:Microsoft.Office.Tools.Word.Document> *item de host* antes de adicionar um controle. Em soluções do Office, controles gerenciados podem ser adicionados apenas a itens de host, que atuam como contêineres para os controles. Em projetos de suplemento do VSTO, itens de host podem ser criadas em tempo de execução usando o método GetVstoObject.  
  
 Adicionar métodos para o `ThisAddIn` classe que pode ser chamado para adicionar ou remover um <xref:Microsoft.Office.Tools.Word.Controls.Button> ou <xref:Microsoft.Office.Tools.Word.RichTextContentControl> no documento ativo. Posteriormente neste passo a passo, você chamará esses métodos de <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> manipuladores de eventos das caixas de seleção na faixa de opções.  
  
#### <a name="to-add-and-remove-controls-on-the-active-document"></a>Para adicionar e remover controles no documento ativo  
  
1.  Em **Solution Explorer**, clique duas vezes em ThisAddIn.cs ou ThisAddIn para abrir o arquivo no Editor de códigos.  
  
2.  Adicione o seguinte código para o `ThisAddIn` classe. Esse código declara <xref:Microsoft.Office.Tools.Word.Controls.Button> e <xref:Microsoft.Office.Tools.Word.RichTextContentControl> objetos que representam os controles que serão adicionados ao documento.  
  
     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#1](../vsto/codesnippet/VisualBasic/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.vb#1)]
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#1](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.cs#1)]  
  
3.  Adicione o seguinte método à classe `ThisAddIn`. Quando o usuário clica o **botão Adicionar** caixa de seleção na faixa de opções, este método adiciona uma <xref:Microsoft.Office.Tools.Word.Controls.Button> à seleção atual no documento se a caixa de seleção estiver selecionada ou remove o <xref:Microsoft.Office.Tools.Word.Controls.Button> se a caixa de seleção estiver desmarcada.  
  
     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#2](../vsto/codesnippet/VisualBasic/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.vb#2)]
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#2](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.cs#2)]  
  
4.  Adicione o seguinte método à classe `ThisAddIn`. Quando o usuário clica o **adicionar controle de Rich Text** caixa de seleção na faixa de opções, este método adiciona uma <xref:Microsoft.Office.Tools.Word.RichTextContentControl> à seleção atual no documento se a caixa de seleção estiver selecionada ou remove o <xref:Microsoft.Office.Tools.Word.RichTextContentControl> se a caixa de seleção estiver desmarcada.  
  
     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#3](../vsto/codesnippet/VisualBasic/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.vb#3)]
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#3](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.cs#3)]  
  
## <a name="removing-the-button-control-when-the-document-is-saved"></a>A remoção do botão controle quando o documento é salvo  
 Controles de formulários do Windows não são mantidos quando o documento é salvo e fechado. No entanto, um wrapper do ActiveX para cada controle permanecerá no documento e a borda desse wrapper pode ser vista pelos usuários finais quando o documento for aberto novamente. Há várias maneiras para limpar os controles de formulários do Windows criados dinamicamente nos suplementos do VSTO. Neste passo a passo, você remove programaticamente o <xref:Microsoft.Office.Tools.Word.Controls.Button> controlar quando o documento é salvo.  
  
#### <a name="to-remove-the-button-control-when-the-document-is-saved"></a>Para remover o controle de botão quando o documento é salvo  
  
1.  No arquivo de código ThisAddIn.cs ou ThisAddIn, adicione o seguinte método para o `ThisAddIn` classe. Esse método é um manipulador de eventos para o <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> evento. Se o documento salvo tem um <xref:Microsoft.Office.Tools.Word.Document> obtém o item de host de item de host que está associado ele, o manipulador de eventos e remove o <xref:Microsoft.Office.Tools.Word.Controls.Button> controlar, se ele existir.  
  
     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#4](../vsto/codesnippet/VisualBasic/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.vb#4)]
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#4](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.cs#4)]  
  
2.  No c#, adicione o seguinte código para o `ThisAddIn_Startup` manipulador de eventos. Esse código é necessária em c# para conectar o `Application_DocumentBeforeSave` manipulador de eventos com o <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> evento.  
  
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#5](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.cs#5)]  
  
## <a name="adding-and-removing-controls-when-the-user-clicks-the-check-boxes-on-the-ribbon"></a>Adicionando e removendo controla quando o usuário clica as caixas de seleção na faixa de opções  
 Finalmente, modifique o <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> manipuladores de eventos, as caixas de seleção que você adicionou à faixa de opções para adicionar ou remover controles no documento.  
  
#### <a name="to-add-or-remove-controls-when-the-user-clicks-the-check-boxes-on-the-ribbon"></a>Para adicionar ou remover controla quando o usuário clica as caixas de seleção na faixa de opções  
  
1.  No arquivo de código MyRibbon.cs ou MyRibbon.vb, substitua gerado `addButtonCheckBox_Click` e `addRichTextCheckBox_Click` manipuladores de eventos com o código a seguir. Esse código redefine esses manipuladores de eventos para chamar o `ToggleButtonOnDocument` e `ToggleRichTextControlOnDocument` métodos que você adicionou para a `ThisAddIn` classe anteriormente neste passo a passo.  
  
     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#6](../vsto/codesnippet/VisualBasic/Trin_WordAddInDynamicControlsWalkthrough/MyRibbon.vb#6)]
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#6](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/MyRibbon.cs#6)]  
  
## <a name="testing-the-solution"></a>Testando a solução  
 Adicione controles a um documento selecionando-os a partir da guia personalizada na faixa de opções. Quando você salvar o documento, o <xref:Microsoft.Office.Tools.Word.Controls.Button> controle é removido.  
  
#### <a name="to-test-the-solution"></a>Para testar a solução.  
  
1.  Pressione F5 para executar o projeto.  
  
2.  No documento ativo, pressione ENTER várias vezes para adicionar novos parágrafos vazios para o documento.  
  
3.  Selecione o primeiro parágrafo.  
  
4.  Clique o **Add-Ins** guia.  
  
5.  No **adicionar controles** de grupo, clique em **botão Adicionar**.  
  
     Um botão é exibido no primeiro parágrafo.  
  
6.  Selecione o último parágrafo.  
  
7.  No **adicionar controles** de grupo, clique em **adicionar controle de Rich Text**.  
  
     Um controle de conteúdo rich text é adicionado à última parágrafo.  
  
8.  Salve o documento.  
  
     O botão será removido do documento.  
  
## <a name="next-steps"></a>Próximas etapas  
 Você pode aprender mais sobre os controles no suplemento do VSTO com estes tópicos:  
  
-   Para obter um exemplo que demonstra como adicionar muitos outros tipos de controles a um documento em tempo de execução e recrie os controles quando o documento for aberto novamente, consulte o Word Add-In dinâmico controles de exemplo em [amostras de desenvolvimento do Office e explicações passo a passo](../vsto/office-development-samples-and-walkthroughs.md).  
  
-   Para uma explicação passo a passo que demonstra como adicionar controles a uma planilha usando um suplemento do VSTO para Excel, consulte [passo a passo: adicionando controles a uma planilha em tempo de execução no VSTO suplemento no projeto](../vsto/walkthrough-adding-controls-to-a-worksheet-at-run-time-in-vsto-add-in-project.md).  
  
## <a name="see-also"></a>Consulte também  
 [Soluções do Word](../vsto/word-solutions.md)   
 [Adicionando controles a documentos do Office em tempo de execução](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Mantendo controles dinâmicos em documentos do Office](../vsto/persisting-dynamic-controls-in-office-documents.md)   
 [Como: adicionar controles a documentos do Office do Windows Forms](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [Como: adicionar controles Content a documentos do Word](../vsto/how-to-add-content-controls-to-word-documents.md)   
 [Estendendo documentos do Word e pastas de trabalho do Excel em suplementos do VSTO no tempo de execução](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)  
  
  