---
title: Criar um controle de usuário compatível com associação de dados simples
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom controls [Visual Studio], Data Sources Window
- Data Sources Window, controls
ms.assetid: b1488366-6dfb-454e-9751-f42fd3f3ddfb
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: ab4ee8f468b3d6fa138984e17f3bbe843082e987
ms.sourcegitcommit: 3a11feebad45a0dd4ac45efcbfdf172fce46e1de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/07/2018
ms.locfileid: "39582441"
---
# <a name="create-a-windows-forms-user-control-that-supports-simple-data-binding"></a>Criar um controle de usuário do Windows Forms que dá suporte à vinculação de dados simples

Ao exibir dados em formulários em aplicativos do Windows, você pode escolher os controles existentes dos **caixa de ferramentas**, ou você pode criar controles personalizados se seu aplicativo requer funcionalidade que não está disponível nos controles padrão. Este passo a passo mostra como criar um controle que implementa o <xref:System.ComponentModel.DefaultBindingPropertyAttribute>. Os controles que implementam o <xref:System.ComponentModel.DefaultBindingPropertyAttribute> contêm uma propriedade que pode ser associada a dados. Tais controles são semelhantes a um <xref:System.Windows.Forms.TextBox> ou <xref:System.Windows.Forms.CheckBox>.

Para obter mais informações sobre criação de controle, consulte [desenvolvendo controles dos Windows Forms em tempo de Design](/dotnet/framework/winforms/controls/developing-windows-forms-controls-at-design-time).

Ao criar controles para uso em cenários de vinculação de dados, você deve implementar um dos seguintes atributos de associação de dados:

|Uso do atributo de associação de dados|
|-----------------------------------|
|Implemente o <xref:System.ComponentModel.DefaultBindingPropertyAttribute> em controles simples, como um <xref:System.Windows.Forms.TextBox>, que exibe uma única coluna (ou propriedade) de dados. (Esse processo é descrito nesta página de passo a passo.)|
|Implemente o <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> nos controles, como um <xref:System.Windows.Forms.DataGridView> que exibe listas (ou tabelas) de dados. Para obter mais informações, consulte [criar um controle de usuário do Windows Forms que dá suporte à vinculação de dados complexos](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).|
|Implemente o <xref:System.ComponentModel.LookupBindingPropertiesAttribute> nos controles, como um <xref:System.Windows.Forms.ComboBox>que exibe listas (ou tabelas) de dados, mas também precisa apresentar uma única coluna ou propriedade. Para obter mais informações, consulte [criar um controle de usuário do Windows Forms que dá suporte à vinculação de dados de pesquisa](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).|

Este passo a passo cria um controle simples que exibe dados de uma única coluna em uma tabela. Este exemplo usa a coluna `Phone` da tabela `Customers` do banco de dados de exemplo Northwind. O controle de usuário simples exibe números de telefone dos clientes em um formato de número de telefone padrão, usando um <xref:System.Windows.Forms.MaskedTextBox> e definindo a máscara para um número de telefone.

Durante este passo a passo, você aprenderá a:

-   Criar um novo **aplicativo do Windows Forms**.

-   Adicione um novo **controle de usuário** ao seu projeto.

-   Projetar visualmente o controle do usuário.

-   Implementar o atributo `DefaultBindingProperty`.

-   Criar um conjunto de dados com o **configuração de fonte de dados** assistente.

-   Definir o **telefone** coluna o **fontes de dados** janela para usar o novo controle.

-   Criar um formulário para exibir dados no novo controle.

## <a name="prerequisites"></a>Pré-requisitos

Este passo a passo usa o SQL Server Express LocalDB e o banco de dados de exemplo Northwind.

1.  Se você não tiver o SQL Server Express LocalDB, instalá-lo a partir de [página de download do SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), ou por meio de **instalador do Visual Studio**. No **instalador do Visual Studio**, você pode instalar o SQL Server Express LocalDB como parte do **armazenamento de dados e processamento** carga de trabalho, ou como um componente individual.

