---
title: Salvar os dados com o TableAdapter DBDirect métodos
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- TableAdapters, walkthroughs
- data [Visual Studio], saving
- saving data, walkthroughs
- data [Visual Studio], TableAdapter
ms.assetid: 74a6773b-37e1-4d96-a39c-63ee0abf49b1
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: aae296898bfcddfa451875fe78b29f2ae95fc9df
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/19/2018
---
# <a name="save-data-with-the-tableadapter-dbdirect-methods"></a>Salvar os dados com o TableAdapter DBDirect métodos
Este passo a passo fornece instruções detalhadas para executar instruções SQL diretamente em um banco de dados usando os métodos DBDirect de um TableAdapter. Os métodos DBDirect de um TableAdapter fornecem um bom nível de controle sobre as atualizações de banco de dados. Você pode usá-los para executar instruções SQL específicas e procedimentos armazenados chamando o indivíduo `Insert`, `Update`, e `Delete` métodos conforme necessário para seu aplicativo (em vez de sobrecarregados `Update` método que executa a atualização Instruções INSERT e DELETE todas em uma chamada).

 Durante este passo a passo, você aprenderá a:

-   Criar um novo **aplicativo do Windows Forms**.

-   Criar e configurar um conjunto de dados com o [Assistente de configuração de fonte de dados](../data-tools/media/data-source-configuration-wizard.png).

