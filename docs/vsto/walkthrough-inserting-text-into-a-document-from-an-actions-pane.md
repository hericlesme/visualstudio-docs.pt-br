---
title: "Passo a passo: Inserindo texto em um documento de um painel de ações | Microsoft Docs"
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
- smart documents [Office development in Visual Studio], creating in Word
- smart documents [Office development in Visual Studio], adding controls
- actions panes [Office development in Visual Studio], creating in Word
- actions panes [Office development in Visual Studio], adding controls
ms.assetid: fd14c896-5737-4a20-94f7-6064b67112c5
caps.latest.revision: "70"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 789ad22524a5c0128320bfb833b8ad97e294a86f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-inserting-text-into-a-document-from-an-actions-pane"></a>Instruções passo a passo: inserindo texto em um documento a partir de um painel Ações
  Este passo a passo demonstra como criar um painel de ações em um documento do Microsoft Office Word. O painel de ações contém dois controles que coletam informações e, em seguida, enviar o texto para o documento.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Esta explicação passo a passo ilustra as seguintes tarefas:  
  
-   Criando uma interface por meio de controles de formulários do Windows em um controle de painel de ações.  
  
-   Quando o aplicativo é aberto, exibindo o painel de ações.  
  
> [!NOTE]  
>  Seu computador pode mostrar diferentes nomes ou locais para alguns dos elementos de interface do usuário do Visual Studio nas instruções a seguir. A edição do Visual Studio que você possui e as configurações que você usa determinam esses elementos. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Você precisa dos seguintes componentes para concluir esta instrução passo a passo:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] ou [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].  
  
## <a name="creating-the-project"></a>Criando o Projeto  
 A primeira etapa é criar um projeto de Documento do Word.  
  
#### <a name="to-create-a-new-project"></a>Para criar um novo projeto  
  
