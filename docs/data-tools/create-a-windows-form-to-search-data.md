---
title: Criar um formulário do Windows para pesquisar dados
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Windows Forms, searching data
- Windows Forms, displaying data
- parameters, displaying filtered data
- data [Visual Studio], parameterizing queries
- data [Visual Studio], searching
ms.assetid: 65ca79a9-7458-466c-af55-978cd24c549e
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 4e04b0e4ef2f77381e305b992c5457bc46dc8261
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="create-a-windows-form-to-search-data"></a>Criar um formulário do Windows para pesquisar dados
Um cenário de aplicativo comum exibirá dados selecionados em um formulário. Por exemplo, você pode querer exibir os pedidos de um cliente específico ou os detalhes de um pedido específico. Nesse cenário, um usuário insere informações em um formulário e uma consulta é executada com a entrada do usuário como parâmetro, ou seja, os dados são selecionados com base em uma consulta parametrizada. A consulta retorna apenas os dados que satisfazem os critérios inseridos pelo usuário. Este passo a passo mostra como criar uma consulta que retorna clientes de uma cidade específica, como mudar a interface do usuário para que os usuários possam inserir o nome de uma cidade e pressionar um botão para executar a consulta.

 O uso de consultas parametrizadas ajuda a tornar seu aplicativo eficiente, permitindo que o banco de dados funcione melhor, filtrando registros rapidamente. Por outro lado, se você solicitar uma tabela de banco de dados inteiro, transferi-la através da rede e, em seguida, use a lógica do aplicativo para localizar os registros que você deseja, seu aplicativo pode se tornar lento ineficiente.

 Você pode adicionar consultas parametrizadas a qualquer TableAdapter (e controles para aceitar valores de parâmetro e executar a consulta) usando o **construtor de critérios de pesquisa** caixa de diálogo. Abra a caixa de diálogo selecionando o **adicionar consulta** comando o **dados** menu (ou em qualquer marca inteligente TableAdapter).

 As tarefas ilustradas neste passo a passo incluem:

-   Criar um novo projeto de aplicativo do Windows Forms.

-   Criando e configurando a fonte de dados em seu aplicativo com o **configuração da fonte de dados** assistente.

-   Definição do tipo subjacente dos itens a **fontes de dados**janela.

-   Criando controles que exibem dados, arrastando itens a partir de **fontes de dados** janela em um formulário.

-   Adicionar controles para exibir os dados no formulário.

-   Concluindo a **construtor de critérios de pesquisa** caixa de diálogo.

-   Inserir parâmetros para o formulário e executar a consulta com parâmetros.

## <a name="prerequisites"></a>Pré-requisitos

Este passo a passo usa o SQL Server Express LocalDB e o banco de dados de exemplo Northwind.

1.  Se você não tiver o SQL Server Express LocalDB, instale-o do [página de download do SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), ou por meio de **instalador do Visual Studio**. No instalador do Visual Studio, o SQL Server Express LocalDB pode ser instalado como parte do **armazenamento de dados e processamento** carga de trabalho, ou como um componente individual.

2.  Instale o banco de dados de exemplo Northwind seguindo estas etapas:

    1. No Visual Studio, abra o **Pesquisador de objetos do SQL Server** janela. (Pesquisador de objetos do SQL Server é instalado como parte do **armazenamento de dados e processamento** carga de trabalho em que o instalador do Visual Studio.) Expanda o **do SQL Server** nó. Clique com botão direito em sua instância de LocalDB e selecione **nova consulta...** .

       Abre uma janela do editor de consultas.

    2. Copie o [script Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) para sua área de transferência. Este script T-SQL cria o banco de dados Northwind desde o início e a preenche com dados.

    3. Cole o script T-SQL no editor de consultas e, em seguida, escolha o **Execute** botão.

       Após um curto período de tempo, a consulta termina de ser executado e o banco de dados Northwind é criado.

## <a name="create-the-windows-forms-application"></a>Criar o aplicativo do Windows Forms
 A primeira etapa é criar um **aplicativo do Windows Forms**. Atribuir um nome para o projeto é opcional nesta etapa, mas você poderá nomeá-lo aqui porque você poderá salvar o projeto mais tarde.

#### <a name="to-create-the-new-windows-forms-application-project"></a>Para criar o novo projeto de aplicativo do Windows Forms

1. No Visual Studio, no **arquivo** menu, selecione **novo**, **projeto...** .

2. Expanda **Visual C#** ou **Visual Basic** no painel esquerdo, selecione **área de trabalho clássica do Windows**.

3. No painel central, selecione a **aplicativo do Windows Forms** tipo de projeto.

4. Nomeie o projeto **como WindowsSearchForm**e, em seguida, escolha **Okey**.

     O **como WindowsSearchForm** projeto é criado e adicionado ao **Gerenciador de soluções**.

