---
title: "Salvar dados em um banco de dados (várias tabelas) | Microsoft Docs"
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
- updating datasets, walkthroughs
- data [Visual Studio], saving
- saving data, walkthroughs
- data [Visual Studio], updating
ms.assetid: 7ebe03da-ce8c-4cbc-bac0-a2fde4ae4d07
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: e3841a0052081700be899576e1adc0a0740fecec
ms.sourcegitcommit: 49aa031cbebdd9c7ec070c713afb1a97d1ecb701
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2018
---
# <a name="save-data-to-a-database-multiple-tables"></a>Salvar dados em um banco de dados (várias tabelas)
Um dos cenários mais comuns no desenvolvimento de aplicativos é exibir dados de um formulário em um aplicativo do Windows, editar e enviá-los atualizados de volta para o banco de dados. Essa explicação passo a passo cria um formulário que exibe dados de duas tabelas relacionadas e mostra como editar registros e salvar alterações no banco de dados. Este exemplo usa as tabelas `Customers` e `Orders` do banco de dados de exemplo Northwind.  
  
 Você pode salvar os dados em seu aplicativo de volta no banco de dados chamando o método `Update` de um TableAdapter. Quando você arrasta a tabelas do **fontes de dados** window para um formulário, o código necessário para salvar dados é adicionado automaticamente. Quaisquer tabelas adicionais que são adicionadas a um formulário exigem a inclusão manual deste código. Essa explicação passo a passo mostra como adicionar código para salvar atualizações de mais de uma tabela.  
  
> [!NOTE]
>  Caixas de diálogo e comandos de menu encontrados podem diferir daqueles descritos na Ajuda, dependendo de suas configurações ativas ou a edição que você está usando. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
 As tarefas ilustradas neste passo a passo incluem:  
  
-   Criando um novo **aplicativo do Windows Forms** projeto.  
  
-   Criando e configurando uma fonte de dados em seu aplicativo com o [Assistente de configuração de fonte de dados](../data-tools/media/data-source-configuration-wizard.png).  
  
