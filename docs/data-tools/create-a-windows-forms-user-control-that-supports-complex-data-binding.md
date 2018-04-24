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
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 0b7431ca6f0d4ac73a07a51893fd0c17c4fada57
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/19/2018
---
# <a name="create-a-windows-forms-user-control-that-supports-complex-data-binding"></a>Criar um controle de usuário do Windows Forms que dá suporte à associação de dados complexos

Ao exibir dados em formulários em aplicativos do Windows, você pode escolher os controles existentes da **caixa de ferramentas**, ou você pode criar controles personalizados se seu aplicativo requer uma funcionalidade que não está disponível nos controles padrão. Este passo a passo mostra como criar um controle que implementa o <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>. Os controles que implementam o <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> contêm uma propriedade de `DataSource` e `DataMember` que pode ser associada a dados. Tais controles são semelhantes a um <xref:System.Windows.Forms.DataGridView> ou <xref:System.Windows.Forms.ListBox>.

Para obter mais informações sobre criação de controle, consulte [desenvolvendo controles dos Windows Forms em tempo de Design](/dotnet/framework/winforms/controls/developing-windows-forms-controls-at-design-time).

Ao criar controles para uso em cenários de associação de dados, você precisa implementar um dos seguintes atributos de associação de dados:

|Uso do atributo de associação de dados|
|-----------------------------------|
|Implemente o <xref:System.ComponentModel.DefaultBindingPropertyAttribute> em controles simples, como um <xref:System.Windows.Forms.TextBox>, que exibe uma única coluna (ou propriedade) de dados. Para obter mais informações, consulte [criar um controle de usuário do Windows Forms que dá suporte à associação de dados simples](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).|
|Implemente o <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> nos controles, como um <xref:System.Windows.Forms.DataGridView> que exibe listas (ou tabelas) de dados. (Esse processo é descrito nesta página de passo a passo.)|
|Implemente o <xref:System.ComponentModel.LookupBindingPropertiesAttribute> nos controles, como um <xref:System.Windows.Forms.ComboBox>que exibe listas (ou tabelas) de dados, mas também precisa apresentar uma única coluna ou propriedade. Para obter mais informações, consulte [criar um controle de usuário do Windows Forms que dá suporte à associação de dados de pesquisa](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).|

 Este passo a passo cria um controle complexo que exibe linhas de dados de uma tabela. Este exemplo usa a tabela `Customers` do banco de dados de exemplo Northwind. O controle de usuário complexo exibirá a tabela de clientes em uma <xref:System.Windows.Forms.DataGridView> no controle personalizado.

Durante este passo a passo, você aprenderá a:

- Criar um novo **aplicativo do Windows Forms**.

- Adicionar um novo **controle de usuário** ao seu projeto.

- Projetar visualmente o controle do usuário.

- Implementar o atributo `ComplexBindingProperty`.

- Criar um conjunto de dados com o [Assistente de configuração de fonte de dados](../data-tools/media/data-source-configuration-wizard.png).

- Definir o **clientes** tabela o [janela fontes de dados](add-new-data-sources.md) para usar o novo controle complexo.

- Adicione o novo controle, arrastando-o do **janela fontes de dados** para **Form1**.

## <a name="prerequisites"></a>Pré-requisitos

Este passo a passo usa o SQL Server Express LocalDB e o banco de dados de exemplo Northwind.

1. Se você não tiver o SQL Server Express LocalDB, instale-o do [página de download do SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), ou por meio de **instalador do Visual Studio**. No instalador do Visual Studio, o SQL Server Express LocalDB pode ser instalado como parte do **armazenamento de dados e processamento** carga de trabalho, ou como um componente individual.

1. Instale o banco de dados de exemplo Northwind seguindo estas etapas:

    1. No Visual Studio, abra o **Pesquisador de objetos do SQL Server** janela. (Pesquisador de objetos do SQL Server é instalado como parte do **armazenamento de dados e processamento** carga de trabalho em que o instalador do Visual Studio.) Expanda o **do SQL Server** nó. Clique com botão direito em sua instância de LocalDB e selecione **nova consulta...** .

       Abre uma janela do editor de consultas.

    1. Copie o [script Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) para sua área de transferência. Este script T-SQL cria o banco de dados Northwind desde o início e a preenche com dados.

    1. Cole o script T-SQL no editor de consultas e, em seguida, escolha o **Execute** botão.

       Após um curto período de tempo, a consulta termina de ser executado e o banco de dados Northwind é criado.

## <a name="create-a-windows-forms-application"></a>Criar um aplicativo Windows Forms

 A primeira etapa é criar um **aplicativo do Windows Forms**.

### <a name="to-create-the-new-windows-project"></a>Para criar o novo projeto do Windows

1. No Visual Studio, no **arquivo** menu, selecione **novo**, **projeto...** .

1. Expanda **Visual C#** ou **Visual Basic** no painel esquerdo, selecione **área de trabalho clássica do Windows**.

1. No painel central, selecione a **aplicativo do Windows Forms** tipo de projeto.

1. Nomeie o projeto **ComplexControlWalkthrough**e, em seguida, escolha **Okey**.

    O **ComplexControlWalkthrough** projeto é criado e adicionado ao **Gerenciador de soluções**.

## <a name="add-a-user-control-to-the-project"></a>Adicionar um controle de usuário ao projeto

Como este passo a passo cria um controle complexo de ligação de dados de um **controle de usuário**, você deve adicionar um **controle de usuário** item ao projeto.

