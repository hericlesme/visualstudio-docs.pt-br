---
title: Associar controles WPF a um WCF data Services | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio], walkthroughs
- WPF Designer, data binding
ms.assetid: 8823537c-82f0-41f7-bf30-705f0e5e59fd
caps.latest.revision: "40"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: ec13e17aac37a24e92732b9b052147c7d9faa916
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="bind-wpf-controls-to-a-wcf-data-service"></a>Associar controles WPF a um WCF data Services
Neste passo a passo, você criará um aplicativo WPF que contém controles de associação de dados. Os controles estão associados a registros de clientes que são encapsulados em um [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)]. Você também adicionará botões que os clientes podem usar para exibir e atualizar registros.  
  
Esta explicação passo a passo ilustra as seguintes tarefas:  
  
- Criando um Modelo de Dados de Entidade que é gerado a partir de dados no banco de dados de exemplo AdventureWorksLT.  
  
- Criando um [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] que expõe os dados no modelo de dados de entidade para um aplicativo do WPF.  
  
- Criando um conjunto de controles associados a dados, arrastando itens a partir de **fontes de dados** janela para o designer do WPF.  
  
- Criando botões que navegam para a frente e para trás nos registros de clientes.  
  
- Criar um botão que salva as alterações nos dados em controles para o [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] e a fonte de dados subjacente.  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## <a name="prerequisites"></a>Pré-requisitos  
Você precisa dos seguintes componentes para concluir esta instrução passo a passo:  
  
-   [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]  
  
-   Acesso a uma instância em execução do SQL Server ou SQL Server Express que tenha o banco de dados de exemplo AdventureWorksLT anexado a ele. Você pode baixar o banco de dados AdventureWorksLT o [site da CodePlex](http://go.microsoft.com/fwlink/?linkid=87843).  
  
Conhecimento prévio dos conceitos a seguir também é útil, mas não é necessário para concluir o passo a passo:  
  
-   WCF Data Services. Para obter mais informações, consulte [visão geral](/dotnet/framework/data/wcf/wcf-data-services-overview).  
  
-   Modelos de dados no [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)].  
  
-   Modelos de Dados de Entidade e o ADO.NET Entity Framework. Para obter mais informações, consulte [visão geral do Entity Framework](/dotnet/framework/data/adonet/ef/overview).  
  
-   Associação de dados do WPF. Para obter mais informações, consulte [Visão geral de vinculação de dados](/dotnet/framework/wpf/data/data-binding-overview).  
  
## <a name="create-the-service-project"></a>Criar o projeto de serviço  
Comece este passo a passo criando um projeto para um [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)].  
  
#### <a name="to-create-the-service-project"></a>Para criar o projeto de serviço  
  
1.  Inicie o Visual Studio.  
  
2.  No menu **Arquivo**, aponte para **Novo** e clique em **Projeto**.  
  
3.  Expanda **Visual C#** ou **Visual Basic**e, em seguida, selecione **Web**.  
  
4.  Selecione o modelo de projeto **Aplicativo Web ASP.NET**.  
  
5.  No **nome** , digite `AdventureWorksService` e clique em **Okey**.  
  
     O Visual Studio cria o `AdventureWorksService` projeto.  
  
6.  Em **Solution Explorer**, clique com botão direito **Default.aspx** e selecione **excluir**. Este arquivo não é necessário neste passo a passo.  
  
## <a name="create-an-entity-data-model-for-the-service"></a>Criar um modelo de dados de entidade para o serviço  
Para expor os dados para um aplicativo usando um [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)], você deve definir um modelo de dados para o serviço. O [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] dá suporte a dois tipos de modelos de dados: modelos de dados de entidade e modelos de dados personalizados que são definidos usando objetos common language runtime (CLR) que implementa o <xref:System.Linq.IQueryable%601> interface. Neste passo a passo, você criará um Modelo de Dados de Entidade para o modelo de dados.  
  
#### <a name="to-create-an-entity-data-model"></a>Para criar um Modelo de Dados de Entidade  
  
1.  No menu **Projeto**, clique em **Adicionar Novo Item**.  
  
2.  Na lista de modelos instalados, clique em **dados**e, em seguida, selecione o **modelo de dados de entidade ADO.NET** item de projeto.  
  
3.  Altere o nome para `AdventureWorksModel.edmx`e clique em **adicionar**.  
  
     O **modelo de dados de entidade** assistente é aberto.  
  
4.  No **escolher o modelo de conteúdo** , clique em **gerar do banco de dados**e clique em **próximo**.  
  
