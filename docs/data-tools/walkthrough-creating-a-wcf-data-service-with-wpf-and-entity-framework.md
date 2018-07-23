---
title: 'Passo a passo: Criando um serviço de dados do WCF com WPF e Entity Framework'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data services in Visual Studio
- WCF Data Services, Visual Studio
- ADO.NET Data Services, Visual Studio
- WCF data services in Visual Studio
ms.assetid: da66ad1b-a25d-485c-af13-2d18f0422e3d
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: b796bf5b17460425d25ec91f3ecca7c147784039
ms.sourcegitcommit: f37affbc1b885dfe246d4b2c295a6538b383a0ca
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37174967"
---
# <a name="walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework"></a>Passo a passo: Criando um serviço de dados do WCF com WPF e Entity Framework
Este passo a passo demonstra como criar um simples [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] que é hospedado em um [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplicativo Web e, em seguida, acessá-lo de um aplicativo Windows Forms.

Neste passo a passo você:

-   Criará um aplicativo Web para hospedar um [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)].

-   Criar uma [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] que representa o `Customers` tabela no banco de dados Northwind.

-   Criará um [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)].

-   Criará um aplicativo cliente e adicionará uma referência ao [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)].

-   Habilitará a associação de dados ao serviço e gerará a interface de usuário.

-   Se desejar, adicionará recursos de filtragem ao aplicativo.

## <a name="prerequisites"></a>Pré-requisitos
Este passo a passo usa o SQL Server Express LocalDB e o banco de dados de exemplo Northwind.

1.  Se você não tiver o SQL Server Express LocalDB, instalá-lo a partir de [página de download do SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), ou por meio de **instalador do Visual Studio**. No **instalador do Visual Studio**, você pode instalar o SQL Server Express LocalDB como parte do **armazenamento de dados e processamento** carga de trabalho, ou como um componente individual.

2.  Instale o banco de dados de exemplo Northwind, seguindo estas etapas:

    1. No Visual Studio, abra o **SQL Server Object Explorer** janela. (**Pesquisador de objetos do SQL Server** é instalado como parte do **armazenamento de dados e processamento** carga de trabalho no instalador do Visual Studio.) Expanda o **SQL Server** nó. Clique com botão direito na instância do LocalDB e selecione **nova consulta**.

       Abre uma janela do editor de consulta.

    2. Cópia de [script Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) na área de transferência. Este script T-SQL cria o banco de dados Northwind do zero e a preenche com dados.

    3. Cole o script T-SQL no editor de consultas e, em seguida, escolha o **Execute** botão.

       Após alguns instantes, a consulta termina a execução e o banco de dados Northwind é criado.

## <a name="creating-the-service"></a>Criando o serviço
Para criar um [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)], você adicionará um projeto Web, criará um [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] e, em seguida, criará o serviço usando o modelo.

A primeira etapa, você adiciona um projeto Web para hospedar o serviço.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

#### <a name="to-create-the-web-project"></a>Para criar o projeto Web

1.  Na barra de menus, selecione **Arquivo** > **Novo** > **Projeto**.

2.  No **novo projeto** diálogo caixa, expanda o **Visual Basic** ou **Visual c#** e **Web** nós e, em seguida, escolha o **ASP. Aplicativo de Web do NET** modelo.

3.  No **nome** texto, digite **NorthwindWeb**e, em seguida, escolha o **Okey** botão.

4.  No **novo projeto ASP.NET** na caixa de **selecionar um modelo** , escolha **vazio**e, em seguida, escolha o **Okey** botão.

A próxima etapa, você criará um [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] que representa o `Customers` tabela no banco de dados Northwind.

#### <a name="to-create-the-entity-data-model"></a>Para criar o Modelo de Dados de Entidade

1.  Na barra de menus, escolha **Projeto** > **Adicionar Novo Item**.

2.  No **Adicionar Novo Item** diálogo caixa, escolha o **dados** nó e, em seguida, escolha o **modelo de dados de entidade ADO.NET** item.

3.  No **nome** texto, digite `NorthwindModel`e, em seguida, escolha o **Add** botão.

     O Assistente do Modelo de Dados de Entidade é aberto.

4.  No Assistente de modelo de dados de entidade, na **escolher conteúdo do modelo** , escolha o **EF Designer do banco de dados** item e, em seguida, escolha o **próxima** botão.

5.  Sobre o **escolha sua Conexão de dados** , execute uma das seguintes etapas:

    -   Se uma conexão de dados com o banco de dados de exemplo Northwind estiver disponível na lista suspensa, selecione-a.

         -ou-

    -   Escolha o **nova Conexão** botão para configurar uma nova conexão de dados. Para obter mais informações, consulte [adicionar novas conexões](../data-tools/add-new-connections.md).

6.  Se o banco de dados exigir uma senha, escolha o **Sim, incluir dados confidenciais na cadeia de conexão** botão de opção e, em seguida, escolha o **próxima** botão.

    > [!NOTE]
    >  Se uma caixa de diálogo for exibida, escolha **Sim** para salvar o arquivo ao seu projeto.

