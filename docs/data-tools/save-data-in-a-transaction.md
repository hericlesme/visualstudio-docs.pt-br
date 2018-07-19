---
title: 'Passo a passo: salvar dados em uma transação'
ms.date: 09/08/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- System.Transactions namespace
- data [Visual Studio], saving in a transaction
- transactions, saving data
- Transactions namespace
- saving data
ms.assetid: 80260118-08bc-4b37-bfe5-9422ee7a1e4e
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 2829e1dffa0975a1970b8727f9baf79febf9b32c
ms.sourcegitcommit: f37affbc1b885dfe246d4b2c295a6538b383a0ca
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37174881"
---
# <a name="walkthrough-save-data-in-a-transaction"></a>Passo a passo: salvar dados em uma transação
Este passo a passo demonstra como salvar dados em uma transação usando o <xref:System.Transactions> namespace. Neste passo a passo, você criará um aplicativo do Windows Forms. Você usará o Assistente de configuração de fonte de dados para criar um conjunto de dados de duas tabelas no banco de dados de exemplo Northwind. Você adicionará controles ligados a dados a um formulário do Windows, e você modificará o código para do BindingNavigator botão Salvar atualizar o banco de dados dentro de um TransactionScope.

## <a name="prerequisites"></a>Pré-requisitos
Este passo a passo usa o SQL Server Express LocalDB e o banco de dados de exemplo Northwind.

1.  Se você não tiver o SQL Server Express LocalDB, instalá-lo a partir de [página de download do SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), ou por meio de **instalador do Visual Studio**. No instalador do Visual Studio, o SQL Server Express LocalDB pode ser instalado como parte dos **desenvolvimento de área de trabalho do .NET** carga de trabalho, ou como um componente individual.

2.  Instale o banco de dados de exemplo Northwind, seguindo estas etapas:

    1. No Visual Studio, abra o **SQL Server Object Explorer** janela. (Pesquisador de objetos do SQL Server é instalado como parte dos **armazenamento de dados e processamento** carga de trabalho no instalador do Visual Studio.) Expanda o **SQL Server** nó. Clique com botão direito na instância do LocalDB e selecione **nova consulta**.

       Abre uma janela do editor de consulta.

    2. Cópia de [script Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) na área de transferência. Este script T-SQL cria o banco de dados Northwind do zero e a preenche com dados.

    3. Cole o script T-SQL no editor de consultas e, em seguida, escolha o **Execute** botão.

       Após alguns instantes, a consulta termina a execução e o banco de dados Northwind é criado.

## <a name="create-a-windows-forms-application"></a>Criar um aplicativo Windows Forms
 A primeira etapa é criar uma **aplicativo do Windows Forms**.

#### <a name="to-create-the-new-windows-project"></a>Para criar o novo projeto do Windows

1. No Visual Studio, sobre o **arquivo** menu, selecione **New** > **projeto**.

2. Expanda o **Visual c#** ou **Visual Basic** no painel esquerdo, em seguida, selecione **área de trabalho do Windows**.

3. No painel central, selecione a **aplicativo do Windows Forms** tipo de projeto.

4. Nomeie o projeto **SavingDataInATransactionWalkthrough**e, em seguida, escolha **Okey**.

     O **SavingDataInATransactionWalkthrough** projeto é criado e adicionado ao **Gerenciador de soluções**.

## <a name="create-a-database-data-source"></a>Criar uma fonte de dados do banco de dados
 Esta etapa usa a **Data Source Configuration Wizard** para criar uma fonte de dados com base nas `Customers` e `Orders` tabelas no banco de dados de exemplo Northwind.

#### <a name="to-create-the-data-source"></a>Para criar a fonte de dados

1.  Sobre o **dados** menu, selecione **Show Data Sources**.

2.  No **fontes de dados** janela, selecione **Add New Data Source** para iniciar o **Data Source Configuration Wizard**.

3.  Sobre o **escolher um tipo de fonte de dados** tela, selecione **banco de dados**e, em seguida, selecione **próxima**.

4.  Sobre o **escolha sua Conexão de dados** tela faça o seguinte:

    -   Se uma conexão de dados com o banco de dados de exemplo Northwind estiver disponível na lista suspensa, selecione-o.

         -ou-

    -   Selecione **nova Conexão** para iniciar o **Adicionar/Modificar Conexão** caixa de diálogo caixa e criar uma conexão ao banco de dados Northwind.

5.  Se seu banco de dados exigir uma senha, selecione a opção para incluir dados confidenciais e, em seguida, selecione **próxima**.

6.  Sobre o **salvar a cadeia de caracteres de conexão para o arquivo de configuração de aplicativo** tela, selecione **próxima**.

7.  Sobre o **Choose your Database Objects** , expanda o **tabelas** nó.

8.  Selecione o `Customers` e `Orders` tabelas e, em seguida, selecione **concluir**.

     O **NorthwindDataSet** é adicionado ao seu projeto e o `Customers` e `Orders` as tabelas aparecem no **fontes de dados** janela.

