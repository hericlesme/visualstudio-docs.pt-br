---
title: Ferramentas de dados do Visual Studio para C++
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CPP
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
- cplusplus
ms.openlocfilehash: d2e74fca7109a19c789215424526eef6190b568c
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34752392"
---
# <a name="visual-studio-data-tools-for-c"></a>Ferramentas de dados do Visual Studio para C++

C++ nativo geralmente pode fornecer o melhor desempenho quando você está acessando fontes de dados. No entanto, dados de ferramentas para aplicativos do C++ no Visual Studio não são tão avançados quanto para aplicativos .NET. Por exemplo, as janelas de fontes de dados não podem ser usadas para arrastar e soltar fontes de dados em uma superfície de design do C++. Se você precisar de uma camada de objeto relacional, você precisará escrever suas próprias ou usar um produto de terceiros.  O mesmo é verdadeiro para a funcionalidade de associação de dados, embora os aplicativos que usam a biblioteca Microsoft Foundation Class podem usar algumas classes de banco de dados, juntamente com documentos e exibições, para armazenar dados na memória e exibi-lo para o usuário. Para obter mais informações, consulte [acesso a dados no Visual C++](/cpp/data/data-access-in-cpp).

Para se conectar a bancos de dados SQL, os aplicativos nativos do C++ podem usar os drivers ODBC e OLE DB e o provedor ADO que estão incluídos no Windows. Eles podem se conectar a qualquer banco de dados que oferece suporte a essas interfaces. O driver ODBC é o padrão. OLE DB é fornecido para compatibilidade com versões anteriores. Para obter mais informações sobre essas tecnologias de dados, consulte [Windows Data Access Components](https://msdn.microsoft.com/library/windows/desktop/aa968814.aspx).

Para tirar proveito da funcionalidade personalizada no SQL Server 2005 e posterior, use o [SQL Server Native Client](/sql/relational-databases/native-client/sql-server-native-client). O native client também contém o driver ODBC do SQL Server e o provedor OLE DB do SQL Server em uma biblioteca de vínculo dinâmico (DLL). Eles oferecem suporte a aplicativos que usam APIs de código nativo (ODBC, OLE DB e ADO) para o Microsoft SQL Server.  SQL Server Native Client é instalado com o SQL Server Data Tools. O guia de programação está aqui: [SQL Server Native Client programação](/sql/relational-databases/native-client/sql-server-native-client-programming).

## <a name="to-connect-to-localdb-through-odbc-and-sql-native-client-from-a-c-application"></a>Para conectar-se ao localDB por meio de ODBC e SQL Native Client em um aplicativo C++

1.  Instale o SQL Server Data Tools.

2.  Se você precisar de um banco de dados SQL de exemplo para se conectar ao, baixe o banco de dados Northwind e descompacte-o para um novo local.

3.  Use o SQL Server Management Studio para anexar o arquivo mdf descompactado para o localDB. Início do SQL Server Management Studio, conecte-se ao (localdb) \MSSQLLocalDB.

     ![Caixa de diálogo de conexão do SSMS](../data-tools/media/raddata-ssms-connect-dialog.png)

     Em seguida, clique com botão direito no nó de localdb no painel esquerdo e escolha **Attach**.

     ![SSMS anexar banco de dados](../data-tools/media/raddata-ssms-attach-database.png)

4.  Baixe a amostra de SDK do Windows de ODBC e descompacte-o para um novo local. Este exemplo mostra os comandos básicos do ODBC que são usados para se conectar a um banco de dados e emitir consultas e comandos. Você pode aprender mais sobre essas funções no [Microsoft ODBC Open Database Connectivity ()](/sql/odbc/microsoft-open-database-connectivity-odbc). Quando você primeiro carrega a solução (está na pasta C++), o Visual Studio oferecem atualizar a solução para a versão atual do Visual Studio. Clique em **Sim**.

5.  Para usar o native client, você precisa de seu arquivo de cabeçalho e o arquivo de biblioteca. Esses arquivos contêm as funções e definições específicas para o SQL Server, além de funções ODBC definidas no SQL. Em **projeto** > **propriedades** > **diretórios VC + +**, adicione o seguinte diretório de inclusão:

**%ProgramFiles%\Microsoft SQL Server\110\SDK\Include**

E esse diretório de biblioteca:

**%ProgramFiles%\Microsoft SQL Server\110\SDK\Lib**

6.  Adicione essas linhas odbcsql.cpp. O #define impede irrelevantes definições de OLE DB de que está sendo compilada.

    ```cpp
    #define _SQLNCLI_ODBC_
    #include <sqlncli.h>
    ```

    Observe que o exemplo não realmente usar qualquer funcionalidade cliente nativo, portanto, as etapas anteriores não são necessárias compilar e executar. Mas o projeto agora está configurado para usar essa funcionalidade. Para obter mais informações, consulte [SQL Server Native Client programação](/sql/relational-databases/native-client/sql-server-native-client).

7.  Especifique qual driver usar no subsistema ODBC. O exemplo passa o atributo de cadeia de caracteres de conexão do DRIVER no como um argumento de linha de comando. Em **projeto** > **propriedades** > **depuração**, adicionar esse argumento de comando:

    ```cpp
    DRIVER="SQL Server Native Client 11.0"
    ```

8.  Pressione F5 para compilar e executar o aplicativo. Você deve ver uma caixa de diálogo do driver que solicita que você insira um banco de dados. Digite `(localdb)\MSSQLLocalDB`e verifique **Conexão confiável do uso**. Press **OK**. Você deve ver um console com as mensagens que indicam uma conexão bem-sucedida. Você também verá um prompt de comando em que você pode digitar uma instrução SQL. A tela a seguir mostra um exemplo de consulta e os resultados:

     ![Saída de consulta de exemplo do ODBC](../data-tools/media/raddata-odbc-sample-query-output.png)

## <a name="see-also"></a>Consulte também

- [Acessando dados no Visual Studio](../data-tools/accessing-data-in-visual-studio.md)