## <a name="create-the-data-source"></a>Criar a fonte de dados
Essa etapa cria uma fonte de dados de um banco de dados usando o **configuração da fonte de dados** assistente.

#### <a name="to-create-the-data-source"></a>Para criar a fonte de dados

1.  Sobre o **dados** menu, clique em **Mostrar fontes de dados**.

2.  No **fontes de dados** janela, selecione **adicionar nova fonte de dados** para iniciar o **configuração da fonte de dados** assistente.

3.  Selecione **banco de dados** no **escolher um tipo de fonte de dados** página e, em seguida, clique em **próximo**.

4.  Sobre o **escolha sua Conexão de dados** página faça o seguinte:

    -   Se uma conexão de dados com o banco de dados de exemplo Northwind estiver disponível na lista suspensa, selecione-o.

    -   Selecione **nova Conexão** para iniciar o **Adicionar/Modificar Conexão** caixa de diálogo.

5.  Se seu banco de dados exigir uma senha, selecione a opção para incluir dados confidenciais e, em seguida, clique em **próximo**.

6.  No **salvar a cadeia de caracteres de conexão para o arquivo de configuração de aplicativo** , clique em **próximo**.

7.  Sobre o **escolher seus objetos de banco de dados** página, expanda o **tabelas** nó.

8.  Selecione o **clientes** de tabela e, em seguida, clique em **concluir**.

     O **NorthwindDataSet** é adicionado ao seu projeto e o **clientes** tabela aparece no **fontes de dados** janela.

## <a name="create-the-form"></a>Criar o formulário
 Você pode criar os controles associados a dados, arrastando itens a partir de **fontes de dados** window para seu formulário.

#### <a name="to-create-data-bound-controls-on-the-form"></a>Para criar controles de associação de dados no formulário

1.  Expanda o **clientes** nó o **fontes de dados** janela.

2.  Arraste o **clientes** nó do **fontes de dados** janela para o formulário.

     Um <xref:System.Windows.Forms.DataGridView> e uma faixa de ferramentas (<xref:System.Windows.Forms.BindingNavigator>) para navegação em registros são exibidos no formulário. Um [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource>, e <xref:System.Windows.Forms.BindingNavigator> aparecem na bandeja do componente.

## <a name="add-parameterization-search-functionality-to-the-query"></a>Adicionar parametrização (funcionalidade de pesquisa) à consulta
 Você pode adicionar uma cláusula WHERE para a consulta original usando o **construtor de critérios de pesquisa** caixa de diálogo.

#### <a name="to-create-a-parameterized-query-and-controls-to-enter-the-parameters"></a>Para criar uma consulta parametrizada e controles para inserir os parâmetros

1.  Selecione o <xref:System.Windows.Forms.DataGridView> de controle e, em seguida, escolha **adicionar consulta** no **dados** menu.

2.  Tipo `FillByCity` no **novo nome de consulta** área o **construtor de critérios de pesquisa** caixa de diálogo.

3.  Adicionar `WHERE City = @City` para a consulta no **texto da consulta** área.

     A consulta deve ser semelhante ao seguinte:

     ```sql
     SELECT CustomerID, CompanyName, ContactName, ContactTitle,
          Address, City, Region, PostalCode, Country, Phone, Fax
     FROM Customers
     WHERE City = @City
     ```

    > [!NOTE]
    >  Fontes de dados do Access e o OLE DB usam o ponto de interrogação ('? ') para denotar parâmetros, portanto a cláusula WHERE teria esta aparência: `WHERE City = ?`.

4.  Clique em **Okey** para fechar o **construtor de critérios de pesquisa** caixa de diálogo.

     Um **FillByCityToolStrip** é adicionado ao formulário.

## <a name="testing-the-application"></a>Testando o aplicativo
 A execução do aplicativo abre o formulário pronto para receber o parâmetro como entrada.

#### <a name="to-test-the-application"></a>Para testar o aplicativo

1.  Pressione F5 para executar o aplicativo.

2.  Tipo **Londres** para o **City** caixa de texto e clique **FillByCity**.

     Grade de dados é populada com os clientes que atendem aos critérios. Neste exemplo, a grade de dados exibe apenas os clientes que têm um valor de **Londres** em seus **City** coluna.

## <a name="next-steps"></a>Próximas etapas
 Dependendo dos requisitos de aplicativo, existem várias etapas que você talvez queira realizar após criar um formulário parametrizado. Entre algumas das melhorias que você poderia fazer nessa explicação passo a passo estão:

-   Adicionar controles que exibem dados relacionados. Para obter mais informações, consulte [relacionamentos em conjuntos de dados](relationships-in-datasets.md).

-   Editando o conjunto de dados para adicionar ou remover objetos de banco de dados. Para obter mais informações, consulte [Create and configure datasets (Criar e configurar conjuntos de dados)](../data-tools/create-and-configure-datasets-in-visual-studio.md).

## <a name="see-also"></a>Consulte também

- [Associando controles do Windows Forms a dados no Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)