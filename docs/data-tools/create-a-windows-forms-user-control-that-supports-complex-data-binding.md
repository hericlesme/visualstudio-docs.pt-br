---
title: Criar um controle de usuário do Windows Forms com associação de dados
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data binding, user controls
- data binding, complex
- user controls [Visual Studio], complex data binding
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: b0189682576c495d031cf160261e16fd920a1615
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36758375"
---
# <a name="create-a-windows-forms-user-control-that-supports-complex-data-binding"></a>Criar um controle de usuário do Windows Forms que dá suporte à vinculação de dados complexos

Ao exibir dados em formulários em aplicativos do Windows, você pode escolher os controles existentes dos **caixa de ferramentas**, ou você pode criar controles personalizados se seu aplicativo requer funcionalidade que não está disponível nos controles padrão. Este passo a passo mostra como criar um controle que implementa o <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>. Os controles que implementam o <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> contêm uma propriedade de `DataSource` e `DataMember` que pode ser associada a dados. Tais controles são semelhantes a um <xref:System.Windows.Forms.DataGridView> ou <xref:System.Windows.Forms.ListBox>.

Para obter mais informações sobre criação de controle, consulte [controla o desenvolvimento de Windows Forms em tempo de design](/dotnet/framework/winforms/controls/developing-windows-forms-controls-at-design-time).

Ao criar controles para uso em cenários de vinculação de dados, você precisa implementar um dos seguintes atributos de associação de dados:

|Uso do atributo de associação de dados|
|-----------------------------------|
|Implemente o <xref:System.ComponentModel.DefaultBindingPropertyAttribute> em controles simples, como um <xref:System.Windows.Forms.TextBox>, que exibe uma única coluna (ou propriedade) de dados. Para obter mais informações, consulte [criar um controle de usuário do Windows Forms que dá suporte à vinculação de dados simples](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).|
|Implemente o <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> nos controles, como um <xref:System.Windows.Forms.DataGridView> que exibe listas (ou tabelas) de dados. (Esse processo é descrito nesta página de passo a passo.)|
|Implemente o <xref:System.ComponentModel.LookupBindingPropertiesAttribute> nos controles, como um <xref:System.Windows.Forms.ComboBox>que exibe listas (ou tabelas) de dados, mas também precisa apresentar uma única coluna ou propriedade. Para obter mais informações, consulte [criar um controle de usuário do Windows Forms que dá suporte à vinculação de dados de pesquisa](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).|

 Este passo a passo cria um controle complexo que exibe linhas de dados de uma tabela. Este exemplo usa a tabela `Customers` do banco de dados de exemplo Northwind. O controle de usuário complexo exibirá a tabela de clientes em uma <xref:System.Windows.Forms.DataGridView> no controle personalizado.

Durante este passo a passo, você aprenderá a:

- Criar um novo **aplicativo do Windows Forms**.

- Adicione um novo **controle de usuário** ao seu projeto.

- Projetar visualmente o controle do usuário.

- Implementar o atributo `ComplexBindingProperty`.

- Criar um conjunto de dados com o [Data Source Configuration Wizard](../data-tools/media/data-source-configuration-wizard.png).

- Defina as **clientes** na tabela a [janela fontes de dados](add-new-data-sources.md) para usar o novo controle complexo.

- Adicione o novo controle, arrastando-o do **janela fontes de dados** até **Form1**.

## <a name="prerequisites"></a>Pré-requisitos

Este passo a passo usa o SQL Server Express LocalDB e o banco de dados de exemplo Northwind.

1. Se você não tiver o SQL Server Express LocalDB, instalá-lo a partir de [página de download do SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), ou por meio de **instalador do Visual Studio**. No **instalador do Visual Studio**, você pode instalar o SQL Server Express LocalDB como parte do **armazenamento de dados e processamento** carga de trabalho, ou como um componente individual.

1. Instale o banco de dados de exemplo Northwind, seguindo estas etapas:

    1. No Visual Studio, abra o **SQL Server Object Explorer** janela. (Pesquisador de objetos do SQL Server é instalado como parte dos **armazenamento de dados e processamento** carga de trabalho no instalador do Visual Studio.) Expanda o **SQL Server** nó. Clique com botão direito na instância do LocalDB e selecione **nova consulta**.

       Abre uma janela do editor de consulta.

    1. Cópia de [script Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) na área de transferência. Este script T-SQL cria o banco de dados Northwind do zero e a preenche com dados.

    1. Cole o script T-SQL no editor de consultas e, em seguida, escolha o **Execute** botão.

       Após alguns instantes, a consulta termina a execução e o banco de dados Northwind é criado.

## <a name="create-a-windows-forms-application"></a>Criar um aplicativo Windows Forms

 A primeira etapa é criar uma **aplicativo do Windows Forms**.

### <a name="to-create-the-new-windows-project"></a>Para criar o novo projeto do Windows

1. No Visual Studio, sobre o **arquivo** menu, selecione **New** > **projeto**.

1. Expanda o **Visual c#** ou **Visual Basic** no painel esquerdo, em seguida, selecione **área de trabalho do Windows**.

1. No painel central, selecione a **aplicativo do Windows Forms** tipo de projeto.

1. Nomeie o projeto **ComplexControlWalkthrough**e, em seguida, escolha **Okey**.

    O **ComplexControlWalkthrough** projeto é criado e adicionado ao **Gerenciador de soluções**.

## <a name="add-a-user-control-to-the-project"></a>Adicionar um controle de usuário ao projeto

Porque este passo a passo cria um controle associável a dados complexo de um **controle de usuário**, você deve adicionar uma **controle de usuário** item ao projeto.

