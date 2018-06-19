---
title: Compatibilidade de banco de dados do Visual Studio
ms.date: 09/06/2017
ms.topic: conceptual
helpviewer_keywords:
- database systems
- database compatibility
- databases for Visual Studio
ms.assetid: 821de34b-eaa9-40af-b9aa-b8305de16899
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 883287c782742aa7bfb7d24f9e2d846a1caa149e
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31923617"
---
# <a name="compatible-database-systems-for-visual-studio"></a>Sistemas de banco de dados compatível para o Visual Studio

Para desenvolver um aplicativo conectado a dados no Visual Studio, você normalmente instala o sistema de banco de dados em seu computador de desenvolvimento local e, em seguida, implanta o aplicativo e o banco de dados em um ambiente de produção quando estiverem prontas. Visual Studio instala o SQL Server Express LocalDB no seu computador como parte do **armazenamento de dados e processamento** carga de trabalho. Esta instância de LocalDB é útil para desenvolvimento de aplicativos de dados conectados com rapidez e facilidade.

Para um sistema de banco de dados possam ser acessadas de aplicativos .NET e fique visível em janelas de ferramentas de dados do Visual Studio, ele deverá ter um provedor de dados ADO.NET. Um provedor especificamente deve oferecer suporte a Entity Framework se você planeja usar modelos de dados de entidade em seu aplicativo .NET. Muitos provedores são oferecidos por meio do Gerenciador de pacotes do NuGet ou por meio do Visual Studio Marketplace.

Se você estiver usando APIs de armazenamento do Azure, instale os emuladores de armazenamento do Azure em sua máquina local durante o desenvolvimento para evitar encargos até que você está pronto para implantar na produção. Para obter mais informações, consulte [usar o emulador de armazenamento do Azure para desenvolvimento e testes](/azure/storage/common/storage-use-emulator).

A lista a seguir inclui alguns dos sistemas de banco de dados mais populares que podem ser usados em projetos do Visual Studio. A lista não é exaustiva. Para obter uma lista de fornecedores que oferecem provedores de dados ADO.NET que habilitar a integração profunda com ferramentas do Visual Studio, consulte [provedores de dados ADO.NET](/dotnet/framework/data/adonet/data-providers).

## <a name="microsoft-sql-server"></a>Microsoft SQL Server

O SQL Server é o banco de dados do Microsoft principal da oferta. SQL Server 2016 oferece um desempenho inovador, segurança avançada e rico e integrado, relatórios e análises. Ele é fornecido em várias edições são projetadas para usos diferentes: de análise de negócios altamente escalonável e de alto desempenho, para usar em um único computador. SQL Server Express é uma edição completa do SQL Server que seja adequado para a redistribuição e inserção.  O LocalDB é uma edição simplificada do SQL Server Express que não requer configuração e é executado no processo do aplicativo. Você pode baixar um ou ambos os produtos a [página de download do SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express). Muitos dos exemplos de SQL nesta seção usam o LocalDB do SQL Server. SQL Server Management Studio (SSMS) é um aplicativo de gerenciamento de banco de dados autônomo que tenha mais funcionalidade que é fornecido no Visual Studio SQL Server Object Explorer. Você pode obter o SSMS do link anterior.

## <a name="oracle"></a>Oracle

Você pode baixar uma edição gratuita ou paga do banco de dados Oracle do [Oracle Technology Network](http://www.oracle.com/technetwork/database/enterprise-edition/downloads/index-092322.html) página. Suporte de tempo de design para o Entity Framework e TableAdapters, será necessário o [Oracle Developer Tools para Visual Studio](http://www.oracle.com/technetwork/developer-tools/visual-studio/overview/index.html). Outros produtos oficiais do Oracle, incluindo o cliente instantâneo Oracle, estão disponíveis por meio do Gerenciador de pacotes do NuGet.  Você pode baixar esquemas de exemplo do Oracle, seguindo as instruções de [documentação on-line Oracle](http://docs.oracle.com/cd/E11882_01/server.112/e10831/toc.htm).

## <a name="mysql"></a>MySQL

MySQL é um sistema de banco de dados de código aberto popular que é amplamente usado em empresas e sites. Downloads para MySQL, o MySQL para Visual Studio e produtos relacionados são em [MySQL no Windows](http://www.mysql.com/why-mysql/windows/).  Terceiros oferecem várias extensões do Visual Studio e aplicativos de gerenciamento independente para MySQL. Você pode procurar as ofertas o NuGet Package Manager (**ferramentas** > **NuGet Package Manager** > **gerenciar pacotes NuGet para solução**) .

## <a name="postgresql"></a>PostgreSQL

PostgreSQL é um sistema de banco de dados relacional de objeto livre, o código-fonte aberto. Para instalá-lo no Windows, você pode baixá-lo do [página de download PostgreSQL](http://www.postgresql.org/download/windows/).  Você também pode criar PostgreSQL do código-fonte.  O sistema básico de PostgreSQL inclui uma interface de linguagem C. Muitos terceiros fornecem pacotes do NuGet para usar PostgreSQL de aplicativos .NET.  Você pode procurar as ofertas o NuGet Package Manager (**ferramentas** > **NuGet Package Manager** > **gerenciar pacotes NuGet para solução**) . Talvez o pacote mais popular é fornecido pelo [npgsql.org](http://www.npgsql.org).

## <a name="sqlite"></a>SQLite

SQLite é um mecanismo de banco de dados SQL inserido que é executado no processo do aplicativo. Você pode baixá-lo do [página de download do SQLite](http://www.sqlite.org/download.html). Muitos pacotes de NuGet de terceiros para SQLite também estão disponíveis. Você pode procurar as ofertas o NuGet Package Manager (**ferramentas** > **NuGet Package Manager** > **gerenciar pacotes NuGet para solução**) .

## <a name="firebird"></a>Firebird

Firebird é um sistema de banco de dados SQL do código-fonte aberto. Você pode baixá-lo do [página de download Firebird](http://firebirdsql.org/en/downloads/). Um provedor de dados ADO.NET está disponível por meio do Gerenciador de pacotes do NuGet.

## <a name="see-also"></a>Consulte também

- [Acessando dados no Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
- [Como determinar a versão e edição do SQL Server e seus componentes](http://support.microsoft.com/kb/321185)