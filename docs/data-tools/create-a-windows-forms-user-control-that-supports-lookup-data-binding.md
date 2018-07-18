---
title: Usar tabelas de pesquisa na associação de dados - controles dos Windows Forms | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data binding, user controls
- LookupBindingPropertiesAttribute class, examples
- user controls [Visual Basic], creating
ms.assetid: c48b4d75-ccfc-4950-8b14-ff8adbfe4208
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: e79d4ba6db70876539aa2e85f0579953937cab14
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36756318"
---
# <a name="create-a-windows-forms-user-control-that-supports-lookup-data-binding"></a>Criar um controle de usuário do Windows Forms que dá suporte à vinculação de dados de pesquisa
Ao exibir dados nos Windows Forms, você pode escolher os controles existentes dos **caixa de ferramentas**, ou você pode criar controles personalizados se seu aplicativo requer funcionalidade não está disponível nos controles padrão. Este passo a passo mostra como criar um controle que implementa o <xref:System.ComponentModel.LookupBindingPropertiesAttribute>. Os controles que implementam o <xref:System.ComponentModel.LookupBindingPropertiesAttribute> contêm três propriedade que podem ser associadas a dados. Tais controles são semelhantes a um <xref:System.Windows.Forms.ComboBox>.

 Para obter mais informações sobre criação de controle, consulte [controla o desenvolvimento de Windows Forms em tempo de design](/dotnet/framework/winforms/controls/developing-windows-forms-controls-at-design-time).

 Ao criar controles para uso em cenários de associação de dados, é necessário implementar um dos seguintes atributos de associação de dados:

|Uso do atributo de associação de dados|
|-----------------------------------|
|Implemente o <xref:System.ComponentModel.DefaultBindingPropertyAttribute> em controles simples, como um <xref:System.Windows.Forms.TextBox>, que exibe uma única coluna (ou propriedade) de dados. Para obter mais informações, consulte [criar um controle de usuário do Windows Forms que dá suporte à vinculação de dados simples](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).|
|Implemente o <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> nos controles, como um <xref:System.Windows.Forms.DataGridView> que exibe listas (ou tabelas) de dados. Para obter mais informações, consulte [criar um controle de usuário do Windows Forms que dá suporte à vinculação de dados complexos](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).|
|Implemente o <xref:System.ComponentModel.LookupBindingPropertiesAttribute> nos controles, como um <xref:System.Windows.Forms.ComboBox>que exibe listas (ou tabelas) de dados, mas também precisa apresentar uma única coluna ou propriedade. (Esse processo é descrito nesta página de passo a passo.)|

 Este passo a passo cria um controle de pesquisa que se associa aos dados de duas tabelas. Este exemplo usa as tabelas `Customers` e `Orders` do banco de dados de exemplo Northwind. O controle de pesquisa está associado para o `CustomerID` campo o `Orders` tabela. Ele usa esse valor para pesquisar o `CompanyName` do `Customers` tabela.

 Durante este passo a passo, você aprenderá a:

-   Criar um novo **aplicativo do Windows Forms**.

-   Adicione um novo **controle de usuário** ao seu projeto.

-   Projetar visualmente o controle do usuário.

-   Implementar o atributo `LookupBindingProperty`.

-   Criar um conjunto de dados com o **configuração de fonte de dados** assistente.

-   Definir a **CustomerID** coluna sobre o **pedidos** tabela, o **fontes de dados** janela, para usar o novo controle.

-   Criar um formulário para exibir dados no novo controle.

## <a name="prerequisites"></a>Pré-requisitos

Este passo a passo usa o SQL Server Express LocalDB e o banco de dados de exemplo Northwind.

1.  Se você não tiver o SQL Server Express LocalDB, instalá-lo a partir de [página de download do SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), ou por meio de **instalador do Visual Studio**. No **instalador do Visual Studio**, você pode instalar o SQL Server Express LocalDB como parte do **armazenamento de dados e processamento** carga de trabalho, ou como um componente individual.

