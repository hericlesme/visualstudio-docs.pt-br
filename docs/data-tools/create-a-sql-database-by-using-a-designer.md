---
title: Crie um arquivo de banco de dados e usar o designer de tabela no Visual Studio
ms.date: 11/03/2017
ms.topic: conceptual
helpviewer_keywords:
- database tables, creating
- database files, creating
- table designer
ms.assetid: 99c2b06f-47aa-414e-8057-a3453712fd23
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 53f34fbed4a2067836c5f2c7a8d4bf8aa6c09d29
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34747034"
---
# <a name="create-a-database-and-add-tables-in-visual-studio"></a>Criar um banco de dados e adicionar tabelas no Visual Studio
Você pode usar o Visual Studio para criar e atualizar um arquivo de banco de dados local no SQL Server Express LocalDB. Você também pode criar um banco de dados executando instruções Transact-SQL a **Pesquisador de objetos do SQL Server** janela de ferramenta no Visual Studio. Neste tópico, vamos criar um arquivo. mdf e adicionar tabelas e chaves usando o Designer de tabela.

## <a name="prerequisites"></a>Pré-requisitos
Para concluir este passo a passo, você deve ter opcional **armazenamento de dados e processamento** instalada no Visual Studio de carga de trabalho. Para instalá-lo, abra **instalador do Visual Studio** e escolha o **cargas de trabalho** guia. Em **Web e nuvem**, escolha **processamento e armazenamento de dados**. Escolha o **modificar** botão para adicionar a carga de trabalho para o Visual Studio.

## <a name="create-a-project-and-a-local-database-file"></a>Criar um projeto e um arquivo de banco de dados local

### <a name="to-create-a-project-and-a-database-file"></a>Para criar um projeto e um arquivo de banco de dados
1.  Criar um projeto de formulários do Windows chamado `SampleDatabaseWalkthrough`.

2.  Na barra de menus, selecione **projeto**, **Adicionar Novo Item**.

3.  Na lista de modelos de item, role para baixo e selecione **banco de dados baseado em serviço**.

     ![Caixa de diálogo de modelos de item](../data-tools/media/raddata-vsitemtemplates.png)

4.  Nome do banco de dados **SampleDatabase**e, em seguida, selecione o **adicionar** botão.

### <a name="to-add-a-data-source"></a>Para adicionar uma fonte de dados
5.  Se o **fontes de dados** janela não estiver aberta, abra-o, selecionando o **Shift + Alt + D** chaves ou, na barra de menus, selecionando **exibição**, **outras janelas**, **Fontes de dados**.

6.  No **fontes de dados** janela, selecione o **adicionar nova fonte de dados** link.

    O **Assistente de configuração de fonte de dados** é aberto.

7. Sobre o **escolher um tipo de fonte de dados** página, escolha **banco de dados** e, em seguida, escolha **próximo**.

8. Sobre o **escolha um modelo de banco de dados** página, escolha **próximo** para aceitar o padrão (conjunto de dados).

9. No **escolha sua Conexão de dados** página, selecione o **SampleDatabase** de arquivo na lista suspensa e, em seguida, escolha **próximo**.

10. Sobre o **salvar a cadeia de Conexão no arquivo de configuração do aplicativo** página, escolha **próximo**.

11. Um o **escolher seus objetos de banco de dados** página, você verá uma mensagem que diz que o banco de dados não contém todos os objetos. Escolha **Concluir**.

### <a name="to-view-properties-of-the-data-connection"></a>Para exibir as propriedades de conexão de dados
Você pode exibir a cadeia de caracteres de conexão para o arquivo SampleDatabase abrindo a janela de propriedades de conexão de dados:

-   No Visual Studio, selecione **exibição**, **Pesquisador de objetos do SQL Server** se essa janela não estiver aberta. Abra a janela Propriedades, expandindo o **conexões de dados** nó, abrindo o menu de atalho para SampleDatabase e, em seguida, selecionando **propriedades**.

-   Como alternativa, você pode selecionar **exibição**, **Server Explorer**, se essa janela não estiver aberta. Abra a janela Propriedades, expandindo o **conexões de dados** nó. Abra o menu de atalho SampleDatabase e, em seguida, selecione **propriedades**.

## <a name="create-tables-and-keys-by-using-table-designer"></a>Criar tabelas e chaves usando o Designer de tabela
Nesta seção, você criará duas tabelas, uma chave primária em cada tabela e algumas linhas de dados de exemplo. Você também criará uma chave estrangeira para especificar como os registros de uma tabela correspondem aos registros em outra tabela.

### <a name="to-create-the-customers-table"></a>Para criar a tabela Customers
1.  Em **Server Explorer** ou **Pesquisador de objetos do SQL Server**, expanda o **conexões de dados** nó e, em seguida, expanda o **SampleDatabase**nó.

2.  Abra o menu de atalho para **tabelas**e, em seguida, selecione **adicionar nova tabela**.

     O **Designer de tabela** é aberto e mostra uma grade com padrão de uma linha, que representa uma única coluna na tabela que você está criando. Adicionando linhas à grade, você adicionará colunas na tabela.

