---
title: Passar dados entre formulários
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- walkthroughs [Windows Forms], data
- walkthroughs [Visual Studio], data
- data [Visual Studio], passing between forms
- forms, passing data between
- Windows Forms, walkthroughs
ms.assetid: 78bf038b-9296-4fbf-b0e8-d881d1aff0df
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: c8d400f8fa46fa10876d1827205671b6d90a3e33
ms.sourcegitcommit: e9d1018a01af62c3dc5aeb6b325faba7e20bd496
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/28/2018
ms.locfileid: "37089432"
---
# <a name="pass-data-between-forms"></a>Passar dados entre formulários
Este passo a passo fornece instruções detalhadas de como passar os dados de um formulário para outro. Usando as tabelas customers e orders do Northwind, um formulário que os usuários selecionem um cliente e um segundo formulário exibe os pedidos do cliente selecionado. Este passo a passo mostra como criar um método no segundo formulário que recebe dados do primeiro formulário.

> [!NOTE]
>  Este passo a passo demonstra apenas uma maneira de passar dados entre formulários. Há outras opções para passar dados para um formulário, incluindo a criação de um segundo construtor para receber dados, ou criando uma propriedade pública que pode ser definida com os dados do primeiro formulário.

 As tarefas ilustradas neste passo a passo incluem:

-   Criando um novo **aplicativo do Windows Forms** projeto.

-   Criando e configurando um conjunto de dados com o [Data Source Configuration Wizard](../data-tools/media/data-source-configuration-wizard.png).

