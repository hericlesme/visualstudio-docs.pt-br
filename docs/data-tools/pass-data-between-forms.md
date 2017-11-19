---
title: "Passar dados entre formulários | Microsoft Docs"
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
- walkthroughs [Windows Forms], data
- walkthroughs [Visual Studio], data
- data [Visual Studio], passing between forms
- forms, passing data between
- Windows Forms, walkthroughs
ms.assetid: 78bf038b-9296-4fbf-b0e8-d881d1aff0df
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: f401224657e64922fc9f6102a33eaf1cf824a556
ms.sourcegitcommit: ec1c7e7e3349d2f3a4dc027e7cfca840c029367d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2017
---
# <a name="pass-data-between-forms"></a>Passar dados entre formulários
Este passo a passo fornece instruções detalhadas de como passar os dados de um formulário para outro. Usando as tabelas customers e orders da Northwind, um formulário permite que os usuários selecionem um cliente e um segundo formulário exibe os pedidos do cliente selecionado. Este passo a passo mostra como criar um método no segundo formulário que recebe dados do primeiro formulário.  
  
> [!NOTE]
>  Este passo a passo demonstra apenas uma maneira de passar dados entre formulários. Há outras opções para passar dados para um formulário, incluindo a criação de um segundo construtor para receber dados, ou criando uma propriedade pública que pode ser definido com dados do primeiro formulário.  
  
 As tarefas ilustradas neste passo a passo incluem:  
  
-   Criando um novo **aplicativo do Windows Forms** projeto.  
  
-   Criando e configurando um conjunto de dados com o [Assistente de configuração de fonte de dados](../data-tools/media/data-source-configuration-wizard.png).  
  
