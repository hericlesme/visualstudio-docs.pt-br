---
title: "Passo a passo: Vinculação de dados de um serviço em um VSTO suplemento projeto | Microsoft Docs"
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
- databases [Office development in Visual Studio], scrolling records
- records [Office development in Visual Studio], scrolling
- data [Office development in Visual Studio], scrolling database records
ms.assetid: 9b008be4-06a3-4ffc-9f02-79dd6cfe00ab
caps.latest.revision: "38"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6874dd125c692b6d853dc89cc533bf3d623aad51
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-binding-to-data-from-a-service-in-a-vsto-add-in-project"></a>Passo a passo: Associando a dados de um serviço em um projeto de suplemento do VSTO
  Você pode associar dados a controles de host em projetos de suplemento do VSTO. Este passo a passo demonstra como adicionar controles a um documento do Microsoft Office Word, vincular controles a dados recuperados do serviço de conteúdo do MSDN e responder a eventos em tempo de execução.  
  
 **Aplica-se a:** as informações neste tópico se aplicam a projetos no nível do aplicativo para o Word 2010. Para obter mais informações, consulte [recursos disponibilizados pelo aplicativo do Office e pelo tipo de projeto](../vsto/features-available-by-office-application-and-project-type.md).  
  
 Esta explicação passo a passo ilustra as seguintes tarefas:  
  
-   Adicionando um <xref:Microsoft.Office.Tools.Word.RichTextContentControl> controle a um documento em tempo de execução.  
  
-   Associação de <xref:Microsoft.Office.Tools.Word.RichTextContentControl> controle aos dados de um serviço Web.  
  
-   Respondendo ao <xref:Microsoft.Office.Tools.Word.ContentControlBase.Entering> eventos de um <xref:Microsoft.Office.Tools.Word.RichTextContentControl> controle.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Você precisa dos seguintes componentes para concluir esta instrução passo a passo:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] ou [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].  
  
## <a name="creating-a-new-project"></a>Criando um novo projeto  
 A primeira etapa é criar um projeto de suplemento do VSTO do Word.  
  
#### <a name="to-create-a-new-project"></a>Para criar um novo projeto  
  
1.  Criar um projeto de suplemento do VSTO Word com o nome **MTPS serviço conteúdo**, usando o Visual Basic ou c#.  
  
     Para obter mais informações, consulte [como: criar projetos do Office no Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     O Visual Studio abrirá o `ThisAddIn.vb` ou `ThisAddIn.cs` de arquivos e adiciona o projeto para **Gerenciador de soluções**.  
  
## <a name="adding-a-web-service"></a>Adicionando um serviço Web  
 Para este passo a passo, use um serviço Web chamado serviço MTPS conteúdo. Esse serviço da Web retorna informações de um artigo do MSDN especificado na forma de uma cadeia de caracteres XML ou texto sem formatação. Uma etapa posterior mostra como exibir as informações retornadas em um controle de conteúdo.  
  
#### <a name="to-add-the-mtps-content-service-to-the-project"></a>Para adicionar o serviço de conteúdo MTPS ao projeto  
  
1.  Sobre o **dados** menu, clique em **adicionar nova fonte de dados**.  
  
2.  No **Assistente de configuração de fonte de dados**, clique em **Service**e, em seguida, clique em **próximo**.  
  
3.  No **endereço** campo, digite a seguinte URL:  
  
     **http://Services.msdn.microsoft.com/contentservices/contentservice.asmx**  
  
4.  Click **Go**.  
  
5.  No **Namespace** , digite **ContentService**e clique em **Okey**.  
  
6.  No **Assistente de adição de referência** caixa de diálogo, clique em **concluir**.  
  
## <a name="adding-a-content-control-and-binding-to-data-at-run-time"></a>Adicionando um controle de conteúdo e associação de dados em tempo de execução  
 Em projetos de suplemento do VSTO, adicionar e vincular controles em tempo de execução. Para este passo a passo, configure o controle de conteúdo para recuperar dados do serviço da Web quando um usuário clica dentro do controle.  
  
#### <a name="to-add-a-content-control-and-bind-to-data"></a>Para adicionar um controle de conteúdo e associar a dados  
  
1.  No `ThisAddIn` classe, declare as variáveis para o serviço de conteúdo MTPS, o controle de conteúdo e a associação de dados.  
  
     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#2](../vsto/codesnippet/CSharp/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.cs#2)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#2](../vsto/codesnippet/VisualBasic/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.vb#2)]  
  
2.  Adicione o seguinte método à classe `ThisAddIn`. Esse método cria um controle de conteúdo no início do documento ativo.  
  
     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#4](../vsto/codesnippet/CSharp/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.cs#4)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#4](../vsto/codesnippet/VisualBasic/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.vb#4)]  
  
3.  Adicione o seguinte método à classe `ThisAddIn`. Esse método inicializa os objetos necessários para criar e enviar uma solicitação ao serviço Web.  
  
     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#6](../vsto/codesnippet/CSharp/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.cs#6)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#6](../vsto/codesnippet/VisualBasic/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.vb#6)]  
  
4.  Crie um manipulador de eventos para recuperar o documento da biblioteca do MSDN sobre o conteúdo controla quando um usuário clica dentro do conteúdo de controle e associar os dados para o controle de conteúdo.  
  
     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#5](../vsto/codesnippet/CSharp/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.cs#5)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#5](../vsto/codesnippet/VisualBasic/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.vb#5)]  
  
5.  Chamar o `AddRichTextControlAtRange` e `InitializeServiceObjects` métodos de `ThisAddIn_Startup` método. Para programadores de c#, adicione um manipulador de eventos.  
  
     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#3](../vsto/codesnippet/CSharp/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.cs#3)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#3](../vsto/codesnippet/VisualBasic/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.vb#3)]  
  
## <a name="testing-the-add-in"></a>Testando o suplemento  
 Ao abrir o Word, o <xref:Microsoft.Office.Tools.Word.RichTextContentControl> controle aparece. O texto no controle muda quando você clica nele.  
  
#### <a name="to-test-the-vsto-add-in"></a>Para testar o suplemento do VSTO  
  
1.  Pressione **F5**.  
  
2.  Clique dentro do controle de conteúdo.  
  
     Informações são baixadas do serviço MTPS conteúdo e exibidas dentro do controle de conteúdo.  
  
## <a name="see-also"></a>Consulte também  
 [Associando dados a controles em soluções do Office](../vsto/binding-data-to-controls-in-office-solutions.md)  
  
  