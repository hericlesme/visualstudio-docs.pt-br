---
title: Criando soluções de fluxo de trabalho do SharePoint | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VSTO.NewSharePointWorkflowWizard.Page3
- VS.SharePointTools.Workflow.WorkflowName
- VSTO.NewSharePointWorkflowWizard.Page2
- VSTO.NewSharePointWorkflowWizard.Page1
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, workflows
- workflows [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: bc78726146b67a39f8e8988dda6c7d2baf5c49b3
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/01/2018
ms.locfileid: "34691918"
---
# <a name="creating-sharepoint-workflow-solutions"></a>Criando soluções de fluxo de trabalho do SharePoint
  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] fornece ferramentas para ajudá-lo a criar fluxos de trabalho personalizados que gerenciam o ciclo de vida de documentos e itens de lista em um site do SharePoint. Itens fornecidos incluem um designer, um conjunto de controles de atividade e as referências de assembly necessárias. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] também inclui o **Assistente de personalização do SharePoint**, para ajudar a criar e configurar os fluxos de trabalho.  
  
 Para obter a lista de pré-requisitos para a criação de projetos do SharePoint no [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], consulte [requisitos para desenvolver soluções do SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md). Para obter mais informações sobre o SharePoint, consulte [tecnologias e produtos do Microsoft SharePoint](http://go.microsoft.com/fwlink/?LinkId=178470).  
  
## <a name="workflows-in-sharepoint"></a>Fluxos de trabalho no SharePoint  
 Quando você adiciona um fluxo de trabalho a uma lista ou biblioteca do SharePoint, você pode impor um processo de negócios em todos os itens na lista ou biblioteca. Um fluxo de trabalho descreve as ações que o sistema ou os usuários devem executar em cada item, como o envio do item a ser editado e, em seguida, revisado. Essas ações, conhecidas como *atividades*, são os blocos de construção do fluxo de trabalho.  
  
 Você pode criar fluxos de trabalho do SharePoint no [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] e implantá-los em um site do SharePoint. Depois que um fluxo de trabalho é implantado no SharePoint, você pode associá-lo com uma lista ou biblioteca. Ele pode então ser iniciado automaticamente, por um processo, ou manualmente, por um usuário. Para obter mais informações sobre a operação de fluxo de trabalho, consulte [SharePoint desenvolver fluxos de trabalho usando o Visual Studio](https://docs.microsoft.com/sharepoint/dev/general-development/develop-sharepoint-workflows-using-visual-studio).  
  
## <a name="create-custom-sharepoint-workflows"></a>Criar fluxos de trabalho do SharePoint personalizados
 Dois projetos de fluxo de trabalho do SharePoint estão disponíveis em [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]: **fluxo de trabalho sequencial** e **fluxo de trabalho de máquina de estado**.  
  
 Um *fluxo de trabalho sequencial* representa uma série de etapas. As etapas são realizadas após o outro até que a última atividade seja concluída. Fluxos de trabalho sequenciais sempre são estritamente sequenciais em sua execução. Porque eles podem receber eventos externos e incluir fluxos de lógica paralela, a ordem exata de execução pode variar. A ilustração a seguir mostra um exemplo de um fluxo de trabalho sequencial.  
  
 ![Fluxo de trabalho sequencial](../sharepoint/media/sp-sequential.png "fluxo de trabalho sequencial")  
  
 Um *fluxo de trabalho de máquina de estado* representa um conjunto de estados, transições e ações. As etapas em um fluxo de trabalho de máquina de estado são executadas de forma assíncrona. Isso significa que eles não são necessariamente realizados após o outro, mas em vez disso, são disparados por estados e ações. Um estado é atribuído como o estado inicial e, em seguida, uma transição com base em um evento, é feita para outro estado. A máquina de estado pode ter um estado final que determina o final do fluxo de trabalho. O diagrama a seguir mostra um exemplo de um fluxo de trabalho de máquina de estado.  
  
 ![Fluxo de trabalho de máquina de estado](../sharepoint/media/sp-state.png "fluxo de trabalho de máquina de estado")  
  
 Para obter mais informações sobre os tipos de fluxo de trabalho, consulte [tipos de fluxo de trabalho](http://go.microsoft.com/fwlink/?LinkId=178995).  
  
### <a name="using-the-wizard"></a>Usando o Assistente
 Quando você cria um projeto de fluxo de trabalho do SharePoint no [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], primeiro você especifique suas configurações no **Assistente de personalização do SharePoint**. O assistente usa essas configurações para criar um projeto no **Gerenciador de soluções**. Este projeto contém um arquivo de código, vários arquivos que são usados para implantar o fluxo de trabalho, e as referências aos assemblies que são necessárias para criar um fluxo de trabalho do SharePoint personalizado.  
  
 Depois de criar o fluxo de trabalho, você pode modificar suas propriedades na janela Propriedades. Embora a maioria das propriedades de fluxo de trabalho pode ser alterado diretamente na janela Propriedades, algumas exigem que você clica em um botão de reticências (![elipse ASP.NET Mobile Designer](../sharepoint/media/mwellipsis.gif "elipse ASP.NET Mobile Designer")) para Altere seus valores. Esse botão reinicia o **Assistente de personalização do SharePoint**. Depois que você definir a propriedade valor de alterações, escolha o **concluir** botão para finalizá-los.  
  
> [!NOTE]  
>  O **tipo de fluxo de trabalho** propriedade é somente leitura e não pode ser alterada. Se você quiser alterar o tipo de fluxo de trabalho, você deve criar outro fluxo de trabalho.  
  
## <a name="design-a-sharepoint-workflow"></a>Criar um fluxo de trabalho do SharePoint
 Depois de definir todas as etapas do processo de negócios, use o [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] designer de fluxo de trabalho para criar o fluxo de trabalho do SharePoint. Para abrir o designer, clique duas vezes em workflow1 ou Workflow1.vb em **Solution Explorer**, ou abra o menu de atalho para qualquer um desses arquivos e, em seguida, escolha **abrir**.  
  
### <a name="activities"></a>Atividades  
 Para criar um fluxo de trabalho, adicionar atividades a **caixa de ferramentas** para um *agenda de fluxo de trabalho* no designer. Uma agenda de fluxo de trabalho contém a sequência de atividades na ordem em que eles devem ser executados.  
  
 Há dois tipos de atividades:  
  
-   *As atividades simples* executar uma única unidade de trabalho, como "retardar por 1 dia" ou "iniciar o serviço Web".  
  
-   *Atividades compostas* contêm outras atividades; por exemplo, uma atividade condicional pode conter duas ramificações.  
  
 Os dois tipos de atividades estão disponíveis no **caixa de ferramentas**.  
  
 As atividades podem ter propriedades, métodos e eventos. Use o **propriedades** janela para definir as propriedades de uma atividade.  
  
 Você também pode criar uma atividade personalizada. Para obter mais informações, consulte [passo a passo: criar uma atividade de fluxo de trabalho de Site personalizado](../sharepoint/walkthrough-create-a-custom-site-workflow-activity.md).  
  
 As atividades são organizadas nas guias a seguir no **caixa de ferramentas**:  
  
-   **Fluxo de trabalho do SharePoint**  
  
-   **Fluxo de trabalho do Windows v 3.0**  
  
-   **Windows Workflow v 3.5**  
  
 Nem todas as atividades de fluxo de trabalho principal são suportadas pelo SharePoint. Para obter mais informações, consulte [fluxo de trabalho para o Windows SharePoint Services visão geral das atividades](http://go.microsoft.com/fwlink/?LinkID=156094).  
  
#### <a name="sharepoint-workflow-activities"></a>Atividades de fluxo de trabalho do SharePoint
 O **fluxo de trabalho do SharePoint** guias contêm atividades especializadas para uso em [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)]. Essas atividades simplificam e simplificar o desenvolvimento de fluxos de trabalho de ciclo de vida de documento. Para obter mais informações sobre as atividades listadas no **fluxo de trabalho do SharePoint** guia, consulte [fluxo de trabalho para o Windows SharePoint Services visão geral das atividades](http://go.microsoft.com/fwlink/?LinkID=156094).  
  
#### <a name="windows-workflow-activities"></a>Atividades de fluxo de trabalho do Windows
 O **Windows Workflow** guias contêm as atividades que são fornecidas pelo [!INCLUDE[TLA#tla_workflow](../sharepoint/includes/tlasharptla-workflow-md.md)]. Você pode usar essas atividades para criar agendas de fluxo de trabalho para qualquer tipo de aplicativo de fluxo de trabalho do Windows.  
  
 Para obter mais informações sobre as atividades listadas no **fluxos de trabalho do Windows** guia, consulte [atividades do Windows Workflow Foundation](http://go.microsoft.com/fwlink/?LinkID=156096). Para obter mais informações sobre o Windows Workflow Foundation, consulte [visão geral do Windows Workflow Foundation](http://go.microsoft.com/fwlink/?LinkID=128632).  
  
### <a name="work-with-activities-in-the-designer"></a>Trabalhar com atividades no designer
 O agendamento de fluxo de trabalho pode conter uma combinação de atividades de fluxo de trabalho do Windows e atividades de fluxo de trabalho do SharePoint.  
  
 O designer exibe indicações visuais para ajudar a posicionar e configurar atividades corretamente. Quando você arrasta ou copia uma atividade para a programação de fluxo de trabalho, o designer exibe ícones de verde-sinal de adição (+) que mostram locais válidos para a atividade no fluxo de trabalho. Você não pode colocar uma atividade em um local onde não é válido. Por exemplo, você não pode posicionar uma atividade enviar como a primeira atividade em uma ramificação de atividade de escuta. Para obter mais informações, consulte [SharePoint Designer Developer Center](http://go.microsoft.com/fwlink/?LinkId=178476).  
  
## <a name="collect-information-during-the-workflow"></a>Coletar informações durante o fluxo de trabalho
 Talvez você queira coletar informações de usuários em momentos no fluxo de trabalho predefinidos. Você pode coletar informações usando formulários ou propriedades do item.  
  
### <a name="forms"></a>Formulários  
 Os formulários são como caixas de diálogo que contêm perguntas e fornecem maneiras para os usuários fornecer respostas.  
  
 Há quatro tipos de formulários que podem ser usados em um fluxo de trabalho:  
  
-   Associação  
  
-   Iniciação  
  
-   Modificação  
  
-   Tarefa  
  
 Desses, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] inclui modelos de item para formulários de associação e inicialização. Um exemplo de um *formulário de associação* que permite que o administrador que está instalando o fluxo de trabalho é inserir parâmetros relacionados ao fluxo de trabalho, como um limite de gastos para um fluxo de trabalho de despesa. Um exemplo de um *formulário de iniciação* é aquele que permite que o usuário de um fluxo de trabalho de despesa insira a quantidade que eles gastam no fluxo de trabalho. Para obter mais informações sobre esses tipos de formulários, consulte [projeto do SharePoint e modelos de Item de projeto](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
### <a name="item-properties"></a>Propriedades de item
 Você também pode coletar informações de usuários usando as propriedades de um item na lista ou biblioteca do SharePoint. O arquivo de código principal (workflow1 ou Workflow1.vb) declara uma instância da classe Microsoft.SharePoint.Workflow.SPWorkflowActivationProperties.WorkflowProperties chamada `workflowProperties`. Use o `workflowProperties` objeto para acessar as propriedades da biblioteca ou lista no código. Para obter um exemplo, consulte [passo a passo: Criando e depurando uma solução de fluxo de trabalho do SharePoint](../sharepoint/walkthrough-creating-and-debugging-a-sharepoint-workflow-solution.md).  
  
## <a name="debug-a-sharepoint-workflow-template"></a>Depurar um modelo de fluxo de trabalho do SharePoint
 Você pode depurar um projeto de fluxo de trabalho do SharePoint o mesmo durante a depuração outros [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projetos baseados na Web. Quando você inicia o [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] depurador, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] usa as configurações que você especificar o **Assistente de personalização do SharePoint** para abrir o site do SharePoint apropriado e associar automaticamente o modelo de fluxo de trabalho com a lista ou biblioteca apropriada. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] também anexa o [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] do depurador para o [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] processo chamado w3wp.exe.  
  
 Para testar o fluxo de trabalho, você deve iniciá-lo manualmente. Para obter mais informações, consulte a seção "Depuração de fluxos de trabalho" em [soluções do SharePoint de depuração](../sharepoint/debugging-sharepoint-solutions.md). Para obter mais informações sobre [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] depuração de aplicativo na Web, consulte [Depurando aplicativos da Web e o Script](/visualstudio/debugger/debugging-web-applications-and-script).  
  
## <a name="deploy-a-sharepoint-workflow-template"></a>Implantar um modelo de fluxo de trabalho do SharePoint
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Implantar projetos de fluxo de trabalho do SharePoint como outros [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projetos do SharePoint. Para obter mais informações, consulte [empacotamento e implantação de soluções do SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md).  
  
## <a name="import-globally-reusable-workflows"></a>Importar fluxos de trabalho reutilizáveis globalmente
 Além de criar fluxos de trabalho reutilizáveis específicas do site, o SharePoint Designer permite que você crie *fluxos de trabalho reutilizáveis globalmente*, que são fluxos de trabalho que podem ser usados por qualquer site do SharePoint. O projeto de importar fluxo de trabalho reutilizável no [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] atualmente não importar fluxos de trabalho reutilizáveis globalmente. No entanto, você pode usar o SharePoint Designer para converter um fluxo de trabalho reutilizável globalmente em um fluxo de trabalho reutilizável ou importar o fluxo de trabalho como um fluxo de trabalho declarativo não convertido. Para obter mais informações, consulte [importar itens de um Site do SharePoint existente](../sharepoint/importing-items-from-an-existing-sharepoint-site.md).  
  
## <a name="related-topics"></a>Tópicos relacionados
  
|Título|Descrição|  
|-----------|-----------------|  
|[Instruções passo a passo: criando e depurando uma solução de fluxo de trabalho do SharePoint](../sharepoint/walkthrough-creating-and-debugging-a-sharepoint-workflow-solution.md)|Leva você passo a passo sobre a criação e depuração de um simples [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] fluxo de trabalho.|  
|[Instruções passo a passo: criando um fluxo de trabalho com associação e formulários de inicialização](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)|Leva você passo a passo para criar um mais completo [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] conclui o fluxo de trabalho com formulários de associação e inicialização.|  
|[Instruções passo a passo: adicionar uma página de aplicativo a um fluxo de trabalho](../sharepoint/walkthrough-add-an-application-page-to-a-workflow.md)|Amplia o tópico [passo a passo: Criando um fluxo de trabalho com associação e formulários de iniciação](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md) adicionando uma página de aplicativo. aspx adicionais que relata os dados inseridos no fluxo de trabalho.|  
|[Instruções passo a passo: criar uma atividade personalizada de fluxo de trabalho do site](../sharepoint/walkthrough-create-a-custom-site-workflow-activity.md)|Demonstra como executar duas tarefas principais: criar um fluxo de trabalho de nível de site e criar uma atividade de fluxo de trabalho personalizado.|  
|[Instruções passo a passo: importar um fluxo de trabalho reutilizável do designer do SharePoint para o Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)|Demonstra como importar reutilizáveis fluxos de trabalho criados no SharePoint Designer 2010 em um [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projeto do SharePoint.|  
  
## <a name="see-also"></a>Consulte também
 [Desenvolver soluções do SharePoint](../sharepoint/developing-sharepoint-solutions.md)   
 [Compilando e depurando soluções do SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)   
 [Criando páginas de aplicativo para o SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)  
  
 