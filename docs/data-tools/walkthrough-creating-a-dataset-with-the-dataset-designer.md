---
title: 'Passo a passo: Criando um conjunto de dados com o Designer de conjunto de dados | Microsoft Docs'
ms.custom: 
ms.date: 09/11/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- datasets [Visual Basic], walkthroughs
- XML schemas, creating datasets
- data [Visual Studio], Dataset Designer
- Dataset Designer, walkthroughs
- datasets [Visual Basic], creating
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: 35f98e7442c6600baa1afcc38642abf8e7aeb3ba
ms.sourcegitcommit: 49aa031cbebdd9c7ec070c713afb1a97d1ecb701
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2018
---
# <a name="walkthrough-creating-a-dataset-with-the-dataset-designer"></a>Instruções passo a passo: criando um conjunto de dados com o Designer de Conjunto de Dados

Neste passo a passo, você irá criar um conjunto de dados usando o **Dataset Designer**. Levará você pelo processo de criar um novo projeto e adicionar um novo **DataSet** item a ele. Você aprenderá como criar tabelas com base em tabelas em um banco de dados sem usar um assistente.  

As tarefas ilustradas neste passo a passo incluem:  

-   Criando um novo **aplicativo do Windows Forms** projeto.  

-   Adicionando vazio **DataSet** item ao projeto.  

-   Criar e configurar uma fonte de dados em seu aplicativo, criando um dataset com o **Dataset Designer**.  
 
-   Criar uma conexão ao banco de dados Northwind em **Server Explorer**.  

-   Criando tabelas com TableAdapters no conjunto de dados com base em tabelas no banco de dados.  

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## <a name="prerequisites"></a>Pré-requisitos  
Este passo a passo usa o SQL Server Express LocalDB e o banco de dados de exemplo Northwind.  
  
1.  Se você não tiver o SQL Server Express LocalDB, instale-o do [página de download do SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), ou por meio de **instalador do Visual Studio**. No instalador do Visual Studio, o SQL Server Express LocalDB pode ser instalado como parte do **armazenamento de dados e processamento** carga de trabalho, ou como um componente individual.  
  
2.  Instale o banco de dados de exemplo Northwind seguindo estas etapas:  

    1. No Visual Studio, abra o **Pesquisador de objetos do SQL Server** janela. (Pesquisador de objetos do SQL Server é instalado como parte do **armazenamento de dados e processamento** carga de trabalho em que o instalador do Visual Studio.) Expanda o **do SQL Server** nó. Clique com botão direito em sua instância de LocalDB e selecione **nova consulta...** .  

       Abre uma janela do editor de consultas.  

    2. Copie o [script Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) para sua área de transferência. Este script T-SQL cria o banco de dados Northwind desde o início e a preenche com dados.  

    3. Cole o script T-SQL no editor de consultas e, em seguida, escolha o **Execute** botão.  

       Após um curto período de tempo, a consulta termina de ser executado e o banco de dados Northwind é criado.  
  
## <a name="creating-a-new-windows-forms-application-project"></a>Criando um novo projeto de aplicativo do Windows Forms  
  
#### <a name="to-create-a-new-windows-forms-application-project"></a>Para criar um novo projeto de aplicativo do Windows Forms  
  
1. No Visual Studio, no **arquivo** menu, selecione **novo**, **projeto...** .  
  
2. Expanda **Visual C#** ou **Visual Basic** no painel esquerdo, selecione **área de trabalho clássica do Windows**.  

3. No painel central, selecione a **aplicativo do Windows Forms** tipo de projeto.  

4. Nomeie o projeto **como DatasetDesignerWalkthrough**e, em seguida, escolha **Okey**.  
  
     O Visual Studio adiciona o projeto para **Solution Explorer** e um novo formulário é exibido no designer.  
  
## <a name="adding-a-new-dataset-to-the-application"></a>Adicionando um novo conjunto de dados para o aplicativo  
  
#### <a name="to-add-a-new-dataset-item-to-the-project"></a>Para adicionar um novo item de conjunto de dados ao projeto  
  
1.  Sobre o **projeto** menu, selecione **Adicionar Novo Item...** .  
  
     A caixa de diálogo **Adicionar Novo Item** é exibida.  
  
2.  No painel esquerdo, selecione **dados**, em seguida, selecione **conjunto de dados** no painel central.  
  
3.  Nome do conjunto de dados **NorthwindDataset**e, em seguida, escolha **adicionar**.  
  
     O Visual Studio adiciona um arquivo chamado **NorthwindDataSet** ao projeto e abre-na **Dataset Designer**.  
  
## <a name="creating-a-data-connection-in-server-explorer"></a>Criando uma Conexão de dados no Gerenciador de servidores  
  
#### <a name="to-create-a-connection-to-the-northwind-database"></a>Para criar uma conexão ao banco de dados Northwind  
  
1.  Sobre o **exibição** menu, clique em **Server Explorer**.  
  
2.  Em **Server Explorer**, clique no **conectar-se ao banco de dados** botão.  
  
3.  Crie uma conexão ao banco de dados de exemplo Northwind.  
  
## <a name="creating-the-tables-in-the-dataset"></a>A criação de tabelas no conjunto de dados  
Esta seção explica como adicionar tabelas ao conjunto de dados.  
  
#### <a name="to-create-the-customers-table"></a>Para criar a tabela Customers  
  
1.  Expanda a conexão de dados que você criou na **Server Explorer**e, em seguida, expanda o **tabelas** nó.  
  
2.  Arraste o **clientes** tabela **Server Explorer** para o **Dataset Designer**.  
  
     Um **clientes** tabela de dados e **CustomersTableAdapter** são adicionados ao conjunto de dados.  
  
#### <a name="to-create-the-orders-table"></a>Para criar a tabela Orders  
  
-   Arraste o **pedidos** tabela **Gerenciador de servidores** para o **Dataset Designer**.  
  
     Um **pedidos** tabela de dados, **OrdersTableAdapter**e a relação de dados entre o **clientes** e **pedidos** tabelas são adicionadas ao conjunto de dados.  
  
#### <a name="to-create-the-orderdetails-table"></a>Para criar a tabela OrderDetails  
  
-   Arraste o **detalhes do pedido** tabela **Server Explorer** para o **Dataset Designer**.  
  
     Um **Order Details** tabela de dados, **OrderDetailsTableAdapter**e a relação de dados entre o **pedidos** e **OrderDetails** tabelas são adicionadas ao conjunto de dados.  
  
## <a name="next-steps"></a>Próximas etapas  
  
### <a name="to-add-functionality-to-your-application"></a>Para adicionar funcionalidade ao seu aplicativo  
  
-   Salve o conjunto de dados.  
  
-   Selecione os itens na **fontes de dados** janela e arraste-os para um formulário. Para obter mais informações, consulte [controla associar Windows Forms a dados no Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md).  
  
-   Adicione mais consultas aos TableAdapters. 
  
-   Adicionar a lógica de validação de <xref:System.Data.DataTable.ColumnChanging> ou <xref:System.Data.DataTable.RowChanging> eventos das tabelas de dados no conjunto de dados. Para obter mais informações, consulte [validar dados em conjuntos de dados](../data-tools/validate-data-in-datasets.md).  
  
## <a name="see-also"></a>Consulte também
[Criar e configurar conjuntos de dados no Visual Studio](../data-tools/create-and-configure-datasets-in-visual-studio.md)  
[Associar controles do Windows Forms a dados no Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
[Associar controles a dados no Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
[Validando dados](../data-tools/validate-data-in-datasets.md)   
[Salvando dados](../data-tools/saving-data.md)