3.  Na grade, adicione uma linha para cada uma das seguintes entradas:

    |Nome da coluna|Tipo de dados|Permitir nulos|
    |-----------------|---------------|-----------------|
    |`CustomerID`|`nchar(5)`|Falso (desmarcado)|
    |`CompanyName`|`nvarchar(50)`|Falso (desmarcado)|
    |`ContactName`|`nvarchar (50)`|Verdadeiro (marcado)|
    |`Phone`|`nvarchar (24)`|Verdadeiro (marcado)|

4.  Abra o menu de atalho para o `CustomerID` de linha e, em seguida, selecione **definir chave primária**.

5.  Abra o menu de atalho para a linha padrão e, em seguida, selecione **excluir**.

6.  Nomeie a tabela Clientes atualizando a primeira linha no painel de script de acordo com o seguinte exemplo:

    ```sql
    CREATE TABLE [dbo].[Customers]
    ```

    Você deve ver algo parecido com isso:

    ![Designer de Tabela](../data-tools/media/raddata-table-designer.png)

7.  No canto superior esquerdo do **Designer de tabela**, selecione o **atualização** botão.

8.  No **atualizações de banco de dados de visualização** caixa de diálogo, selecione o **Atualizar banco de dados** botão.

    As alterações são salvas no arquivo do banco de dados local.

### <a name="to-create-the-orders-table"></a>Para criar a tabela Orders
1.  Adicione outra tabela e uma linha para cada entrada na seguinte tabela:

    |Nome da coluna|Tipo de dados|Permitir nulos|
    |-----------------|---------------|-----------------|
    |`OrderID`|`int`|Falso (desmarcado)|
    |`CustomerID`|`nchar(5)`|Falso (desmarcado)|
    |`OrderDate`|`datetime`|Verdadeiro (marcado)|
    |`OrderQuantity`|`int`|Verdadeiro (marcado)|

2.  Definir **OrderID** como a chave primária e, em seguida, exclua a linha padrão.

3.  Nomeie a tabela Orders atualizando a primeira linha no painel de script de acordo com o seguinte exemplo:

    ```sql
    CREATE TABLE [dbo].[Orders]
    ```

4.  No canto superior esquerdo do **Designer de tabela**, selecione o **atualização** botão.

5.  No **atualizações de banco de dados de visualização** caixa de diálogo, selecione o **Atualizar banco de dados** botão.

    As alterações são salvas no arquivo do banco de dados local.

### <a name="to-create-a-foreign-key"></a>Para criar uma chave estrangeira
1.  No painel de contexto no lado direito da grade, abra o menu de atalho **chaves estrangeiras**e, em seguida, selecione **adicionar nova chave estrangeira**, como mostra a ilustração a seguir.

     ![Adicionar uma chave estrangeira no Designer de tabela](../data-tools/media/foreignkey.png)

2.  Na caixa de texto que aparece, substitua **ToTable** com `Customers`.

3.  No painel de T-SQL, atualize a última linha para coincidir com o exemplo a seguir:

    ```sql
    CONSTRAINT [FK_Orders_Customers] FOREIGN KEY ([CustomerID]) REFERENCES [Customers]([CustomerID])
    ```

4.  No canto superior esquerdo do **Designer de tabela**, selecione o **atualização** botão.

5.  No **atualizações de banco de dados de visualização** caixa de diálogo, selecione o **Atualizar banco de dados** botão.

    As alterações são salvas no arquivo do banco de dados local.

## <a name="populate-the-tables-with-data"></a>Preencher as tabelas com dados

### <a name="to-populate-the-tables-with-data"></a>Para popular as tabelas com dados

1.  Em **Server Explorer** ou **Pesquisador de objetos do SQL Server**, expanda o nó para o banco de dados de exemplo.

2.  Abra o menu de atalho para o **tabelas** nó, selecione **atualizar**e, em seguida, expanda o **tabelas** nó.

3.  Abra o menu de atalho para a tabela clientes e, em seguida, selecione **Mostrar dados da tabela**.

4.  Adicione os dados que você deseja para alguns clientes.

    É possível especificar cinco caracteres desejados como IDs de cliente, mas escolha pelo menos um do qual é possível se lembrar para uso posteriormente neste procedimento.

5.  Abra o menu de atalho para a tabela de pedidos e, em seguida, selecione **Mostrar dados da tabela**.

6.  Adicione dados para alguns pedidos.

    > [!IMPORTANT]
    > Certifique-se de que todos os IDs de ordem e quantidades de ordem são números inteiros e que cada ID de cliente corresponde a um valor que você especificou na coluna CustomerID da tabela Customers.

7.  Na barra de menus, selecione **arquivo**, **Salvar tudo**.

## <a name="see-also"></a>Consulte também

- [Acessando dados no Visual Studio](accessing-data-in-visual-studio.md)