1.  Criar um projeto de documento do Word com o nome **meu painel de ações básicas**. No assistente, selecione **criar um novo documento**. Para obter mais informações, consulte [como: criar projetos do Office no Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio abre o novo documento do Word no designer e adiciona o **meu painel de ações básicas** projeto **Gerenciador de soluções**.  
  
## <a name="adding-text-and-bookmarks-to-the-document"></a>Adicionando texto e indicadores no documento  
 O painel de ações enviará texto para indicadores no documento. Para criar o documento, digite algum texto para criar um formulário básico.  
  
#### <a name="to-add-text-to-your-document"></a>Para adicionar texto ao documento  
  
1.  Digite o seguinte texto no documento do Word:  
  
     **21 de março de 2008**  
  
     **Nome**  
  
     **Endereço**  
  
     **Este é um exemplo de um painel de ações básicas no Word.**  
  
 Você pode adicionar uma <xref:Microsoft.Office.Tools.Word.Bookmark> controle ao documento, arrastando-o do **caixa de ferramentas** no Visual Studio ou usando o **indicador** caixa de diálogo no Word.  
  
#### <a name="to-add-a-bookmark-control-to-your-document"></a>Para adicionar um controle de indicador no documento  
  
1.  Do **controles Word** guia do **caixa de ferramentas**, arraste um <xref:Microsoft.Office.Tools.Word.Bookmark> controle ao documento.  
  
     O **adicionar controle do indicador** caixa de diálogo é exibida.  
  
2.  Selecionar a palavra **nome**, sem selecionar a marca de parágrafo e clique em **Okey**.  
  
    > [!NOTE]  
    >  A marca de parágrafo deve ficar fora do indicador. Se as marcas de parágrafo não estiverem visíveis no documento, clique no **ferramentas** , aponte para **ferramentas do Microsoft Office Word** e, em seguida, clique em **opções**. Clique no **exibição** guia e selecione o **marcas de parágrafo** caixa de seleção a **marcas de formatação** seção o **opções** caixa de diálogo.  
  
3.  No **propriedades** janela, altere o **nome** propriedade **Bookmark1** para **showName**.  
  
4.  Selecionar a palavra **endereço**, sem selecionar a marca de parágrafo.  
  
5.  No **inserir** guia da faixa de opções, no **Links** de grupo, clique em **indicador**.  
  
6.  No **indicador** caixa de diálogo, digite **showAddress** no **nome do indicador** caixa e clique em **adicionar**.  
  
## <a name="adding-controls-to-the-actions-pane"></a>Adicionando controles para o painel de ações  
 Para criar a interface do painel de ações, adicionar um controle do painel Ações para o projeto e, em seguida, adicionar controles de formulários do Windows para o controle do painel Ações.  
  
#### <a name="to-add-an-actions-pane-control"></a>Para adicionar um controle de painel de ações  
  
1.  Selecione o **meu painel de ações básicas** project no **Gerenciador de soluções**.  
  
2.  No menu **Projeto**, clique em **Adicionar Novo Item**.  
  
3.  No **Adicionar Novo Item** caixa de diálogo, clique em **controle do painel Ações**, nomeie o controle **InsertTextControl,** e clique em **adicionar**.  
  
#### <a name="to-add-windows-form-controls-to-the-actions-pane-control"></a>Para adicionar controles de formulários do Windows para o controle de painel de ações  
  
1.  Se o controle de painel de ações não estiver visível no designer, clique duas vezes em **InsertTextControl**.  
  
2.  Do **controles comuns** guia do **caixa de ferramentas**, arraste um **rótulo** controle para o controle de painel de ações.  
  
3.  Alterar o **texto** propriedade do controle de rótulo para **nome**.  
  
4.  Adicionar um **Textbox** o controle para o controle do painel Ações e alterar as propriedades a seguir.  
  
    |Propriedade|Valor|  
    |--------------|-----------|  
    |**Nome**|**getName**|  
    |**Size**|**130, 20**|  
  
5.  Adicionar um segundo **rótulo** o controle para o controle do painel Ações e altere o **texto** propriedade **endereço**.  
  
6.  Adicionar um segundo **Textbox** o controle para o controle do painel Ações e alterar as propriedades a seguir.  
  
    |Propriedade|Valor|  
    |--------------|-----------|  
    |**Nome**|**getAddress**|  
    |**Aceita o retorno**|**True**|  
    |**Multilinha**|**True**|  
    |**Size**|**130, 40**|  
  
7.  Adicionar um **botão** o controle para o controle do painel Ações e alterar as propriedades a seguir.  
  
    |Propriedade|Valor|  
    |--------------|-----------|  
    |**Nome**|**addText**|  
    |**Texto**|**Inserir**|  
  
## <a name="adding-code-to-insert-text-into-the-document"></a>Adicionando código para inserir texto no documento  
 No painel Ações, escrever código que insere o texto das caixas de texto apropriada <xref:Microsoft.Office.Tools.Word.Bookmark> controles no documento. Você pode usar o `Globals` classe para acessar os controles no documento de controles no painel Ações. Para obter mais informações, consulte [acesso Global a objetos em projetos do Office](../vsto/global-access-to-objects-in-office-projects.md).  
  
#### <a name="to-insert-text-from-the-actions-pane-in-a-bookmark-in-the-document"></a>Para inserir texto no painel de ações em um indicador no documento  
  
1.  Adicione o seguinte código para o <xref:System.Windows.Forms.Control.Click> manipulador de eventos do **addText** botão.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#8](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/InsertTextControl.cs#8)]
     [!code-vb[Trin_VstcoreActionsPaneWord#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/InsertTextControl.vb#8)]  
  
2.  Em c#, você deve adicionar um manipulador de eventos para o clique do botão. Você pode colocar esse código no `InsertTextControl` construtor após a chamada a `IntializeComponent`. Para obter informações sobre como criar manipuladores de eventos, consulte [como: criar manipuladores de eventos em projetos do Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#9](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/InsertTextControl.cs#9)]  
  
## <a name="adding-code-to-show-the-actions-pane"></a>Adicionando código para mostrar o painel de ações  
 Para mostrar o painel de ações, adicione o controle que você criou para a coleção de controle.  
  
#### <a name="to-show-the-actions-pane"></a>Para mostrar o painel de ações  
  
1.  Criar uma nova instância do controle de painel de ações no `ThisDocument` classe.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#10](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#10)]
     [!code-vb[Trin_VstcoreActionsPaneWord#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#10)]  
  
2.  Adicione o seguinte código para o <xref:Microsoft.Office.Tools.Word.Document.Startup> manipulador de eventos do `ThisDocument`.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#11](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#11)]
     [!code-vb[Trin_VstcoreActionsPaneWord#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#11)]  
  
## <a name="testing-the-application"></a>Testando o aplicativo  
 Teste seu documento para verificar se o painel de ações é aberto quando o documento é aberto e se o texto digitado nas caixas de texto é inserido nos indicadores quando o botão é clicado.  
  
#### <a name="to-test-your-document"></a>Para testar o documento  
  
1.  Pressione F5 para executar o projeto.  
  
2.  Confirme se o painel de ações está visível.  
  
3.  Digite seu nome e endereço nas caixas de texto no painel Ações e clique em **inserir**.  
  
## <a name="next-steps"></a>Próximas etapas  
 Estas são algumas tarefas que podem vir a seguir:  
  
-   Criando um painel de ações no Excel. Para obter mais informações, consulte [como: adicionar um painel de ações para pastas de trabalho do Excel](http://msdn.microsoft.com/en-us/62abfce6-e44f-419d-85d8-26bf59f33872).  
  
-   Associando dados a controles em um painel de ações. Para obter mais informações, consulte [passo a passo: vinculação de dados a controles em um painel de ações do Word](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md).  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral do painel de ações](../vsto/actions-pane-overview.md)   
 [Como: adicionar um painel de ações a documentos do Word ou pastas de trabalho do Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [Como: adicionar um painel de ações para pastas de trabalho do Excel](http://msdn.microsoft.com/en-us/62abfce6-e44f-419d-85d8-26bf59f33872)   
 [Como: gerenciar o controle Layout em painéis de ações](../vsto/how-to-manage-control-layout-on-actions-panes.md)   
 [Controle do Indicador](../vsto/bookmark-control.md)  
  
  