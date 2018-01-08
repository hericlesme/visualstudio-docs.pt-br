---
title: "Designer de faixa de opções | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: Designer_Microsoft.VisualStudio.Tools.Office.Ribbon.Design.RibbonDesigner
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom Ribbon, about Ribbon Designer
- controls [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio], controls
- customizing the Ribbon, about Ribbon Designer
- Ribbon [Office development in Visual Studio], visual designer
- customizing the Ribbon
- custom Ribbon
- designers [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio], customizing
- Ribbon [Office development in Visual Studio], common tasks
- Ribbon Designer [Office development in Visual Studio]
- read-only properties
- Ribbon [Office development in Visual Studio], shortcut keys
ms.assetid: 26617206-f4da-416f-a18a-d817b2d4872d
caps.latest.revision: "79"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 2655cd8f8c75f9c10063a1b85d2390b153782d85
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ribbon-designer"></a>Designer da faixa de opções
  O Designer de faixa de opções é uma tela de design visual. Use o Designer de faixa de opções para adicionar guias personalizadas, grupos e controles da faixa de opções de um aplicativo do Microsoft Office.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
 Para abrir o Designer de faixa de opções, adicione um **faixa de opções (Visual Designer)** item ao seu projeto. Você pode usar as ferramentas de design para as seguintes tarefas:  
  
