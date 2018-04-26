---
title: Criar um aplicativo simples de dados usando o ADO.NET no Visual Studio
ms.date: 08/23/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: 2222841f-e443-4a3d-8c70-4506aa905193
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 3d0b60bb4e7048e2dc49774ec69d3eea4fc0ce6c
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="create-a-simple-data-application-by-using-adonet"></a>Criar um aplicativo simples de dados usando o ADO.NET

Quando você cria um aplicativo que manipule dados em um banco de dados, você pode executar tarefas básicas, como definindo cadeias de conexão, inserir dados e executar procedimentos armazenados. Ao seguir neste tópico, você pode descobrir como interagir com um banco de dados de dentro de um aplicativo simples de "formulários sobre dados" do Windows Forms usando o Visual c# ou Visual Basic e ADO.NET.  Todas as tecnologias de dados do .NET, inclusive conjuntos de dados, o LINQ to SQL e Entity Framework —, por fim, execute as etapas que são muito semelhantes aos mostrados neste artigo.

 Este artigo demonstra uma maneira simples de obter dados de um banco de dados de uma maneira muito rápida. Se seu aplicativo precisar modificar dados de maneiras não trivial e atualizar o banco de dados, você deve considerar usando o Entity Framework e usando associação de dados para sincronizar automaticamente os controles de interface do usuário para as alterações nos dados subjacentes.

> [!IMPORTANT]
> Para simplificar o código, não inclui a manipulação de exceção prontos para produção.

## <a name="prerequisites"></a>Pré-requisitos

Para criar o aplicativo, você precisará de:

-   Visual Studio.

-   SQL Server Express LocalDB. Se você não tiver o SQL Server Express LocalDB, você pode instalá-lo do [página de download do SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express).