-   Selecionando o controle a ser criado no formulário ao arrastar itens a partir de **fontes de dados** janela. Para obter mais informações, consulte [definir o controle a ser criado quando arrastado da janela fontes de dados](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
-   Criando um controle de associação de dados arrastando itens a partir de **fontes de dados** janela em um formulário.  
  
-   Criar um segundo formulário com uma grade para exibir dados.  
  
-   Criar uma consulta TableAdapter para buscar pedidos de um cliente específico.  
  
-   Passar dados entre formulários.  
  
## <a name="prerequisites"></a>Pré-requisitos  
Este passo a passo usa o SQL Server Express LocalDB e o banco de dados de exemplo Northwind.  
  
1.  Se você não tiver o SQL Server Express LocalDB, instale-o do [página de download de edições do SQL Server](https://www.microsoft.com/en-us/server-cloud/Products/sql-server-editions/sql-server-express.aspx), ou por meio de **instalador do Visual Studio**. No instalador do Visual Studio, o SQL Server Express LocalDB pode ser instalado como parte do **armazenamento de dados e processamento** carga de trabalho, ou como um componente individual.  
  
2.  Instale o banco de dados de exemplo Northwind seguindo estas etapas:  

    1. No Visual Studio, abra o **Pesquisador de objetos do SQL Server** janela. (Pesquisador de objetos do SQL Server é instalado como parte do **armazenamento de dados e processamento** carga de trabalho em que o instalador do Visual Studio.) Expanda o **do SQL Server** nó. Clique com botão direito em sua instância de LocalDB e selecione **nova consulta...** .  

       Abre uma janela do editor de consultas.  

    2. Copie o [script Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) para sua área de transferência. Este script T-SQL cria o banco de dados Northwind desde o início e a preenche com dados.  

    3. Cole o script T-SQL no editor de consultas e, em seguida, escolha o **Execute** botão.  

       Após um curto período de tempo, a consulta termina de ser executado e o banco de dados Northwind é criado.  
  
## <a name="create-the-windows-forms-application"></a>Criar o aplicativo do Windows Forms  
  
#### <a name="to-create-the-new-windows-project"></a>Para criar o novo projeto do Windows  
  
1. No Visual Studio, no **arquivo** menu, selecione **novo**, **projeto...** .  
  
2. Expanda **Visual C#** ou **Visual Basic** no painel esquerdo, selecione **área de trabalho clássica do Windows**.  

3. No painel central, selecione a **aplicativo do Windows Forms** tipo de projeto.  

4. Nomeie o projeto **PassingDataBetweenForms**e, em seguida, escolha **Okey**. 
  
     O **PassingDataBetweenForms** projeto é criado e adicionado ao **Gerenciador de soluções**.  
  
## <a name="create-the-data-source"></a>Criar a fonte de dados  
  
#### <a name="to-create-the-data-source"></a>Para criar a fonte de dados  
  
1.  Sobre o **dados** menu, clique em **Mostrar fontes de dados**.  
  
2.  No **fontes de dados** janela, selecione **adicionar nova fonte de dados** para iniciar o **configuração da fonte de dados** assistente.  
  
3.  Selecione **banco de dados** no **escolher um tipo de fonte de dados** página e, em seguida, clique em **próximo**.  
  
4.  No **escolha um modelo de banco de dados** Verifique **conjunto de dados** for especificado e, em seguida, clique em **próximo**.  
  
5.  Sobre o **escolha sua Conexão de dados** página, faça o seguinte:  
  
    -   Se uma conexão de dados com o banco de dados de exemplo Northwind estiver disponível na lista suspensa, selecione-o.  
  
    -   Selecione **nova Conexão** para iniciar o **Adicionar/Modificar Conexão** caixa de diálogo.  
  
6.  Se seu banco de dados requer uma senha e se a opção para incluir dados confidenciais é ativada, selecione a opção e, em seguida, clique em **próximo**.  
  
7.  No **salvar a cadeia de caracteres de conexão para o arquivo de configuração de aplicativo** , clique em **próximo**.  
  
8.  Sobre o **escolher seus objetos de banco de dados** página, expanda o **tabelas** nó.  
  
9. Selecione o **clientes** e **pedidos** tabelas e depois clique em **concluir**.  
  
     O **NorthwindDataSet** é adicionado ao seu projeto e o **clientes** e **pedidos** as tabelas aparecem no **fontes de dados** janela.  
  
## <a name="create-the-first-form-form1"></a>Criar o primeiro formulário (Form1)  
 Você pode criar uma grade de dados associados (uma <xref:System.Windows.Forms.DataGridView> controle), arrastando o **clientes** nó do **fontes de dados** janela para o formulário.  
  
#### <a name="to-create-a-data-bound-grid-on-the-form"></a>Para criar uma grade de associação de dados no formulário  
  
-   Arraste principal **clientes** nó a partir de **fontes de dados** janela para **Form1**.  
  
     Um <xref:System.Windows.Forms.DataGridView> e uma faixa de ferramenta (<xref:System.Windows.Forms.BindingNavigator>) para navegar pelos registros aparecem no **Form1**. Um [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource>, e <xref:System.Windows.Forms.BindingNavigator> aparecem na bandeja do componente.  
  
## <a name="create-the-second-form-form2"></a>Criar o segundo formulário (Form2)  
  
#### <a name="to-create-a-second-form-to-pass-the-data-to"></a>Para criar um segundo formulário para o qual passar os dados  
  
1.  No menu **Projeto**, escolha **Adicionar Formulário do Windows**.  
  
2.  Deixe o nome padrão do **Form2**e clique em **adicionar**.  
  
3.  Arraste principal **pedidos** nó a partir de **fontes de dados** janela para **Form2**.  
  
     Um <xref:System.Windows.Forms.DataGridView> e uma faixa de ferramenta (<xref:System.Windows.Forms.BindingNavigator>) para navegar pelos registros aparecem no **Form2**. Um [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource>, e <xref:System.Windows.Forms.BindingNavigator> aparecem na bandeja do componente.  
  
4.  Excluir o **OrdersBindingNavigator** da bandeja do componente.  
  
     O **OrdersBindingNavigator** desaparece da **Form2**.  
  
## <a name="add-a-tableadapter-query-to-form2-to-load-orders-for-the-selected-customer-on-form1"></a>Adicionar uma consulta do TableAdapter ao Form2 para carregar pedidos do cliente selecionado no Form1  
  
#### <a name="to-create-a-tableadapter-query"></a>Para criar uma consulta do TableAdapter  
  
1.  Clique duas vezes o **NorthwindDataSet** arquivo **Gerenciador de soluções**.  
  
2.  Clique com botão direito do **OrdersTableAdapter**e selecione **adicionar consulta**.  
  
3.  Deixe a opção padrão de **instruções SQL Use**e, em seguida, clique em **próximo**.  
  
4.  Deixe a opção padrão de **SELECT que retorna linhas**e, em seguida, clique em **próximo**.  
  
5.  Adicionar uma cláusula WHERE para a consulta retornar `Orders` com base no `CustomerID`. A consulta deve ser semelhante ao seguinte:  
  
    ```  
    SELECT OrderID, CustomerID, EmployeeID, OrderDate, RequiredDate, ShippedDate, ShipVia, Freight, ShipName, ShipAddress, ShipCity, ShipRegion, ShipPostalCode, ShipCountry  
    FROM Orders   
    WHERE CustomerID = @CustomerID  
    ```  
  
    > [!NOTE]
    >  Verifique a sintaxe de parâmetro correta para o seu banco de dados. Por exemplo, no Microsoft Access, a cláusula WHERE seria algo como: `WHERE CustomerID = ?`.  
  
6.  Clique em **Avançar**.  
  
7.  Para o **preencher um nome de DataTableMethod**, tipo `FillByCustomerID`.  
  
8.  Limpar o **retornar uma DataTable** opção e, em seguida, clique em **próximo**.  
  
9. Clique em **Finalizar**.  
  
## <a name="create-a-method-on-form2-to-pass-data-to"></a>Criar um método no Form2 para passar dados  
  
#### <a name="to-create-a-method-to-pass-data-to"></a>Para criar um método para o qual passar dados  
  
1.  Clique com botão direito **Form2**e selecione **Exibir código** abrir **Form2** no **Editor de código**.  
  
2.  Adicione o seguinte código para **Form2** depois que o `Form2_Load` método:  
  
     [!code-vb[VbRaddataDisplaying#1](../data-tools/codesnippet/VisualBasic/pass-data-between-forms_1.vb)]
     [!code-csharp[VbRaddataDisplaying#1](../data-tools/codesnippet/CSharp/pass-data-between-forms_1.cs)]  
  
## <a name="create-a-method-on-form1-to-pass-data-and-display-form2"></a>Criar um método no Form1 para passar dados e exibir o Form2  
  
#### <a name="to-create-a-method-to-pass-data-to-form2"></a>Para criar um método para passar dados para o Form2  
  
1.  Em **Form1**, clique com botão direito da grade de dados do cliente e, em seguida, clique em **propriedades**.  
  
2.  Na janela **Propriedades**, clique em **Eventos**.  
  
3.  Clique duas vezes o **CellDoubleClick** eventos.  
  
     O Editor de Códigos é exibido.  
  
4.  Atualize a definição de método para corresponder ao seguinte exemplo:  
  
     [!code-csharp[VbRaddataDisplaying#2](../data-tools/codesnippet/CSharp/pass-data-between-forms_2.cs)]
     [!code-vb[VbRaddataDisplaying#2](../data-tools/codesnippet/VisualBasic/pass-data-between-forms_2.vb)]  
  
## <a name="run-the-application"></a>Executar o aplicativo  
  
#### <a name="to-run-the-application"></a>Para executar o aplicativo  
  
-   Pressione F5 para executar o aplicativo.  
  
-   Clique duas vezes em um registro de cliente em **Form1** abrir **Form2** com pedidos do cliente.  
  
## <a name="next-steps"></a>Próximas etapas  
 Dependendo dos requisitos de aplicativo, existem várias etapas que você talvez queira realizar após passar dados entre formulários. Entre algumas das melhorias que você poderia fazer nessa explicação passo a passo estão:  
  
-   Editar o conjunto de dados, para adicionar ou remover objetos de banco de dados. Para obter mais informações, consulte [Create and configure datasets (Criar e configurar conjuntos de dados)](../data-tools/create-and-configure-datasets-in-visual-studio.md).  
  
-   Adicionar funcionalidade para salvar dados de volta no banco de dados. Para obter mais informações, consulte [salvar dados no banco de dados](../data-tools/save-data-back-to-the-database.md).  
  
## <a name="see-also"></a>Consulte também  
 [Associando controles do Windows Forms a dados no Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)