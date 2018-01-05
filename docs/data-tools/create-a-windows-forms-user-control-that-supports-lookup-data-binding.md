---
title: "Usando tabelas de pesquisa na associação de dados - controles de formulários do Windows | Microsoft Docs"
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
- data binding, user controls
- LookupBindingPropertiesAttribute class, examples
- user controls [Visual Basic], creating
ms.assetid: c48b4d75-ccfc-4950-8b14-ff8adbfe4208
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: c3ecb38b4f208eac3a49cc2f0e21fb98ef81ea68
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="create-a-windows-forms-user-control-that-supports-lookup-data-binding"></a>Criar um controle de usuário do Windows Forms que dá suporte à associação de dados de pesquisa
Ao exibir dados em formulários do Windows, você pode escolher os controles existentes da **caixa de ferramentas**, ou você pode criar controles personalizados se seu aplicativo requer uma funcionalidade não disponível nos controles padrão. Este passo a passo mostra como criar um controle que implementa o <xref:System.ComponentModel.LookupBindingPropertiesAttribute>. Os controles que implementam o <xref:System.ComponentModel.LookupBindingPropertiesAttribute> contêm três propriedade que podem ser associadas a dados. Tais controles são semelhantes a um <xref:System.Windows.Forms.ComboBox>.  
  
 Para obter mais informações sobre criação de controle, consulte [desenvolvendo controles dos Windows Forms em tempo de Design](/dotnet/framework/winforms/controls/developing-windows-forms-controls-at-design-time).  
  
 Ao criar controles para uso em cenários de associação de dados, você precisa implementar um dos seguintes atributos de associação de dados:  
  
|Uso do atributo de associação de dados|  
|-----------------------------------|  
|Implemente o <xref:System.ComponentModel.DefaultBindingPropertyAttribute> em controles simples, como um <xref:System.Windows.Forms.TextBox>, que exibe uma única coluna (ou propriedade) de dados. Para obter mais informações, consulte [criar um controle de usuário do Windows Forms que dá suporte à associação de dados simples](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).|  
|Implemente o <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> nos controles, como um <xref:System.Windows.Forms.DataGridView> que exibe listas (ou tabelas) de dados. Para obter mais informações, consulte [criar um controle de usuário do Windows Forms que dá suporte à associação de dados complexos](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).|  
|Implemente o <xref:System.ComponentModel.LookupBindingPropertiesAttribute> nos controles, como um <xref:System.Windows.Forms.ComboBox>que exibe listas (ou tabelas) de dados, mas também precisa apresentar uma única coluna ou propriedade. (Esse processo é descrito nesta página de passo a passo.)|  
  
 Este passo a passo cria um controle de pesquisa que se associa aos dados de duas tabelas. Este exemplo usa as tabelas `Customers` e `Orders` do banco de dados de exemplo Northwind. O controle de pesquisa será associado ao campo `CustomerID` da tabela `Orders`. Ele usará este valor para pesquisar `CompanyName` na tabela `Customers`.  
  
 Durante este passo a passo, você aprenderá a:  
  
-   Criar um novo **aplicativo do Windows Forms**.  
  
-   Adicionar um novo **controle de usuário** ao seu projeto.  
  
-   Projetar visualmente o controle do usuário.  
  
-   Implementar o atributo `LookupBindingProperty`.  
  
-   Criar um conjunto de dados com o **configuração da fonte de dados** assistente.  
  
-   Definir o **CustomerID** coluna o **pedidos** tabela, no **fontes de dados** janela, para usar o novo controle.  
  
-   Criar um formulário para exibir dados no novo controle.  
  
## <a name="prerequisites"></a>Pré-requisitos  
Este passo a passo usa o SQL Server Express LocalDB e o banco de dados de exemplo Northwind.  
  