7.  No **escolha sua versão** , escolha o **Entity Framework 5.0** botão de opção e, em seguida, escolha o **próxima** botão.

    > [!NOTE]
    >  Para usar a versão mais recente do Entity Framework 6 com os serviços WCF, você precisará instalar o pacote NuGet de provedor do WCF Data Services Entity Framework. Ver [usar o WCF Data Services 5.6.0 com o Entity Framework 6 +](http://blogs.msdn.com/b/odatateam/archive/2013/10/02/using-wcf-data-services-5-6-0-with-entity-framework-6.aspx).

8.  No **Choose Your Database Objects** página, expanda o **tabelas** nó, selecione o **clientes** caixa de seleção e, em seguida, escolha o **concluir** botão.

     Exibe o diagrama de modelo de entidade e um *NorthwindModel* arquivo é adicionado ao seu projeto.

Na próxima etapa, você pode cria e testar o serviço de dados.

#### <a name="to-create-the-data-service"></a>Para criar o serviço de dados

1.  Na barra de menus, escolha **Projeto** > **Adicionar Novo Item**.

2.  No **Adicionar Novo Item** diálogo caixa, escolha o **Web** nó e, em seguida, escolha o **WCF Data Services 5.6** item.

3.  No **nome** texto, digite `NorthwindCustomers`e, em seguida, escolha o **Add** botão.

     O **Northwindcustomers** arquivo aparece na **Editor de códigos**.

4.  No **Editor de códigos**, localize o primeiro `TODO:` comentar e substitua o código a seguir:

     [!code-vb[WCFDataServiceWalkthrough#1](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework_1.vb)]
     [!code-csharp[WCFDataServiceWalkthrough#1](../data-tools/codesnippet/CSharp/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework_1.cs)]

5.  Substitua os comentários no manipulador de eventos `InitializeService` pelo seguinte código:

     [!code-vb[WCFDataServiceWalkthrough#2](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework_2.vb)]
     [!code-csharp[WCFDataServiceWalkthrough#2](../data-tools/codesnippet/CSharp/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework_2.cs)]

6.  Na barra de menus, escolha **Debug** > **Start Without Debugging** para executar o serviço. Uma janela do navegador abre e exibe o esquema XML para o serviço.

7.  No **endereço** barra, insira `Customers` no final da URL **Northwindcustomers**e, em seguida, escolha o **Enter** chave.

     Uma representação XML dos dados no `Customers` tabela é exibida.

    > [!NOTE]
    >  Em alguns casos, o Internet Explorer interpretará incorretamente os dados como um RSS feed. Você deve verificar se a opção para exibir RSS feeds está desabilitada. Para obter mais informações, consulte [Solucionando problemas de referências de serviço](../data-tools/troubleshooting-service-references.md).

8.  Feche a janela do navegador.

As próximas etapas, você cria um aplicativo de cliente do Windows Forms para consumir o serviço.

## <a name="creating-the-client-application"></a>Criando o aplicativo cliente
 Para criar o aplicativo cliente, você adicionar um segundo projeto, adicione uma referência de serviço ao projeto, configurar uma fonte de dados e cria uma interface do usuário para exibir os dados do serviço.

 Na primeira etapa, você pode adicionar um projeto do Windows Forms à solução e defini-lo como o projeto de inicialização.

#### <a name="to-create-the-client-application"></a>Para criar o aplicativo cliente

1.  Na barra de menus, escolha arquivo, **Add** > **novo projeto**.

2.  No **novo projeto** diálogo caixa, expanda o **Visual Basic** ou **Visual c#** nó, escolha o **Windows** nó e, em seguida, escolha  **Aplicativo de formulários do Windows**.

3.  Na caixa de texto **Nome**, insira `NorthwindClient` e, em seguida, escolha o botão **OK**.

4.  Na **Gerenciador de soluções**, escolha o **NorthwindClient** nó do projeto.

5.  Na barra de menus, escolha **Project**, **definir como projeto de inicialização**.

Na próxima etapa, você adiciona uma referência de serviço para o [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] no projeto da Web.

#### <a name="to-add-a-service-reference"></a>Para adicionar uma referência de serviço

1.  Na barra de menus, escolha **Project** > **Add Service Reference**.

2.  No **adicionar referência de serviço** diálogo caixa, escolha o **Discover** botão.

     A URL do serviço NorthwindCustomers é exibida na **endereço** campo.

3.  Escolha o **Okey** botão para adicionar a referência de serviço.

Na próxima etapa, você deve configurar uma fonte de dados para habilitar a associação de dados para o serviço.

#### <a name="to-enable-data-binding-to-the-service"></a>Para habilitar a associação de dados ao serviço

1.  Na barra de menus, escolha **modo de exibição** > **Other Windows** > **fontes de dados**.

2.  No **fontes de dados** janela, escolha o **Add New Data Source** botão.

3.  No **escolher um tipo de fonte de dados** página do **Data Source Configuration Wizard**, escolha **objeto**e, em seguida, escolha o **Avançar** botão .

4.  Sobre o **selecione os objetos de dados** página, expanda o **NorthwindClient** nó e, em seguida, expanda o **NorthwindClient.ServiceReference1** nó.

5.  Selecione **Customer** caixa de seleção e, em seguida, escolha o **concluir** botão.

A próxima etapa, você cria a interface do usuário que exibe os dados do serviço.

#### <a name="to-create-the-user-interface"></a>Para criar a interface do usuário

1.  No **fontes de dados** janela, abra o menu de atalho para o **clientes** nó e escolha **cópia**.

2.  No **Form1.vb** ou **Form1.cs** designer de formulário, abra o menu de atalho e escolha **colar**.

     Um controle <xref:System.Windows.Forms.DataGridView>, um componente <xref:System.Windows.Forms.BindingSource> e um componente <xref:System.Windows.Forms.BindingNavigator> são adicionados ao formulário.

3.  Escolha o **CustomersDataGridView** controle e, em seguida, no **propriedades** conjunto de janela a **Dock** propriedade a ser **preencher**.

4.  Na **Gerenciador de soluções**, abra o menu de atalho para o **Form1** nó e escolha **Exibir código** para abrir o Editor de códigos e adicione o seguinte `Imports` ou `Using`instrução na parte superior do arquivo:

    ```vb
    Imports NorthwindClient.ServiceReference1
    ```

    ```csharp
    using NorthwindClient.ServiceReference1;
    ```

5.  Adicione o seguinte código ao manipulador de eventos do `Form1_Load`:

    ```vb
    Private Sub Form1_Load(sender As Object, e As EventArgs) Handles MyBase.Load
            Dim proxy As New NorthwindEntities _
    (New Uri("http://localhost:53161/NorthwindCustomers.svc/"))
            Me.CustomersBindingSource.DataSource = proxy.Customers
        End Sub
    ```

    ```csharp
    private void Form1_Load(object sender, EventArgs e)
    {
    NorthwindEntities proxy = new NorthwindEntities(new Uri("http://localhost:53161/NorthwindCustomers.svc/"));
    this.CustomersBindingSource.DataSource = proxy.Customers;
    }

    ```

6.  Na **Gerenciador de soluções**, abra o menu de atalho para o **Northwindcustomers** arquivo e escolha **exibir no navegador**. Internet Explorer é aberto e exibe o esquema XML para o serviço.

7.  Copie a URL da barra de endereços do Internet Explorer.

8.  No código que você adicionou na etapa 4, selecione `http://localhost:53161/NorthwindCustomers.svc/` e o substitua pela URL que acabou de copiar.

9. Na barra de menus, escolha **Debug** > **iniciar depuração** para executar o aplicativo. As informações do cliente são mostradas.

 Agora você tem um aplicativo funcional que exibe uma lista de clientes do serviço NorthwindCustomers. Se desejar expor dados adicionais por meio do serviço, você pode modificar o [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] para incluir tabelas adicionais do banco de dados da Northwind.

A próxima etapa opcional, você aprenderá como filtrar os dados que são retornados pelo serviço.

## <a name="adding-filtering-capabilities"></a>Adicionando recursos de filtragem
 Nesta etapa, você deve personalizar o aplicativo para filtrar os dados por cidade do cliente.

#### <a name="to-add-filtering-by-city"></a>Para adicionar a filtragem por cidade

1.  Na **Gerenciador de soluções**, abra o menu de atalho para o **Form1.vb** ou **Form1.cs** nó e escolha **abrir**.

2.  Adicionar um <xref:System.Windows.Forms.TextBox> controle e um <xref:System.Windows.Forms.Button> controlar da **caixa de ferramentas** ao formulário.

3.  Abra o menu de atalho para o <xref:System.Windows.Forms.Button> de controle, escolha **Exibir código**e, em seguida, adicione o seguinte código no `Button1_Click` manipulador de eventos:

    ```vb
    Private Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click
            Dim proxy As New northwindEntities _
    (New Uri("http://localhost:53161/NorthwindCustomers.svc"))
            Dim city As String = TextBox1.Text

            If city <> "" Then
                Me.CustomersBindingSource.DataSource = From c In _
             proxy.Customers Where c.City = city
            End If

        End Sub
    ```

    ```csharp
    private void Button1_Click(object sender, EventArgs e)
    {
    ServiceReference1.northwindModel.northwindEntities proxy = new northwindEntities(new Uri("http://localhost:53161/NorthwindCustomers.svc"));
    string city = TextBox1.Text;

    if (!string.IsNullOrEmpty(city)) {
    this.CustomersBindingSource.DataSource = from c in proxy.Customers where c.City == city;
    }

    }
    ```

4.  No código anterior, substitua `http://localhost:53161/NorthwindCustomers.svc` pela URL do manipulador de eventos `Form1_Load`.

5.  Na barra de menus, escolha **Debug** > **iniciar depuração** para executar o aplicativo.

6.  Na caixa de texto, insira **Londres**e, em seguida, escolha o botão. Somente os clientes de London são exibidos.

## <a name="see-also"></a>Consulte também

- [Serviços do Windows Communication Foundation e WCF Data Services no Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
- [Como: adicionar, atualizar ou remover uma referência de WCF Data Service](../data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference.md)