5.  Sobre o **escolha sua Conexão de dados** , selecione uma das opções a seguir:  
  
    -   Se uma conexão de dados com o banco de dados de exemplo AdventureWorksLT estiver disponível na lista suspensa, selecione-a.  
  
    -   Clique em **nova Conexão**e criar uma conexão ao banco de dados AdventureWorksLT.  
  
6.  No **escolha sua Conexão de dados** página, certifique-se de que o **salvar configurações de conexão de entidade no App. config como** opção é selecionada e, em seguida, clique em **próximo**.  
  
7.  Sobre o **escolher seus objetos de banco de dados** página, expanda **tabelas**e, em seguida, selecione o **SalesOrderHeader** tabela.  
  
8.  Clique em **Finalizar**.  
  
## <a name="create-the-service"></a>Criar o serviço  
Criar um [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] para expor os dados no modelo de dados de entidade para um aplicativo do WPF.  
  
#### <a name="to-create-the-service"></a>Para criar o serviço  
  
1.  Sobre o **projeto** menu, selecione **Adicionar Novo Item**.  
  
2.  Na lista de modelos instalados, clique em **Web**e, em seguida, selecione o **WCF Data Service** item de projeto.  
  
3.  No **nome** , digite `AdventureWorksService.svc`e clique em **adicionar**.  
  
     O Visual Studio adiciona o `AdventureWorksService.svc` ao projeto.  
  
## <a name="configure-the-service"></a>Configurar o serviço  
Você deve configurar o serviço para operar no Modelo de Dados de Entidades que você criou.  
  
#### <a name="to-configure-the-service"></a>Para configurar o serviço  
  
