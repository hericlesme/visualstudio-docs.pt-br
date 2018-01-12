---
title: "Passo a passo: Exibindo texto em uma caixa de texto em um documento usando um botão | Microsoft Docs"
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
helpviewer_keywords: text boxes, displaying text in documents
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 803dcbe27eedc4b93443a6389b4acf7ee2dc08cf
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button"></a>Instruções passo a passo: exibindo texto em uma caixa de texto em um documento usando um botão
  Este passo a passo demonstra como usar os botões e caixas de texto em uma personalização no nível do documento para o Microsoft Office Word.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Esta explicação passo a passo ilustra as seguintes tarefas:  
  
-   Adicionando controles para o documento do Word em um projeto no nível de documento em tempo de design.  
  
-   Preencher uma caixa de texto quando um botão é clicado.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Você precisa dos seguintes componentes para concluir esta instrução passo a passo:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word  
  
## <a name="creating-the-project"></a>Criando o Projeto  
 A primeira etapa é criar um projeto de Documento do Word.  
  
#### <a name="to-create-a-new-project"></a>Para criar um novo projeto  
  
1.  Criar um projeto de documento do Word com o nome **Meus palavra botão**. No assistente, selecione **criar um novo documento**.  
  
     Para obter mais informações, consulte [como: criar projetos do Office no Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio abre o novo documento do Word no designer e adiciona o **Meus palavra botão** projeto **Gerenciador de soluções**.  
  
## <a name="adding-controls-to-the-word-document"></a>Adicionando controles a documento do Word  
 Os controles de interface de usuário consistem em um botão e uma caixa de texto no documento do Word.  
  
#### <a name="to-add-a-button-and-a-text-box"></a>Para adicionar um botão e uma caixa de texto  
  
1.  Verifique se o documento é aberto no designer do Visual Studio.  
  
2.  Do **controles comuns** guia do **caixa de ferramentas**, arraste um <xref:Microsoft.Office.Tools.Word.Controls.TextBox> controle o documento.  
  
    > [!NOTE]  
    >  No Word, os controles são descartados em linha com o texto por padrão. Você pode modificar os maneira como os controles e objetos de forma são inseridos, alterando o padrão no **editar** guia do **opções** caixa de diálogo no Word.  
  
3.  Sobre o **exibição** menu, clique em **janela propriedades**.  
  
4.  Localizar **TextBox1** no **propriedades** caixa de lista suspensa da janela e altere o **nome** propriedade da caixa de texto para **texto exibido**.  
  
5.  Arraste um **botão** controlar o documento e alterar as propriedades a seguir.  
  
    |Propriedade|Valor|  
    |--------------|-----------|  
    |**Nome**|**insertText**|  
    |**Texto**|**Inserir texto**|  
  
 Agora você pode escrever o código que será executado quando o botão é clicado.  
  
## <a name="populating-the-text-box-when-the-button-is-clicked"></a>Preenchendo a caixa de texto quando o botão é clicado  
 Toda vez que o usuário clica no botão **Olá, mundo!** é adicionado à caixa de texto.  
  
#### <a name="to-write-to-the-text-box-when-the-button-is-clicked"></a>Para gravar na caixa de texto quando o botão é clicado  
  
1.  Em **Solution Explorer**, clique com botão direito **ThisDocument**e, em seguida, clique em **Exibir código** no menu de atalho.  
  
2.  Adicione o seguinte código para o <xref:System.Windows.Forms.Control.Click> manipulador de eventos do botão.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsWord#7](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#7)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#7](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#7)]  
  
3.  Em c#, você deve adicionar um manipulador de eventos para o botão de <xref:Microsoft.Office.Tools.Word.Document.Startup> eventos. Para obter informações sobre como criar manipuladores de eventos, consulte [como: criar manipuladores de eventos em projetos do Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#8](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#8)]  
  
## <a name="testing-the-application"></a>Testando o aplicativo  
 Agora você pode testar o documento para certificar-se de que a mensagem **Olá, mundo!** aparece na caixa de texto quando você clicar no botão.  
  
#### <a name="to-test-your-document"></a>Para testar o documento  
  
1.  Pressione F5 para executar o projeto.  
  
2.  Clique no botão.  
  
3.  Confirme se **Hello World!** é exibida na caixa de texto.  
  
## <a name="next-steps"></a>Próximas etapas  
 Este passo a passo mostra os fundamentos de como usar os botões e caixas de texto em documentos do Word. Estas são algumas tarefas que podem vir a seguir:  
  
-   Usando uma caixa de combinação para alterar a formatação. Para obter mais informações, consulte [passo a passo: alterando documento formatação usando controles CheckBox](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md).  
  
-   Usando botões de opção para selecionar estilos de gráfico. Para obter mais informações, consulte [passo a passo: atualizando um gráfico em um documento usando botões](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md).  
  
## <a name="see-also"></a>Consulte também  
 [Controles em Visão geral de documentos do Office do Windows Forms](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Explicações passo a passo usando o Word](../vsto/walkthroughs-using-word.md)   
 [Explicações passo a passo e exemplos de desenvolvimento do office](../vsto/office-development-samples-and-walkthroughs.md)   
 [Como: adicionar controles a documentos do Office do Windows Forms](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [Visão geral dos Controles de Host e dos Itens de Host](../vsto/host-items-and-host-controls-overview.md)  
  
  