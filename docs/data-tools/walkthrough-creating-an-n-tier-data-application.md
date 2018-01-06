---
title: 'Passo a passo: Criando um aplicativo de dados de N camadas | Microsoft Docs'
ms.custom: 
ms.date: 09/08/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- n-tier applications, creating
- n-tier applications, walkthroughs
ms.assetid: d15e4d31-2839-48d9-9e0e-2e73404d82a2
caps.latest.revision: "48"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: 7cc4d8420cd823964aeed790a412e462b14634c0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-creating-an-n-tier-data-application"></a>Instruções passo a passo: criando um aplicativo de dados de N camadas
*N-camadas* aplicativos de dados são aplicativos que acessam dados e são separados em várias camadas lógicas, ou *camadas*. A separação de componentes de aplicativos em camadas discretas aumenta a capacidade de manutenção e a escalabilidade do aplicativo. Isso é feito pela adoção com mais facilidade de novas tecnologias que podem ser aplicadas a uma única camada, sem precisar reprojetar toda a solução. A arquitetura de N camadas inclui uma camada de apresentação, uma camada intermediária e uma camada de dados. A camada intermediária geralmente inclui uma camada de acesso a dados, uma camada lógica de negócios e componentes compartilhados, tais como autenticação e validação. A camada de dados inclui um banco de dados relacional. Os aplicativos de N camadas geralmente armazenam informações confidenciais na camada de acesso a dados da camada intermediária para manter o isolamento de usuários finais que acessam a camada de apresentação. Para obter mais informações, consulte [visão geral de aplicativos de dados de N camadas](../data-tools/n-tier-data-applications-overview.md).  
  
Uma maneira de separar as várias camadas em um aplicativo de N camadas é criar projetos discretos para cada camada que você deseja incluir em seu aplicativo. Os conjuntos de dados digitados contêm uma propriedade `DataSet Project` que determina quais projetos o conjunto de dados gerado e o código `TableAdapter` devem acessar.  
  
Este passo a passo demonstra como separar dataset e `TableAdapter` código em projetos de biblioteca de classe discreto usando o **Dataset Designer**. Após você separar o dataset e TableAdapter o código, você criará uma [serviços do Windows Communication Foundation e WCF Data Services no Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md) serviço para chamar a camada de acesso a dados. Finalmente, você criará um aplicativo do Windows Forms como a camada de apresentação. Essa camada acessa dados do serviço de dados.  
  
Durante este passo a passo, você executará as seguintes etapas:  
  
-   Criar uma nova solução de N camadas que conterá vários projetos.  
  
-   Adicionar dois projetos de bibliotecas de classes na solução de N camadas.  
  
-   Criar um conjunto de dados tipado usando o **Assistente de configuração de fonte de dados**.  
  
-   Separar gerado [TableAdapters](create-and-configure-tableadapters.md) e código de dataset em projetos distintos.  
  
-   Criar um serviço do Windows Communication Foundation (WCF) a ser chamado na camada de acesso a dados.  
  
-   Criar funções no serviço para recuperar dados da camada de acesso a dados.  
  
-   Criar um aplicativo do Windows Forms para servir como a camada de apresentação.  
  
-   Criar controles do Windows Forms associados à fonte de dados.  
  
-   Gravar código para preencher as tabelas de dados.  
  
