---
title: "Passo a passo: Personalizando a inserção, atualização e exclusão de comportamento de classes de entidade | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
ms.assetid: 03ff1146-706e-4780-91cb-56a83df63eea
caps.latest.revision: "3"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: f711c0fcdd4866a1b097585052cdcb3733e426d8
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/09/2017
---
# <a name="walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes"></a>Passo a passo: Personalizando a inserção, atualização e exclusão de comportamento de classes de entidade
O [LINQ to SQL Tools no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) fornece uma superfície de design visual para criar e editar [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] classes (classes de entidade) que são baseadas em objetos em um banco de dados. Usando [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index), você pode usar a tecnologia LINQ para acessar bancos de dados SQL. Para saber mais, veja [LINQ (Consulta Integrada à Linguagem)](http://msdn.microsoft.com/Library/a73c4aec-5d15-4e98-b962-1274021ea93d).  
  
Por padrão, a lógica para executar atualizações é fornecida pelo tempo de execução do [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]. O tempo de execução cria instruções padrão Insert, Update e Delete com base no esquema da tabela (as definições de coluna e as informações da chave primária). Quando você não deseja usar o comportamento padrão, poderá configurar o comportamento de atualização e designar procedimentos armazenados específicos para executar as inserções, as atualizações e as exclusões necessárias para trabalhar com os dados no banco de dados. Você também pode fazer isso quando o comportamento padrão não é gerado, por exemplo, quando as classes de entidade mapeiam para as exibições. Além disso, você pode substituir o comportamento de atualização padrão quando o banco de dados exige acesso à tabela por meio dos procedimentos armazenados. Para obter mais informações, consulte [personalizando operações, usando procedimentos armazenados](/dotnet/framework/data/adonet/sql/linq/customizing-operations-by-using-stored-procedures).  
  
> [!NOTE]
>  Este passo a passo requer a disponibilidade do **InsertCustomer**, **UpdateCustomer**, e **DeleteCustomer** procedimentos armazenados para o banco de dados Northwind.  
  
Essa explicação passo a passo fornece as etapas que você deve seguir para substituir o comportamento padrão de tempo de execução LINQ to SQL para salvar dados de volta para um banco de dados usando procedimentos armazenados.  
  
Durante essa explicação passo a passo, será ensinado como realizar as seguintes tarefas:  
  
-   Crie um novo aplicativo do Windows Forms e adicione um arquivo [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] a ele.  
  
-   Crie uma classe de entidade que está mapeada para a tabela Customers Northwind.  
  
-   Crie uma fonte de dados de objeto que referencia a classe de cliente LINQ to SQL.  
  
-   Crie um Windows Form que contém um <xref:System.Windows.Forms.DataGridView> que está associado à classe Customer.  
  
-   Implemente a funcionalidade de salvar para o formulário.  
  
-   Crie métodos de <xref:System.Data.Linq.DataContext> adicionando procedimentos armazenados ao [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
-   Configure a classe Customer para usar procedimentos armazenados para executar inserções, atualizações e exclusões.  
  
## <a name="prerequisites"></a>Pré-requisitos  
Este passo a passo usa o SQL Server Express LocalDB e o banco de dados de exemplo Northwind.  
  
1.  Se você não tiver o SQL Server Express LocalDB, instale-o do [página de download de edições do SQL Server](https://www.microsoft.com/en-us/server-cloud/Products/sql-server-editions/sql-server-express.aspx), ou por meio de **instalador do Visual Studio**. No instalador do Visual Studio, o SQL Server Express LocalDB pode ser instalado como parte do **armazenamento de dados e processamento** carga de trabalho, ou como um componente individual.  
  
2.  Instale o banco de dados de exemplo Northwind seguindo estas etapas:  

    1. No Visual Studio, abra o **Pesquisador de objetos do SQL Server** janela. (Pesquisador de objetos do SQL Server é instalado como parte do **armazenamento de dados e processamento** carga de trabalho em que o instalador do Visual Studio.) Expanda o **do SQL Server** nó. Clique com botão direito em sua instância de LocalDB e selecione **nova consulta...** .  

       Abre uma janela do editor de consultas.  

    2. Copie o [script Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) para sua área de transferência. Este script T-SQL cria o banco de dados Northwind desde o início e a preenche com dados.  

    3. Cole o script T-SQL no editor de consultas e, em seguida, escolha o **Execute** botão.  

       Após um curto período de tempo, a consulta termina de ser executado e o banco de dados Northwind é criado.  
  
## <a name="creating-an-application-and-adding-linq-to-sql-classes"></a>Criando um aplicativo e adicionando classes LINQ to SQL  
Como você estará trabalhando com classes do [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] e exibindo os dados em um Windows Form, crie um novo aplicativo do Windows Forms e adicione um arquivo de classes LINQ to SQL.  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### <a name="to-create-a-new-windows-forms-application-project-that-contains-linq-to-sql-classes"></a>Para criar um novo projeto de aplicativo do Windows Forms que contém o LINQ para classes do SQL  
  
1. No Visual Studio, no **arquivo** menu, selecione **novo**, **projeto...** .  
  
2. Expanda **Visual C#** ou **Visual Basic** no painel esquerdo, selecione **área de trabalho clássica do Windows**.  

3. No painel central, selecione a **aplicativo do Windows Forms** tipo de projeto.  

4. Nomeie o projeto **UpdatingWithSProcsWalkthrough**e, em seguida, escolha **Okey**. 
  
     O **UpdatingWithSProcsWalkthrough** projeto é criado e adicionado ao **Gerenciador de soluções**.  
  
4.  No menu **Projeto**, clique em **Adicionar Novo Item**.  
  
5.  Clique o **Classes LINQ to SQL** modelo e tipo **dbml** no **nome** caixa.  
  
6.  Clique em **Adicionar**.  
  
     Um arquivo de classes LINQ to SQL vazio (Northwind.dbml) é adicionado ao projeto, e o [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] é aberto.  
  
## <a name="creating-the-customer-entity-class-and-object-data-source"></a>Criando a Classe Entidade de Cliente e o Objeto de Fonte de Dados  
 Criar [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] classes que são mapeados para tabelas de banco de dados arrastando as tabelas de **Server Explorer**/**Pesquisador de objetos de banco de dados** até o [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. O resultado são classes de entidade do LINQ to SQL que mapeiam para as tabelas no banco de dados. Depois de criar classes de entidade, elas podem ser usadas como fontes de dados de objeto assim como outras classes que têm propriedades públicas.  
  
#### <a name="to-create-a-customer-entity-class-and-configure-a-data-source-with-it"></a>Para criar uma classe de entidade Customer e configurar uma fonte de dados com ela  
  
1.  Em **Server Explorer**/**Pesquisador de objetos de banco de dados**, localize a tabela de clientes na versão do SQL Server do banco de dados de exemplo Northwind. 
  
2.  Arraste o **clientes** nó do **Server Explorer**/**Pesquisador de objetos de banco de dados** até o [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] superfície.  
  
     Uma classe de entidade nomeada **cliente** é criado. Ela tem propriedades que correspondem às colunas na tabela Customers. A classe de entidade é nomeada **cliente** (não **clientes**) porque ela representa um único cliente da tabela Customers.  
  
    > [!NOTE]
    >  Esse comportamento de renomeação é chamado *pluralização*. Ele pode ser ativado ou desativada [caixa de diálogo Opções](../ide/reference/options-dialog-box-visual-studio.md). Para obter mais informações, consulte [como: ative em pluralization e off (Object Relational Designer)](../data-tools/how-to-turn-pluralization-on-and-off-o-r-designer.md).  
  
3.  No **criar** menu, clique em **UpdatingwithSProcsWalkthrough Build** para compilar o projeto.  
  
4.  Sobre o **dados** menu, clique em **Mostrar fontes de dados**.  
  
5.  No **fontes de dados** janela, clique em **adicionar nova fonte de dados**.  
  
6.  Clique em **objeto** no **escolher um tipo de fonte de dados** página e, em seguida, clique em **próximo**.  
  
7.  Expanda o **UpdatingwithSProcsWalkthrough** nó e localize e selecione o **cliente** classe.  
  
    > [!NOTE]
    >  Se o **cliente** classe não está disponível, cancele o assistente, compile o projeto e execute o assistente novamente.  
8.  Clique em **concluir** para criar a fonte de dados e adicionar o **cliente** classe da entidade para o **fontes de dados** janela.  
  
## <a name="creating-a-datagridview-to-display-the-customer-data-on-a-windows-form"></a>Criando um DataGridView para exibir os dados do cliente em um Windows Form  
 Criar controles que estão associados a classes de entidade arrastando [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] itens a partir da fonte de dados de **fontes de dados** janela em um Windows Form.  
  
#### <a name="to-add-controls-that-are-bound-to-the-entity-classes"></a>Para adicionar controles que estão associados às classes de entidade  
  
1.  Abrir Form1 na exibição Design.  
  
2.  Do **fontes de dados** janela, arraste o **cliente** nó Form1.  
  
    > [!NOTE]
    >  Para exibir o **fontes de dados** janela, clique em **Mostrar fontes de dados** no **dados** menu.  
  
3.  Abra o Form1 no Editor de Códigos.  
  
4.  Adicione o seguinte código ao formulário, global para o formulário, fora de qualquer método específico, mas dentro da classe Form1:  
  
    ```vb  
    Private NorthwindDataContext1 As New NorthwindDataContext  
    ```  
  
    ```csharp  
    private NorthwindDataContext northwindDataContext1  
        = new NorthwindDataContext();    
    ```  
  
5.  Crie um manipulador de eventos para o evento `Form_Load` e adicione o seguinte código ao manipulador:  
  
    ```vb  
    CustomerBindingSource.DataSource = NorthwindDataContext1.Customers  
    ```  
  
    ```csharp  
    customerBindingSource.DataSource  
        = northwindDataContext1.Customers;    
    ```  
  
## <a name="implementing-save-functionality"></a>Implementando a funcionalidade de salvar  
 Por padrão, o botão de salvar não está habilitado e a funcionalidade de salvar não está implementada. Além disso, o código não será automaticamente adicionado para salvar dados modificados no banco de dados quando os controles associados a dados forem criados para fontes de dados de objeto. Esta seção explica como habilitar o salvamento botão e implementar a funcionalidade para de salvar [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] objetos.  
  
#### <a name="to-implement-save-functionality"></a>Para implementar a funcionalidade de salvar  
  
1.  Abrir Form1 na exibição Design.  
  
2.  Selecione Salvar botão o **CustomerBindingNavigator** (o botão com o ícone de disquete).  
  
3.  No **propriedades** janela, defina o **habilitado** propriedade **True**.  
  
4.  Clique duas vezes no botão de salvar para criar um manipulador de eventos e alternar para o Editor de Códigos.  
  
5.  Adicione o código a seguir no manipulador de eventos do botão de salvar:  
  
    ```vb  
    NorthwindDataContext1.SubmitChanges()  
    ```  
  
    ```csharp  
    northwindDataContext1.SubmitChanges();  
    ```  
  
## <a name="overriding-the-default-behavior-for-performing-updates-inserts-updates-and-deletes"></a>Substituindo o comportamento padrão para realizar atualizações (inserções, atualizações e exclusões)  
  
#### <a name="to-override-the-default-update-behavior"></a>Para substituir o comportamento padrão de atualização  
  
1.  Abra o arquivo LINQ to SQL no [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. (Clique duas vezes o **dbml** arquivo **Solution Explorer**.)  
  
2.  Em **Server Explorer**/**Pesquisador de objetos de banco de dados**, expanda os bancos de dados Northwind **procedimentos armazenados** nó e localize o  **InsertCustomers**, **UpdateCustomers**, e **DeleteCustomers** procedimentos armazenados.  
  
3.  Arraste os três procedimentos armazenados para o [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
     Os procedimentos armazenados são adicionados ao painel dos métodos como métodos <xref:System.Data.Linq.DataContext>. Para obter mais informações, consulte [métodos DataContext (Object Relational Designer)](../data-tools/datacontext-methods-o-r-designer.md).  
  
4.  Selecione o **cliente** na classe da entidade a [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
5.  No **propriedades** janela, selecione o **inserir** propriedade.  
  
6.  Clique no botão de reticências (...) próximo a **tempo de execução de uso** para abrir o **configurar comportamento** caixa de diálogo.  
  
7.  Selecione **personalizar**.  
  
8.  Selecione o **InsertCustomers** método o **personalizar** lista.  
  
9. Clique em **aplicar** para salvar a configuração para a classe e comportamento selecionados.  
  
    > [!NOTE]
    >  Você pode continuar a configurar o comportamento para cada combinação de classe/comportamento enquanto você clica em **aplicar** após cada alteração. Se você alterar a classe ou o comportamento antes de clicar em **aplicar**, uma caixa de diálogo de aviso fornecendo uma oportunidade para aplicar as alterações serão exibidas.  
  
10. Selecione **atualização** no **comportamento** lista.  
  
11. Selecione **personalizar**.  
  
12. Selecione o **UpdateCustomers** método o **personalizar** lista.  
  
     Inspecione a lista de **argumentos de método** e **propriedades da classe** e observe que há dois **argumentos de método** e dois **propriedades da classe**para algumas colunas na tabela. Isso facilita controlar as alterações e criar as instruções que conferem a existência de violações de simultaneidade.  
  
13. Mapa de **Original_CustomerID** argumento de método para o **CustomerID (Original)** propriedade da classe.  
  
    > [!NOTE]
    >  Por padrão, os argumentos do método mapearão para as propriedades da classe quando os nomes corresponderem. Se os nomes de propriedade forem modificados e não corresponderem entre a tabela e a classe de entidade, você poderá ter que selecionar a propriedade da classe equivalente para a qual mapear se o Designer Relacional de Objetos não puder determinar o mapeamento correto. Além disso, se os argumentos de método não tem propriedades de classe válida para mapear, você pode definir o **propriedades da classe** valor **(nenhum)**.  
  
14. Clique em **aplicar** para salvar a configuração para a classe e comportamento selecionados.  
  
15. Selecione **excluir** no **comportamento** lista.  
  
16. Selecione **personalizar**.  
  
17. Selecione o **DeleteCustomers** método o **personalizar** lista.  
  
18. Mapa de **Original_CustomerID** argumento de método para o **CustomerID (Original)** propriedade da classe.  
  
19. Clique em **OK**.  
  
> [!NOTE]
>  Embora isso não seja um problema para essa explicação passo a passo específica, vale observar que o [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] manipula automaticamente os valores gerados por banco de dados para as colunas identidade (incremento automático), rowguidcol (GUID gerado por banco de dados) e carimbo de data/hora durante inserções e atualizações. Os valores gerados pelo banco de dados em outros tipos de coluna resultarão inesperadamente em um valor nulo. Para retornar os valores gerados pelo banco de dados, você deve definir manualmente <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> para `true` e <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> para um dos seguintes: <xref:System.Data.Linq.Mapping.AutoSync>, <xref:System.Data.Linq.Mapping.AutoSync>, ou <xref:System.Data.Linq.Mapping.AutoSync>.  
  
## <a name="testing-the-application"></a>Testando o aplicativo  
 Execute o aplicativo novamente para verificar se o **UpdateCustomers** procedimento armazenado corretamente atualiza o registro do cliente no banco de dados.  
  
#### <a name="to-test-the-application"></a>Para testar o aplicativo  
  
1.  Pressione F5.  
  
2.  Modifique um registro na grade para testar o comportamento de atualização.  
  
3.  Adicione um novo registro para testar o comportamento de inserção.  
  
4.  Clique no botão de salvar para salvar as alterações de volta para o banco de dados.  
  
5.  Feche o formulário.  
  
6.  Pressione F5 e verifique se o registro atualizado e o registro inserido recentemente persistiram.  
  
7.  Exclua o novo registro que você criou na etapa 3 para testar o comportamento de exclusão.  
  
8.  Clique no botão de salvar para enviar as alterações e remova o registro excluído do banco de dados  
  
9. Feche o formulário.  
  
10. Pressione F5 e verifique se o registro excluído foi removido do banco de dados.  
  
    > [!NOTE]
    >  Se seu aplicativo usa o SQL Server Express Edition, dependendo do valor da **copiar para diretório de saída** propriedade do arquivo de banco de dados, as alterações não podem aparecer quando você pressionar F5 na etapa 10. 
  
## <a name="next-steps"></a>Próximas etapas  
Dependendo dos requisitos de aplicativo, há várias etapas que você pode desejar executar depois de criar [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] classes de entidade. Entre algumas das melhorias que você pode fazer neste aplicativo estão:  
  
-   Implementar verificação de simultaneidade durante atualizações. Para obter informações, consulte [simultaneidade otimista: Visão geral do](/dotnet/framework/data/adonet/sql/linq/optimistic-concurrency-overview).  
  
-   Adicionar consultas LINQ para filtrar dados. Para obter informações, consulte [Introdução às consultas do LINQ (c#)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).  
  
## <a name="see-also"></a>Consulte também
[LINQ to SQL Tools no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)     
[Métodos DataContext](../data-tools/datacontext-methods-o-r-designer.md)   
[Como: atribuir procedimentos armazenados para executar atualizações, inserções e exclusões](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)  
[LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)  
[Consultas LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/linq-to-sql-queries)  
 