1.  Se você não tiver o SQL Server Express LocalDB, instale-o do [página de download de edições do SQL Server](https://www.microsoft.com/en-us/server-cloud/Products/sql-server-editions/sql-server-express.aspx), ou por meio de **instalador do Visual Studio**. No instalador do Visual Studio, o SQL Server Express LocalDB pode ser instalado como parte do **armazenamento de dados e processamento** carga de trabalho, ou como um componente individual.  
  
2.  Instale o banco de dados de exemplo Northwind seguindo estas etapas:  

    1. No Visual Studio, abra o **Pesquisador de objetos do SQL Server** janela. (Pesquisador de objetos do SQL Server é instalado como parte do **armazenamento de dados e processamento** carga de trabalho em que o instalador do Visual Studio.) Expanda o **do SQL Server** nó. Clique com botão direito em sua instância de LocalDB e selecione **nova consulta...** .  

       Abre uma janela do editor de consultas.  

    2. Copie o [script Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) para sua área de transferência. Este script T-SQL cria o banco de dados Northwind desde o início e a preenche com dados.  

    3. Cole o script T-SQL no editor de consultas e, em seguida, escolha o **Execute** botão.  

       Após um curto período de tempo, a consulta termina de ser executado e o banco de dados Northwind é criado.  
  
## <a name="create-a-windows-forms-application"></a>Criar um aplicativo do Windows Forms  
 A primeira etapa é criar um **aplicativo do Windows Forms**.  
  
#### <a name="to-create-the-new-windows-project"></a>Para criar o novo projeto do Windows  
  
1. No Visual Studio, no **arquivo** menu, selecione **novo**, **projeto...** .  
  
2. Expanda **Visual C#** ou **Visual Basic** no painel esquerdo, selecione **área de trabalho clássica do Windows**.  

3. No painel central, selecione a **aplicativo do Windows Forms** tipo de projeto.  

4. Nomeie o projeto **LookupControlWalkthrough**e, em seguida, escolha **Okey**. 
  
     O **LookupControlWalkthrough** projeto é criado e adicionado ao **Gerenciador de soluções**.  
  
## <a name="add-a-user-control-to-the-project"></a>Adicionar um controle de usuário ao projeto  
 Este passo a passo cria um controle de pesquisa de um **controle de usuário**, para adicionar um **controle de usuário** item para o **LookupControlWalkthrough** projeto.  
  
#### <a name="to-add-a-user-control-to-the-project"></a>Para adicionar um controle de usuário ao projeto  
  
1.  Do **projeto** menu, selecione **adicionar controle de usuário**.  
  
2.  Tipo `LookupBox` no **nome** área e clique **adicionar**.  
  
     O **LookupBox** controle for adicionado ao **Solution Explorer**e é aberto no designer.  
  
## <a name="design-the-lookupbox-control"></a>Criar o controle LookupBox  
  
#### <a name="to-design-the-lookupbox-control"></a>Para projetar o controle LookupBox  
  
-   Arraste um <xref:System.Windows.Forms.ComboBox> do **caixa de ferramentas** na superfície de design do controle de usuário.  
  
## <a name="add-the-required-data-binding-attribute"></a>Adicione o atributo de associação de dados necessário  
 Para controles de pesquisa que suportam associação de dados, você pode implementar o <xref:System.ComponentModel.LookupBindingPropertiesAttribute>.  
  
#### <a name="to-implement-the-lookupbindingproperties-attribute"></a>Para implementar o atributo LookupBindingProperties  
  
1.  Opção de **LookupBox** controle a exibição de código. (No **exibição** menu, escolha **código**.)  
  
2.  Substitua o código no `LookupBox` pelo seguinte:  
  
     [!code-vb[VbRaddataDisplaying#5](../data-tools/codesnippet/VisualBasic/create-a-windows-forms-user-control-that-supports-lookup-data-binding_1.vb)]
     [!code-csharp[VbRaddataDisplaying#5](../data-tools/codesnippet/CSharp/create-a-windows-forms-user-control-that-supports-lookup-data-binding_1.cs)]  
  
3.  No menu **Compilação**, escolha **Compilar Solução**.  
  
## <a name="create-a-data-source-from-your-database"></a>Criar uma fonte de dados do banco de dados  
Essa etapa cria uma fonte de dados usando o **configuração da fonte de dados**assistente, com base no `Customers` e `Orders` tabelas no banco de dados de exemplo Northwind.  
  
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
  
8.  Selecione o `Customers` e `Orders` tabelas e depois clique em **concluir**.  
  
     O **NorthwindDataSet** é adicionado ao seu projeto e o `Customers` e `Orders` as tabelas aparecem no **fontes de dados** janela.  
  
## <a name="set-the-customerid-column-of-the-orders-table-to-use-the-lookupbox-control"></a>Definir a coluna CustomerID da tabela Orders para usar o controle LookupBox  
 Dentro de **fontes de dados** janela, você pode definir o controle a ser criado antes de arrastar itens para seu formulário.  
  
#### <a name="to-set-the-customerid-column-to-bind-to-the-lookupbox-control"></a>Para definir a coluna CustomerID para se associar ao controle LookupBox  
  
1.  Abra **Form1** no designer.  
  
2.  Expanda o **clientes** nó o **fontes de dados** janela.  
  
3.  Expanda o **pedidos** nó (à **clientes** abaixo do nó a **Fax** coluna).  
  
4.  Clique na seta suspensa no **pedidos** nó e escolha **detalhes** na lista de controle.  
  
5.  Clique na seta suspensa no **CustomerID** coluna (no **pedidos** nó) e escolha **personalizar**.  
  
6.  Selecione o **LookupBox** da lista de **controles associados** no **opções de personalização da interface do usuário de dados** caixa de diálogo.  
  
7.  Clique em **OK**.  
  
8.  Clique na seta suspensa no **CustomerID** coluna e escolha **LookupBox**.  
  
## <a name="add-controls-to-the-form"></a>Adicionar controles ao formulário  
 Você pode criar os controles associados a dados, arrastando itens a partir de **fontes de dados** janela para **Form1**.  
  
#### <a name="to-create-data-bound-controls-on-the-windows-form"></a>Para criar controles de associação de dados no Windows Form  
  
-   Arraste o **pedidos** nó do **fontes de dados** janela para o formulário do Windows e verifique o **LookupBox** controle é usado para exibir os dados a `CustomerID` coluna.  
  
## <a name="bind-the-control-to-look-up-companyname-from-the-customers-table"></a>Associar o controle para pesquisar CompanyName da tabela de clientes  
  
#### <a name="to-setup-the-lookup-bindings"></a>Para configurar associações de pesquisa  
  
-   Selecione principal **clientes** nó o **fontes de dados** janela e arraste-a para a caixa de combinação caixa o **CustomerIDLookupBox** na **Form1** .  
  
     Isso configura a associação de dados para exibir o `CompanyName` do `Customers` tabela, mantendo o `CustomerID` valor o `Orders` tabela.  
  
## <a name="running-the-application"></a>Executando o aplicativo  
  
#### <a name="to-run-the-application"></a>Para executar o aplicativo  
  
-   Pressione F5 para executar o aplicativo.  
  
-   Navegue em alguns registros e verifique o `CompanyName` aparece no `LookupBox` controle.  
  
## <a name="see-also"></a>Consulte também  
 [Associando controles do Windows Forms a dados no Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