![link para vídeo](../data-tools/media/playvideo.gif "PlayVideo") para uma versão de vídeo deste tópico, consulte [vídeo como fazer: criar um aplicativo de dados de N camadas](http://go.microsoft.com/fwlink/?LinkId=115188).  
  
## <a name="prerequisites"></a>Pré-requisitos  
Este passo a passo usa o SQL Server Express LocalDB e o banco de dados de exemplo Northwind.  
  
1.  Se você não tiver o SQL Server Express LocalDB, instale-o do [página de download de edições do SQL Server](https://www.microsoft.com/en-us/server-cloud/Products/sql-server-editions/sql-server-express.aspx), ou por meio de **instalador do Visual Studio**. No instalador do Visual Studio, o SQL Server Express LocalDB pode ser instalado como parte do **desenvolvimento de área de trabalho do .NET** carga de trabalho, ou como um componente individual.  
  
2.  Instale o banco de dados de exemplo Northwind seguindo estas etapas:  

    1. No Visual Studio, abra o **Pesquisador de objetos do SQL Server** janela. (Pesquisador de objetos do SQL Server é instalado como parte do **armazenamento de dados e processamento** carga de trabalho em que o instalador do Visual Studio.) Expanda o **do SQL Server** nó. Clique com botão direito em sua instância de LocalDB e selecione **nova consulta...** .  

       Abre uma janela do editor de consultas.  

    2. Copie o [script Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) para sua área de transferência. Este script T-SQL cria o banco de dados Northwind desde o início e a preenche com dados.  

    3. Cole o script T-SQL no editor de consultas e, em seguida, escolha o **Execute** botão.  

       Após um curto período de tempo, a consulta termina de ser executado e o banco de dados Northwind é criado.  
  
## <a name="creating-the-n-tier-solution-and-class-library-to-hold-the-dataset-dataentitytier"></a>Criando a solução de N camadas e a biblioteca de classes para manter o conjunto de dados (DataEntityTier)  
 A primeira etapa deste passo a passo é criar uma solução e dois projetos de biblioteca de classes. A primeira biblioteca de classes manterá o conjunto de dados (a classe DataSet digitada gerada e DataTables, que manterá os dados do aplicativo). Este projeto é usado como a camada de entidade de dados do aplicativo e geralmente está localizada na camada intermediária. O datasetis usado para criar o conjunto de dados inicial e separar automaticamente o código em duas classe bibliotecas.  
  
> [!NOTE]
>  Certifique-se de nome de projeto e solução corretamente antes de clicar em **Okey**. Isso facilitará a conclusão deste passo a passo.  
  
#### <a name="to-create-the-n-tier-solution-and-dataentitytier-class-library"></a>Para criar a solução de N camadas e a biblioteca de classes DataEntityTier  

1. No Visual Studio, no **arquivo** menu, selecione **novo**, **projeto...** .  
  
2. Expanda **Visual C#** ou **Visual Basic** no painel esquerdo, selecione **área de trabalho clássica do Windows**.  

3. No painel central, selecione a **biblioteca de classes** tipo de projeto.  
  
4. Nomeie o projeto **Database**.  
  
5. Nome da solução **Explorer**e, em seguida, escolha **Okey**.  
  
     Um solution Explorer que contém o projeto Database é criado e adicionado ao **Gerenciador de soluções**.  
  
## <a name="creating-the-class-library-to-hold-the-tableadapters-dataaccesstier"></a>Criando a biblioteca de classes para manter os TableAdapters (DataAccessTier)  
 A próxima etapa após a criação do projeto DataEntityTier é criar outro projeto de biblioteca de classes. Este projeto manterá gerado `TableAdapter`s e é chamado de *da camada de acesso de dados* do aplicativo. A camada de acesso a dados contém as informações necessárias para se conectar ao banco de dados e geralmente está localizada na camada intermediária.  
  
#### <a name="to-create-a-separate-class-library-for-the-tableadapters"></a>Para criar uma biblioteca de classe separada para os TableAdapters  
  
1.  Com o botão direito na solução no Gerenciador de soluções e escolha **adicionar**, **novo projeto...** .  
  
2.  No **novo projeto** caixa de diálogo, no painel central, selecione **biblioteca de classes**.  
  
3.  Nomeie o projeto **num projeto** e escolha **Okey**.  
  
     O projeto DataAccessTier é criado e adicionado à solução NTierWalkthrough.  
  
## <a name="creating-the-dataset"></a>Criando o conjunto de dados  
 A próxima etapa é criar um conjunto de dados tipado. Os conjuntos de dados tipado são criados com a classe do conjunto de dados (incluindo as classes DataTables) e as classes `TableAdapter` em um único projeto. (Todas as classes são geradas em um único arquivo.) Quando você separa o conjunto de dados e os `TableAdapter`s em projetos diferentes, é a classe do conjunto de dados que é movida para o outro projeto, mantendo as classes `TableAdapter` no projeto original. Portanto, crie o conjunto de dados no projeto que conterá, por fim, os `TableAdapter`s (o projeto DataAccessTier). Você criará o conjunto de dados usando o **Assistente de configuração de fonte de dados**.  
  
> [!NOTE]
>  É preciso ter acesso ao banco de dados de exemplo Northwind para criar a conexão. Para obter informações sobre como configurar o banco de dados de exemplo Northwind, consulte [como: instalar bancos de dados de exemplo](../data-tools/installing-database-systems-tools-and-samples.md).  
  
#### <a name="to-create-the-dataset"></a>Para criar o conjunto de dados  
  
1.  Selecione num projeto em **Gerenciador de soluções**.  
  
2.  Sobre o **dados** menu, selecione **Mostrar fontes de dados**.  
  
3.  No **fontes de dados** janela, selecione **adicionar nova fonte de dados** para iniciar o **Assistente de configuração de fonte de dados**.  
  
4.  Sobre o **escolher um tipo de fonte de dados** página, selecione **banco de dados** e, em seguida, selecione **próximo**.  
  
5.  Sobre o **escolha sua Conexão de dados** página, execute uma das seguintes ações:  
  
     Se uma conexão de dados com o banco de dados de exemplo Northwind estiver disponível na lista suspensa, selecione-o.  
  
     -ou-  
  
     Selecione **nova Conexão** para abrir o **Adicionar Conexão** caixa de diálogo.  
  
6.  Se o banco de dados exigir uma senha, selecione a opção para incluir dados confidenciais e, em seguida, escolha **próximo**.  
  
    > [!NOTE]
    >  Se você escolheu um arquivo do banco de dados local (em vez de se conectar ao SQL Server), talvez seja perguntado se deseja adicionar o arquivo ao projeto. Escolha **Sim** para adicionar o arquivo de banco de dados para o projeto.  
  
7.  Selecione **próximo** no **salvar a cadeia de Conexão no arquivo de configuração do aplicativo** página.  
  
8.  Expanda o **tabelas** nó sob o **escolher seus objetos de banco de dados** página.  
  
9.  Marque as caixas de seleção para o **clientes** e **pedidos** tabelas e, em seguida, escolha **concluir**.  
  
     NorthwindDataSet é adicionado ao projeto num projeto e aparece no **fontes de dados** janela.  
  
## <a name="separating-the-tableadapters-from-the-dataset"></a>Separando os TableAdapters do Conjunto de Dados  
 Depois de criar o conjunto de dados, separe a classe do conjunto de dados gerada a partir dos TableAdapters. Você pode fazer isso definindo o **projeto DataSet** propriedade para o nome do projeto no qual armazenar a separados sem classe dataset.  
  
#### <a name="to-separate-the-tableadapters-from-the-dataset"></a>Para separar os TableAdapters do Conjunto de Dados  
  
1.  Clique duas vezes em **NorthwindDataSet** na **Solution Explorer** para abrir o conjunto de dados a **Dataset Designer**.  
  
2.  Selecione uma área vazia no designer.  
  
3.  Localize o **projeto DataSet** nó o **propriedades** janela.  
  
4.  No **projeto DataSet** lista, selecione **Database**.  
  
5.  Sobre o **criar** menu, selecione **compilar solução**.  
  
 O conjunto de dados e os TableAdapters são separados em dois projetos de biblioteca de classes. O projeto que continha originalmente todo o conjunto de dados (DataAccessTier) contém agora somente os TableAdapters. O projeto designado no **projeto DataSet** propriedade (Database) contém o conjunto de dados tipado: NorthwindDataSet (ou designer.cs).  
  
> [!NOTE]
>  Quando você separar conjuntos de dados e TableAdapters (definindo o **projeto DataSet** propriedade), classes parciais dataset existentes no projeto não serão movidas automaticamente. As classes parciais do conjunto de dados existentes devem ser movidas manualmente para o projeto do conjunto de dados.  
  
## <a name="creating-a-new-service-application"></a>Criando um novo aplicativo de serviço  
Este passo a passo demonstra como acessar a camada de acesso de dados usando um serviço WCF, portanto, vamos criar um novo aplicativo de serviço do WCF.  
  
#### <a name="to-create-a-new-wcf-service-application"></a>Para criar um novo aplicativo de Serviço WCF  
  
1.  Com o botão direito na solução no Gerenciador de soluções e escolha **adicionar**, **novo projeto...** .  
  
2.  No **novo projeto** caixa de diálogo, no painel esquerdo, selecione **WCF**.  No painel central, selecione **biblioteca de serviços WCF**.  
  
3.  Nomeie o projeto **DataService** e selecione **Okey**.  
  
     O projeto DataService é criado e adicionado à solução NTierWalkthrough.  
  
## <a name="creating-methods-in-the-data-access-tier-to-return-the-customers-and-orders-data"></a>Criando métodos na camada de acesso a dados para retornar os dados de clientes e pedidos  
 O serviço de dados deve chamar dois métodos na camada de acesso a dados: GetCustomers e GetOrders. Esses métodos retornarão as tabelas Clientes e Pedidos do Northwind. Crie os métodos GetCustomers e GetOrders no projeto DataAccessTier.  
  
#### <a name="to-create-a-method-in-the-data-access-tier-that-returns-the-customers-table"></a>Para criar um método na camada de acesso a dados que retorna a tabela Clientes  
  
1.  Em **Solution Explorer**, clique duas vezes em NorthwindDataSet para abrir o conjunto de dados.
  
2.  Mouse CustomersTableAdapter e clique em **adicionar consulta**.  
  
3.  Sobre o **escolher um tipo de comando** , deixe o valor padrão de **instruções Use SQL** e clique em **próximo**.  
  
4.  Sobre o **escolher um tipo de consulta** , deixe o valor padrão de **SELECT que retorna linhas** e clique em **próximo**.  
  
5.  Sobre o **especificar uma instrução SQL SELECT** página, deixe a consulta padrão e clique em **próximo**.  
  
6.  No **escolha métodos para gerar** página, digite **GetCustomers** para o **nome do método** no **retornar uma DataTable** seção.  
  
7.  Clique em **Finalizar**.  
  
#### <a name="to-create-a-method-in-the-data-access-tier-that-returns-the-orders-table"></a>Para criar um método na camada de acesso a dados que retorna a tabela Pedidos  
  
1.  Clique com botão direito OrdersTableAdapter e clique em **adicionar consulta**.  
  
2.  Sobre o **escolher um tipo de comando** , deixe o valor padrão de **instruções Use SQL** e clique em **próximo**.  
  
3.  Sobre o **escolher um tipo de consulta** , deixe o valor padrão de **SELECT que retorna linhas** e clique em **próximo**.  
  
4.  Sobre o **especificar uma instrução SQL SELECT** página, deixe a consulta padrão e clique em **próximo**.  
  
5.  No **escolha métodos para gerar** página, digite **GetOrders** para o **nome do método** no **retornar uma DataTable** seção.  
  
6.  Clique em **Finalizar**.  
  
7.  No menu **Compilar**, clique em **Compilar Solução**.  
  
## <a name="adding-a-reference-to-the-data-entity-and-data-access-tiers-to-the-data-service"></a>Adicionando uma referência à entidade de dados e às camadas de acesso a dados para o serviço de dados  
 Como o serviço de dados requer informações do conjunto de dados e dos TableAdapters, adicione referências aos projetos DataEntityTier e DataAccessTier.  
  
#### <a name="to-add-references-to-the-data-service"></a>Para adicionar referência aos serviço de dados  
  
1.  Clique com botão direito DataService em **Solution Explorer** e clique em **adicionar referência**.  
  
2.  Clique o **projetos** guia o **adicionar referência** caixa de diálogo.  
  
3.  Selecione o **num projeto** e **Database** projetos.  
  
4.  Clique em **OK**.  
  
## <a name="adding-functions-to-the-service-to-call-the-getcustomers-and-getorders-methods-in-the-data-access-tier"></a>Adicionando funções ao serviço para chamar os métodos GetCustomers e GetOrders na camada de acesso a dados  
 Agora que a camada de acesso a dados contém os métodos para retornar dados, crie métodos no serviço de dados para chamar os métodos na camada de acesso a dados.  
  
> [!NOTE]
>  Para projetos C#, adicione uma referência ao assembly `System.Data.DataSetExtensions` para que o código a seguir seja compilado.  
  
#### <a name="to-create-the-getcustomers-and-getorders-functions-in-the-data-service"></a>Para criar as funções GetCustomers e GetOrders no serviço de dados  
  
1.  No **DataService** do projeto, clique duas vezes em IService1.vb ou Iservice1.  
  
2.  Adicione o seguinte código sob o **adicionar suas operações de serviço** comentário:  
  
    ```vb  
    <OperationContract()> _  
    Function GetCustomers() As DataEntityTier.NorthwindDataSet.CustomersDataTable  
  
    <OperationContract()> _  
    Function GetOrders() As DataEntityTier.NorthwindDataSet.OrdersDataTable  
    ```  
  
    ```csharp  
    [OperationContract]  
    DataEntityTier.NorthwindDataSet.CustomersDataTable GetCustomers();  
  
    [OperationContract]  
    DataEntityTier.NorthwindDataSet.OrdersDataTable GetOrders();  
    ```  
  
3.  No projeto DataService, dê um clique duplo em Service1.vb (ou Service1.cs).  
  
4.  Adicione o seguinte código à classe Service1:  
  
    ```vb  
    Public Function GetCustomers() As DataEntityTier.NorthwindDataSet.CustomersDataTable Implements IService1.GetCustomers  
        Dim CustomersTableAdapter1 As New DataAccessTier.NorthwindDataSetTableAdapters.CustomersTableAdapter  
        Return CustomersTableAdapter1.GetCustomers()  
    End Function  
  
    Public Function GetOrders() As DataEntityTier.NorthwindDataSet.OrdersDataTable Implements IService1.GetOrders  
        Dim OrdersTableAdapter1 As New DataAccessTier.NorthwindDataSetTableAdapters.OrdersTableAdapter  
        Return OrdersTableAdapter1.GetOrders()  
    End Function  
    ```  
  
    ```csharp  
    public DataEntityTier.NorthwindDataSet.CustomersDataTable GetCustomers()  
    {  
        DataAccessTier.NorthwindDataSetTableAdapters.CustomersTableAdapter  
             CustomersTableAdapter1  
            = new DataAccessTier.NorthwindDataSetTableAdapters.CustomersTableAdapter();  
        return CustomersTableAdapter1.GetCustomers();  
    }  
    public DataEntityTier.NorthwindDataSet.OrdersDataTable GetOrders()  
    {  
        DataAccessTier.NorthwindDataSetTableAdapters.OrdersTableAdapter  
             OrdersTableAdapter1  
            = new DataAccessTier.NorthwindDataSetTableAdapters.OrdersTableAdapter();  
        return OrdersTableAdapter1.GetOrders();  
    }  
    ```  
  
5.  No menu **Compilar**, clique em **Compilar Solução**.  
  
## <a name="creating-a-presentation-tier-to-display-data-from-the-data-service"></a>Criando uma camada de apresentação para exibir dados a partir do serviço de dados  
 Agora que a solução contém o serviço de dados que possui métodos chamados na camada de acesso a dados, crie outro projeto que será chamado no serviço de dados e apresente os dados aos usuários. Neste passo a passo, crie um aplicativo do Windows Forms, o qual será a camada de apresentação do aplicativo de N camadas.  
  
#### <a name="to-create-the-presentation-tier-project"></a>Para criar o projeto da camada de apresentação  
  
1.  Com o botão direito na solução no Gerenciador de soluções e escolha **adicionar**, **novo projeto...** .  
  
2.  No **novo projeto** caixa de diálogo, no painel esquerdo, selecione **área de trabalho clássica do Windows**. No painel central, selecione **aplicativo do Windows Forms**.  
  
3.  Nomeie o projeto **projeto** e clique em **Okey**.  
  
    O projeto PresentationTier é criado e adicionado à solução NTierWalkthrough.  
  
## <a name="setting-the-presentationtier-project-as-the-startup-project"></a>Configurando o projeto PresentationTier como o projeto de inicialização  
Vamos definir o projeto para o projeto de inicialização para a solução, porque é o aplicativo cliente real que é usado para apresentar e interagir com os dados.  
  
#### <a name="to-set-the-new-presentation-tier-project-as-the-startup-project"></a>Para configurar o novo projeto de camada de apresentação como o projeto de inicialização  
  
-   Em **Solution Explorer**, clique com botão direito **projeto** e clique em **definir como projeto de inicialização**.  
  
## <a name="adding-references-to-the-presentation-tier"></a>Adicionando referências à camada de apresentação  
 O aplicativo cliente PresentationTier requer uma referência de serviço para o serviço de dados a fim de acessar os métodos no serviço. Além disso, uma referência ao conjunto de dados é necessária para permitir o compartilhamento de tipos pelo serviço WCF. O código adicionado à classe do conjunto de dados parcial estará disponível na camada de apresentação somente após você permitir o compartilhamento de tipos por meio do serviço de dados. Como você geralmente adiciona código como validação para os eventos de alteração de linha e coluna de uma tabela de dados, é provável que você queira acessar esse código a partir do cliente.  
  
#### <a name="to-add-a-reference-to-the-presentation-tier"></a>Para adicionar uma referência à camada de apresentação  
  
1.  Em **Solution Explorer**, nó do projeto e selecione **adicionar referência**.  
  
2.  No **adicionar referência** caixa de diálogo, selecione o **projetos** guia.  
  
3.  Selecione **Database** e escolha **Okey**.  
  
#### <a name="to-add-a-service-reference-to-the-presentation-tier"></a>Para adicionar uma referência de serviço à camada de apresentação  
  
1.  Em **Solution Explorer**, nó do projeto e selecione **adicionar referência de serviço**.  
  
2.  No **adicionar referência de serviço** caixa de diálogo, selecione **Discover**.  
  
3.  Selecione **Service1** e escolha **Okey**.  
  
    > [!NOTE]
    >  Se você tiver vários serviços no computador atual, escolha o serviço criado anteriormente neste passo a passo (o serviço que contém os métodos GetCustomers e GetOrders).  
  
## <a name="adding-datagridviews-to-the-form-to-display-the-data-returned-by-the-data-service"></a>Adicionando DataGridViews ao formulário para exibir os dados retornados pelo serviço de dados  
 Depois de adicionar a referência de serviço para o serviço de dados, o **fontes de dados** janela é preenchida automaticamente com os dados que são retornados pelo serviço.  
  
#### <a name="to-add-two-data-bound-datagridviews-to-the-form"></a>Para adicionar duas associações de dados DataGridViews ao formulário  
  
1.  Em **Solution Explorer**, selecione o projeto.  
  
2.  No **fontes de dados** janela, expanda **NorthwindDataSet** e localize o **clientes** nó.  
  
3.  Arraste o **clientes** nó Form1.  
  
4.  No **fontes de dados** janela, expanda o **clientes** nó e localize relacionado **pedidos** nó (o **pedidos** nó aninhado no  **Os clientes** nó).  
  
5.  Arraste relacionado **pedidos** nó Form1.  
  
6.  Crie um manipulador de eventos `Form1_Load` ao clicar duas vezes em uma área vazia do formulário.  
  
7.  Adicione o seguinte código ao manipulador de eventos do `Form1_Load`.  
  
    ```vb  
    Dim DataSvc As New ServiceReference1.Service1Client  
    NorthwindDataSet.Customers.Merge(DataSvc.GetCustomers)  
    NorthwindDataSet.Orders.Merge(DataSvc.GetOrders)  
    ```  
  
    ```csharp  
    ServiceReference1.Service1Client DataSvc =   
        new ServiceReference1.Service1Client();  
    northwindDataSet.Customers.Merge(DataSvc.GetCustomers());  
    northwindDataSet.Orders.Merge(DataSvc.GetOrders());  
    ```  
  
## <a name="increasing-the-maximum-message-size-allowed-by-the-service"></a>Aumentando o tamanho máximo da mensagem permitida pelo serviço  
O valor padrão para maxReceivedMessageSize não é grande o suficiente para manter os dados recuperados das tabelas Customers e Orders. Nas etapas a seguir, você poderá aumentar o valor para 6553600. Você irá alterar o valor no cliente, que automaticamente atualiza a referência de serviço.  
  
> [!NOTE]
>  O menor tamanho padrão se destina a limitar a exposição para ataques de negação de serviço (DoS). Para obter mais informações, consulte <xref:System.ServiceModel.WSHttpBindingBase.MaxReceivedMessageSize%2A>.  
  
#### <a name="to-increase-the-maxreceivedmessagesize-value"></a>Para aumentar o valor maxReceivedMessageSize  
  
1.  Em **Solution Explorer**, duas vezes no arquivo App. config do projeto.  
  
2.  Localize o **m axReceivedMessage** atributo de tamanho e altere o valor para `6553600`.  
  
## <a name="testing-the-application"></a>Testando o aplicativo  
Execute o aplicativo pressionando **F5**. Os dados das tabelas Clientes e Pedidos são recuperados a partir do serviço de dados e exibidos no formulário.  
  
## <a name="next-steps"></a>Próximas etapas  
 Dependendo dos requisitos do aplicativo, existem várias etapas que você talvez queira realizar após salvar os dados relacionados no aplicativo baseado em Windows. Por exemplo, você poderia fazer as seguintes melhorias a este aplicativo:  
  
-   Adicionar validação ao conjunto de dados. 
  
-   Adicionar métodos adicionais ao serviço para atualizar dados novamente no banco de dados.  
  
## <a name="see-also"></a>Consulte também  
 [Trabalhar com conjuntos de dados em aplicativos de n camadas](../data-tools/work-with-datasets-in-n-tier-applications.md)   
 [Atualização hierárquica](../data-tools/hierarchical-update.md)   
 [Acessando dados no Visual Studio](../data-tools/accessing-data-in-visual-studio.md)