1.  No `AdventureWorks.svc` arquivo de código, substitua o `AdventureWorksService` classe declaração com o código a seguir.  
  
     [!code-csharp[Data_WPFWCF#1](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_1.cs)]
     [!code-vb[Data_WPFWCF#1](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_1.vb)]  
  
     Esse código atualiza a `AdventureWorksService` de classe, para que deriva de um <xref:System.Data.Services.DataService%601> que opera no `AdventureWorksLTEntities` classe em seu modelo de dados de entidade de contexto do objeto. Ele também atualiza o método `InitializeService` para permitir aos clientes do serviço acesso completo de leitura/gravação à entidade `SalesOrderHeader`.  
  
2.  Crie o projeto e verifique se ele foi criado sem erros.  
  
## <a name="create-the-wpf-client-application"></a>Criar o aplicativo cliente WPF  
Para exibir os dados do [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)], crie um novo aplicativo WPF com uma fonte de dados que se baseie no serviço. A seguir neste passo a passo, você adicionará controles de associação de dados ao aplicativo.  
  
#### <a name="to-create-the-wpf-client-application"></a>Para criar o aplicativo cliente WPF  
  
1.  Em **Solution Explorer**, com o botão direito no nó da solução, clique em **adicionar**e selecione **novo projeto**.  
  
2.  No **novo projeto** caixa de diálogo, expanda **Visual C#** ou **Visual Basic**e, em seguida, selecione **Windows**.  
  
3.  Selecione o **aplicativo WPF** modelo de projeto.  
  
4.  No **nome** , digite `AdventureWorksSalesEditor`e clique em **Okey**.  
  
     O Visual Studio adiciona o `AdventureWorksSalesEditor` projeto à solução.  
  
5.  Sobre o **dados** menu, clique em **Mostrar fontes de dados**.  
  
     O **fontes de dados** janela será aberta.  
  
6.  No **fontes de dados** janela, clique em **adicionar nova fonte de dados**.  
  
     O **configuração da fonte de dados** assistente é aberto.  
  
7.  No **escolher um tipo de fonte de dados** página do assistente, selecione **Service**e, em seguida, clique em **próximo**.  
  
8.  No **adicionar referência de serviço** caixa de diálogo, clique em **Discover**.  
  
     O Visual Studio procura a atual solução de serviços disponíveis e adiciona `AdventureWorksService.svc` à lista de serviços disponíveis no **serviços** caixa.  
  
9. No **Namespace** , digite `AdventureWorksService`.  
  
10. No **serviços** , clique em **AdventureWorksService.svc**e, em seguida, clique em **Okey**.  
  
     Visual Studio baixará as informações de serviço e, em seguida, retorna para o **configuração da fonte de dados** assistente.  
  
11. No **adicionar referência de serviço** , clique em **concluir**.  
  
     O Visual Studio adiciona nós que representam os dados retornados pelo serviço para o **fontes de dados** janela.  
  
## <a name="define-the-user-interface-of-the-window"></a>Definir a interface do usuário da janela  
Adicione vários botões à janela, modificando o XAML no WPF Designer. A seguir neste passo a passo, você adicionará código que permite aos usuários exibir e atualizar registros de vendas usando esses botões.  
  
#### <a name="to-create-the-window-layout"></a>Para criar o layout da janela  
  
1.  Em **Solution Explorer**, clique duas vezes em **MainWindow**.  
  
     A janela é aberta no WPF Designer.  
  
2.  Na exibição [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] do designer, adicione o seguinte código entre as marcas `<Grid>`:  
  
    ```xaml  
    <Grid.RowDefinitions>  
        <RowDefinition Height="75" />  
        <RowDefinition Height="525" />  
    </Grid.RowDefinitions>  
    <Button HorizontalAlignment="Left" Margin="22,20,0,24" Name="backButton" Width="75"><</Button>  
    <Button HorizontalAlignment="Left" Margin="116,20,0,24" Name="nextButton" Width="75">></Button>  
    <Button HorizontalAlignment="Right" Margin="0,21,46,24" Name="saveButton" Width="110">Save changes</Button>  
    ```  
  
3.  Compile o projeto.  
  
## <a name="create-the-data-bound-controls"></a>Criar os controles associados a dados  
Criar controles que exibem os registros de clientes, arrastando o `SalesOrderHeaders` nó do **fontes de dados** janela no Designer.  
  
#### <a name="to-create-the-data-bound-controls"></a>Para criar os controles de associação de dados  
  
1.  No **fontes de dados** janela, clique no menu suspenso para a **SalesOrderHeaders** nó e selecione **detalhes**.  
  
2.  Expanda o **SalesOrderHeaders** nó.  
  
3.  Neste exemplo, alguns campos não serão exibidos, então clique no menu suspenso ao lado de nós seguir e selecione **nenhum**:  
  
    -   **CreditCardApprovalCode**  
  
    -   **ModifiedDate**  
  
    -   **OnlineOrderFlag**  
  
    -   **RevisionNumber**  
  
    -   **ROWGUID**  
  
    Essa ação impede que o Visual Studio crie controles de associação de dados para esses nós na etapa seguinte. Para este passo a passo, assuma que o usuário final não precisa ver esses dados.  
  
4.  Do **fontes de dados** janela, arraste o **SalesOrderHeaders** nó para a linha de grade sob a linha que contém os botões.  
  
     O Visual Studio gera XAML e código que cria um conjunto de controles associados a dados de **produto** tabela. Para obter mais informações sobre o XAML e o código gerado, consulte [WPF associar controles a dados no Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).  
  
5.  No designer, clique na caixa de texto ao lado de **Customer ID** rótulo.  
  
6.  No **propriedades** janela, selecione a caixa de seleção ao lado de **IsReadOnly** propriedade.  
  
7.  Definir o **IsReadOnly** propriedade para cada uma das seguintes caixas de texto:  
  
    -   **Número de ordem de compra**  
  
    -   **ID do pedido de vendas**  
  
    -   **Número do pedido de vendas**  
  
## <a name="load-the-data-from-the-service"></a>Carregar os dados do serviço  
Use o objeto de proxy de serviço para carregar dados de vendas do serviço. Atribua os dados retornados para a fonte de dados para o <xref:System.Windows.Data.CollectionViewSource> na janela do WPF.  
  
#### <a name="to-load-the-data-from-the-service"></a>Para carregar os dados do serviço  
  
1.  No designer, para criar o `Window_Loaded` manipulador de eventos, clique duas vezes o texto: **MainWindow**.  
  
2.  Substitua o manipulador de eventos pelo código a seguir. Certifique-se de que você substitua o *localhost* endereço nesse código com o endereço do host local no computador de desenvolvimento.  
  
     [!code-csharp[Data_WPFWCF#2](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_2.cs)]
     [!code-vb[Data_WPFWCF#2](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_2.vb)]  
  
## <a name="navigate-sales-records"></a>Navegar pelos registros de vendas  
Adicione o código que permite aos usuários percorrer registros de vendas usando o  **\<**  e  **>**  botões.  
  
#### <a name="to-enable-users-to-navigate-sales-records"></a>Para permitir que os usuários naveguem nos registros de vendas  
  
1.  No designer, clique duas vezes o  **<**  botão na superfície de janela.  
  
     Visual Studio abre o arquivo code-behind e cria um novo `backButton_Click` manipulador de eventos para o <xref:System.Windows.Controls.Primitives.ButtonBase.Click> evento.  
  
2.  Adicione o seguinte código ao manipulador de eventos `backButton_Click` gerado:  
  
     [!code-csharp[Data_WPFWCF#3](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_3.cs)]
     [!code-vb[Data_WPFWCF#3](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_3.vb)]  
  
3.  Retornar ao designer e clique duas vezes o  **>**  botão.  
  
     Visual Studio abre o arquivo code-behind e cria um novo `nextButton_Click` manipulador de eventos para o <xref:System.Windows.Controls.Primitives.ButtonBase.Click> evento.  
  
4.  Adicione o seguinte código ao manipulador de eventos `nextButton_Click` gerado:  
  
     [!code-csharp[Data_WPFWCF#4](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_4.cs)]
     [!code-vb[Data_WPFWCF#4](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_4.vb)]  
  
## <a name="saving-changes-to-sales-records"></a>Salvar alterações em registros de vendas  
Adicione o código que permite que os usuários de exibir e salvar as alterações em registros de vendas, usando o **salvar alterações** botão.  
  
#### <a name="to-add-the-ability-to-save-changes-to-sales-records"></a>Para adicionar a capacidade de salvar as alterações em registros de vendas  
  
1.  No designer, clique duas vezes o **salvar alterações** botão.  
  
     Visual Studio abre o arquivo code-behind e cria um novo `saveButton_Click` manipulador de eventos para o <xref:System.Windows.Controls.Primitives.ButtonBase.Click> evento.  
  
2.  Adicione o seguinte código ao manipulador de eventos do `saveButton_Click`.  
  
     [!code-csharp[Data_WPFWCF#5](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_5.cs)]
     [!code-vb[Data_WPFWCF#5](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_5.vb)]  
  
## <a name="testing-the-application"></a>Testando o aplicativo  
Compile e execute o aplicativo para verificar se é possível exibir e atualizar os registros do cliente.  
  
#### <a name="to-test-the-application"></a>Para testar o aplicativo  
  
1.  Em **criar** menu, clique em **compilar solução**. Verifique se a solução é compilada sem erros.  
  
2.  Pressione **Ctrl + F5**.  
  
     O Visual Studio inicia o **AdventureWorksService** projeto sem depurá-lo.  
  
3.  Em **Solution Explorer**, com o botão direito do **AdventureWorksSalesEditor** projeto.  
  
4.  No menu de contexto, em **depurar**, clique em **iniciar nova instância**.  
  
     O aplicativo é executado. Verifique o seguinte:  
  
    -   As caixas de texto exibem diferentes campos de dados a partir do primeiro registro de vendas, que tem a ID de ordem de venda **71774**.  
  
    -   Você pode clicar no  **>**  ou  **<**  botões para navegar por meio de outros registros de vendas.  
  
5.  Em um dos registros de vendas, digite o texto a **comentário** caixa e, em seguida, clique em **salvar alterações**.  
  
6.  Feche o aplicativo e depois inicie-o novamente no Visual Studio.  
  
7.  Navegue até o registro de vendas que você alterou e verifique se a alteração persiste depois de fechar e reabrir o aplicativo.  
  
8.  Feche o aplicativo.  
  
## <a name="next-steps"></a>Próximas etapas  
Depois de completar este passo a passo, você poderá realizar as seguintes tarefas relacionadas:  
  
-   Saiba como usar o **fontes de dados** controles de janela no Visual Studio para associar WPF para outros tipos de fontes de dados. Para obter mais informações, consulte [WPF associar controles a um conjunto de dados](../data-tools/bind-wpf-controls-to-a-dataset.md).  
  
-   Saiba como usar o **fontes de dados** janela no Visual Studio para exibir dados relacionados (ou seja, os dados em uma relação pai-filho) em controles WPF. Para obter mais informações, consulte [passo a passo: exibindo dados relacionados em um aplicativo WPF](../data-tools/display-related-data-in-wpf-applications.md).  
  
## <a name="see-also"></a>Consulte também
[Vincular controles WPF a dados no Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)   
[Associar controles WPF a um conjunto de dados](../data-tools/bind-wpf-controls-to-a-dataset.md)   
[Visão geral do WCF (.NET Framework)](/dotnet/framework/data/wcf/wcf-data-services-overview)   
[Visão geral do Entity Framework (.NET Framework)](/dotnet/framework/data/adonet/ef/overview)  
[Visão geral (.NET Framework) de associação de dados](/dotnet/framework/wpf/data/data-binding-overview)