-   Controla os itens a [janela fontes de dados](add-new-data-sources.md). Para obter mais informações, consulte [definir o controle a ser criado quando arrastado da janela fontes de dados](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
-   Criando controles associados a dados, arrastando itens a partir de **fontes de dados** window para seu formulário.  
  
-   Modificando alguns registros em cada tabela no conjunto de dados.  
  
-   Modificando o código para enviar os dados atualizados no conjunto de dados de volta ao banco de dados.  
  
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
 A primeira etapa é criar um **aplicativo do Windows Forms**. Atribuir um nome para o projeto é opcional durante esta etapa, mas vamos dar-um nome de nós será salvar o projeto mais tarde.  
  
#### <a name="to-create-the-new-windows-forms-application-project"></a>Para criar o novo projeto de aplicativo do Windows forms  
  
1. No Visual Studio, no **arquivo** menu, selecione **novo**, **projeto...** .  
  
2. Expanda **Visual C#** ou **Visual Basic** no painel esquerdo, selecione **área de trabalho clássica do Windows**.  

3. No painel central, selecione a **aplicativo do Windows Forms** tipo de projeto.  

4. Nomeie o projeto **UpdateMultipleTablesWalkthrough**e, em seguida, escolha **Okey**. 
  
     O **UpdateMultipleTablesWalkthrough** projeto é criado e adicionado ao **Gerenciador de soluções**.  
  
## <a name="create-the-data-source"></a>Criar a fonte de dados  
 Essa etapa cria uma fonte de dados do banco de dados Northwind usando o **Assistente de configuração de fonte de dados**. É preciso ter acesso ao banco de dados de exemplo Northwind para criar a conexão. Para obter informações sobre como configurar o banco de dados de exemplo Northwind, consulte [como: instalar bancos de dados de exemplo](../data-tools/installing-database-systems-tools-and-samples.md).  
  
#### <a name="to-create-the-data-source"></a>Para criar a fonte de dados  
  
1.  Sobre o **dados** menu, selecione **Mostrar fontes de dados**.  
  
2.  No **fontes de dados** janela, selecione**adicionar nova fonte de dados** para iniciar o **Assistente de configuração de fonte de dados**.  
  
3.  Sobre o **escolher um tipo de fonte de dados** tela, selecione **banco de dados**e, em seguida, selecione **próximo**.  
  
4.  Sobre o **escolha sua Conexão de dados** tela faça o seguinte:  
  
    -   Se uma conexão de dados com o banco de dados de exemplo Northwind estiver disponível na lista suspensa, selecione-o.  
  
         -ou-  
  
    -   Selecione **nova Conexão** para abrir o **Adicionar/Modificar Conexão** caixa de diálogo.  
  
5.  Se seu banco de dados exigir uma senha, selecione a opção para incluir dados confidenciais e, em seguida, selecione **próximo**.  
  
6.  Sobre o **salvar a cadeia de caracteres de conexão para o arquivo de configuração de aplicativo**, selecione **próximo**.  
  
7.  Sobre o **escolher seus objetos de banco de dados**tela, expanda o **tabelas** nó.  
  
8.  Selecione o **clientes** e **pedidos** tabelas e, em seguida, selecione **concluir**.  
  
     O **NorthwindDataSet** é adicionado ao seu projeto, e as tabelas aparecem no **fontes de dados** janela.  
  
## <a name="set-the-controls-to-be-created"></a>Definir os controles a ser criado  
 Para este passo a passo, os dados a `Customers` a tabela está em um **detalhes** layout onde os dados são exibidos em controles individuais. Os dados do `Orders` a tabela está em um **grade** layout é exibido em um <xref:System.Windows.Forms.DataGridView> controle.  
  
#### <a name="to-set-the-drop-type-for-the-items-in-the-data-sources-window"></a>Definir o tipo de remoção dos itens na Janela Fontes de Dados  
  
1.  No **fontes de dados** janela, expanda o **clientes** nó.  
  
2.  No **clientes** nó, selecione **detalhes** na lista de controle para alterar o controle do **clientes** tabela para os controles individuais. Para obter mais informações, consulte [definir o controle a ser criado quando arrastado da janela fontes de dados](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
## <a name="create-the-data-bound-form"></a>Criar o formulário de associação de dados  
 Você pode criar os controles associados a dados, arrastando itens a partir de **fontes de dados** window para seu formulário.  
  
#### <a name="to-create-data-bound-controls-on-the-form"></a>Para criar controles de associação de dados no formulário  
  
1.  Arraste principal **clientes** nó a partir de **fontes de dados** janela para **Form1**.  
  
     Os controles de associação de dados com rótulos descritivos são exibidos no formulário, juntamente com uma faixa de ferramentas (<xref:System.Windows.Forms.BindingNavigator>) para registros de navegação. Um [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), `CustomersTableAdapter`, <xref:System.Windows.Forms.BindingSource>, e <xref:System.Windows.Forms.BindingNavigator> aparecem na bandeja do componente.  
  
2.  Arraste relacionado **pedidos** nó a partir de **fontes de dados** janela para **Form1**.  
  
    > [!NOTE]
    >  Relacionado **pedidos** nó está localizado abaixo do **Fax** coluna e é um nó filho a **clientes** nó.  
  
     Um controle <xref:System.Windows.Forms.DataGridView> e uma faixa de ferramentas (<xref:System.Windows.Forms.BindingNavigator>) para navegação em registros são exibidos no formulário. Um `OrdersTableAdapter` e <xref:System.Windows.Forms.BindingSource> aparecem na bandeja do componente.  
  
## <a name="add-code-to-update-the-database"></a>Adicione código para atualizar o banco de dados  
 Você pode atualizar o banco de dados chamando o `Update` métodos do **clientes** e **pedidos** TableAdapters. Por padrão, um manipulador de eventos para o **salvar** botão do<xref:System.Windows.Forms.BindingNavigator> é adicionado ao código do formulário para enviar atualizações para o banco de dados. Este procedimento modifica o código para enviar atualizações na ordem correta. Isso elimina a possibilidade de gerar erros de integridade referencial. O código também implementa manipulação de erros com a quebra automática da chamada de atualização em um bloco try-catch. Você pode mudar o código para atender às necessidades do seu aplicativo.  
  
> [!NOTE]
>  Para maior clareza, este passo a passo não usa uma transação. No entanto, se você estiver atualizando dois ou mais tabelas relacionadas, inclua toda a lógica de atualização dentro de uma transação. Uma transação é um processo que garante que todas as alterações relacionadas a um banco de dados forem bem-sucedidas, antes que as alterações sejam confirmadas. Para obter mais informações, consulte [transações e simultaneidade](/dotnet/framework/data/adonet/transactions-and-concurrency).  
  
#### <a name="to-add-update-logic-to-the-application"></a>Para adicionar lógica de atualização ao aplicativo  
  
1.  Selecione o **salvar** botão o <xref:System.Windows.Forms.BindingNavigator>. Isso abre o Editor de código para o `bindingNavigatorSaveItem_Click` manipulador de eventos.  
  
2.  Substitua o código no manipulador de eventos para chamar os métodos `Update` dos TableAdapters relacionados. O código a seguir primeiro cria três tabelas de dados temporárias para armazenar as informações de cada <xref:System.Data.DataRowState> (<xref:System.Data.DataRowState.Deleted>, <xref:System.Data.DataRowState.Added> e <xref:System.Data.DataRowState.Modified>). Em seguida, as atualizações são executadas na ordem correta. O código deve se parecer com o seguinte:  
  
     [!code-vb[VbRaddataSaving#10](../data-tools/codesnippet/VisualBasic/save-data-to-a-database-multiple-tables_1.vb)]
     [!code-csharp[VbRaddataSaving#10](../data-tools/codesnippet/CSharp/save-data-to-a-database-multiple-tables_1.cs)]  
  
## <a name="test-the-application"></a>Testar o aplicativo  
  
#### <a name="to-test-the-application"></a>Para testar o aplicativo  
  
1.  Selecione **F5**.  
  
2.  Faça algumas alterações nos dados de um ou mais registros em cada tabela.  
  
3.  Selecione o **salvar** botão.  
  
4.  Confira os valores no banco de dados para verificar se as alterações foram salvas.  
  
  
## <a name="see-also"></a>Consulte também  
 [Salvar dados de volta no banco de dados](../data-tools/save-data-back-to-the-database.md)