-   Selecione o controle a ser criado no formulário ao arrastar itens a partir de **fontes de dados** janela. Para obter mais informações, consulte [definir o controle a ser criado quando arrastado da janela fontes de dados](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

-   Criar um formulário de associação de dados arrastando itens a partir de **fontes de dados** janela para o formulário.

-   Adicionar métodos para acessar o banco de dados diretamente e executar inserções, atualizações e exclusões.

## <a name="prerequisites"></a>Pré-requisitos
Este passo a passo usa o SQL Server Express LocalDB e o banco de dados de exemplo Northwind.

1.  Se você não tiver o SQL Server Express LocalDB, instale-o do [página de download do SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), ou por meio de **instalador do Visual Studio**. No instalador do Visual Studio, o SQL Server Express LocalDB pode ser instalado como parte do **armazenamento de dados e processamento** carga de trabalho, ou como um componente individual.

2.  Instale o banco de dados de exemplo Northwind seguindo estas etapas:

    1. No Visual Studio, abra o **Pesquisador de objetos do SQL Server** janela. (Pesquisador de objetos do SQL Server é instalado como parte do **armazenamento de dados e processamento** carga de trabalho em que o instalador do Visual Studio.) Expanda o **do SQL Server** nó. Clique com botão direito em sua instância de LocalDB e selecione **nova consulta...** .

       Abre uma janela do editor de consultas.

    2. Copie o [script Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) para sua área de transferência. Este script T-SQL cria o banco de dados Northwind desde o início e a preenche com dados.

    3. Cole o script T-SQL no editor de consultas e, em seguida, escolha o **Execute** botão.

       Após um curto período de tempo, a consulta termina de ser executado e o banco de dados Northwind é criado.

## <a name="create-a-windows-forms-application"></a>Criar um aplicativo Windows Forms
 A primeira etapa é criar um **aplicativo do Windows Forms**.

#### <a name="to-create-the-new-windows-project"></a>Para criar o novo projeto do Windows

1. No Visual Studio, no **arquivo** menu, selecione **novo**, **projeto...** .

2. Expanda **Visual C#** ou **Visual Basic** no painel esquerdo, selecione **área de trabalho clássica do Windows**.

3. No painel central, selecione a **aplicativo do Windows Forms** tipo de projeto.

4. Nomeie o projeto **TableAdapterDbDirectMethodsWalkthrough**e, em seguida, escolha **Okey**.

     O **TableAdapterDbDirectMethodsWalkthrough** projeto é criado e adicionado ao **Gerenciador de soluções**.

## <a name="create-a-data-source-from-your-database"></a>Criar uma fonte de dados do banco de dados
 Esta etapa usa a **Assistente de configuração de fonte de dados** para criar uma fonte de dados com base no `Region` tabela no banco de dados de exemplo Northwind. É preciso ter acesso ao banco de dados de exemplo Northwind para criar a conexão. Para obter informações sobre como configurar o banco de dados de exemplo Northwind, consulte [como: instalar bancos de dados de exemplo](../data-tools/installing-database-systems-tools-and-samples.md).

#### <a name="to-create-the-data-source"></a>Para criar a fonte de dados

1.  Sobre o **dados** menu, selecione **Mostrar fontes de dados**.

2.  No **fontes de dados** janela, selecione **adicionar nova fonte de dados** para iniciar o **Assistente de configuração de fonte de dados**.

3.  Sobre o **escolher um tipo de fonte de dados** tela, selecione **banco de dados**e, em seguida, selecione **próximo**.

4.  Sobre o **escolha sua Conexão de dados** tela, faça o seguinte:

    -   Se uma conexão de dados com o banco de dados de exemplo Northwind estiver disponível na lista suspensa, selecione-o.

         -ou-

    -   Selecione **nova Conexão** para iniciar o **Adicionar/Modificar Conexão** caixa de diálogo.

5.  Se seu banco de dados exigir uma senha, selecione a opção para incluir dados confidenciais e, em seguida, selecione **próximo**.

6.  Sobre o **salvar a cadeia de caracteres de conexão para o arquivo de configuração de aplicativo** tela, selecione **próximo**.

7.  Sobre o **escolher seus objetos de banco de dados** tela, expanda o **tabelas** nó.

8.  Selecione o `Region` de tabela e, em seguida, selecione **concluir**.

     O **NorthwindDataSet** é adicionado ao seu projeto e o `Region` tabela aparece no **fontes de dados** janela.

## <a name="add-controls-to-the-form-to-display-the-data"></a>Adicionar controles ao formulário para exibir os dados
 Criar os controles associados a dados, arrastando itens a partir de **fontes de dados** window para seu formulário.

#### <a name="to-create-data-bound-controls-on-the-windows-form"></a>Para criar dados associados a controles no formulário do Windows

-   Arraste principal **região** nó a partir de **fontes de dados** janela para o formulário.

     Um controle <xref:System.Windows.Forms.DataGridView> e uma faixa de ferramentas (<xref:System.Windows.Forms.BindingNavigator>) para navegação em registros são exibidos no formulário. Um [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), `RegionTableAdapter`, <xref:System.Windows.Forms.BindingSource>, e <xref:System.Windows.Forms.BindingNavigator> aparecem na bandeja do componente.

#### <a name="to-add-buttons-that-will-call-the-individual-tableadapter-dbdirect-methods"></a>Para adicionar botões que chamam os métodos individuais DbDirect de um TableAdapter

1.  Arraste três <xref:System.Windows.Forms.Button> controla do **caixa de ferramentas** para **Form1** (abaixo de **RegionDataGridView**).

2.  Defina o seguinte **nome** e **texto** propriedades em cada botão.

    |Nome|Texto|
    |----------|----------|
    |`InsertButton`|**Inserir**|
    |`UpdateButton`|**Atualizar**|
    |`DeleteButton`|**Excluir**|

#### <a name="to-add-code-to-insert-new-records-into-the-database"></a>Para adicionar código para inserir novos registros no banco de dados

1.  Selecione **InsertButton** para criar um manipulador de eventos para o evento click e abrir o formulário no editor de códigos.

2.  Substitua o manipulador de eventos `InsertButton_Click` pelo seguinte código:

     [!code-vb[VbRaddataSaving#1](../data-tools/codesnippet/VisualBasic/save-data-with-the-tableadapter-dbdirect-methods_1.vb)]
     [!code-csharp[VbRaddataSaving#1](../data-tools/codesnippet/CSharp/save-data-with-the-tableadapter-dbdirect-methods_1.cs)]

#### <a name="to-add-code-to-update-records-in-the-database"></a>Para adicionar código para atualizar registros no banco de dados

1.  Clique duas vezes o **UpdateButton** para criar um manipulador de eventos para o evento click e abrir o formulário no editor de códigos.

2.  Substitua o manipulador de eventos `UpdateButton_Click` pelo seguinte código:

     [!code-vb[VbRaddataSaving#2](../data-tools/codesnippet/VisualBasic/save-data-with-the-tableadapter-dbdirect-methods_2.vb)]
     [!code-csharp[VbRaddataSaving#2](../data-tools/codesnippet/CSharp/save-data-with-the-tableadapter-dbdirect-methods_2.cs)]

#### <a name="to-add-code-to-delete-records-from-the-database"></a>Para adicionar código para excluir registros do banco de dados

1.  Selecione **DeleteButton** para criar um manipulador de eventos para o evento click e abrir o formulário no editor de códigos.

2.  Substitua o manipulador de eventos `DeleteButton_Click` pelo seguinte código:

     [!code-vb[VbRaddataSaving#3](../data-tools/codesnippet/VisualBasic/save-data-with-the-tableadapter-dbdirect-methods_3.vb)]
     [!code-csharp[VbRaddataSaving#3](../data-tools/codesnippet/CSharp/save-data-with-the-tableadapter-dbdirect-methods_3.cs)]

## <a name="run-the-application"></a>Executar o aplicativo

#### <a name="to-run-the-application"></a>Para executar o aplicativo

-   Selecione **F5** para executar o aplicativo.

-   Selecione o **inserir** botão e, em seguida, verifique se o novo registro aparece na grade.

-   Selecione o **atualização** botão e, em seguida, verifique se o registro é atualizado na grade.

-   Selecione o **excluir** botão e, em seguida, verifique se o registro é removido da grade.

## <a name="next-steps"></a>Próximas etapas
 Dependendo dos requisitos de aplicativo, há várias etapas que você pode desejar executar depois de criar um formulário de associação de dados. Entre algumas das melhorias que você poderia fazer nessa explicação passo a passo estão:

-   Adicionando funcionalidade de busca ao formulário.

-   Adicionar tabelas adicionais ao conjunto de dados selecionando **configurar o conjunto de dados com o assistente** de dentro de **fontes de dados** janela. Você pode adicionar controles que exibem dados relacionados, arrastando os nós relacionados para o formulário. Para obter mais informações, consulte [relacionamentos em conjuntos de dados](relationships-in-datasets.md).

## <a name="see-also"></a>Consulte também

- [Salvar dados de volta no banco de dados](../data-tools/save-data-back-to-the-database.md)