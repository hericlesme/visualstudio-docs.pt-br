---
title: Painéis de tarefas personalizados
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, task panes
- user interface panels [Office development in Visual Studio]
- task panes [Office development in Visual Studio]
- user interfaces [Office development in Visual Studio], custom task panes
- custom task panes [Office development in Visual Studio], creating
- task panes [Office development in Visual Studio]. multiple application windows
- custom task panes [Office development in Visual Studio], multiple application windows
- task panes [Office development in Visual Studio], creating
- application-level add-ins [Office development in Visual Studio], custom task panes
- multiple applications windows with custom task panes [Office development in Visual Studio]
- add-ins [Office development in Visual Studio], custom task panes
- custom task panes [Office development in Visual Studio]
- task panes [Office development in Visual Studio], about custom task panes
- custom task panes [Office development in Visual Studio], about custom task panes
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 4dff9c5f8602f1e11ef020400a11d7d165b23b04
ms.sourcegitcommit: 697162f54d3c4e30df702fd0289e447e211e3a85
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/25/2018
---
# <a name="custom-task-panes"></a>Painéis de tarefas personalizados
  Painéis de tarefas estão os painéis de interface do usuário que são normalmente encaixados em um dos lados de uma janela em um aplicativo do Microsoft Office. Painéis de tarefas personalizados oferecem uma maneira de criar seu próprio painel de tarefas e fornecer aos usuários uma interface familiar para acessar recursos da solução. Por exemplo, a interface pode conter controles que execute o código para modificar documentos ou exibir dados de uma fonte de dados.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
> [!NOTE]  
>  Um painel tarefa personalizada é diferente no painel Ações. O painel de ações é parte de personalizações no nível de documento para o Microsoft Office Word e Microsoft Office Excel. Para obter mais informações, consulte [visão geral do painel de ações](../vsto/actions-pane-overview.md).  
  
## <a name="benefits-of-custom-task-panes"></a>Benefícios dos painéis de tarefas personalizados  
 Painéis de tarefas personalizados permitem que você integre seus recursos em uma interface de usuário familiar. Você pode criar um painel tarefa personalizada rapidamente usando ferramentas do Visual Studio.  
  
### <a name="familiar-user-interface"></a>Interface de usuário familiar  
 Os usuários de aplicativos do Microsoft Office System já estão familiarizados com o uso de painéis de tarefas, como o **estilos e formatação** painel de tarefas no Word. Painéis de tarefas personalizados se comportam como outros painéis de tarefas no Microsoft Office system. Os usuários podem encaixar painéis de tarefas personalizados para diferentes lados da janela do aplicativo ou pode arrastar painéis de tarefas personalizados para qualquer local na janela. Você pode criar um VSTO suplemento que exibe vários painéis de tarefas personalizados ao mesmo tempo, e os usuários podem controlar individualmente cada painel de tarefas.  
  
### <a name="windows-forms-support"></a>Suporte ao Windows forms  
 A interface do usuário de um painel tarefa personalizada que você cria usando as ferramentas de desenvolvimento do Office no Visual Studio se baseia em controles de formulários do Windows. Você pode usar o Designer de formulários do Windows familiares para criar a interface do usuário para um painel tarefa personalizada. Você também pode usar o suporte à associação de dados em formulários do Windows para associar a uma fonte de dados a controles no painel de tarefas.  
  
## <a name="create-a-custom-task-pane"></a>Criar um painel tarefa personalizada  
 Você pode criar um painel tarefa personalizada básica em duas etapas:  
  
1.  Criar uma interface do usuário para o painel de tarefas personalizadas, adicionando controles de formulários do Windows para uma <xref:System.Windows.Forms.UserControl> objeto.  
  
2.  Instanciar o painel de tarefas, passando o controle de usuário para o <xref:Microsoft.Office.Tools.CustomTaskPaneCollection> objeto no seu suplemento do VSTO. Esta coleção retorna um novo <xref:Microsoft.Office.Tools.CustomTaskPane> objeto que você pode usar para modificar a aparência do painel de tarefas e responder a eventos do usuário.  
  
 Para obter mais informações, consulte [como: adicionar um painel tarefa personalizada a um aplicativo](../vsto/how-to-add-a-custom-task-pane-to-an-application.md).  
  