Este tópico pressupõe que você está familiarizado com a funcionalidade básica do IDE do Visual Studio e pode criar um aplicativo Windows Forms, adicionar formas ao projeto, coloque os botões e outros controles em formulários, definir propriedades de controles e eventos de código simples. Se você não estiver familiarizado com essas tarefas, sugerimos que você conclua a [guia de Introdução ao Visual c# e Visual Basic](../ide/getting-started-with-visual-csharp-and-visual-basic.md) tópico antes de começar este passo a passo.

## <a name="set-up-the-sample-database"></a>Configurar o banco de dados de exemplo

Crie o banco de dados de exemplo seguindo estas etapas:

1. No Visual Studio, abra o **Server Explorer** janela.

2. Clique duas vezes em **conexões de dados** e escolha * * Criar novo servidor de banco de dados SQL... ".

3. No **nome do servidor** texto, digite **(localdb) \mssqllocaldb**.

4. No **novo nome de banco de dados** texto, digite **vendas**, em seguida, escolha **Okey**.

     Vazio **vendas** banco de dados é criado e adicionado ao nó de conexões de dados no Gerenciador de servidores.

5. Clique com botão direito no **vendas** conexão de dados e selecione **nova consulta**.

     Abre uma janela do editor de consultas.

6. Copie o [script Transact-SQL de vendas](https://github.com/MicrosoftDocs/visualstudio-docs/raw/master/docs/data-tools/samples/sales.sql) para sua área de transferência.

7. Cole o script T-SQL no editor de consultas e, em seguida, escolha o **Execute** botão.

     Após um curto período de tempo, a consulta termina de ser executado e os objetos de banco de dados são criados. O banco de dados contém duas tabelas: clientes e pedidos. Essas tabelas não contêm dados inicialmente, mas você pode adicionar dados ao executar o aplicativo que você criará. O banco de dados também contém quatro procedimentos armazenados simples.

## <a name="create-the-forms-and-add-controls"></a>As formas de criar e adicionar controles

1.  Criar um projeto para um aplicativo Windows Forms e nomeie-a como SimpleDataApp.

     Visual Studio cria o projeto e vários arquivos, inclusive um formulário Windows vazio chamado Form1.

2.  Adicionar dois formulários do Windows ao seu projeto para que ele tenha três formas e, em seguida, conceder a eles os nomes a seguir:

    -   Navegação

    -   NewCustomer

    -   FillOrCancel

3.  Para cada formulário, adicione as caixas de texto, botões e outros controles que aparecem nas ilustrações a seguir. Para cada controle, defina as propriedades que descrevem as tabelas.

    > [!NOTE]
    >  A caixa de grupo e os controles de rótulo adicionar maior clareza, mas não são usados no código.

 **Formulário de navegação**

 ![Caixa de diálogo de navegação](../data-tools/media/simpleappnav.png "SimpleAppNav")

|Controles para o formulário de navegação|Propriedades|
|--------------------------------------|----------------|
|Botão|Nome = btnGoToAdd|
|Botão|Nome = btnGoToFillOrCancel|
|Botão|Nome = btnExit|

 **Formulário de NewCustomer**

 ![Adicionar um novo cliente e fazer um pedido](../data-tools/media/simpleappnewcust.png "SimpleAppNewCust")

|Controles para o formulário NewCustomer|Propriedades|
|---------------------------------------|----------------|
|TextBox|Nome = txtCustomerName|
|TextBox|Nome = txtCustomerID<br /><br /> ReadOnly = True|
|Botão|Name = btnCreateAccount|
|NumericUpdown|DecimalPlaces = 0<br /><br /> Máximo = 5000<br /><br /> Nome = numOrderAmount|
|DateTimePicker|Formato = curto<br /><br /> Nome = dtpOrderDate|
|Botão|Nome = btnPlaceOrder|
|Botão|Name = btnAddAnotherAccount|
|Botão|Nome = btnAddFinish|

 **Formulário FillOrCancel**

 ![Preencha ou cancelar pedidos](../data-tools/media/simpleappcancelfill.png "SimpleAppCancelFill")

|Controles do formulário FillOrCancel|Propriedades|
|----------------------------------------|----------------|
|TextBox|Nome = txtOrderID|
|Botão|Name = btnFindByOrderID|
|DateTimePicker|Formato = curto<br /><br /> Nome = dtpFillDate|
|DataGridView|Nome = dgvCustomerOrders<br /><br /> ReadOnly = True<br /><br /> RowHeadersVisible = False|
|Botão|Nome = btnCancelOrder|
|Botão|Nome = btnFillOrder|
|Botão|Nome = btnFinishUpdates|

## <a name="store-the-connection-string"></a>Armazenar a cadeia de caracteres de conexão
 Quando seu aplicativo tenta abrir uma conexão ao banco de dados, seu aplicativo deve ter acesso à cadeia de conexão. Para evitar inserir a cadeia de caracteres manualmente em cada formulário, armazenar a cadeia de caracteres no arquivo App. config em seu projeto e criar um método que retorna a cadeia de caracteres quando o método é chamado de qualquer forma em seu aplicativo.

 Você pode encontrar a cadeia de caracteres de conexão clicando no **vendas** conexão de dados em **Server Explorer** e escolhendo **propriedades**. Localize o **ConnectionString** propriedade e, em seguida, use Ctrl + A tecla Ctrl + C para selecionar e copiar a cadeia de caracteres para a área de transferência.

1.  Se você estiver usando c#, na **Solution Explorer**, expanda o **propriedades** nó sob o projeto e, em seguida, abra o **Settings** arquivo.
    Se você estiver usando o Visual Basic, em **Solution Explorer**, clique em **Mostrar todos os arquivos**, expanda o **meu projeto** nó e, em seguida, abra o **Settings** arquivo.

2.  No **nome** coluna, digite `connString`.

3.  No **tipo** lista, selecione **(cadeia de caracteres de Conexão)**.

4.  No **escopo** lista, selecione **aplicativo**.

5.  No **valor** coluna, digite a cadeia de caracteres de conexão (sem qualquer fora aspas) e, em seguida, salvar suas alterações.

> [!NOTE]
> Em um aplicativo real, você deve armazenar a cadeia de caracteres de conexão segura, conforme descrito em [cadeias de caracteres de Conexão e arquivos de configuração](/dotnet/framework/data/adonet/connection-strings-and-configuration-files).

##  <a name="write-the-code-for-the-forms"></a>Escreva o código para os formulários

Esta seção contém uma visão geral breve do que faz cada formulário. Ele também fornece o código que define a lógica subjacente quando um botão no formulário é clicado.

### <a name="navigation-form"></a>Formulário de navegação

O formulário de navegação abre quando você executar o aplicativo. O **adicionar uma conta** botão abre o formulário NewCustomer. O **ordens de preenchimento ou cancelar** botão abre o formulário FillOrCancel. O **Exit** botão fecha o aplicativo.

#### <a name="make-the-navigation-form-the-startup-form"></a>Verifique o painel de navegação formam o formulário de inicialização

Se você estiver usando c#, na **Solution Explorer**, abra Program.cs e, em seguida, altere o `Application.Run` linha a este: `Application.Run(new Navigation());`

Se você estiver usando o Visual Basic, em **Solution Explorer**, abra o **propriedades** janela, selecione o **aplicativo** guia e, em seguida, selecione  **SimpleDataApp.Navigation** no **formulário de inicialização** lista.

#### <a name="create-auto-generated-event-handlers"></a>Criar manipuladores de eventos gerados automaticamente

Clique duas vezes em três botões no formulário de navegação para criar métodos do manipulador de eventos em branco. Também é duas vezes os botões adiciona o código gerado automaticamente no arquivo de código de Designer que permite que um clique de botão disparar um evento.

#### <a name="add-code-for-the-navigation-form-logic"></a>Adicione código para a lógica de formulário de navegação

Na página de código para o formulário de navegação, concluir os corpos de método do botão três clique manipuladores de eventos conforme mostrado no código a seguir.

[!code-csharp[Navigation#1](../data-tools/codesnippet/CSharp/SimpleDataApp/Navigation.cs#1)]
[!code-vb[Navigation#1](../data-tools/codesnippet/VisualBasic/SimpleDataApp/Navigation.vb#1)]

### <a name="newcustomer-form"></a>Formulário de NewCustomer

Quando você inserir um nome de cliente e, em seguida, selecione o **criar conta** botão, o formulário NewCustomer cria uma conta de cliente e o SQL Server retorna um valor de identidade como a nova ID de cliente. Você pode colocar um pedido para a nova conta, especificando um valor e uma data do pedido e selecionando o **fazer pedido** botão.

#### <a name="create-auto-generated-event-handlers"></a>Criar manipuladores de eventos gerados automaticamente

Criar um vazio, clique em cada botão no formulário NewCustomer clicando duas vezes em cada um dos quatro botões no manipulador de eventos. Também é duas vezes os botões adiciona o código gerado automaticamente no arquivo de código de Designer que permite que um clique de botão disparar um evento.

#### <a name="add-code-for-the-newcustomer-form-logic"></a>Adicione código para a lógica de formulário NewCustomer

Para concluir a lógica de formulário NewCustomer, siga estas etapas.

1. Coloque o `System.Data.SqlClient` namespace no escopo para que você não precisa totalmente qualificar os nomes de seus membros.

     ```csharp
     using System.Data.SqlClient;
     ```
     ```vb
     Imports System.Data.SqlClient
     ```

2. Adicione variáveis e métodos auxiliares à classe, conforme mostrado no código a seguir.

     [!code-csharp[NewCustomer#1](../data-tools/codesnippet/CSharp/SimpleDataApp/NewCustomer.cs#1)]
     [!code-vb[NewCustomer#1](../data-tools/codesnippet/VisualBasic/SimpleDataApp/NewCustomer.vb#1)]

3. Concluir os corpos de método do botão quatro clique manipuladores de eventos conforme mostrado no código a seguir.

     [!code-csharp[NewCustomer#2](../data-tools/codesnippet/CSharp/SimpleDataApp/NewCustomer.cs#2)]
     [!code-vb[NewCustomer#2](../data-tools/codesnippet/VisualBasic/SimpleDataApp/NewCustomer.vb#2)]

### <a name="fillorcancel-form"></a>Formulário FillOrCancel

O formulário FillOrCancel executa uma consulta para retornar uma ordem quando você inserir uma ID do pedido e, em seguida, clique no **localizar ordem** botão. A linha retornada é exibida em uma grade de dados somente leitura. Você pode marcar a ordem como cancelada (X), se você selecionar o **Cancelar pedido** botão, ou você pode marcar a ordem como preenchido (F) se você selecionar o **ordem preencher** botão. Se você selecionar o **localizar ordem** botão novamente, a linha atualizada é exibida.

#### <a name="create-auto-generated-event-handlers"></a>Criar manipuladores de eventos gerados automaticamente

Criar vazio clique manipuladores de eventos para os quatro botões no formulário FillOrCancel clicando nos botões. Também é duas vezes os botões adiciona o código gerado automaticamente no arquivo de código de Designer que permite que um clique de botão disparar um evento.

#### <a name="add-code-for-the-fillorcancel-form-logic"></a>Adicione código para a lógica de forma FillOrCancel

Para concluir a lógica de forma FillOrCancel, siga estas etapas.

1. Coloque os namespaces a seguir no escopo para que você não precisa qualificar totalmente os nomes de seus membros.

     ```csharp
     using System.Data.SqlClient;
     using System.Text.RegularExpressions;
     ```
     ```vb
     Imports System.Data.SqlClient
     Imports System.Text.RegularExpressions
     ```

2. Adicione um método de variável e auxiliares à classe, conforme mostrado no código a seguir.

     [!code-csharp[FillOrCancel#1](../data-tools/codesnippet/CSharp/SimpleDataApp/FillOrCancel.cs#1)]
     [!code-vb[FillOrCancel#1](../data-tools/codesnippet/VisualBasic/SimpleDataApp/FillOrCancel.vb#1)]

3. Concluir os corpos de método do botão quatro clique manipuladores de eventos conforme mostrado no código a seguir.

     [!code-csharp[FillOrCancel#2](../data-tools/codesnippet/CSharp/SimpleDataApp/FillOrCancel.cs#2)]
     [!code-vb[FillOrCancel#2](../data-tools/codesnippet/VisualBasic/SimpleDataApp/FillOrCancel.vb#2)]

## <a name="test-your-application"></a>Testar seu aplicativo

Selecione o **F5** chave para compilar e testar seu aplicativo depois que você cada manipulador de eventos de clique, o código e, em seguida, depois de concluir a codificação.

## <a name="see-also"></a>Consulte também

- [Ferramentas de dados do Visual Studio para .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
