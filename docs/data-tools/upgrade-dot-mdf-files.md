---
title: Atualizar os arquivos. mdf | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL Server Express
- SQL Server LocalDB
- LocalDB
- SQLEXPRESS
- upgrading SQLExpress to SQLExpress
- upgrading to LocalDB
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: c02ae1ba7091871f92d1fdf00f55f7d0ded6024f
ms.sourcegitcommit: e951faab601f5c05ad6606d8fd0cd2059fc4cc25
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/14/2017
---
# <a name="upgrade-mdf-files"></a>Atualizar os arquivos. mdf

Este tópico descreve as opções de atualização de um arquivo de banco de dados (. mdf) depois de instalar uma versão mais recente do Visual Studio. Ele inclui instruções para as seguintes tarefas:

- Atualizar um arquivo de banco de dados para usar uma versão mais recente do SQL Server Express LocalDB

- Atualizar um arquivo de banco de dados para usar uma versão mais recente do SQL Server Express

- Trabalhar com um arquivo de banco de dados no Visual Studio, mas manter a compatibilidade com uma versão mais antiga do SQL Server Express ou o LocalDB

- Verifique o SQL Server Express o mecanismo de banco de dados padrão

Você pode usar o Visual Studio para abrir um projeto que contém um arquivo de banco de dados (. mdf) que foi criado usando uma versão mais antiga do SQL Server Express ou LocalDB. No entanto, para continuar a desenvolver o projeto no Visual Studio, você deve ter a versão do SQL Server Express ou LocalDB instalada no mesmo computador que o Visual Studio, ou você deve atualizar o arquivo de banco de dados. Se você atualizar o arquivo de banco de dados, você não poderá acessá-lo usando versões anteriores do SQL Server Express ou LocalDB.

Você também pode ser solicitado para atualizar um arquivo de banco de dados que foi criado por meio de uma versão anterior do SQL Server Express ou LocalDB se a versão do arquivo não é compatível com a instância do SQL Server Express ou LocalDB instalado no momento. Para resolver o problema, o Visual Studio solicitará que você atualizar o arquivo.

> [!IMPORTANT]
> É recomendável que você faça backup do arquivo de banco de dados antes de atualizá-lo.

> [!WARNING]
> Se você atualizar um arquivo. mdf que foi criado no LocalDB 2014 (V12) de 32 bits para o LocalDB 2016 (V13) ou posterior, você não poderá abrir o arquivo novamente na versão de 32 bits do LocalDB.

Antes de atualizar um banco de dados, considere os seguintes critérios:
  
-   Não atualize se desejar trabalhar em seu projeto em uma versão mais antiga e uma versão mais recente do Visual Studio.  
  
-   Não atualize se seu aplicativo será usado em ambientes que usam o SQL Server Express em vez de LocalDB.  
  
-   Não atualize se seu aplicativo usa conexões remotas, porque o LocalDB não aceitá-los.  
  
-   Não atualize se seu aplicativo se baseia em serviços de informações da Internet (IIS).  
  
-   Considere a atualização se você deseja testar aplicativos de banco de dados em um ambiente de área restrita, mas não quiser administrar um banco de dados.  
  
### <a name="to-upgrade-a-database-file-to-use-the-localdb-version"></a>Para atualizar um arquivo de banco de dados para usar a versão de LocalDB
  
1.  Em **Server Explorer**, selecione o **conectar-se ao banco de dados** botão.  
  
2.  No **Adicionar Conexão** caixa de diálogo, especifique as seguintes informações:  
  
    -   **Fonte de dados**:`Microsoft SQL Server (SqlClient)`  
  
    -   **Nome do servidor**:  
  
        -   Para usar a versão padrão: `(localdb)\MSSQLLocalDB`.  Isso especificará ProjectV12 ou ProjectV13, dependendo de qual versão do Visual Studio está instalado e em que a primeira instância de LocalDB foi criada. O **MSSQLLocalDB** nó **Pesquisador de objetos do SQL Server** mostra qual versão apontando para.  
  
        -   Para usar uma versão específica: `(localdb)\ProjectsV12` ou `(localdb)\ProjectsV13`, onde V12 é LocalDB 2014 e V13 é 2016 LocalDB.  
  
    -   **Anexar um arquivo de banco de dados**: O caminho físico do arquivo. mdf primário.  
  
    -   **Nome lógico**: O nome que você deseja usar com o arquivo.  
  
3.  Selecione o botão **OK**.  
  
4.  Quando você for solicitado, selecione o **Sim** botão para atualizar o arquivo.  
  
    O banco de dados é atualizado, é anexado ao mecanismo de banco de dados LocalDB e não é mais compatível com a versão mais antiga do LocalDB.  
  
Você também pode modificar uma conexão de SQL Server Express para usar LocalDB abrindo o menu de atalho para a conexão e, em seguida, selecionando **Modificar Conexão**. No **Modificar Conexão** caixa de diálogo, altere o nome do servidor para `(LocalDB)\MSSQLLocalDB`. No **propriedades avançadas** caixa de diálogo caixa, certifique-se de que **instância de usuário** é definido como **False**.

### <a name="to-upgrade-a-database-file-to-use-the-sql-server-express-version"></a>Para atualizar um arquivo de banco de dados para usar a versão SQL Server Express  
  
1.  No menu de atalho para a conexão ao banco de dados, selecione **Modificar Conexão**.  
  
2.  No **Modificar Conexão** caixa de diálogo, selecione o **avançado** botão.  
  
3.  No **propriedades avançadas** caixa de diálogo, selecione o **Okey** botão sem alterar o nome do servidor.  
  
    O arquivo de banco de dados é atualizado para corresponder à versão atual do SQL Server Express.  
  
### <a name="to-work-with-the-database-in-visual-studio-but-retain-compatibility-with-sql-server-express"></a>Para trabalhar com o banco de dados no Visual Studio, mas manter a compatibilidade com o SQL Server Express  
  
-   No Visual Studio, abra o projeto sem atualizá-lo.  
  
    -   Para executar o projeto, selecione o **F5** chave.  
  
    -   Para editar o banco de dados, abra o arquivo. mdf em **Solution Explorer**e expanda o nó em **Server Explorer** para trabalhar com seu banco de dados.  
  
### <a name="to-make-sql-server-express-the-default-database-engine"></a>Para tornar o SQL Server Express o mecanismo de banco de dados padrão  
  
1.  Na barra de menus, selecione **ferramentas**, **opções**.  
  
2.  No **opções** caixa de diálogo caixa, expanda o **ferramentas de banco de dados** opções e, em seguida, selecione **conexões de dados**.  
  
3.  No **nome da instância do SQL Server** texto, especifique o nome da instância do SQL Server Express ou LocalDB que você deseja usar. Se a instância não nomeada, especifique `.\SQLEXPRESS or (LocalDB)\MSSQLLocalDB`.  
  
4.  Selecione o botão **OK**.  
  
    SQL Server Express será o mecanismo de banco de dados padrão para seus aplicativos.

## <a name="see-also"></a>Consulte também

[Acessando dados no Visual Studio](accessing-data-in-visual-studio.md)