### <a name="to-add-a-user-control-to-the-project"></a>Para adicionar um controle de usuário ao projeto

1. Dos **Project** menu, escolha **adicionar controle de usuário**.

1. Tipo de **ComplexDataGridView** na **nome** área e clique **adicionar**.

    O **ComplexDataGridView** controle é adicionado à **Gerenciador de soluções**e o abre no designer.

## <a name="design-the-complexdatagridview-control"></a>Criar o controle ComplexDataGridView

Esta etapa adiciona um <xref:System.Windows.Forms.DataGridView> ao controle de usuário.

### <a name="to-design-the-complexdatagridview-control"></a>Para projetar o controle ComplexDataGridView

- Arraste uma <xref:System.Windows.Forms.DataGridView> do **caixa de ferramentas** na superfície de design do controle de usuário.

## <a name="add-the-required-data-binding-attribute"></a>Adicione o atributo obrigatório de associação de dados

Para controles complexos que suportam associação de dados, você pode implementar o <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>.

### <a name="to-implement-the-complexbindingproperties-attribute"></a>Para implementar o atributo ComplexBindingProperties

1. Opção de **ComplexDataGridView** controle a exibição de código. (Sobre o **modo de exibição** menu, selecione **código**.)

1. Substitua o código no `ComplexDataGridView` pelo seguinte:

    [!code-csharp[VbRaddataDisplaying#4](../data-tools/codesnippet/CSharp/create-a-windows-forms-user-control-that-supports-complex-data-binding_1.cs)]
    [!code-vb[VbRaddataDisplaying#4](../data-tools/codesnippet/VisualBasic/create-a-windows-forms-user-control-that-supports-complex-data-binding_1.vb)]

1. No menu **Compilação**, escolha **Compilar Solução**.

## <a name="creating-a-data-source-from-your-database"></a>Criando uma fonte de dados do banco de dados

Esta etapa usa a **Data Source Configuration** Assistente para criar uma fonte de dados com base no `Customers` tabela no banco de dados de exemplo Northwind.

### <a name="to-create-the-data-source"></a>Para criar a fonte de dados

1.  Sobre o **dados** menu, clique em **Show Data Sources**.

2.  No **fontes de dados** janela, selecione **Add New Data Source** para iniciar o **configuração de fonte de dados** assistente.

3.  Selecione **banco de dados** sobre o **escolher um tipo de fonte de dados** página e, em seguida, clique em **próxima**.

4.  Sobre o **escolha sua Conexão de dados** página faça o seguinte:

    - Se uma conexão de dados com o banco de dados de exemplo Northwind estiver disponível na lista suspensa, selecione-o.

    - Selecione **nova Conexão** para iniciar o **Adicionar/Modificar Conexão** caixa de diálogo.

5.  Se seu banco de dados exigir uma senha, selecione a opção para incluir dados confidenciais e, em seguida, clique em **próxima**.

6.  Sobre o **salvar a cadeia de caracteres de conexão para o arquivo de configuração de aplicativo** , clique em **próxima**.

7.  Sobre o **Choose your Database Objects** página, expanda o **tabelas** nó.

8.  Selecione o `Customers` de tabela e, em seguida, clique em **concluir**.

    O **NorthwindDataSet** é adicionado ao seu projeto e o `Customers` tabela aparece no **fontes de dados** janela.

## <a name="set-the-customers-table-to-use-the-complexdatagridview-control"></a>Definir a tabela de clientes para usar o controle ComplexDataGridView

Dentro de **fontes de dados** janela, você pode definir o controle a ser criado antes de arrastar itens para seu formulário.

### <a name="to-set-the-customers-table-to-bind-to-the-complexdatagridview-control"></a>Para configurar a coluna Clientes para se associar ao controle ComplexDataGridView

1. Abra **Form1** no designer.

1. Expanda o **clientes** nó na **fontes de dados** janela.

1. Clique na seta suspensa na **clientes** nó e escolha **personalizar**.

1. Selecione o **ComplexDataGridView** na lista de **controles associados** no **opções de personalização da interface do usuário de dados** caixa de diálogo.

1. Clique na seta suspensa na `Customers` da tabela e escolha **ComplexDataGridView** na lista de controle.

## <a name="add-controls-to-the-form"></a>Adicionar controles ao formulário

Você pode criar os controles ligados a dados arrastando itens dos **fontes de dados** window para seu formulário.

### <a name="to-create-data-bound-controls-on-the-form"></a>Para criar controles de associação de dados no formulário

Arraste principal **clientes** nó a partir do **fontes de dados** janela para o formulário. Verifique se que o **ComplexDataGridView** controle é usado para exibir os dados da tabela.

## <a name="running-the-application"></a>Executando o aplicativo

### <a name="to-run-the-application"></a>Para executar o aplicativo

Pressione **F5** para executar o aplicativo.

## <a name="next-steps"></a>Próximas etapas

Dependendo dos requisitos do aplicativo, existem várias etapas que você pode realizar após criar um controle com suporte a associação de dados. Algumas etapas seguintes típicas incluem:

- Colocando os controles personalizados em uma biblioteca de controles para que você possa reutilizá-los em outros aplicativos.

- Criando controles que suportam cenários de pesquisa. Para obter mais informações, consulte [criar um controle de usuário do Windows Forms que dá suporte à vinculação de dados de pesquisa](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).

## <a name="see-also"></a>Consulte também

- [Associando controles do Windows Forms a dados no Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Definir o controle a ser criado quando arrastado da janela Fontes de Dados](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)
- [Controles dos Windows Forms](/dotnet/framework/winforms/controls/index)