2.  Instale o banco de dados de exemplo Northwind, seguindo estas etapas:

    1. No Visual Studio, abra o **SQL Server Object Explorer** janela. (Pesquisador de objetos do SQL Server é instalado como parte dos **armazenamento de dados e processamento** carga de trabalho na **instalador do Visual Studio**.) Expanda o **SQL Server** nó. Clique com botão direito na instância do LocalDB e selecione **nova consulta**.

       Abre uma janela do editor de consulta.

    2. Cópia de [script Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) na área de transferência. Este script T-SQL cria o banco de dados Northwind do zero e a preenche com dados.

    3. Cole o script T-SQL no editor de consultas e, em seguida, escolha o **Execute** botão.

       Após alguns instantes, a consulta termina a execução e o banco de dados Northwind é criado.

## <a name="create-a-windows-forms-application"></a>Criar um aplicativo do Windows Forms

A primeira etapa é criar uma **aplicativo do Windows Forms**:

1. No Visual Studio, sobre o **arquivo** menu, selecione **New** > **projeto**.

2. Expanda o **Visual c#** ou **Visual Basic** no painel esquerdo, em seguida, selecione **área de trabalho do Windows**.

3. No painel central, selecione a **aplicativo do Windows Forms** tipo de projeto.

4. Nomeie o projeto **SimpleControlWalkthrough**e, em seguida, escolha **Okey**.

     O **SimpleControlWalkthrough** projeto é criado e adicionado ao **Gerenciador de soluções**.

## <a name="add-a-user-control-to-the-project"></a>Adicionar um controle de usuário ao projeto

Este passo a passo cria um simples controle associável a dados de um **controle de usuário**. Adicionar um **controle de usuário** de item para o **SimpleControlWalkthrough** projeto:

1.  Dos **Project** menu, escolha **adicionar controle de usuário**.

2.  Tipo de **PhoneNumberBox** na área nome e clique **Add**.

     O **PhoneNumberBox** controle é adicionado à **Gerenciador de soluções**e o abre no designer.

## <a name="design-the-phonenumberbox-control"></a>Projetar o controle PhoneNumberBox

Este passo a passo expande existente <xref:System.Windows.Forms.MaskedTextBox> para criar o **PhoneNumberBox** controle:

1.  Arraste uma <xref:System.Windows.Forms.MaskedTextBox> do **caixa de ferramentas** na superfície de design do controle de usuário.

2.  Selecione a marca inteligente sobre o <xref:System.Windows.Forms.MaskedTextBox> você acabou de arrastar e escolha **definir máscara**.

3.  Selecione **número de telefone** na **máscara de entrada** caixa de diálogo e clique em **Okey** para configurar a máscara.

## <a name="add-the-required-data-binding-attribute"></a>Adicione o atributo obrigatório de associação de dados

Para controles que suportam associação de dados, o simples implementar o <xref:System.ComponentModel.DefaultBindingPropertyAttribute>:

1.  Opção de **PhoneNumberBox** controle a exibição de código. (Sobre o **modo de exibição** menu, escolha **código**.)