-   [Criar o layout de faixa de opções](#DesigningRibbonLayout)  
  
-   [Manipular eventos e definir propriedades de controle](#HandleEventsSetProperties)  
  
-   [Adicionar controles à exibição Backstage](#CustomizingMicrosoftOfficeButton)  
  
> [!NOTE]  
>  Há algumas tarefas que você não pode realizar usando o Designer de faixa de opções. Para obter mais informações sobre essas tarefas e como você pode realizá-las, consulte [visão geral da faixa de opções](../vsto/ribbon-overview.md).  
  
 ![link para vídeo](../vsto/media/playvideo.gif "link para vídeo") para uma demonstração de vídeo relacionada, consulte [como fazer: usar o Designer de faixa de opções para personalizar a faixa de opções no Outlook?](http://go.microsoft.com/fwlink/?LinkID=130312).  
  
## <a name="adding-a-ribbon-visual-designer-item-to-a-project"></a>Adicionar um Item de faixa de opções (Visual Designer) a um projeto  
 Para usar o Designer de faixa de opções, adicione um novo **faixa de opções (Visual Designer)** item ao seu projeto. Para obter mais informações, consulte [como: obter iniciado Personalizando a faixa de opções](../vsto/how-to-get-started-customizing-the-ribbon.md).  
  
 Quando você adiciona um novo **faixa de opções (Visual Designer)** item, o Visual Studio adiciona automaticamente os arquivos a seguir ao seu projeto:  
  
-   Um arquivo de código da faixa de opções. Este arquivo tem o nome que você especificar para o **faixa de opções (Visual Designer)** item o **Adicionar Novo Item** caixa de diálogo. Adicione código para tratar eventos de faixa de opções para esse arquivo.  
  
-   Um arquivo de código de Designer de faixa de opções. Este arquivo contém o código gerado pelo Designer de faixa de opções e não deve ser editado diretamente.  
  
-   Um arquivo de recurso. Este arquivo contém os valores de propriedade de cada controle na faixa de opções.  
  
 Se você já tiver um **faixa de opções (Visual Designer)** item de outro projeto, você pode reutilizá-lo em seu projeto atual usando o **Add Existing Item** caixa de diálogo.  
  
##  <a name="DesigningRibbonLayout"></a>Criando uma faixa de opções  
 Há três maneiras de abrir o Designer de faixa de opções:  
  
-   Em **Solution Explorer**, clique duas vezes no arquivo de código da faixa de opções.  
  
-   Em **Solution Explorer**, clique no arquivo de código da faixa de opções e, em seguida, clique em **Designer de exibição**.  
  
-   Em **Solution Explorer**, selecione o arquivo de código da faixa de opções e, em seguida, clique em **Designer** no **exibição** menu.  
  
 O Designer de faixa de opções contém uma guia padrão e o grupo. Você pode remover a guia padrão e o grupo do Designer de faixa de opções. Para remover o grupo padrão, clique com botão direito **Group1**e, em seguida, clique em **excluir**. Para remover a guia padrão, clique em uma área vazia da superfície de design e, em seguida, clique em **Remover guia de faixa de opções**.  
  
 Você também pode adicionar guias personalizadas, grupos e controles para o Designer de faixa de opções. Você pode encontrar esses controles no **caixa de ferramentas**, no **controles de faixa de opções do Office** grupo. Há três maneiras de adicionar controles a partir de **controles de faixa de opções do Office** grupo para o Designer de faixa de opções:  
  
-   Arraste um controle para a área apropriada no Designer de faixa de opções.  
  
-   Clique em um controle e, em seguida, clique em uma área apropriada no Designer de faixa de opções.  
  
-   Selecione uma área apropriada no designer e, em seguida, clique duas vezes em um controle no **caixa de ferramentas**.  
  
### <a name="ribbon-design-workflow"></a>Fluxo de trabalho de Design de faixa de opções  
 Siga estas etapas básicas para criar o layout de faixa de opções:  
  
1.  [Adicionar uma guia a faixa de opções](#AddTabToRibbon).  
  
2.  [Adicionar grupos para a guia](#AddGroupsToTab).  
  
3.  [Adicionar controles aos grupos](#AddControlsToGroups).  
  
 Controles podem ser descartados somente nos grupos; Você não pode arrastar um controle diretamente a uma guia ou a faixa de opções. Grupos podem ser descartados somente nas guias; Você não pode arrastar um grupo diretamente a uma faixa de opções.  
  
 Organize controles arrastando-os para as posições corretas. Você pode definir as propriedades de um controle usando o **propriedades** janela.  
  
 Você não pode arrastar controles de uma guia para outra na faixa de opções. Se você quiser mover um controle para outra guia, você deve usar o **Recortar** comando para remover o controle de uma guia e, em seguida, cole o controle em outra guia. Se você recortar o controle e colá-lo, o manipulador de eventos para de funcionar. Você pode reconectar o manipulador de eventos de **propriedades** janela. Para obter mais informações, consulte [janela propriedades](/visualstudio/ide/reference/properties-window).  
  
###  <a name="AddTabToRibbon"></a>Adicionando guias personalizadas para a faixa de opções  
 Há três maneiras de adicionar uma guia personalizada à faixa de opções:  
  
-   Adicionar uma guia do **caixa de ferramentas**.  
  
-   Clique com botão direito do Designer de faixa de opções e, em seguida, clique em **Adicionar guia de faixa de opções**.  
  
-   Abra o **guia Editor de coleção**e, em seguida, clique em **adicionar**.  
  
     Para abrir o **guia Editor de coleção**, no **propriedades** janela, selecione o **guias** propriedade e, em seguida, clique no botão de reticências ![ASP.NET para dispositivos móveis Elipse Designer](../sharepoint/media/mwellipsis.gif "elipse ASP.NET Mobile Designer").  
  
 Depois de adicionar uma guia, você pode adicionar grupos para conter controles.  
  
#### <a name="removing-custom-tabs-from-the-ribbon"></a>Removendo guias personalizadas na faixa de opções  
 Há três maneiras de remover uma guia da faixa de opções:  
  
-   Clique com botão direito do designer e, em seguida, clique em **Remover guia de faixa de opções**.  
  
-   No **comandos** painel do **propriedades** janela, clique em **Remover guia de faixa de opções**.  
  
-   Abra o **guia Editor de coleção**, selecione a guia e, em seguida, clique em **remover**.  
  
#### <a name="changing-the-position-of-a-tab-on-the-ribbon"></a>Alterar a posição de uma guia na faixa de opções  
 Você pode alterar a ordem das guias personalizadas em uma faixa de opções. Você também pode posicionar guias personalizadas antes ou depois de uma guia interna na faixa de opções. Para obter mais informações, consulte [como: alterar a posição de uma guia na faixa de opções](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md).  
  
#### <a name="customizing-built-in-tabs-on-the-ribbon"></a>Personalizando guias internas da faixa de opções  
 Uma guia interna é um que já está na faixa de opções de um aplicativo do Microsoft Office. Por exemplo, o **dados** guia é uma guia interna no Excel.  
  
 Você pode adicionar grupos e controles a uma guia interna. Por padrão, um grupo personalizado aparece como o último grupo em uma guia interna, que você pode movê-la antes ou depois de um grupo interno na guia.  
  
 Não é possível remover os grupos internos.  
  
 Para obter detalhes sobre como personalizar uma guia interna, consulte [como: personalizar uma guia interna](../vsto/how-to-customize-a-built-in-tab.md).  
  
###  <a name="AddGroupsToTab"></a>Adicionar grupos a uma guia  
 Os grupos organizam logicamente controles na faixa de opções. Adicione grupos às guias. Adicione todos os outros controles para o grupo.  
  
###  <a name="AddControlsToGroups"></a>Adicionando controles a grupos  
 Adicione um ou mais controles a um grupo. A tabela a seguir descreve cada controle.  
  
|Controle|Descrição|  
|-------------|-----------------|  
|**Caixa**|Um contêiner que organiza os controles em um grupo. Você pode adicionar qualquer controle a uma caixa, exceto um separador, um grupo ou uma guia. Uma caixa pode ser horizontal ou vertical.|  
|**Button**|Um botão que inicia uma ação. Você pode adicionar um botão a um grupo, um grupo de botões, uma lista suspensa, uma galeria, um menu ou um botão de divisão.|  
|**Grupo de botões**|Um grupo que contém um ou mais botões, botões de alternância, menus, botões de divisão e galerias. Você pode adicionar um grupo de botões para um grupo ou um menu.|  
|**CheckBox**|Uma caixa que é marcada ou desmarcada para ativar ou desativar uma opção.|  
|**ComboBox**|Uma caixa de edição com uma caixa de listagem anexada. Usuários podem digitar ou selecionar sua preferência. A caixa exibe a seleção atual. Use o <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.Items%2A> propriedade para adicionar e remover itens em tempo de execução antes ou depois que a faixa de opções é carregada no aplicativo do Office.|  
|**Lista suspensa**|Uma lista de itens que o usuário pode selecionar. O usuário não é possível digitar um novo item em uma lista suspensa.<br /><br /> Use o <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.Items%2A> propriedade para adicionar itens à lista. Você pode adicionar e remover itens em tempo de execução.<br /><br /> Use o <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.Buttons%2A> propriedade a adicionar os botões à lista. No entanto, você não pode adicionar e remover botões em tempo de execução depois que a faixa de opções é carregada no aplicativo do Office.|  
|**EditBox**|Uma caixa em que o usuário pode digitar o texto.|  
|**Galeria**|Um menu que apresenta uma matriz ou grade de opções visuais do qual os usuários podem selecionar. Você pode controlar o layout das seleções no menu. Use o <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ColumnCount%2A> e <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.RowCount%2A> propriedades para especificar o número de linhas e colunas que exibição os itens e os botões da Galeria.|  
|**Rótulo**|Texto que você pode usar para identificar os controles da faixa de opções.|  
|**Menu**|Uma lista suspensa que pode conter qualquer um dos seguintes controles:<br /><br /> -Botão<br />-Caixa de seleção<br />-Galeria<br />-Menu<br />-Botão de divisão<br />-Botão de alternância<br />-Separador<br /><br /> Para adicionar um controle a um menu no Designer de faixa de opções, clique na seta para baixo no menu para expor a superfície de design do menu. Em seguida, você pode arrastar os controles de faixa de opções do **caixa de ferramentas** para o menu. Para organizar controles, arraste-os para as posições desejadas.<br /><br /> Para adicionar controles para o <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu> depois que a faixa de opções é carregada no aplicativo do Office, você deve definir o <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu.Dynamic%2A> propriedade **true** antes que a faixa de opções é carregada. Para obter informações sobre como fazer isso, consulte [visão geral do modelo de objeto de faixa de opções](../vsto/ribbon-object-model-overview.md).|  
|**Separador**|Uma barra fina usada para separar itens em uma lista. Quando adicionada a um grupo, a barra é vertical. Quando adicionada a um menu, a barra é horizontal.|  
|**SplitButton**|Um botão com um menu anexado. Um botão de divisão pode conter qualquer um dos seguintes controles:<br /><br /> -Botão<br />-Caixa de seleção<br />-Galeria<br />-Menu<br />-Botão de divisão<br />-Botão de alternância<br />-Separador<br /><br /> Como o menu do botão de divisão tem sua própria superfície de design. No entanto, ao contrário de um menu, só é possível atualizar os itens em um botão de divisão para a faixa de opções é carregada no aplicativo do Office. Para obter informações sobre como atualizar os itens em um botão de divisão, consulte [visão geral do modelo de objeto de faixa de opções](../vsto/ribbon-object-model-overview.md).|  
|**ToggleButton**|Um botão que aparece pressionado ou não pressionado.|  
  
##  <a name="HandleEventsSetProperties"></a>Manipulação de eventos e definir propriedades  
 O Designer de faixa de opções permite que você defina propriedades de controle em tempo de design usando a **propriedades** janela. Além disso, a faixa de opções expõe um modelo de objeto fortemente tipada que você pode usar para obter e definir as propriedades de controles de faixa de opções em tempo de execução.  
  
 Clique duas vezes em qualquer controle no designer para abrir um manipulador de eventos para o evento padrão do controle. Você pode criar manipuladores de eventos para todos os outros eventos de controle usando o **propriedades** janela.  
  
 Eventos de faixa de opções e propriedades estão localizadas no <xref:Microsoft.Office.Tools.Ribbon> namespace. O **faixa de opções (Visual Designer)** item automaticamente adiciona uma referência a esse assembly no projeto e insere apropriada **usando** ou **Imports** instrução na parte superior o faixa de opções do arquivo de código.  
  
 Para obter informações sobre a manipulação de eventos de faixa de opções e definindo as propriedades de controles de faixa de opções em tempo de execução, consulte [visão geral do modelo de objeto de faixa de opções](../vsto/ribbon-object-model-overview.md).  
  
##  <a name="CustomizingMicrosoftOfficeButton"></a>Personalizando a exibição Backstage  
 Você pode usar o Designer de faixa de opções para adicionar controles ao menu aberto quando você clica o **arquivo** guia. Esse menu é chamado de modo de exibição Backstage.  
  
 Você não pode posicionar controles antes ou depois de controles internos usando o designer de faixa de opções. Um controle interno é um controle que já aparece no modo de exibição Backstage. Se você desejar posicionar controles antes ou depois de controles internos, você deve usar o XML da faixa de opções. Para obter mais informações sobre **da faixa de opções (XML)**, consulte [XML da faixa de opções](../vsto/ribbon-xml.md). Para obter mais informações sobre como personalizar o modo de exibição Backstage, consulte [introdução para o modo de exibição do Office 2010 Backstage para desenvolvedores](http://go.microsoft.com/fwlink/?LinkId=182189) e [personalizar a exibição do Office 2010 Backstage para desenvolvedores](http://go.microsoft.com/fwlink/?LinkId=182188).  
  
 [!INCLUDE[appliesto_ribbon_2010](../vsto/includes/appliesto-ribbon-2010-md.md)]  
  
 Para obter informações sobre como adicionar controles à exibição Backstage, consulte [como: adicionar controles à exibição Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md).  
  
##  <a name="Accessibility"></a>Acessibilidade no Designer de faixa de opções  
 Você pode usar atalhos de teclado para mover os controles no Designer de faixa de opções. Alguns atalhos de teclado se aplicam a todos os controles e alguns se aplicam somente aos controles que têm menus.  
  
 Os atalhos de teclado que se aplicam a todos os controles são mostrados na tabela a seguir.  
  
|Ação|Atalho de teclado|  
|------------|-----------------------|  
|Mova um controle antes do controle anterior na lista.|CTRL + SETA PARA CIMA<br /><br /> CTRL + ESQUERDA|  
|Mova um controle após o próximo controle na lista.|CTRL + SETA PARA BAIXO<br /><br /> CTRL + SETA PARA DIREITA|  
|Mova a seleção de um controle para outro no mesmo grupo. Para um painel de lista suspensa, alternar entre o controle pai e os controles no painel de lista suspensa.|PARA CIMA<br /><br /> PARA BAIXO|  
|Itere encaminhar todos os controles.|TAB|  
|Itere o inverso em todos os controles.|SHIFT+TAB|  
|Exclua o controle selecionado ou o conjunto de controles.|DELETE|  
|Copie os controles selecionados.|CTRL+C|  
|Recorte os controles selecionados.|CTRL+X|  
|Colar controles da área de transferência.|CTRL+V|  
|Selecione o **caixa de ferramentas**.|CTRL + ALT + X|  
|Selecione o componente pai.|ESC|  
  
 Os atalhos de teclado que se aplicam somente ao Menu do Microsoft Office, <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>, e <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton> são mostrados na tabela a seguir.  
  
|Ação|Atalho de teclado|  
|------------|-----------------------|  
|Se o painel de lista suspensa é aberto e houver um controle selecionado no painel de lista suspensa, selecione o controle pai.|LEFT|  
|Feche o painel de lista suspensa, se o painel de lista suspensa é aberto e controle pai selecionado.|LEFT|  
|Abra o painel de lista suspensa.|RIGHT|  
|Se o painel de lista suspensa é aberto, selecione o primeiro controle no painel de lista suspensa.|RIGHT|  
|Feche o painel de lista suspensa.|ESC|  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral da faixa de opções](../vsto/ribbon-overview.md)   
 [XML da faixa de opções](../vsto/ribbon-xml.md)   
 [Passo a passo: Criando uma guia personalizada usando o Designer de faixa de opções](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Como: exportar uma faixa de opções do Designer de faixa de opções de XML da faixa de opções](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)   
 [Como: personalizar a faixa de opções](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [Acessando a faixa de opções no tempo de execução](../vsto/accessing-the-ribbon-at-run-time.md)  
  
  