---
title: "Passo a passo: Criando uma guia personalizada usando o Designer de faixa de opções | Microsoft Docs"
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
- actions panes [Office development in Visual Studio], controlling from Ribbon
- Ribbon [Office development in Visual Studio], customizing
- Ribbon Designer [Office development in Visual Studio]
- customizing the Ribbon, tabs
- custom Ribbon, tabs
- Custom tab [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: cdbbd7ee286c97a986e89ccdb5bdcfdde4ef7578
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer"></a>Instruções passo a passo: criando uma guia usando o designer da faixa de opções
  Usando o Designer de faixa de opções, você pode criar uma guia personalizada e, em seguida, adicionar e posicionar controles nele.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Esta explicação passo a passo ilustra as seguintes tarefas:  
  
-   [Criando painéis de ações](#BKMK_CreateActionsPanes).  
  
-   [Criando uma guia](#BKMK_CreateCustomTab).  
  
-   [Ocultando e mostrando painéis de ações, usando os botões na guia personalizada](#BKMK_HideShowActionsPane).  
  
> [!NOTE]  
>  Seu computador pode mostrar diferentes nomes ou locais para alguns dos elementos de interface do usuário do Visual Studio nas instruções a seguir. A edição do Visual Studio que você possui e as configurações que você usa determinam esses elementos. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Você precisa dos seguintes componentes para concluir esta instrução passo a passo:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Excel  
  
## <a name="creating-an-excel-workbook-project"></a>Criando um projeto de pasta de trabalho do Excel  
 As etapas para usar o Designer de faixa de opções são quase idênticas para todos os aplicativos do Office. Este exemplo usa uma pasta de trabalho do Excel.  
  
#### <a name="to-create-an-excel-workbook-project"></a>Para criar um projeto de pasta de trabalho do Excel  
  
-   Criar um projeto de pasta de trabalho do Excel com o nome **MyExcelRibbon**. Para obter mais informações, consulte [como: criar projetos do Office no Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio abre a nova pasta de trabalho no designer e adiciona o **MyExcelRibbon** projeto **Gerenciador de soluções**.  
  
##  <a name="BKMK_CreateActionsPanes"></a>Criando painéis de ações  
 Adicione dois painéis de ações personalizadas ao projeto. Posteriormente, você irá adicionar botões de mostram e ocultar esses painéis de ações para a guia personalizada.  
  
#### <a name="to-create-actions-panes"></a>Para criar painéis de ações  
  
1.  No menu **Projeto**, escolha **Adicionar Novo Item**.  
  
2.  No **Adicionar Novo Item** caixa de diálogo, selecione **ActionsPaneControl**e, em seguida, escolha **adicionar**.  
  
     O **ActionsPaneControl1.cs** ou **ActionsPaneControl1.vb** arquivo é aberto no designer.  
  
3.  Do **controles comuns** guia do **caixa de ferramentas**, adicionar um rótulo para a superfície do designer.  
  
4.  No **propriedades** janela, defina o **texto** propriedade Label1 para **1 do painel de ações**.  
  
5.  Repita as etapas 1 a 5 para criar um painel de ações de segundo e um rótulo. Definir o **texto** propriedade do rótulo do segundo para **2 do painel de ações**.  
  
##  <a name="BKMK_CreateCustomTab"></a>Criando uma guia  
 Uma das diretrizes de design de aplicativo do Office é que os usuários sempre devem ter o controle de interface do usuário do aplicativo do Office. Para adicionar esse recurso para os painéis de ações, você pode adicionar botões de mostram e ocultar cada painel de ações de uma guia na faixa de opções. Para criar uma guia personalizada, adicione uma **faixa de opções (Visual Designer)** item ao projeto. O designer ajuda a adicionar e posicionar controles, definir propriedades de controle e tratar eventos de controle.  
  
#### <a name="to-create-a-custom-tab"></a>Para criar uma guia personalizada  
  
1.  No menu **Projeto**, escolha **Adicionar Novo Item**.  
  
2.  No **Adicionar Novo Item** caixa de diálogo, selecione **faixa de opções (Visual Designer)**.  
  
3.  Alterar o nome da nova faixa de opções para **MyRibbon**e escolha **adicionar**.  
  
     O **MyRibbon.cs** ou **MyRibbon.vb** arquivo é aberto no Designer de faixa de opções e exibe um guia padrão e o grupo.  
  
4.  No Designer de faixa de opções, escolha a guia padrão.  
  
5.  No **propriedades** janela, expanda o **ControlId** propriedade e, em seguida, defina o **ControlIdType** propriedade **personalizado**.  
  
6.  Definir o **rótulo** propriedade **My Custom Tab**.  
  
7.  No Designer de faixa de opções, escolha **group1**.  
  
8.  No **propriedades** janela, defina **rótulo** para **Manager do painel de ações**.  
  
9. Do **controles de faixa de opções do Office** guia do **caixa de ferramentas**, arraste um botão para **group1**.  
  
10. Selecione **button1**.  
  
11. No **propriedades** janela, defina **rótulo** para **Mostrar 1 do painel de ações**.  
  
12. Adicionar um segundo botão **group1**e defina o **rótulo** propriedade **Mostrar 2 do painel de ações**.  
  
13. Do **controles de faixa de opções do Office** guia do **caixa de ferramentas**, arraste um **ToggleButton** controle para **group1**.  
  
14. Definir o **rótulo** propriedade **ocultar painel de ações**.  
  
##  <a name="BKMK_HideShowActionsPane"></a>Ocultando e mostrando painéis de ações, usando os botões na guia personalizada  
 A última etapa é adicionar o código que responde ao usuário. Adicionar manipuladores de eventos para o <xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click> eventos de dois botões e o <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> eventos do botão de alternância. Adicione código para esses manipuladores de eventos para habilitar ocultando e mostrando os painéis de ações.  
  
#### <a name="to-hide-and-show-actions-panes-by-using-buttons-in-the-custom-tab"></a>Para ocultar e Mostrar painéis de ações, usando os botões na guia personalizada  
  
1.  Em **Solution Explorer**, abra o menu de atalho para MyRibbon.cs ou MyRibbon.vb e, em seguida, escolha **Exibir código**.  
  
2.  Adicione o seguinte código na parte superior do `MyRibbon` classe. Esse código cria dois objetos do painel de ações.  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab#1](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab/MyRibbon.cs#1)]
     [!code-vb[Trin_Ribbon_Custom_Tab#1](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab/MyRibbon.vb#1)]  
  
3.  Substitua o `MyRibbon_Load` método com o código a seguir. Esse código adiciona os objetos do painel de ações para o <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> coleta e oculta os objetos da exibição. O código do Visual c# também anexa delegados para vários eventos de controle de faixa de opções.  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab#2](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab/MyRibbon.cs#2)]
     [!code-vb[Trin_Ribbon_Custom_Tab#2](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab/MyRibbon.vb#2)]  
  
4.  Adicione os seguintes métodos de manipulador de eventos de três para o `MyRibbon` classe. Esses métodos controlam o <xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click> eventos de dois botões e o <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> eventos do botão de alternância. Manipuladores de eventos para button1 e button2 mostram painéis de ações alternativas. O manipulador de eventos para toggleButton1 mostra e oculta o painel de ações ativa.  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab#3](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab/MyRibbon.cs#3)]
     [!code-vb[Trin_Ribbon_Custom_Tab#3](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab/MyRibbon.vb#3)]  
  
## <a name="testing-the-custom-tab"></a>A guia de teste  
 Quando você executa o projeto, o início do Excel e o **My Custom Tab** guia aparece na faixa de opções. Escolha os botões na **My Custom Tab** para mostrar e ocultar os painéis de ações.  
  
#### <a name="to-test-the-custom-tab"></a>Para testar a guia personalizada  
  
1.  Pressione F5 para executar o projeto.  
  
2.  Escolha o **My Custom Tab** guia.  
  
3.  No **Gerenciador de painel de ações personalizadas** de grupo, escolha **Mostrar 1 do painel de ações**.  
  
     O painel de ações aparece e exibe o rótulo **1 do painel de ações**.  
  
4.  Escolha **Mostrar painel de ações 2**.  
  
     O painel de ações aparece e exibe o rótulo **2 do painel de ações**.  
  
5.  Escolha **ocultar painel de ações**.  
  
     Os painéis de ações não são visíveis.  
  
## <a name="next-steps"></a>Próximas etapas  
 Você pode aprender mais sobre como personalizar a interface do usuário do Office com estes tópicos:  
  
-   Adicione baseado no contexto da interface do usuário para qualquer personalização no nível do documento. Para obter mais informações, consulte [visão geral do painel de ações](../vsto/actions-pane-overview.md).  
  
-   Estenda um formulário personalizado ou padrão do Microsoft Office Outlook. Para obter mais informações, consulte [passo a passo: Criando uma região de formulário do Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md).  
  
## <a name="see-also"></a>Consulte também  
 [Acessando a faixa de opções em tempo de execução](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Visão geral da faixa de opções](../vsto/ribbon-overview.md)   
 [Designer de faixa de opções](../vsto/ribbon-designer.md)   
 [Personalizando uma faixa de opções para Outlook](../vsto/customizing-a-ribbon-for-outlook.md)   
 [Como: personalizar a faixa de opções](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [Como: alterar a posição de uma guia na faixa de opções](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)   
 [Como: personalizar uma guia interna](../vsto/how-to-customize-a-built-in-tab.md)   
 [Como: adicionar controles à exibição Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)   
 [Visão geral do modelo de objeto da faixa de opções](../vsto/ribbon-object-model-overview.md)  
  
  