-   Selecionando o controle a ser criado no formulário ao arrastar itens dos **fontes de dados** janela. Para obter mais informações, consulte [definir o controle a ser criado quando arrastado da janela fontes de dados](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

-   Criando um controle associado a dados arrastando itens dos **fontes de dados** janela em um formulário.

-   Criar um segundo formulário com uma grade para exibir dados.

-   Criar uma consulta TableAdapter para buscar pedidos de um cliente específico.

-   Passar dados entre formulários.

## <a name="prerequisites"></a>Pré-requisitos
Este passo a passo usa o SQL Server Express LocalDB e o banco de dados de exemplo Northwind.

1.  Se você não tiver o SQL Server Express LocalDB, instalá-lo a partir de [página de download do SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), ou por meio de **instalador do Visual Studio**. No instalador do Visual Studio, o SQL Server Express LocalDB pode ser instalado como parte dos **armazenamento de dados e processamento** carga de trabalho, ou como um componente individual.

2.  Instale o banco de dados de exemplo Northwind, seguindo estas etapas:

    1. No Visual Studio, abra o **SQL Server Object Explorer** janela. (Pesquisador de objetos do SQL Server é instalado como parte dos **armazenamento de dados e processamento** carga de trabalho no instalador do Visual Studio.) Expanda o **SQL Server** nó. Clique com botão direito na instância do LocalDB e selecione **nova consulta**.

       Abre uma janela do editor de consulta.

    2. Cópia de [script Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) na área de transferência. Este script T-SQL cria o banco de dados Northwind do zero e a preenche com dados.

    3. Cole o script T-SQL no editor de consultas e, em seguida, escolha o **Execute** botão.

       Após alguns instantes, a consulta termina a execução e o banco de dados Northwind é criado.

## <a name="create-the-windows-forms-application"></a>Criar o aplicativo de formulários do Windows

### <a name="to-create-the-new-windows-project"></a>Para criar o novo projeto do Windows

1. No Visual Studio, sobre o **arquivo** menu, selecione **New** > **projeto**.

2. Expanda o **Visual c#** ou **Visual Basic** no painel esquerdo, em seguida, selecione **área de trabalho do Windows**.

3. No painel central, selecione a **aplicativo do Windows Forms** tipo de projeto.

4. Nomeie o projeto **PassingDataBetweenForms**e, em seguida, escolha **Okey**.

     O **PassingDataBetweenForms** projeto é criado e adicionado ao **Gerenciador de soluções**.

## <a name="create-the-data-source"></a>Criar a fonte de dados

### <a name="to-create-the-data-source"></a>Para criar a fonte de dados

1.  Sobre o **dados** menu, clique em **Show Data Sources**.

2.  No **fontes de dados** janela, selecione **Add New Data Source** para iniciar o **configuração de fonte de dados** assistente.

3.  Selecione **banco de dados** sobre o **escolher um tipo de fonte de dados** página e, em seguida, clique em **próxima**.

4.  No **escolha um modelo de banco de dados** página, verifique **Dataset** é especificado e, em seguida, clique em **próxima**.

5.  Sobre o **escolha sua Conexão de dados** página, faça o seguinte:

    -   Se uma conexão de dados com o banco de dados de exemplo Northwind estiver disponível na lista suspensa, selecione-o.

    -   Selecione **nova Conexão** para iniciar o **Adicionar/Modificar Conexão** caixa de diálogo.

6.  Se seu banco de dados exigir uma senha e se a opção para incluir dados confidenciais é ativada, selecione a opção e, em seguida, clique em **próxima**.

7.  Sobre o **salvar a cadeia de caracteres de conexão para o arquivo de configuração de aplicativo** , clique em **próxima**.

8.  Sobre o **Choose your Database Objects** página, expanda o **tabelas** nó.

9. Selecione o **clientes** e **pedidos** tabelas e clique **concluir**.

     O **NorthwindDataSet** é adicionado ao seu projeto e o **clientes** e **pedidos** tabelas aparecem no **fontes de dados** janela.

## <a name="create-the-first-form-form1"></a>Criar o primeiro formulário (Form1)
 Você pode criar uma grade de associação de dados (um <xref:System.Windows.Forms.DataGridView> controle), arrastando o **clientes** nó a partir de **fontes de dados** janela para o formulário.

### <a name="to-create-a-data-bound-grid-on-the-form"></a>Para criar uma grade de associação de dados no formulário

-   Arraste principal **clientes** nó a partir do **fontes de dados** window para **Form1**.

     Um <xref:System.Windows.Forms.DataGridView> e uma faixa de ferramenta (<xref:System.Windows.Forms.BindingNavigator>) para navegação em registros são exibidos no **Form1**. Um [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter <xref:System.Windows.Forms.BindingSource>, e <xref:System.Windows.Forms.BindingNavigator> aparecem na bandeja de componentes.

## <a name="create-the-second-form-form2"></a>Criar o segundo formulário (Form2)

### <a name="to-create-a-second-form-to-pass-the-data-to"></a>Para criar um segundo formulário para o qual passar os dados

1.  No menu **Projeto**, escolha **Adicionar Formulário do Windows**.

2.  Deixe o nome padrão **Form2**e clique em **Add**.

3.  Arraste principal **pedidos** nó a partir do **fontes de dados** window para **Form2**.

     Um <xref:System.Windows.Forms.DataGridView> e uma faixa de ferramenta (<xref:System.Windows.Forms.BindingNavigator>) para navegação em registros são exibidos no **Form2**. Um [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter <xref:System.Windows.Forms.BindingSource>, e <xref:System.Windows.Forms.BindingNavigator> aparecem na bandeja de componentes.

4.  Excluir o **OrdersBindingNavigator** da bandeja de componentes.

     O **OrdersBindingNavigator** desaparece da **Form2**.

## <a name="add-a-tableadapter-query-to-form2-to-load-orders-for-the-selected-customer-on-form1"></a>Adicionar uma consulta TableAdapter ao Form2 para carregar pedidos do cliente selecionado no Form1

### <a name="to-create-a-tableadapter-query"></a>Para criar uma consulta do TableAdapter

1.  Clique duas vezes o **NorthwindDataSet** arquivo no **Gerenciador de soluções**.

2.  Clique com botão direito do **OrdersTableAdapter**e selecione **Add Query**.

3.  Deixe a opção padrão **usar instruções SQL**e, em seguida, clique em **próxima**.

4.  Deixe a opção padrão **SELECT que retorna linhas**e, em seguida, clique em **próxima**.

5.  Adicionar uma cláusula WHERE à consulta, para retornar `Orders` baseia o `CustomerID`. A consulta deve ser semelhante ao seguinte:

    ```sql
    SELECT OrderID, CustomerID, EmployeeID, OrderDate, RequiredDate, ShippedDate, ShipVia, Freight, ShipName, ShipAddress, ShipCity, ShipRegion, ShipPostalCode, ShipCountry
    FROM Orders
    WHERE CustomerID = @CustomerID
    ```

    > [!NOTE]
    >  Verifique a sintaxe de parâmetro correta para o seu banco de dados. Por exemplo, no Microsoft Access, a cláusula WHERE seria algo como: `WHERE CustomerID = ?`.

6.  Clique em **Avançar**.

7.  Para o **preencha um nome de DataTableMethod**, tipo `FillByCustomerID`.

8.  Desmarque a **retornar uma DataTable** opção e, em seguida, clique em **próxima**.

9. Clique em **Finalizar**.

## <a name="create-a-method-on-form2-to-pass-data-to"></a>Criar um método no Form2 para passar dados para

### <a name="to-create-a-method-to-pass-data-to"></a>Para criar um método para o qual passar dados

1.  Clique com botão direito **Form2**e selecione **Exibir código** para abrir **Form2** no **Editor de códigos**.

2.  Adicione o seguinte código ao **Form2** depois que o `Form2_Load` método:

     [!code-vb[VbRaddataDisplaying#1](../data-tools/codesnippet/VisualBasic/pass-data-between-forms_1.vb)]
     [!code-csharp[VbRaddataDisplaying#1](../data-tools/codesnippet/CSharp/pass-data-between-forms_1.cs)]

## <a name="create-a-method-on-form1-to-pass-data-and-display-form2"></a>Criar um método no Form1 para passar dados e exibir o Form2

### <a name="to-create-a-method-to-pass-data-to-form2"></a>Para criar um método para passar dados para o Form2

1.  Na **Form1**, clique com botão direito da grade de dados do cliente e, em seguida, clique em **propriedades**.

2.  Na janela **Propriedades**, clique em **Eventos**.

3.  Clique duas vezes o **CellDoubleClick** eventos.

     O Editor de Códigos é exibido.

4.  Atualize a definição de método para corresponder ao seguinte exemplo:

     [!code-csharp[VbRaddataDisplaying#2](../data-tools/codesnippet/CSharp/pass-data-between-forms_2.cs)]
     [!code-vb[VbRaddataDisplaying#2](../data-tools/codesnippet/VisualBasic/pass-data-between-forms_2.vb)]

## <a name="run-the-application"></a>Executar o aplicativo

### <a name="to-run-the-application"></a>Para executar o aplicativo

-   Pressione **F5** para executar o aplicativo.

-   Clique duas vezes em um registro de cliente no **Form1** para abrir **Form2** com pedidos do cliente.

## <a name="next-steps"></a>Próximas etapas

Dependendo dos requisitos de aplicativo, existem várias etapas que você talvez queira realizar após passar dados entre formulários. Entre algumas das melhorias que você poderia fazer nessa explicação passo a passo estão:

-   Editando o conjunto de dados para adicionar ou remover objetos de banco de dados. Para obter mais informações, consulte [Create and configure datasets (Criar e configurar conjuntos de dados)](../data-tools/create-and-configure-datasets-in-visual-studio.md).

-   Adicionar funcionalidade para salvar dados de volta no banco de dados. Para obter mais informações, consulte [salvar dados no banco de dados](../data-tools/save-data-back-to-the-database.md).

## <a name="see-also"></a>Consulte também

- [Associando controles do Windows Forms a dados no Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)