2.  Instale o banco de dados de exemplo Northwind, seguindo estas etapas:

    1. No Visual Studio, abra o **SQL Server Object Explorer** janela. (Pesquisador de objetos do SQL Server é instalado como parte dos **armazenamento de dados e processamento** carga de trabalho no instalador do Visual Studio.) Expanda o **SQL Server** nó. Clique com botão direito na instância do LocalDB e selecione **nova consulta**.

       Abre uma janela do editor de consulta.

    2. Cópia de [script Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) na área de transferência. Este script T-SQL cria o banco de dados Northwind do zero e a preenche com dados.

    3. Cole o script T-SQL no editor de consultas e, em seguida, escolha o **Execute** botão.

       Após alguns instantes, a consulta termina a execução e o banco de dados Northwind é criado.

## <a name="create-a-windows-forms-application"></a>Criar um aplicativo do Windows Forms
 A primeira etapa é criar uma **aplicativo do Windows Forms**.

#### <a name="to-create-the-new-windows-project"></a>Para criar o novo projeto do Windows

1. No Visual Studio, sobre o **arquivo** menu, selecione **New** > **projeto**.

2. Expanda o **Visual c#** ou **Visual Basic** no painel esquerdo, em seguida, selecione **área de trabalho do Windows**.

3. No painel central, selecione a **aplicativo do Windows Forms** tipo de projeto.

4. Nomeie o projeto **LookupControlWalkthrough**e, em seguida, escolha **Okey**.

     O **LookupControlWalkthrough** projeto é criado e adicionado ao **Gerenciador de soluções**.

## <a name="add-a-user-control-to-the-project"></a>Adicionar um controle de usuário ao projeto
 Este passo a passo cria um controle de pesquisa de um **controle de usuário**, então, adicione uma **controle de usuário** de item para o **LookupControlWalkthrough** projeto.

#### <a name="to-add-a-user-control-to-the-project"></a>Para adicionar um controle de usuário ao projeto

1.  Dos **Project** menu, selecione **Add User Control**.

2.  Tipo de `LookupBox` no **nome** área e depois clique em **Add**.

     O **LookupBox** controle é adicionado à **Gerenciador de soluções**e o abre no designer.

## <a name="design-the-lookupbox-control"></a>Criar o controle LookupBox

#### <a name="to-design-the-lookupbox-control"></a>Para projetar o controle LookupBox

-   Arraste uma <xref:System.Windows.Forms.ComboBox> do **caixa de ferramentas** na superfície de design do controle de usuário.

## <a name="add-the-required-data-binding-attribute"></a>Adicione o atributo obrigatório de associação de dados
 Para controles de pesquisa que suportam associação de dados, você pode implementar o <xref:System.ComponentModel.LookupBindingPropertiesAttribute>.

#### <a name="to-implement-the-lookupbindingproperties-attribute"></a>Para implementar o atributo LookupBindingProperties

1.  Opção de **LookupBox** controle a exibição de código. (Sobre o **modo de exibição** menu, escolha **código**.)