2.  Substitua o código na **PhoneNumberBox** com o seguinte:

     [!code-csharp[VbRaddataDisplaying#3](../data-tools/codesnippet/CSharp/create-a-windows-forms-user-control-that-supports-simple-data-binding_1.cs)]
     [!code-vb[VbRaddataDisplaying#3](../data-tools/codesnippet/VisualBasic/create-a-windows-forms-user-control-that-supports-simple-data-binding_1.vb)]

3.  No menu **Compilação**, escolha **Compilar Solução**.

## <a name="create-a-data-source-from-your-database"></a>Criar uma fonte de dados do banco de dados

Esta etapa usa a **Data Source Configuration**Assistente para criar uma fonte de dados com base no `Customers` tabela no banco de dados de exemplo Northwind. É preciso ter acesso ao banco de dados de exemplo Northwind para criar a conexão. Para obter informações sobre como configurar o banco de dados de exemplo Northwind, consulte [como: instalar bancos de dados de exemplo](../data-tools/installing-database-systems-tools-and-samples.md).

1.  Sobre o **dados** menu, clique em **Show Data Sources**.

2.  No **fontes de dados** janela, selecione **Add New Data Source** para iniciar o **configuração de fonte de dados** assistente.

3.  Sobre o **escolher um tipo de fonte de dados** página, selecione **banco de dados**e, em seguida, clique em **próxima**.

4.  Sobre o **escolha sua Conexão de dados** página, faça o seguinte:

    -   Se uma conexão de dados com o banco de dados de exemplo Northwind estiver disponível na lista suspensa, selecione-o.

    -   Selecione **nova Conexão** para iniciar o **Adicionar/Modificar Conexão** caixa de diálogo.

5.  Se seu banco de dados exigir uma senha, selecione a opção para incluir dados confidenciais e, em seguida, clique em **próxima**.

6.  Sobre o **salvar a cadeia de caracteres de conexão para o arquivo de configuração de aplicativo** , clique em **próxima**.

7.  Sobre o **Choose your Database Objects** página, expanda o **tabelas** nó.

8.  Selecione o `Customers` de tabela e, em seguida, clique em **concluir**.

     O **NorthwindDataSet** é adicionado ao seu projeto e o `Customers` tabela aparece no **fontes de dados** janela.

## <a name="set-the-phone-column-to-use-the-phonenumberbox-control"></a>Definir a coluna telefone para usar o controle PhoneNumberBox

Dentro de **fontes de dados** janela, você pode definir o controle a ser criado antes de arrastar itens para seu formulário:

1.  Abra **Form1** no designer.

2.  Expanda o **clientes** nó na **fontes de dados** janela.

3.  Clique na seta suspensa na **clientes** nó e escolha **detalhes** na lista de controle.

4.  Clique na seta suspensa na **Phone** coluna e escolha **personalizar**.

5.  Selecione o **PhoneNumberBox** na lista de **controles associados** no **opções de personalização da interface do usuário de dados** caixa de diálogo.

6.  Clique na seta suspensa na **Phone** coluna e escolha **PhoneNumberBox**.

## <a name="add-controls-to-the-form"></a>Adicionar controles ao formulário

Você pode criar os controles ligados a dados arrastando itens dos **fontes de dados** janela para o formulário.

Para criar controles associados a dados no formulário, arraste principal **clientes** nó a partir o **fontes de dados** janela para o formulário e verificar se o **PhoneNumberBox** controle é usado para exibir os dados do **Phone** coluna.

     Data-bound controls with descriptive labels appear on the form, along with a tool strip (<xref:System.Windows.Forms.BindingNavigator>) for navigating records. A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource>, and <xref:System.Windows.Forms.BindingNavigator> appear in the component tray.

## <a name="run-the-application"></a>Executar o aplicativo

Pressione **F5** para executar o aplicativo.

## <a name="next-steps"></a>Próximas etapas

Dependendo dos requisitos do aplicativo, existem várias etapas que você pode realizar após criar um controle com suporte a associação de dados. Algumas etapas seguintes típicas incluem:

-   Colocando os controles personalizados em uma biblioteca de controles para que você possa reutilizá-los em outros aplicativos.

-   Criando controles que suportam cenários de associação de dados mais complexos. Para obter mais informações, consulte [criar um controle de usuário do Windows Forms que dá suporte à vinculação de dados complexos](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md) e [criar um controle de usuário do Windows Forms que dá suporte à vinculação de dados de pesquisa](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).

## <a name="see-also"></a>Consulte também

- [Associando controles do Windows Forms a dados no Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Definir o controle a ser criado quando arrastado da janela Fontes de Dados](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)