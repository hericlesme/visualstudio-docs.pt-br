---
title: 'Passo a passo: Criando uma guia usando o XML da faixa de opções | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Ribbon [Office development in Visual Studio], tabs
- customizing the Ribbon, tabscustom Ribbon, tabs
- Ribbon [Office development in Visual Studio], XML
- XML [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio], customizing
- Custom tab [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 759aee9692ee905e33ce55ff068b74d4a289c78a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-creating-a-custom-tab-by-using-ribbon-xml"></a>Instruções passo a passo: criando uma guia usando o XML da faixa de opções
  Este passo a passo demonstra como criar uma guia faixa de opções personalizada usando o **da faixa de opções (XML)** item.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
 Esta explicação passo a passo ilustra as seguintes tarefas:  
  
-   Adicionando botões para o **Add-Ins** guia. O **Add-Ins** guia é o padrão que é definido no arquivo XML da faixa de opções.  
  
-   Automatizando o Microsoft Office Word usando os botões a **Add-Ins** guia.  
  
> [!NOTE]  
>  Seu computador pode mostrar diferentes nomes ou locais para alguns dos elementos de interface do usuário do Visual Studio nas instruções a seguir. A edição do Visual Studio que você possui e as configurações que você usa determinam esses elementos. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Você precisa dos seguintes componentes para concluir esta instrução passo a passo:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word.  
  
## <a name="creating-the-project"></a>Criando o Projeto  
 A primeira etapa é criar um projeto de suplemento do VSTO do Word. Você personalizará posteriormente o **Add-Ins** guia deste documento.  
  
#### <a name="to-create-a-new-project"></a>Para criar um novo projeto  
  
1.  Criar um **palavra em** projeto com o nome **MyRibbonAddIn**.  
  
     Para obter mais informações, consulte [como: criar projetos do Office no Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Abre o **ThisAddIn.cs** ou **ThisAddIn** arquivo de código e adiciona o **MyRibbonAddIn** projeto **Gerenciador de soluções**.  
  
## <a name="creating-the-vsto-add-ins-tab"></a>Criando a guia de suplementos do VSTO  
 Para criar o **Add-Ins** guia, adicione um **da faixa de opções (XML)** item ao seu projeto. Posteriormente neste passo a passo, você irá adicionar alguns botões para este guia.  
  
#### <a name="to-create-the-add-ins-tab"></a>Para criar a guia de suplementos  
  
1.  No menu **Projeto**, clique em **Adicionar Novo Item**.  
  
2.  No **Adicionar Novo Item** caixa de diálogo, selecione **da faixa de opções (XML)**.  
  
3.  Alterar o nome da nova faixa de opções para **MyRibbon**e clique em **adicionar**.  
  
     O **MyRibbon.cs** ou **MyRibbon.vb** arquivo é aberto no designer. Um arquivo XML denominado **MyRibbon.xml** também é adicionado ao seu projeto.  
  
4.  Em **Solution Explorer**, clique com botão direito **ThisAddin.cs** ou **ThisAddIn**e, em seguida, clique em **Exibir código**.  
  
5.  Adicione o seguinte código para o **ThisAddin** classe. Esse código substitui o método CreateRibbonExtensibilityObject e retorna a classe de XML da faixa de opções para o aplicativo do Office.  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.cs#1)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.vb#1)]  
  
6.  Em **Solution Explorer**, com o botão direito do **MyRibbonAddIn** do projeto e, em seguida, clique em **criar**. Verifique se o projeto é compilado sem erros.  
  
## <a name="adding-buttons-to-the-add-ins-tab"></a>Adicionando botões para a guia de suplementos  
 A meta para o suplemento do VSTO é fornecer aos usuários uma maneira de adicionar o texto clichê e uma tabela específica para o documento ativo. Para fornecer a interface do usuário, adicione dois botões para o **Add-Ins** guia modificando o arquivo XML da faixa de opções. Posteriormente neste passo a passo, você definirá os métodos de retorno de chamada para os botões. Para obter mais informações sobre o arquivo XML da faixa de opções, consulte [XML da faixa de opções](../vsto/ribbon-xml.md).  
  
#### <a name="to-add-buttons-to-the-add-ins-tab"></a>Para adicionar os botões para a guia Add-Ins  
  
1.  Em **Solution Explorer**, clique com botão direito **MyRibbon.xml** e, em seguida, clique em **abrir**.  
  
2.  Substitua o conteúdo do **guia** elemento com o XML a seguir. Esse XML altera o rótulo do grupo de controle padrão para **conteúdo**, e adiciona dois novos botões com os rótulos **inserir texto** e **Inserir tabela**.  
  
    ```  
    <tab idMso="TabAddIns">  
        <group id="ContentGroup" label="Content">  
            <button id="textButton" label="Insert Text"  
                 screentip="Text" onAction="OnTextButton"  
                 supertip="Inserts text at the cursor location."/>  
            <button id="tableButton" label="Insert Table"  
                 screentip="Table" onAction="OnTableButton"  
                 supertip="Inserts a table at the cursor location."/>  
        </group>  
    </tab>  
    ```  
  
## <a name="automating-the-document-by-using-the-buttons"></a>Automatizando o documento usando os botões  
 Você deve adicionar `onAction` métodos de retorno de chamada para o **inserir texto** e **Inserir tabela** botões para executar ações quando o usuário clica neles. Para obter mais informações sobre métodos de retorno de chamada para controles de faixa de opções, consulte [XML da faixa de opções](../vsto/ribbon-xml.md).  
  
#### <a name="to-add-callback-methods-for-the-buttons"></a>Para adicionar métodos de retorno de chamada para os botões  
  
1.  Em **Solution Explorer**, clique com botão direito **MyRibbon.cs** ou **MyRibbon.vb**e, em seguida, clique em **abrir**.  
  
2.  Adicione o seguinte código na parte superior do **MyRibbon.cs** ou **MyRibbon.vb** arquivo. Esse código cria um alias para o <xref:Microsoft.Office.Interop.Word> namespace.  
  
     [!code-csharp[Trin_RibbonButtons#1](../vsto/codesnippet/CSharp/Trin_RibbonButtons/MyRibbon.cs#1)]
     [!code-vb[Trin_RibbonButtons#1](../vsto/codesnippet/VisualBasic/Trin_RibbonButtons/MyRibbon.vb#1)]  
  
3.  Adicione o seguinte método à classe `MyRibbon`. Este é um método de retorno de chamada para o **inserir texto** botão que adiciona uma cadeia de caracteres para o documento ativo no local atual do cursor.  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#2](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.cs#2)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#2](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.vb#2)]  
  
4.  Adicione o seguinte método à classe `MyRibbon`. Este é um método de retorno de chamada para o **Inserir tabela** botão que adiciona uma tabela para o documento ativo no local atual do cursor.  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#3](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.cs#3)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#3](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.vb#3)]  
  
## <a name="testing-the-vsto-add-in"></a>Testando o suplemento do VSTO  
 Quando você executar o projeto, o Word é aberto e na guia denominada **Add-Ins** aparece na faixa de opções. Clique o **inserir texto** e **Inserir tabela** botões o **Add-Ins** tab para testar o código.  
  
#### <a name="to-test-your-vsto-add-in"></a>Para testar o suplemento do VSTO  
  
1.  Pressione F5 para executar o projeto.  
  
2.  Confirme se o **Add-Ins** guia ficará visível na faixa de opções.  
  
3.  Clique o **Add-Ins** guia.  
  
4.  Confirme se o **conteúdo** grupo está visível na faixa de opções.  
  
5.  Clique o **inserir texto** no botão de **conteúdo** grupo.  
  
     Uma cadeia de caracteres é adicionada ao documento no local atual do cursor.  
  
6.  Clique o **Inserir tabela** no botão de **conteúdo** grupo.  
  
     Uma tabela é adicionada ao documento no local atual do cursor.  
  
## <a name="next-steps"></a>Próximas etapas  
 Você pode aprender mais sobre como personalizar a interface do usuário do Office com estes tópicos:  
  
-   Personalize a faixa de opções de outro aplicativo do Office. Para obter mais informações sobre os aplicativos que oferecem suporte a personalização da faixa de opções, consulte [visão geral da faixa de opções](../vsto/ribbon-overview.md).  
  
-   Personalize a faixa de opções de um aplicativo do Office usando o Designer de faixa de opções. Para obter mais informações, consulte [Fitas](../vsto/ribbon-designer.md).  
  
-   Crie um painel de ações personalizadas. Para obter mais informações, consulte [visão geral do painel de ações](../vsto/actions-pane-overview.md).  
  
-   Personalize a interface do usuário do Microsoft Office Outlook usando regiões de formulário do Outlook. Para obter mais informações, consulte [passo a passo: Criando uma região de formulário do Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md).  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral da faixa de opções](../vsto/ribbon-overview.md)   
 [XML da faixa de opções](../vsto/ribbon-xml.md)   
 [Instruções passo a passo: criando uma guia personalizada usando o designer da faixa de opções](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)  
  
  