2.  Substitua o código no `LookupBox` pelo seguinte:

     [!code-vb[VbRaddataDisplaying#5](../data-tools/codesnippet/VisualBasic/create-a-windows-forms-user-control-that-supports-lookup-data-binding_1.vb)]
     [!code-csharp[VbRaddataDisplaying#5](../data-tools/codesnippet/CSharp/create-a-windows-forms-user-control-that-supports-lookup-data-binding_1.cs)]

3.  No menu **Compilação**, escolha **Compilar Solução**.

## <a name="create-a-data-source-from-your-database"></a>Criar uma fonte de dados do banco de dados
Esta etapa cria uma fonte de dados usando o **Data Source Configuration** assistente, com base nas `Customers` e `Orders` tabelas no banco de dados de exemplo Northwind.

#### <a name="to-create-the-data-source"></a>Para criar a fonte de dados

1.  Sobre o **dados** menu, clique em **Show Data Sources**.

2.  No **fontes de dados** janela, selecione **Add New Data Source** para iniciar o **configuração de fonte de dados** assistente.

3.  Selecione **banco de dados** sobre o **escolher um tipo de fonte de dados** página e, em seguida, clique em **próxima**.

4.  Sobre o **escolha sua Conexão de dados** página faça o seguinte:

    -   Se uma conexão de dados com o banco de dados de exemplo Northwind estiver disponível na lista suspensa, selecione-o.

    -   Selecione **nova Conexão** para iniciar o **Adicionar/Modificar Conexão** caixa de diálogo.

5.  Se seu banco de dados exigir uma senha, selecione a opção para incluir dados confidenciais e, em seguida, clique em **próxima**.

6.  Sobre o **salvar a cadeia de caracteres de conexão para o arquivo de configuração de aplicativo** , clique em **próxima**.

7.  Sobre o **Choose your Database Objects** página, expanda o **tabelas** nó.

8.  Selecione o `Customers` e `Orders` tabelas e clique **concluir**.

     O **NorthwindDataSet** é adicionado ao seu projeto e o `Customers` e `Orders` as tabelas aparecem no **fontes de dados** janela.

## <a name="set-the-customerid-column-of-the-orders-table-to-use-the-lookupbox-control"></a>Definir a coluna CustomerID da tabela Orders para usar o controle LookupBox
 Dentro de **fontes de dados** janela, você pode definir o controle a ser criado antes de arrastar itens para seu formulário.

#### <a name="to-set-the-customerid-column-to-bind-to-the-lookupbox-control"></a>Para definir a coluna CustomerID para se associar ao controle LookupBox

1.  Abra **Form1** no designer.

2.  Expanda o **clientes** nó na **fontes de dados** janela.

3.  Expanda o **pedidos** nó (na **clientes** abaixo do nó de **Fax** coluna).

4.  Clique na seta suspensa na **pedidos** nó e escolha **detalhes** na lista de controle.

5.  Clique na seta suspensa na **CustomerID** coluna (na **pedidos** nó) e escolha **personalizar**.

6.  Selecione o **LookupBox** na lista de **controles associados** no **opções de personalização da interface do usuário de dados** caixa de diálogo.

7.  Clique em **OK**.

8.  Clique na seta suspensa na **CustomerID** coluna e escolha **LookupBox**.

## <a name="add-controls-to-the-form"></a>Adicionar controles ao formulário
 Você pode criar os controles ligados a dados arrastando itens dos **fontes de dados** window para **Form1**.

#### <a name="to-create-data-bound-controls-on-the-windows-form"></a>Para criar controles de associação de dados no Windows Form

-   Arraste o **pedidos** nó a partir o **fontes de dados** janela para o formulário do Windows e verificar se o **LookupBox** controle é usado para exibir os dados no `CustomerID` coluna.

## <a name="bind-the-control-to-look-up-companyname-from-the-customers-table"></a>Associar o controle para pesquisar o CompanyName da tabela Customers

#### <a name="to-setup-the-lookup-bindings"></a>Para configurar associações de pesquisa

-   Selecione principal **clientes** nó na **fontes de dados** janela e arraste-a para a caixa de combinação caixa a **CustomerIDLookupBox** na **Form1** .

     Isso configura a vinculação de dados para exibir o `CompanyName` do `Customers` tabela, enquanto mantém a `CustomerID` valor da `Orders` tabela.

## <a name="running-the-application"></a>Executando o aplicativo

#### <a name="to-run-the-application"></a>Para executar o aplicativo

-   Pressione **F5** para executar o aplicativo.

-   Navegue por alguns registros e verifique se que o `CompanyName` aparece no `LookupBox` controle.

## <a name="see-also"></a>Consulte também

- [Associando controles do Windows Forms a dados no Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)