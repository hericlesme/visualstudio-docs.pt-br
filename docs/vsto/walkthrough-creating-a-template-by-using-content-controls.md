---
title: "Passo a passo: Criando um modelo usando os controles de conteúdo | Microsoft Docs"
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
- building blocks [Office development in Visual Studio]
- Word [Office development in Visual Studio], creating documents
- content controls [Office development in Visual Studio], adding to documents
ms.assetid: 88fb9a60-dcc3-4a5f-a8c9-7aff01ca4b4b
caps.latest.revision: "46"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 8508f12d0e0bbf6dbabc0c12f8e5feb8d7d11d1b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-creating-a-template-by-using-content-controls"></a>Instruções passo a passo: criando um modelo usando controle de conteúdo
  Este passo a passo demonstra como criar uma personalização no nível do documento que usa os controles de conteúdo para criar conteúdo reutilizável e em um modelo do Microsoft Office Word.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Word permite que você crie uma coleção de partes do documento reutilizável, chamado *blocos de construção*. Este passo a passo mostra como criar duas tabelas como blocos de construção. Cada tabela contém vários controles de conteúdo que podem conter diferentes tipos de conteúdo, como texto sem formatação ou datas. Uma das tabelas contém informações sobre o funcionário e a outra tabela que contém comentários do cliente.  
  
 Depois de criar um documento do modelo, você pode adicionar qualquer uma das tabelas para o documento usando vários <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl> objetos, que exibem os blocos de construção disponíveis no modelo.  
  
 Esta explicação passo a passo ilustra as seguintes tarefas:  
  
-   Criando tabelas que contêm o conteúdo de uma palavra controla modelo em tempo de design.  
  
-   Preenchendo um controle de conteúdo de caixa de combinação e um controle de conteúdo de lista suspensa programaticamente.  
  
-   Impedindo que os usuários da edição de uma tabela especificada.  
  
-   Adicionando tabelas para a coleção de blocos de construção de um modelo.  
  
-   Criando um controle de conteúdo que exibe os blocos de construção disponíveis no modelo.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Você precisa dos seguintes componentes para concluir esta instrução passo a passo:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word.  
  
## <a name="creating-a-new-word-template-project"></a>Criar um novo projeto de modelo do Word  
 Crie um modelo do Word para que os usuários podem criar suas próprias cópias facilmente.  
  
#### <a name="to-create-a-new-word-template-project"></a>Para criar um novo projeto de modelo do Word  
  