### <a name="to-add-a-user-control-to-the-project"></a>Para adicionar um controle de usuário ao projeto

1. Do **projeto** menu, escolha **adicionar controle de usuário**.

1. Tipo **ComplexDataGridView** no **nome** área e clique **adicionar**.

    O **ComplexDataGridView** controle for adicionado ao **Solution Explorer**e é aberto no designer.

## <a name="design-the-complexdatagridview-control"></a>Criar o controle ComplexDataGridView

Esta etapa adiciona um <xref:System.Windows.Forms.DataGridView> ao controle de usuário.

### <a name="to-design-the-complexdatagridview-control"></a>Para projetar o controle ComplexDataGridView

- Arraste um <xref:System.Windows.Forms.DataGridView> do **caixa de ferramentas** na superfície de design do controle de usuário.

## <a name="add-the-required-data-binding-attribute"></a>Adicione o atributo de associação de dados necessário

Para controles complexos que suportam associação de dados, você pode implementar o <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>.

### <a name="to-implement-the-complexbindingproperties-attribute"></a>Para implementar o atributo ComplexBindingProperties

1. Opção de **ComplexDataGridView** controle a exibição de código. (No **exibição** menu, selecione **código**.)

1. Substitua o código no `ComplexDataGridView` pelo seguinte:

    [!code-csharp[VbRaddataDisplaying#4](../data-tools/codesnippet/CSharp/create-a-windows-forms-user-control-that-supports-complex-data-binding_1.cs)]
    [!code-vb[VbRaddataDisplaying#4](../data-tools/codesnippet/VisualBasic/create-a-windows-forms-user-control-that-supports-complex-data-binding_1.vb)]

1. No menu **Compilação**, escolha **Compilar Solução**.

## <a name="creating-a-data-source-from-your-database"></a>Criar uma fonte de dados do banco de dados

Esta etapa usa a **configuração da fonte de dados** Assistente para criar uma fonte de dados com base no `Customers` tabela no banco de dados de exemplo Northwind.

### <a name="to-create-the-data-source"></a>Para criar a fonte de dados

1.  Sobre o **dados** menu, clique em **Mostrar fontes de dados**.

2.  No **fontes de dados** janela, selecione **adicionar nova fonte de dados** para iniciar o **configuração da fonte de dados** assistente.

3.  Selecione **banco de dados** no **escolher um tipo de fonte de dados** página e, em seguida, clique em **próximo**.

4.  Sobre o **escolha sua Conexão de dados** página faça o seguinte:

    - Se uma conexão de dados com o banco de dados de exemplo Northwind estiver disponível na lista suspensa, selecione-o.

    - Selecione **nova Conexão** para iniciar o **Adicionar/Modificar Conexão** caixa de diálogo.

5.  Se seu banco de dados exigir uma senha, selecione a opção para incluir dados confidenciais e, em seguida, clique em **próximo**.

6.  No **salvar a cadeia de caracteres de conexão para o arquivo de configuração de aplicativo** , clique em **próximo**.

7.  Sobre o **escolher seus objetos de banco de dados** página, expanda o **tabelas** nó.

8.  Selecione o `Customers` de tabela e, em seguida, clique em **concluir**.

    O **NorthwindDataSet** é adicionado ao seu projeto e o `Customers` tabela aparece no **fontes de dados** janela.

## <a name="set-the-customers-table-to-use-the-complexdatagridview-control"></a>Definir a tabela de clientes para usar o controle ComplexDataGridView

Dentro de **fontes de dados** janela, você pode definir o controle a ser criado antes de arrastar itens para seu formulário.

### <a name="to-set-the-customers-table-to-bind-to-the-complexdatagridview-control"></a>Para configurar a coluna Clientes para se associar ao controle ComplexDataGridView

1. Abra **Form1** no designer.

1. Expanda o **clientes** nó o **fontes de dados** janela.

1. Clique na seta suspensa no **clientes** nó e escolha **personalizar**.

1. Selecione o **ComplexDataGridView** da lista de **controles associados** no **opções de personalização da interface do usuário de dados** caixa de diálogo.

1. Clique na seta suspensa no `Customers` da tabela e escolha **ComplexDataGridView** na lista de controle.

## <a name="add-controls-to-the-form"></a>Adicionar controles ao formulário

Você pode criar os controles associados a dados, arrastando itens a partir de **fontes de dados** window para seu formulário.

### <a name="to-create-data-bound-controls-on-the-form"></a>Para criar controles de associação de dados no formulário

Arraste principal **clientes** nó a partir de **fontes de dados** janela para o formulário. Verifique o **ComplexDataGridView** controle é usado para exibir os dados da tabela.

## <a name="running-the-application"></a>Executando o aplicativo

### <a name="to-run-the-application"></a>Para executar o aplicativo

Pressione F5 para executar o aplicativo.

## <a name="next-steps"></a>Próximas etapas

Dependendo dos requisitos do aplicativo, existem várias etapas que você pode realizar após criar um controle com suporte a associação de dados. Algumas etapas seguintes típicas incluem:

- Colocando os controles personalizados em uma biblioteca de controles para que você possa reutilizá-los em outros aplicativos.

- Criando controles que suportam cenários de pesquisa. Para obter mais informações, consulte [criar um controle de usuário do Windows Forms que dá suporte à associação de dados de pesquisa](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).

## <a name="see-also"></a>Consulte também

- [Associando controles do Windows Forms a dados no Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Definir o controle a ser criado quando arrastado da janela Fontes de Dados](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)
- [Controles dos Windows Forms](/dotnet/framework/winforms/controls/index)