## <a name="add-controls-to-the-form"></a>Adicionar controles ao formulário
 Você pode criar os controles ligados a dados arrastando itens dos **fontes de dados** window para seu formulário.

#### <a name="to-create-data-bound-controls-on-the-windows-form"></a>Para criar dados de associação de controles do formulário do Windows

-   No **fontes de dados** janela, expanda o **clientes** nó.

-   Arraste principal **clientes** nó a partir do **fontes de dados** window para **Form1**.

     Um controle <xref:System.Windows.Forms.DataGridView> e uma faixa de ferramentas (<xref:System.Windows.Forms.BindingNavigator>) para navegação em registros são exibidos no formulário. Um [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), `CustomersTableAdapter`, <xref:System.Windows.Forms.BindingSource>, e <xref:System.Windows.Forms.BindingNavigator> aparecem na bandeja de componentes.

-   Arraste relacionado **pedidos** nó (não principal **pedidos** nó, mas o nó de tabela filha relacionada abaixo de **Fax** coluna) para o formulário abaixo o  **CustomersDataGridView**.

     Um <xref:System.Windows.Forms.DataGridView> aparece no formulário. Uma `OrdersTableAdapter` e <xref:System.Windows.Forms.BindingSource> aparecem na bandeja de componentes.

## <a name="add-a-reference-to-the-systemtransactions-assembly"></a>Adicione uma referência ao assembly System. Transactions
 As transações usam o namespace <xref:System.Transactions>. Uma referência do projeto ao assembly system.transactions não é adicionada por padrão, portanto, você precisa adicioná-la manualmente.

#### <a name="to-add-a-reference-to-the-systemtransactions-dll-file"></a>Para adicionar uma referência ao arquivo DLL System.Transactions

1.  Sobre o **Project** menu, selecione **adicionar referência**.

2.  Selecione **System. Transactions** (sobre o **.NET** guia) e, em seguida, selecione **Okey**.

     Uma referência a **System. Transactions** é adicionado ao projeto.

## <a name="modify-the-code-in-the-bindingnavigators-saveitem-button"></a>Modifique o código no botão SaveItem do BindingNavigator
 Para a primeira tabela arrastada para seu formulário, o código é adicionado por padrão para o `click` no botão de evento do salvamento a <xref:System.Windows.Forms.BindingNavigator>. É necessário adicionar manualmente o código para atualizar quaisquer tabelas adicionais. Para este passo a passo, podemos refatorar o código salvar existente manipulador de eventos de clique do botão. Além disso, podemos criar mais alguns métodos para fornecer a funcionalidade de atualização específica com base em se a linha precisa ser adicionada ou excluída.

#### <a name="to-modify-the-auto-generated-save-code"></a>Para modificar o código salvar gerado automaticamente

1.  Selecione o **salve** botão a **CustomersBindingNavigator** (o botão com o ícone de disquete).

2.  Substitua o método `CustomersBindingNavigatorSaveItem_Click` pelo seguinte código:

     [!code-vb[VbRaddataSaving#4](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_1.vb)]
     [!code-csharp[VbRaddataSaving#4](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_1.cs)]

A ordem para reconciliar as alterações aos dados relacionados é a seguinte:

-   Exclua registros filho. (Nesse caso, exclua registros do `Orders` tabela.)

-   Exclua registros pais. (Nesse caso, exclua registros do `Customers` tabela.)

-   Inserir registros pais. (Nesse caso, insira registros no `Customers` tabela.)

-   Inserir registros filhos. (Nesse caso, insira registros no `Orders` tabela.)

#### <a name="to-delete-existing-orders"></a>Para excluir pedidos existentes

-   Adicione o seguinte `DeleteOrders` método **Form1**:

     [!code-vb[VbRaddataSaving#5](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_2.vb)]
     [!code-csharp[VbRaddataSaving#5](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_2.cs)]

#### <a name="to-delete-existing-customers"></a>Para excluir clientes existentes

-   Adicione o seguinte `DeleteCustomers` método **Form1**:

     [!code-vb[VbRaddataSaving#6](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_3.vb)]
     [!code-csharp[VbRaddataSaving#6](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_3.cs)]

#### <a name="to-add-new-customers"></a>Para adicionar novos clientes

-   Adicione o seguinte `AddNewCustomers` método **Form1**:

     [!code-vb[VbRaddataSaving#7](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_4.vb)]
     [!code-csharp[VbRaddataSaving#7](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_4.cs)]

#### <a name="to-add-new-orders"></a>Para adicionar novos pedidos

-   Adicione o seguinte `AddNewOrders` método **Form1**:

     [!code-vb[VbRaddataSaving#8](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_5.vb)]
     [!code-csharp[VbRaddataSaving#8](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_5.cs)]

## <a name="run-the-application"></a>Executar o aplicativo

#### <a name="to-run-the-application"></a>Para executar o aplicativo

-   Selecione **F5** para executar o aplicativo.

## <a name="see-also"></a>Consulte também

- [Como: salvar dados usando uma transação](../data-tools/save-data-by-using-a-transaction.md)
- [Salvar dados de volta no banco de dados](../data-tools/save-data-back-to-the-database.md)