1.  Criar um projeto de modelo do Word com o nome **MyBuildingBlockTemplate**. No assistente, crie um novo documento na solução. Para obter mais informações, consulte [como: criar projetos do Office no Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Abre o novo modelo do Word no designer e adiciona o **MyBuildingBlockTemplate** projeto **Gerenciador de soluções**.  
  
## <a name="creating-the-employee-table"></a>Criando a tabela Employee  
 Crie uma tabela que contém quatro tipos diferentes de controles de conteúdo em que o usuário pode inserir informações sobre um funcionário.  
  
#### <a name="to-create-the-employee-table"></a>Para criar a tabela employee  
  
1.  No modelo do Word que está hospedado no [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] designer, na faixa de opções, clique no **inserir** guia.  
  
2.  No **tabelas** de grupo, clique em **tabela**e inserir uma tabela com colunas de 2 e 4 linhas.  
  
3.  Digite o texto na primeira coluna, para que ele se parece com a seguinte coluna:  
  
    ||  
    |-|  
    |**Nome do funcionário**|  
    |**Data de contratação**|  
    |**Título**|  
    |**Imagem**|  
  
4.  Clique na primeira célula na segunda coluna (lado **nome de funcionário**).  
  
5.  Na faixa de opções, clique no **desenvolvedor** guia.  
  
    > [!NOTE]  
    >  Se o **desenvolvedor** guia não estiver visível, você deve primeiro mostrá-la. Para obter mais informações, consulte [como: Mostrar a guia Desenvolvedor na faixa de opções](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
6.  No **controles** de grupo, clique no **texto** botão ![PlainTextContentControl](../vsto/media/plaintextcontrol.gif "PlainTextContentControl") para adicionar um <xref:Microsoft.Office.Tools.Word.PlainTextContentControl>para a primeira célula.  
  
7.  Clique na segunda célula na segunda coluna (lado **data de contratação**).  
  
8.  No **controles** de grupo, clique no **seletor de data** botão ![DatePickerContentControl](../vsto/media/datepicker.gif "DatePickerContentControl") para adicionar um <xref:Microsoft.Office.Tools.Word.DatePickerContentControl> segunda célula.  
  
9. Clique na terceira célula na segunda coluna (lado **título**).  
  
10. No **controles** de grupo, clique no **caixa de combinação** botão ![ComboBoxContentControl](../vsto/media/combobox.gif "ComboBoxContentControl") para adicionar um <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl>para a terceira célula.  
  
11. Clique na última célula na segunda coluna (lado **imagem**).  
  
12. No **controles** de grupo, clique no **controle de conteúdo de imagem** botão ![PictureContentControl](../vsto/media/pictcontentcontrol.gif "PictureContentControl") para adicionar um <xref:Microsoft.Office.Tools.Word.PictureContentControl> até a última célula.  
  
## <a name="creating-the-customer-feedback-table"></a>A criação da tabela de comentários do cliente  
 Crie uma tabela que contém três tipos diferentes de controles de conteúdo em que o usuário pode inserir informações de comentários do cliente.  
  
#### <a name="to-create-the-customer-feedback-table"></a>Para criar a tabela de comentários do cliente  
  
1.  No modelo do Word, clique na linha após a tabela de funcionários que você adicionou anteriormente e pressione ENTER para adicionar um novo parágrafo.  
  
2.  Na faixa de opções, clique no **inserir** guia.  
  
3.  No **tabelas** de grupo, clique em **tabela**e insira uma tabela com 2 colunas e 3 linhas.  
  
4.  Digite o texto na primeira coluna, para que ele se parece com a seguinte coluna:  
  
    ||  
    |-|  
    |**Nome do cliente**|  
    |**Satisfação**|  
    |**Comentários**|  
  
5.  Clique na primeira célula da segunda coluna (lado **Customer Name**).  
  
6.  Na faixa de opções, clique no **desenvolvedor** guia.  
  
7.  No **controles** de grupo, clique no **texto** botão ![PlainTextContentControl](../vsto/media/plaintextcontrol.gif "PlainTextContentControl") para adicionar um <xref:Microsoft.Office.Tools.Word.PlainTextContentControl>para a primeira célula.  
  
8.  Clique na segunda célula da segunda coluna (lado **satisfação classificação**).  
  
9. No **controles** de grupo, clique no **lista suspensa** botão ![DropDownListContentControl](../vsto/media/dropdownlist.gif "DropDownListContentControl") para adicionar um <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> segunda célula.  
  
10. Clique na última célula da segunda coluna (lado **comentários**).  
  
11. No **controles** de grupo, clique no **Rich Text** botão ![RichTextContentControl](../vsto/media/richtextcontrol.gif "RichTextContentControl") para adicionar um <xref:Microsoft.Office.Tools.Word.RichTextContentControl>até a última célula.  
  
## <a name="populating-the-combo-box-and-drop-down-list-programmatically"></a>Preenchendo a caixa de combinação caixa e a lista suspensa programaticamente  
 Você pode inicializar controles de conteúdo em tempo de design usando a **propriedades** janela no [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Você também pode inicializá-los em tempo de execução, o que permite que você defina seus estados inicias dinamicamente. Para este passo a passo, usar o código para preencher as entradas na <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> e <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> em tempo de execução para que você possa ver como esses objetos funcionam.  
  
#### <a name="to-modify-the-ui-of-the-content-controls-programmatically"></a>Para modificar a interface do usuário dos controles de conteúdo por meio de programação  
  
1.  Em **Solution Explorer**, clique com botão direito **ThisDocument.cs** ou **ThisDocument. vb**e, em seguida, clique em **Exibir código**.  
  
2.  Adicione o seguinte código para o `ThisDocument` classe. Esse código declara vários objetos que você usará posteriormente neste passo a passo.  
  
     [!code-vb[Trin_ContentControlTemplateWalkthrough#1](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#1)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#1](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#1)]  
  
3.  Adicione o seguinte código para o `ThisDocument_Startup` método o `ThisDocument` classe. Esse código adiciona entradas para o <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> e <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> em tabelas e define o texto de espaço reservado que é exibido em cada um desses controles antes que o usuário edita.  
  
     [!code-vb[Trin_ContentControlTemplateWalkthrough#2](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#2)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#2](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#2)]  
  
## <a name="preventing-users-from-editing-the-employee-table"></a>Impedindo que os usuários editem a tabela Employee  
 Use o <xref:Microsoft.Office.Tools.Word.GroupContentControl> do objeto que você declarado anteriormente para proteger a tabela employee. Depois de proteger a tabela, os usuários ainda podem editar os controles de conteúdo na tabela. No entanto, eles não podem editar o texto na primeira coluna ou modificar a tabela de outras maneiras, como adicionar ou excluir linhas e colunas. Para obter mais informações sobre como usar um <xref:Microsoft.Office.Tools.Word.GroupContentControl> para proteger uma parte de um documento, consulte [controles de conteúdo](../vsto/content-controls.md).  
  
#### <a name="to-prevent-users-from-editing-the-employee-table"></a>Para impedir que usuários editem a tabela employee  
  
1.  Adicione o seguinte código para o `ThisDocument_Startup` método o `ThisDocument` classe, após o código que você adicionou na etapa anterior. Esse código impede que os usuários editando a tabela employee colocando tabela dentro do <xref:Microsoft.Office.Tools.Word.GroupContentControl> objeto que é declarado anteriormente.  
  
     [!code-vb[Trin_ContentControlTemplateWalkthrough#3](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#3)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#3](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#3)]  
  
## <a name="adding-the-tables-to-the-building-block-collection"></a>Adicionando as tabelas na coleção de blocos de construção  
 Adicione as tabelas em uma coleção de blocos de construção de documento no modelo para que os usuários podem inserir as tabelas que você criou no documento. Para obter mais informações sobre os blocos de construção de documento, consulte [controles de conteúdo](../vsto/content-controls.md).  
  
#### <a name="to-add-the-tables-to-the-building-blocks-in-the-template"></a>Para adicionar as tabelas para os blocos de construção do modelo  
  
1.  Adicione o seguinte código para o `ThisDocument_Startup` método o `ThisDocument` classe, após o código que você adicionou na etapa anterior. Esse código adiciona novos blocos de construção que contenha as tabelas para a coleção de Microsoft.Office.Interop.Word.BuildingBlockEntries, que contém todos os blocos de construção reutilizáveis no modelo. Os novos blocos de construção são definidos em uma nova categoria chamada **funcionário e informações de cliente** e recebem o tipo de bloco de construção Microsoft.Office.Interop.Word.WdBuildingBlockTypes.wdTypeCustom1.  
  
     [!code-vb[Trin_ContentControlTemplateWalkthrough#4](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#4)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#4](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#4)]  
  
2.  Adicione o seguinte código para o `ThisDocument_Startup` método o `ThisDocument` classe, após o código que você adicionou na etapa anterior. Esse código exclui as tabelas do modelo. As tabelas não são mais necessárias, porque você adicionou à Galeria de blocos de construção reutilizáveis no modelo. O código primeiro coloca o documento no modo de design para que a tabela employee protegido pode ser excluída.  
  
     [!code-vb[Trin_ContentControlTemplateWalkthrough#5](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#5)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#5](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#5)]  
  
## <a name="creating-a-content-control-that-displays-the-building-blocks"></a>Criando um controle de conteúdo que exibe os blocos de construção  
 Crie um controle de conteúdo que fornece acesso para os blocos de construção (ou seja, as tabelas) que você criou anteriormente. Os usuários podem clicar este controle para adicionar as tabelas para o documento.  
  
#### <a name="to-create-a-content-control-that-displays-the-building-blocks"></a>Para criar um controle de conteúdo que exibe os blocos de construção  
  
1.  Adicione o seguinte código para o `ThisDocument_Startup` método o `ThisDocument` classe, após o código que você adicionou na etapa anterior. Esse código inicializa o <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl> objeto que é declarado anteriormente. O <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl> exibe todos os blocos de construção que são definidos na categoria **funcionário e informações de cliente** com o tipo de bloco de construção Microsoft.Office.Interop.Word.WdBuildingBlockTypes.wdTypeCustom1.  
  
     [!code-vb[Trin_ContentControlTemplateWalkthrough#6](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#6)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#6](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#6)]  
  
## <a name="testing-the-project"></a>O projeto de teste  
 Os usuários podem clicar os controles de galeria de blocos de construção do documento para inserir a tabela employee ou a tabela de comentários do cliente. Os usuários podem digite ou selecione respostas em controles de conteúdo em ambas as tabelas. Os usuários podem modificar outras partes da tabela de comentários do cliente, mas não deve ser capazes de modificar outras partes da tabela employee.  
  
#### <a name="to-test-the-employee-table"></a>Para testar a tabela employee  
  
1.  Pressione F5 para executar o projeto.  
  
2.  Clique em **escolha o primeiro bloco de construção** para exibir o primeiro controle conteúdo da Galeria de blocos de construção.  
  
3.  Clique na seta suspensa ao lado de **personalizado Galeria 1** título no controle e selecione **tabela Employee**.  
  
4.  Clique na célula à direita do **nome de funcionário** da célula e digite um nome.  
  
     Verifique se que você pode adicionar texto apenas para essa célula. O <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> permite aos usuários adicionar apenas texto, não outros tipos de conteúdo como arte ou uma tabela.  
  
5.  Clique na célula à direita do **data de contratação** célula e selecione uma data no selecionador de data.  
  
6.  Clique na célula à direita do **título** célula e selecione um dos títulos do trabalho na caixa de combinação.  
  
     Opcionalmente, digite o nome de um cargo que não está na lista. Isso é possível porque o <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> permite que os usuários para selecionar em uma lista de entradas ou digite suas próprias entradas.  
  
7.  Clique no ícone na célula à direita do **imagem** célula e navegue até uma imagem para exibi-lo.  
  
8.  Tente adicionar linhas ou colunas à tabela e tente excluir linhas e colunas da tabela. Verifique se que você não pode modificar a tabela. O <xref:Microsoft.Office.Tools.Word.GroupContentControl> impede que você faça modificações.  
  
#### <a name="to-test-the-customer-feedback-table"></a>Para testar a tabela de comentários do cliente  
  
1.  Clique em **escolha o segundo bloco de construção** para exibir o segundo controle conteúdo da Galeria de blocos de construção.  
  
2.  Clique na seta suspensa ao lado de **personalizado Galeria 1** título no controle e selecione **tabela Customer**.  
  
3.  Clique na célula à direita do **Customer Name** da célula e digite um nome.  
  
4.  Clique na célula à direita do **satisfação classificação** célula e selecione uma das opções disponíveis.  
  
     Verifique se que você não pode digitar sua própria entrada. O <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> permite que os usuários somente selecionar em uma lista de entradas.  
  
5.  Clique na célula à direita do **comentários** da célula e digite alguns comentários.  
  
     Opcionalmente, adicione algum conteúdo diferente de texto, como arte ou uma tabela inserida. Isso é possível porque o <xref:Microsoft.Office.Tools.Word.RichTextContentControl> permite que os usuários adicionem conteúdo diferente de texto.  
  
6.  Verifique se que você pode adicionar linhas ou colunas à tabela, e que você pode excluir linhas e colunas da tabela. Isso é possível porque a tabela não tiver protegido, colocando-o um <xref:Microsoft.Office.Tools.Word.GroupContentControl>.  
  
7.  Feche o modelo.  
  
## <a name="next-steps"></a>Próximas etapas  
 Você pode aprender mais sobre como usar os controles de conteúdo deste tópico:  
  
-   Vincule controles de conteúdo a partes do XML, também chamado de partes XML personalizadas que são inseridos em um documento. Para obter mais informações, consulte [passo a passo: associando controles de conteúdo a partes do XML personalizado](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md).  
  
## <a name="see-also"></a>Consulte também  
 [Automatizando o Word usando objetos estendidos](../vsto/automating-word-by-using-extended-objects.md)   
 [Controles de conteúdo](../vsto/content-controls.md)   
 [Como: adicionar controles Content a documentos do Word](../vsto/how-to-add-content-controls-to-word-documents.md)   
 [Como: proteger partes de documentos usando controles de conteúdo](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md)   
 [Itens de host e visão geral dos controles de Host](../vsto/host-items-and-host-controls-overview.md)   
 [Limitações programáticas de itens de Host e controles de Host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Adicionando controles a documentos do Office no tempo de execução](../vsto/adding-controls-to-office-documents-at-run-time.md)  
  
  