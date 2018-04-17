---
title: 'Passo a passo: Criando um fluxo de trabalho com associação e formulários de iniciação | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, workflows
- SharePoint development in Visual Studio, workflow association forms
- workflows [SharePoint development in Visual Studio]
- association forms [SharePoint development in Visual Studio]
- initiation forms [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, workflow initiation forms
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 92aefd2292976bd9dcb50603e93b460cdf2bf991
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-creating-a-workflow-with-association-and-initiation-forms"></a>Instruções passo a passo: criando um fluxo de trabalho com associação e formulários de inicialização
  Este passo a passo demonstra como criar um fluxo de trabalho sequencial básico que incorpora o uso de formulários de associação e inicialização. Esses são os formulários ASPX que permitem que os parâmetros a serem adicionados a um fluxo de trabalho quando ele é associado pela primeira vez pelo administrador do SharePoint (o formulário de associação), e quando o fluxo de trabalho é iniciado pelo usuário (o formulário de inicialização).  
  
 Este passo a passo descreve um cenário em que um usuário deseja criar um fluxo de trabalho de aprovação para relatórios de despesas que tem os seguintes requisitos:  
  
-   Quando o fluxo de trabalho está associado uma lista, o administrador será solicitado com um formulário de associação onde eles digitarem um limite monetário para relatórios de despesas.  
  
-   Os funcionários carregar seus relatórios de despesas para a lista de documentos compartilhados, iniciar o fluxo de trabalho e, em seguida, insira a despesa total no formulário de iniciação do fluxo de trabalho.  
  
-   Se um relatório de despesas de funcionário total exceder um limite predefinido do administrador, uma tarefa é criada para o gerente do funcionário aprovar o relatório de despesas. No entanto, se o total de relatórios de despesas de um funcionário é menor ou igual ao limite de despesas, uma mensagem de aprovação automática é gravada para a lista de histórico do fluxo de trabalho.  
  
 Esta explicação passo a passo ilustra as seguintes tarefas:  
  
-   Criando um projeto de fluxo de trabalho sequencial do SharePoint lista definição no [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
-   Criando uma agenda de fluxo de trabalho.  
  
-   Manipulação de eventos de atividade de fluxo de trabalho.  
  
-   Criar formulários de associação e inicialização de fluxo de trabalho.  
  
-   Associando o fluxo de trabalho.  
  
-   O fluxo de trabalho é iniciado manualmente.  
  
> [!NOTE]  
>  Embora este passo a passo usa um projeto de fluxo de trabalho sequencial, o processo é o mesmo para fluxos de trabalho de máquina de estado.  
>   
>  Além disso, seu computador pode mostrar diferentes nomes ou locais para alguns do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] elementos de interface do usuário nas instruções a seguir. O [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] edição que você possui e as configurações que você usa determinam esses elementos. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Você precisa dos seguintes componentes para concluir esta instrução passo a passo:  
  
-   Edições do [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] e do SharePoint. Para obter mais informações, consulte [requisitos para desenvolver soluções do SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio.  
  
## <a name="creating-a-sharepoint-sequential-workflow-project"></a>Criando um projeto de fluxo de trabalho sequencial do SharePoint  
 Primeiro, crie um projeto de fluxo de trabalho sequencial no [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Um fluxo de trabalho sequencial é uma série de etapas que é executado na ordem até que a última atividade seja concluída. Neste procedimento, você criará um fluxo de trabalho sequencial que se aplica à lista de documentos compartilhados no SharePoint. Assistente do fluxo de trabalho permite que você associe o fluxo de trabalho com o site ou a definição de lista e permite que você determine quando o fluxo de trabalho será iniciado.  
  
#### <a name="to-create-a-sharepoint-sequential-workflow-project"></a>Para criar um projeto de fluxo de trabalho sequencial do SharePoint  
  
1.  Na barra de menus, escolha **arquivo**, **novo**, **projeto** para exibir o **novo projeto** caixa de diálogo.  
  
2.  Expanda o **SharePoint** nó sob o **Visual C#** ou **Visual Basic**e, em seguida, escolha o **2010** nó.  
  
3.  No **modelos** painel, escolha o **projeto do SharePoint 2010** modelo de projeto.  
  
4.  No **nome** , digite **ExpenseReport** e, em seguida, escolha o **Okey** botão.  
  
     O **Assistente de personalização do SharePoint** é exibida.  
  
5.  No **especificar o nível de site e segurança de depuração** página, escolha o **implantar como uma solução de farm** botão de opção e, em seguida, escolha o **concluir** botão para aceitar o site padrão e o nível de confiança.  
  
     Esta etapa também define o nível de confiança para a solução como solução de farm, que é a única opção disponível para projetos de fluxo de trabalho.  
  
6.  Em **Solution Explorer**, escolha o nó do projeto.  
  
7.  Na barra de menus, escolha **projeto**, **Adicionar Novo Item**.  
  
8.  Em um **Visual C#** ou **Visual Basic**, expanda o **SharePoint** nó e, em seguida, escolha o **2010** nó.  
  
9. No **modelos** painel, escolha **o fluxo de trabalho sequencial (somente solução de Farm)** modelo e, em seguida, escolha o **adicionar** botão.  
  
     O **Assistente de personalização do SharePoint** é exibida.  
  
10. No **especifique o nome do fluxo de trabalho para depuração** página, aceite o nome padrão (**ExpenseReport - Workflow1**). Mantenha o valor de tipo de modelo de fluxo de trabalho padrão (**fluxo de trabalho de lista)**. Escolha o botão **Avançar**.  
  
11. No **você gostaria que o Visual Studio para associar automaticamente o fluxo de trabalho em uma sessão de depuração?** página, desmarque a caixa que associa automaticamente o modelo de fluxo de trabalho, caso ela esteja marcada.  
  
     Esta etapa permite que você associe manualmente o fluxo de trabalho com a lista de documentos compartilhados posterior no, que exibe o formulário de associação.  
  
12. Escolha o **concluir** botão.  
  
## <a name="adding-an-association-form-to-the-workflow"></a>Adicionando um formulário de associação do fluxo de trabalho  
 Em seguida, crie um. Formulário de associação ASPX que aparece quando o administrador do SharePoint primeiro associa o fluxo de trabalho com um documento de relatório de despesas.  
  
#### <a name="to-add-an-association-form-to-the-workflow"></a>Para adicionar um formulário de associação do fluxo de trabalho  
  
1.  Escolha o **Workflow1** nó **Gerenciador de soluções**.  
  
2.  Na barra de menus, escolha **projeto**, **Adicionar Novo Item** para exibir o **Adicionar Novo Item** caixa de diálogo.  
  
3.  Na exibição de árvore de caixa de diálogo, expanda **Visual C#** ou **Visual Basic** (dependendo do idioma do projeto), expanda o **SharePoint** nó e, em seguida, escolha o **2010** nó.  
  
4.  Na lista de modelos, escolha o **formulário de associação de fluxo de trabalho** modelo.  
  
5.  No **nome** texto, digite **ExpenseReportAssocForm.aspx**.  
  
6.  Escolha o **adicionar** botão para adicionar o formulário ao projeto.  
  
## <a name="designing-and-coding-the-association-form"></a>Criação e a codificação de formulário de associação  
 Neste procedimento, você pode introduzir funcionalidade para o formulário de associação adicionando controles e código para ele.  
  
#### <a name="to-design-and-code-the-association-form"></a>Para criar e codificar o formulário de associação  
  
1.  No formulário de associação (ExpenseReportAssocForm.aspx), localize o `asp:Content` elemento que tem `ID="Main"`.  
  
2.  Diretamente após a primeira linha neste elemento de conteúdo, adicione o seguinte código para criar um rótulo e a caixa de texto que solicita o limite de aprovação de despesas (*AutoApproveLimit*):  
  
    ```  
    <asp:Label ID="lblAutoApproveLimit" Text="Auto Approval Limit:" runat="server" />  
  
    <asp:TextBox ID="AutoApproveLimit" runat="server" />  
    <br /><br />  
    ```  
  
3.  Expanda o **ExpenseReportAssocForm.aspx** arquivo **Solution Explorer** para exibir seus arquivos dependentes.  
  
    > [!NOTE]  
    >  Se seu projeto está em [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)], você deve escolher o **exibir todos os arquivos** botão para realizar esta etapa.  
  
4.  Abra o menu de atalho para o arquivo ExpenseReportAssocForm.aspx e escolha **Exibir código**.  
  
5.  Substitua o `GetAssociationData` método com:  
  
    ```vb  
    Private Function GetAssociationData() As String  
        ' TODO: Return a string that contains the association data that   
        ' will be passed to the workflow. Typically, this is in XML   
        ' format.  
        Return Me.AutoApproveLimit.Text  
    End Function  
    ```  
  
    ```csharp  
    private string GetAssociationData()  
    {  
        // TODO: Return a string that contains the association data that   
        // will be passed to the workflow. Typically, this is in XML   
        // format.  
        return this.AutoApproveLimit.Text;  
    }  
    ```  
  
## <a name="adding-an-initiation-form-to-the-workflow"></a>Adicionando um formulário de inicialização para o fluxo de trabalho  
 Em seguida, crie o formulário de inicialização que aparece quando os usuários executam o fluxo de trabalho em relação a seus relatórios de despesas.  
  
#### <a name="to-create-an-initiation-form"></a>Para criar um formulário de inicialização  
  
1.  Escolha o **Workflow1** nó **Gerenciador de soluções**.  
  
2.  Na barra de menus, escolha **projeto**, **Adicionar Novo Item** exibir o **Adicionar Novo Item** caixa de diálogo.  
  
3.  Na exibição de árvore de caixa de diálogo, expanda **Visual C#** ou **Visual Basic** (dependendo do idioma do projeto), expanda o **SharePoint** nó e, em seguida, escolha o **2010** nó.  
  
4.  Na lista de modelos, escolha o **formulário de iniciação do fluxo de trabalho** modelo.  
  
5.  No **nome** texto, digite **ExpenseReportInitForm.aspx**.  
  
6.  Escolha o **adicionar** botão para adicionar o formulário ao projeto.  
  
## <a name="designing-and-coding-the-initiation-form"></a>Criar e codificar o formulário de inicialização  
 Em seguida, apresente a funcionalidade para o formulário de inicialização adicionando controles e código para ele.  
  
#### <a name="to-code-the-initiation-form"></a>Codificar o formulário de inicialização  
  
1.  No formulário de iniciação (ExpenseReportInitForm.aspx), localize o `asp:Content` elemento que contém `ID="Main"`.  
  
2.  Diretamente após a primeira linha neste elemento de conteúdo, adicione o seguinte código para criar um rótulo e a caixa de texto que exibe o limite de aprovação de despesas (*AutoApproveLimit*) que foi inserido no formulário de associação e outro rótulo e caixa de texto para solicitar o total de despesas (*ExpenseTotal*):  
  
    ```  
    <asp:Label ID="lblAutoApproveLimit" Text="Auto Approval Limit:" runat="server" />  
  
    <asp:TextBox ID="AutoApproveLimit" ReadOnly="true" runat="server" />  
    <br /><br />  
    <asp:Label ID="lblExpenseTotal" Text="Expense Total:" runat="server" />  
  
    <asp:TextBox ID="ExpenseTotal" runat="server" />  
    <br /><br />  
    ```  
  
3.  Expanda o **ExpenseReportInitForm.aspx** arquivo **Solution Explorer** para exibir seus arquivos dependentes.  
  
4.  Abra o menu de atalho para o arquivo ExpenseReportInitForm.aspx e escolha **Exibir código**.  
  
5.  Substitua o `Page_Load` método com o exemplo a seguir:  
  
    ```vb  
    Protected Sub Page_Load(ByVal sender As Object, ByVal e As   
      EventArgs) Handles Me.Load  
        InitializeParams()  
        Me.AutoApproveLimit.Text = workflowList.WorkflowAssociations(New   
          Guid(associationGuid)).AssociationData  
        ' Optionally, add code here to pre-populate your form fields.  
    End Sub  
    ```  
  
    ```csharp  
    protected void Page_Load(object sender, EventArgs e)  
    {  
        InitializeParams();  
        this.AutoApproveLimit.Text =   
          workflowList.WorkflowAssociations[new   
          Guid(associationGuid)].AssociationData;  
    }  
    ```  
  
6.  Substitua o `GetInitiationData` método com o exemplo a seguir:  
  
    ```vb  
    ' This method is called when the user clicks the button to start the workflow.  
    Private Function GetInitiationData() As String  
        Return Me.ExpenseTotal.Text  
        ' TODO: Return a string that contains the initiation data that   
        ' will be passed to the workflow. Typically, this is in XML   
        ' format.  
        Return String.Empty  
    End Function  
    ```  
  
    ```csharp  
    // This method is called when the user clicks the button to start the workflow.          
    private string GetInitiationData()  
    {  
        // TODO: Return a string that contains the initiation data that   
        // will be passed to the workflow. Typically, this is in XML   
        // format.  
        return this.ExpenseTotal.Text;  
    }  
    ```  
  
## <a name="customizing-the-workflow"></a>Personalizando o fluxo de trabalho  
 Em seguida, personalize o fluxo de trabalho. Posteriormente, você associará duas formas para o fluxo de trabalho.  
  
#### <a name="to-customize-the-workflow"></a>Para personalizar o fluxo de trabalho  
  
1.  Exiba o fluxo de trabalho no designer de fluxo de trabalho abrindo Workflow1 no projeto.  
  
2.  No **caixa de ferramentas**, expanda o **v 3.0 do fluxo de trabalho do Windows** nó e localize o **IfElse** atividade.  
  
3.  Adicione a atividade ao fluxo de trabalho executando uma das seguintes etapas:  
  
    -   Abra o menu de atalho para o **IfElse** atividade, escolha **cópia**, abra o menu de atalho para a linha abaixo de **onWorkflowActivated1** atividade no designer de fluxo de trabalho, e, em seguida, escolha **colar**.  
  
    -   Arraste o **IfElse** atividade do **caixa de ferramentas**e conecte-se para a linha no **onWorkflowActiviated1** atividade no designer de fluxo de trabalho.  
  
4.  Na caixa de ferramentas, expanda o **fluxo de trabalho do SharePoint** nó e localize o **CreateTask** atividade.  
  
5.  Adicione a atividade ao fluxo de trabalho executando uma das seguintes etapas:  
  
    -   Abra o menu de atalho para o **CreateTask** atividade, escolha **cópia**, abra o menu de atalho para um dos dois **solte atividades aqui** áreas de  **IfElseActivity1** no designer de fluxo de trabalho e, em seguida, escolha **colar**.  
  
    -   Arraste o **CreateTask** atividade do **caixa de ferramentas** em um dos dois **solte atividades aqui** áreas de **IfElseActivity1**.  
  
6.  No **propriedades** janela, digite um valor de propriedade de *taskToken* para o **CorrelationToken** propriedade.  
  
7.  Expanda o **CorrelationToken** propriedade clicando no sinal de adição (![TreeView adição](../sharepoint/media/plus.gif "TreeView adição")) ao lado dela.  
  
8.  Clique na seta suspensa no **OwnerActivityName** sub propriedade e defina o *Workflow1* valor.  
  
9. Escolha o **TaskId** propriedade e, em seguida, escolha o botão de reticências (![elipse ASP.NET Mobile Designer](../sharepoint/media/mwellipsis.gif "elipse ASP.NET Mobile Designer")) botão para exibir o **Associar propriedade** caixa de diálogo.  
  
10. Escolha o **vincular a um novo membro** guia, escolha o **criar campo** botão de opção e, em seguida, escolha o **Okey** botão.  
  
11. Escolha o **TaskProperties** propriedade e, em seguida, escolha o botão de reticências (![elipse ASP.NET Mobile Designer](../sharepoint/media/mwellipsis.gif "elipse ASP.NET Mobile Designer")) botão para exibir o  **Associar a propriedade** caixa de diálogo.  
  
12. Escolha o **vincular a um novo membro** guia, escolha o **criar campo** botão de opção e, em seguida, escolha o **Okey** botão.  
  
13. No **caixa de ferramentas**, expanda o **fluxo de trabalho do SharePoint** nó e localize o **LogToHistoryListActivity** atividade.  
  
14. Adicione a atividade ao fluxo de trabalho executando uma das seguintes etapas:  
  
    -   Abra o menu de atalho para o **LogToHistoryListActivity** atividade, escolha **cópia**, abra o menu de atalho para os outros **solte atividades aqui** área dentro **IfElseActivity1** no designer de fluxo de trabalho e, em seguida, escolha **colar**.  
  
    -   Arraste o **LogToHistoryListActivity** atividade do **caixa de ferramentas**e solte-a outra **solte atividades aqui** área dentro **IfElseActivity1** .  
  
## <a name="adding-code-to-the-workflow"></a>Adicionar código ao fluxo de trabalho  
 Em seguida, adicione código para o fluxo de trabalho para fornecer funcionalidade ele.  
  
#### <a name="to-add-code-to-the-workflow"></a>Para adicionar código ao fluxo de trabalho  
  
1.  Abra o menu de atalho para o **createTask1** atividade no designer de fluxo de trabalho e, em seguida, escolha **Exibir código**.  
  
2.  Adicione o seguinte método:  
  
    ```vb  
    Private Sub createTask1_MethodInvoking(ByVal sender As   
      System.Object, ByVal e As System.EventArgs)  
        createTask1_TaskId1 = Guid.NewGuid  
        createTask1_TaskProperties1.AssignedTo = "somedomain\\someuser"  
        createTask1_TaskProperties1.Description = "Please approve the   
          expense report"  
        createTask1_TaskProperties1.Title = "Expense Report Approval   
          Needed"  
    End Sub   
    ```  
  
    ```csharp  
    private void createTask1_MethodInvoking(object sender, EventArgs e)  
    {  
        createTask1_TaskId1 = Guid.NewGuid();  
        createTask1_TaskProperties1.AssignedTo = "somedomain\\someuser";  
        createTask1_TaskProperties1.Description = "Please approve the   
          expense report";  
        createTask1_TaskProperties1.Title = "Expense Report Approval   
          Needed";  
    }   
    ```  
  
    > [!NOTE]  
    >  No código, substitua `somedomain\\someuser` com um nome de usuário e domínio para o qual uma tarefa será criada, como "`Office\\JoeSch`". Para teste é mais fácil de usar a conta que você está desenvolvendo com.  
  
3.  Abaixo de `MethodInvoking` método, adicione o exemplo a seguir:  
  
    ```vb  
    Private Sub checkApprovalNeeded(ByVal sender As Object, ByVal e As   
      ConditionalEventArgs)  
        Dim approval As Boolean = False  
        If (Convert.ToInt32(workflowProperties.InitiationData) >   
          Convert.ToInt32(workflowProperties.AssociationData)) Then  
            approval = True  
        End If  
        e.Result = approval  
    End Sub   
    ```  
  
    ```csharp  
    private void checkApprovalNeeded(object sender, ConditionalEventArgs   
      e)  
    {  
        bool approval = false;  
        if (Convert.ToInt32(workflowProperties.InitiationData) >   
          Convert.ToInt32(workflowProperties.AssociationData))  
        {  
            approval = true;  
        }  
        e.Result = approval;  
    }   
    ```  
  
4.  No designer de fluxo de trabalho, escolha o **ifElseBranchActivity1** atividade.  
  
5.  No **propriedades** janela, clique na seta suspensa do **condição** propriedade e, em seguida, defina o *código condição* valor.  
  
6.  Expanda o **condição** propriedade clicando no sinal de adição (![TreeView adição](../sharepoint/media/plus.gif "TreeView adição")) ao lado dele e, em seguida, defina seu valor como *checkApprovalNeeded* .  
  
7.  No designer de fluxo de trabalho, abra o menu de atalho para o **logToHistoryListActivity1** atividade e, em seguida, escolha **gerar manipuladores** para gerar um método vazio para o `MethodInvoking` evento.  
  
8.  Substitua o `MethodInvoking` código com o seguinte:  
  
    ```vb  
    Private Sub logToHistoryListActivity1_MethodInvoking(ByVal sender As   
      System.Object, ByVal e As System.EventArgs)  
        Me.logToHistoryListActivity1.HistoryOutcome = ("Expense was auto   
          approved for " + workflowProperties.InitiationData)  
    End Sub   
    ```  
  
    ```csharp  
    private void logToHistoryListActivity1_MethodInvoking(object sender,   
      EventArgs e)  
    {  
        this.logToHistoryListActivity1.HistoryOutcome = "Expense was   
          auto approved for " + workflowProperties.InitiationData;  
    }   
    ```  
  
9. Pressione a tecla F5 para depurar o programa.  
  
     Isso compila o aplicativo de um pacote, implanta, ativa seus recursos, o recicla o [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] pool de aplicativos e, em seguida, inicia o navegador no local especificado no **Url do Site** propriedade.  
  
## <a name="associating-the-workflow-to-the-documents-list"></a>Associando o fluxo de trabalho à lista de documentos  
 Em seguida, exibir o formulário de associação de fluxo de trabalho por meio da associação do fluxo de trabalho com o **SharedDocuments** lista no site do SharePoint.  
  
#### <a name="to-associate-the-workflow"></a>Para associar o fluxo de trabalho  
  
1.  Escolha o **documentos compartilhados** link na barra Início rápido.  
  
2.  Escolha o **biblioteca** link o **ferramentas de biblioteca** guia e, em seguida, escolha o **configurações da biblioteca** botão faixa de opções.  
  
3.  No **permissões e gerenciamento** , escolha o **configurações de fluxo de trabalho** link e, em seguida, escolha o **adicionar um fluxo de trabalho** link o **defluxosdetrabalho** página.  
  
4.  Na lista superior na página de configurações do fluxo de trabalho, escolha o **ExpenseReport - Workflow1** modelo.  
  
5.  No campo próximo, digite **ExpenseReportWorkflow** e, em seguida, escolha o **próximo** botão.  
  
     Isso associa o fluxo de trabalho com o **documentos compartilhados** lista e exibe o formulário de associação de fluxo de trabalho.  
  
6.  No **limite de aprovação automática** texto, digite **1200** e, em seguida, escolha o **associar o fluxo de trabalho** botão.  
  
## <a name="starting-the-workflow"></a>Iniciando o fluxo de trabalho  
 Em seguida, associe o fluxo de trabalho para um dos documentos a **documentos compartilhados** lista para exibir o formulário de inicialização de fluxo de trabalho.  
  
#### <a name="to-start-the-workflow"></a>Para iniciar o fluxo de trabalho  
  
1.  Na página do SharePoint, escolha o **início** botão.  
  
2.  Escolha o **documentos compartilhados** link na barra Início rápido para exibir o **documentos compartilhados** lista.  
  
3.  Escolha o **documentos** link o **ferramentas de biblioteca** guia na parte superior da página e, em seguida, escolha o **carregar documento** botão na faixa de opções para carregar um novo documento no **Documentos compartilhados** lista.  
  
4.  No **carregar documento** caixa de diálogo caixa, escolha o **procurar** botão, escolha qualquer arquivo de documento, escolha o **abrir** botão e, em seguida, escolha o **Okey** botão.  
  
     Você pode alterar as configurações para o documento na caixa de diálogo, mas deixá-los com os valores padrão, escolhendo o **salvar** botão.  
  
5.  Escolha o documento carregado, escolha a seta suspensa que aparece e, em seguida, escolha o **fluxos de trabalho** item.  
  
6.  Escolha a imagem ao lado de ExpenseReportWorkflow.  
  
     Exibe o formulário de inicialização de fluxo de trabalho. (Observe que o valor exibido no **limite de aprovação automática** caixa é somente leitura porque ela foi inserida no formulário de associação.)  
  
7.  No **despesa Total** texto, digite **1600**e, em seguida, escolha o **Iniciar fluxo de trabalho** botão.  
  
     Isso exibe o **documentos compartilhados** lista novamente. Uma nova coluna chamada **ExpenseReportWorkflow** com o valor **concluído** é adicionado ao item acabado de fluxo de trabalho.  
  
8.  Clique na seta suspensa ao lado de documento carregado e, em seguida, escolha o **fluxos de trabalho** item para exibir a página de status do fluxo de trabalho. Escolha o **concluído** valor em **fluxos de trabalho concluída**. A tarefa está listada sob o **tarefas** seção.  
  
9. Escolha o título da tarefa para exibir seus detalhes da tarefa.  
  
10. Volte para o **SharedDocuments** lista e reinicie o fluxo de trabalho, usando o mesmo documento ou um diferente.  
  
11. Insira um valor na página de início é menor ou igual ao valor inserido na página associação (**1200**).  
  
     Quando isso ocorrer, uma entrada na lista de histórico é criada em vez de uma tarefa. Exibe a entrada de **histórico de fluxo de trabalho** seção da página de status do fluxo de trabalho. Observe a mensagem de **resultado** coluna do evento de histórico. Ele contém o texto inserido no `logToHistoryListActivity1.MethodInvoking` evento, que inclui o valor que foi a aprovação automática.  
  
## <a name="next-steps"></a>Próximas etapas  
 Você pode aprender mais sobre como criar modelos de fluxo de trabalho a partir destes tópicos:  
  
-   Para saber mais sobre fluxos de trabalho do SharePoint, consulte [fluxos de trabalho no Windows SharePoint Services](http://go.microsoft.com/fwlink/?LinkID=166275).  
  
## <a name="see-also"></a>Consulte também  
 [Criação de soluções de fluxo de trabalho do SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md)   
 [Instruções passo a passo: adicionar uma página de aplicativo a um fluxo de trabalho](../sharepoint/walkthrough-add-an-application-page-to-a-workflow.md)  
  
  