### <a name="create-the-user-interface"></a>Criar a interface do usuário  
 Todos os painéis de tarefas personalizados que são criados usando as ferramentas de desenvolvimento do Office no Visual Studio contêm um <xref:System.Windows.Forms.UserControl> objeto. Este controle de usuário fornece a interface do usuário do painel de tarefas. Você pode criar o controle de usuário em tempo de design ou em tempo de execução. Se você criar o controle de usuário em tempo de design, você pode usar o Designer de formulários do Windows para construir a interface do usuário do seu painel de tarefas.  
  
### <a name="instantiate-the-custom-task-pane"></a>Instanciar o painel de tarefas  
 Depois de criar um controle de usuário que contém a interface do usuário do painel de tarefas personalizado, você precisa criar uma instância de um <xref:Microsoft.Office.Tools.CustomTaskPane>. Para fazer isso, passe o controle de usuário para o <xref:Microsoft.Office.Tools.CustomTaskPaneCollection> no seu suplemento do VSTO chamando um do <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> métodos. Essa coleção é exposta como o `CustomTaskPanes` campo o `ThisAddIn` classe. O exemplo de código a seguir se destina a ser executado a partir de `ThisAddIn` classe.  
  
 [!code-vb[Trin_TaskPaneBasic#2](../vsto/codesnippet/VisualBasic/Trin_TaskPaneBasic/ThisAddIn.vb#2)]
 [!code-csharp[Trin_TaskPaneBasic#2](../vsto/codesnippet/CSharp/Trin_TaskPaneBasic/ThisAddIn.cs#2)]  
  
 O <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> métodos retornam um novo <xref:Microsoft.Office.Tools.CustomTaskPane> objeto. Você pode usar esse objeto para modificar a aparência do painel de tarefas e para responder a eventos do usuário.  
  
### <a name="control-the-task-pane-in-multiple-windows"></a>Controle de painel de tarefas em várias janelas  
 Painéis de tarefas personalizados estão associados com uma janela de quadro do documento, que apresenta uma exibição de um documento ou item para o usuário. O painel de tarefas é visível apenas quando a janela associada é visível.  
  
 Para determinar qual é a janela exibe o painel de tarefas, use o <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> sobrecarga de método quando você cria o painel de tarefas:  
  
-   Para associar o painel de tarefas na janela ativa, use o <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> método.  
  
-   Para associar o painel de tarefas com um documento que é hospedado por um período especificado, use o <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> método.  
  
 Alguns aplicativos do Office exigem instruções explícitas para quando criar ou exibir o painel de tarefas quando mais de uma janela é aberta. Isso é importante considerar onde instanciar o painel de tarefas em seu código para garantir que o painel de tarefas é exibida com os documentos apropriados ou itens no aplicativo. Para obter mais informações, consulte [gerenciar painéis de tarefas personalizados no aplicativo windows](#Managing).  
  
## <a name="access-the-application-from-the-task-pane"></a>Acessar o aplicativo de painel de tarefas  
 Se quiser automatizar o aplicativo do controle do usuário, você pode acessar diretamente o modelo de objeto usando `Globals.ThisAddIn.Application` em seu código. Estático `Globals` classe fornece acesso para o `ThisAddIn` objeto. O `Application` campo desse objeto é o ponto de entrada no modelo de objeto do aplicativo.  
  
 Para obter mais informações sobre o `Application` campo o `ThisAddIn` de objeto, consulte [suplementos do VSTO do programa](../vsto/programming-vsto-add-ins.md). Para uma explicação passo a passo que demonstra como automatizar um aplicativo de um painel tarefa personalizada, consulte [passo a passo: automático, um aplicativo de um painel tarefa personalizada](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md). Para obter mais informações sobre o `Globals` de classe, consulte [Global de acesso a objetos em projetos do Office](../vsto/global-access-to-objects-in-office-projects.md).  
  
## <a name="manage-the-user-interface-of-the-task-pane"></a>Gerenciar a interface do usuário do painel de tarefas  
 Depois de criar o painel de tarefas, você pode usar propriedades e eventos de <xref:Microsoft.Office.Tools.CustomTaskPane> objeto para controlar a interface do usuário do painel de tarefas e para responder quando o usuário altera o painel de tarefas.  
  
### <a name="make-the-custom-task-pane-visible"></a>Tornar visível o painel de tarefas personalizados  
 Por padrão, o painel de tarefas não é visível. Para tornar o painel de tarefas visível, você deve definir o <xref:Microsoft.Office.Tools.CustomTaskPane.Visible%2A> propriedade **true**.  
  
 Os usuários podem fechar um painel de tarefas a qualquer momento clicando o **fechar** botão (X) no canto do painel de tarefas. No entanto, não há nenhuma maneira de padrão para os usuários abrir o painel de tarefas novamente. Se um usuário fecha um painel tarefa personalizada, o usuário não pode exibir o painel de tarefas novamente, a menos que você fornecer uma maneira para exibi-lo.  
  
 Se você criar um painel tarefa personalizada no seu suplemento do VSTO, você também deve criar um elemento de interface do usuário, como um botão, o que os usuários podem clicar para exibir ou ocultar o painel de tarefas. Se você criar um painel tarefa personalizada em um aplicativo do Microsoft Office que dá suporte a personalização da faixa de opções, você pode adicionar um grupo de controles da faixa de opções com um botão que exibe ou oculta o painel de tarefas. Para uma explicação passo a passo que demonstra como fazer isso, consulte [passo a passo: sincronizar um painel tarefa personalizada com o botão faixa de opções](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md).  
  
 Se você criar um painel tarefa personalizada em um aplicativo do Microsoft Office que não oferece suporte a personalização da faixa de opções, você pode adicionar um <xref:Microsoft.Office.Core.CommandBarButton> que exibe ou oculta o painel de tarefas.  
  
### <a name="modify-the-appearance-of-the-task-pane"></a>Modificar a aparência do painel de tarefas  
 Você pode controlar o tamanho e o local de um painel tarefa personalizada usando propriedades do <xref:Microsoft.Office.Tools.CustomTaskPane> objeto. Você pode fazer muitas outras alterações para a aparência de um painel tarefa personalizada usando propriedades do <xref:System.Windows.Forms.UserControl> objeto contido no painel de tarefas personalizadas. Por exemplo, você pode especificar uma imagem de plano de fundo para um painel tarefa personalizada usando o <xref:System.Windows.Forms.Control.BackgroundImage%2A> propriedade do controle de usuário.  
  
 A tabela a seguir lista as alterações que você pode fazer para um painel tarefa personalizada usando <xref:Microsoft.Office.Tools.CustomTaskPane> propriedades.  
  
|Tarefa|Propriedade|  
|----------|--------------|  
|Para alterar o tamanho do painel de tarefas|<xref:Microsoft.Office.Tools.CustomTaskPane.Height%2A><br /><br /> <xref:Microsoft.Office.Tools.CustomTaskPane.Width%2A>|  
|Para alterar o local do painel de tarefas|<xref:Microsoft.Office.Tools.CustomTaskPane.DockPosition%2A>|  
|Para ocultar o painel de tarefas ou torná-lo visível|<xref:Microsoft.Office.Tools.CustomTaskPane.Visible%2A>|  
|Para impedir que o usuário alterar o local do painel de tarefas|<xref:Microsoft.Office.Tools.CustomTaskPane.DockPositionRestrict%2A>|  
  
### <a name="program-custom-task-pane-events"></a>Eventos de painel de tarefas personalizadas de programa  
 Talvez seja o suplemento do VSTO para responder quando o usuário modifica o painel de tarefas. Por exemplo, se o usuário altera a orientação do painel na vertical para horizontal, você talvez queira reposicionar os controles.  
  
 A tabela a seguir lista os eventos que você pode manipular para responder às alterações que o usuário fez para o painel de tarefas.  
  
|Tarefa|evento|  
|----------|-----------|  
|Para responder quando o usuário altera o local do painel de tarefas.|<xref:Microsoft.Office.Tools.CustomTaskPane.DockPositionChanged>|  
|Para responder quando o usuário oculta o painel de tarefas ou se torna visível.|<xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged>|  
  
## <a name="clean-up-resources-used-by-the-task-pane"></a>Limpar os recursos usados pelo painel de tarefas  
 Depois de criar um painel tarefa personalizada, o <xref:Microsoft.Office.Tools.CustomTaskPane> objeto permanece na memória, desde que o suplemento do VSTO está em execução. O objeto permanece na memória, mesmo depois que o usuário clica o **fechar** botão (X) no canto do painel de tarefas.  
  
 Para limpar os recursos usados pelo painel de tarefas enquanto o suplemento do VSTO ainda está em execução, use o <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Remove%2A> ou <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.RemoveAt%2A> métodos. Esses métodos remover especificado <xref:Microsoft.Office.Tools.CustomTaskPane> de objeto o `CustomTaskPanes` coleta e chamar o <xref:Microsoft.Office.Tools.CustomTaskPane.Dispose%2A> método do objeto.  
  
 O [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] limpa automaticamente os recursos usados pelo painel de tarefas personalizado quando o suplemento do VSTO é descarregado. Não chame o <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Remove%2A> ou <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.RemoveAt%2A> métodos o `ThisAddIn_Shutdown` manipulador de eventos em seu projeto. Esses métodos lançará um <xref:System.ObjectDisposedException>, pois o [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] limpa os recursos usados pelo <xref:Microsoft.Office.Tools.CustomTaskPane> antes do objeto `ThisAddIn_Shutdown` é chamado. Para obter mais informações sobre `ThisAddIn_Shutdown`, consulte [eventos em projetos do Office](../vsto/events-in-office-projects.md)  
  
##  <a name="Managing"></a> Gerenciar os painéis de tarefas personalizados em várias janelas de aplicativo  
 Quando você cria um painel tarefa personalizada em um aplicativo que usa várias janelas para exibir documentos e outros itens, você precisa realizar etapas adicionais para garantir que o painel de tarefas seja visível quando o usuário esperava que fosse.  
  
 Painéis de tarefas personalizados em todos os aplicativos são associados com uma janela de quadro do documento, que apresenta uma exibição de um documento ou item para o usuário. O painel de tarefas é visível apenas quando a janela associada é visível. No entanto, nem todos os aplicativos usam janelas de quadro do documento da mesma maneira.  
  
 Os seguintes grupos de aplicativos têm requisitos diferentes de desenvolvimento:  
  
-   [Outlook](#Outlook)  
  
-   [Word, InfoPath e PowerPoint](#WordAndInfoPath)  
  
 ![link para vídeo](../vsto/media/playvideo.gif "link para vídeo") para uma demonstração de vídeo relacionada, consulte [como fazer gerenciar painéis de tarefas nos suplementos do VSTO Word?](http://go.microsoft.com/fwlink/?LinkId=136781).  
  
##  <a name="Outlook"></a> Outlook  
 Quando você cria um painel tarefa personalizada para o Outlook, o painel de tarefas está associado uma janela de navegador ou Inspetor específica. Pesquisadores são janelas que exibem o conteúdo de uma pasta e inspetores são janelas que exibem um item como uma mensagem de email ou uma tarefa.  
  
 Se você quiser exibir um painel tarefa personalizada com o windows Explorer ou o Inspetor vários, você precisa criar uma nova instância do painel de tarefas personalizado quando uma janela de navegador ou Inspetor é aberta. Para fazer isso, manipular um evento que é gerado quando uma janela de navegador ou Inspetor é criada e, em seguida, criar o painel de tarefas no manipulador de eventos. Você também pode manipular eventos de navegador e Inspetor para ocultar ou exibir os painéis de tarefas dependendo de qual janela está visível.  
  
 Para associar o painel de tarefas com um Explorer ou Inspetor específico, use o <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> método para criar o painel de tarefas e, em seguida, passe o <xref:Microsoft.Office.Interop.Outlook.Explorer> ou <xref:Microsoft.Office.Interop.Outlook.Inspector> o objeto para o *janela* parâmetro. Para obter mais informações sobre a criação de painéis de tarefas personalizados, consulte [visão geral de painéis de tarefas personalizados](../vsto/custom-task-panes.md).  
  
-   <xref:Microsoft.Office.Interop.Outlook.ExplorersEvents_Event.NewExplorer>  
  
-   <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Activate>  
  
-   <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Close>  
  
-   <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Deactivate>  
  
 Para monitorar o estado do Inspetor windows, você pode manipular os seguintes eventos de Inspetor:  
  
-   <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector>  
  
-   <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_10_Event.Activate>  
  
-   <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_10_Event.Close>  
  
-   <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_10_Event.Deactivate>  
  
### <a name="prevent-multiple-instances-of-a-custom-task-pane-in-outlook"></a>Impedir que várias instâncias de um painel tarefa personalizada no Outlook  
 Para impedir que o windows Outlook exiba várias instâncias de um painel tarefa personalizada, remover explicitamente o painel de tarefas do `CustomTaskPanes` coleção do `ThisAddIn` classe quando cada janela for fechada. Chamar o <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Remove%2A> método em um evento que é gerado quando uma janela for fechada, como <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Close> ou <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_10_Event.Close>.  
  
 Se você não remover explicitamente o painel de tarefas, o windows Outlook podem exibir várias instâncias do painel de tarefas personalizadas. Outlook recicla, às vezes, windows e windows reciclados mantém referências a quaisquer painéis de tarefas personalizados que estavam anexados a eles.  
  
##  <a name="WordAndInfoPath"></a> Word, InfoPath e PowerPoint  
 Word, InfoPath e PowerPoint exibe cada documento em uma janela do quadro de documento diferente. Quando você cria um painel tarefa personalizada para esses aplicativos, o painel de tarefas é associado somente um documento específico. Se o usuário abrir um documento diferente, o painel de tarefas personalizado está oculto até que o documento anterior esteja visível novamente.  
  
 Se você quiser exibir um painel tarefa personalizada com vários documentos, crie uma nova instância do painel de tarefas personalizado quando o usuário cria um novo documento ou abre um documento existente. Para fazer isso, manipular eventos que são gerados quando um documento é criado ou aberto e, em seguida, criar o painel de tarefas nos manipuladores de eventos. Você também pode manipular eventos de documento para ocultar ou exibir os painéis de tarefas dependendo de qual documento está visível.  
  
 Para associar o painel de tarefas com uma janela de documento específico, use o <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> método para criar o painel de tarefas e, em seguida, passe uma <xref:Microsoft.Office.Interop.Word.Window> (para o Word) <xref:Microsoft.Office.Interop.InfoPath.WindowObject> (para InfoPath), ou <xref:Microsoft.Office.Interop.PowerPoint.DocumentWindow> (para o PowerPoint) para o *janela*parâmetro.  
  
### <a name="word-events"></a>Eventos do Word  
 Para monitorar o estado de janelas de documento no Word, você pode manipular os eventos a seguir:  
  
-   <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeClose>  
  
-   <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen>  
  
-   <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.NewDocument>  
  
-   <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.WindowActivate>  
  
-   <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.WindowDeactivate>  
  
### <a name="infopath-events"></a>Eventos do InfoPath  
 Para monitorar o estado das janelas de documento no InfoPath, você pode manipular os eventos a seguir:  
  
-   <xref:Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.NewXDocument>  
  
-   <xref:Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.WindowActivate>  
  
-   <xref:Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.WindowDeactivate>  
  
-   <xref:Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.XDocumentBeforeClose>  
  
-   <xref:Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.XDocumentOpen>  
  
### <a name="powerpoint-events"></a>Eventos do PowerPoint  
 Para monitorar o estado das janelas de documento no PowerPoint, você pode manipular os eventos a seguir:  
  
-   <xref:Microsoft.Office.Interop.PowerPoint.EApplication_Event.AfterNewPresentation>  
  
-   <xref:Microsoft.Office.Interop.PowerPoint.EApplication_Event.AfterPresentationOpen>  
  
-   <xref:Microsoft.Office.Interop.PowerPoint.EApplication_Event.NewPresentation>  
  
-   <xref:Microsoft.Office.Interop.PowerPoint.EApplication_Event.PresentationOpen>  
  
-   <xref:Microsoft.Office.Interop.PowerPoint.EApplication_Event.WindowActivate>  
  
-   <xref:Microsoft.Office.Interop.PowerPoint.EApplication_Event.WindowDeactivate>  
  
## <a name="see-also"></a>Consulte também  
 [Como: adicionar um painel tarefa personalizada a um aplicativo](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)   
 [Passo a passo: Automatizar um aplicativo de um painel tarefa personalizada](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)   
 [Passo a passo: Sincronizar um painel tarefa personalizada com o botão faixa de opções](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md)   
 [Passo a passo: Exibir painéis de tarefas personalizada com mensagens de email no Outlook](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md)  
