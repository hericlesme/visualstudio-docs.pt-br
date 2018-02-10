---
title: Acessando dados no Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- "80025080"
helpviewer_keywords:
- data [Visual Studio]
- data access [Visual Studio]
- data [C#]
- ADO.NET, data access
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 7ccee10630a4b5de0aebf361c7acf6cccf8cf49c
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
---
# <a name="accessing-data-in-visual-studio"></a>Acesso a dados no Visual Studio

No Visual Studio, você pode criar aplicativos que se conectam aos dados em praticamente qualquer produto de banco de dados ou um serviço, em qualquer formato, em qualquer lugar — em um computador local, em uma rede local ou em uma nuvem pública, privada ou híbrida.

Para aplicativos em JavaScript, Python, PHP, Ruby ou C++, você se conectar aos dados que você pode fazer qualquer outra coisa, obtendo bibliotecas e escrever código. Para aplicativos .NET, o Visual Studio fornece ferramentas que você pode usar para explorar a fontes de dados, criar modelos de objeto para armazenar e manipular os dados na memória e associar os dados para a interface do usuário. Microsoft Azure fornece SDKs para .NET, Java, Node.js, PHP, Python, Ruby e aplicativos móveis e ferramentas no Visual Studio para se conectar ao armazenamento do Azure.

A lista a seguir mostra apenas alguns os muitos sistemas de banco de dados e armazenamento que podem ser usados no Visual Studio. O [Microsoft Azure](https://azure.microsoft.com/) ofertas são serviços de dados que incluem todos os provisionamento e administração de armazenamento de dados subjacente.  [Ferramentas do Azure para Visual Studio](https://www.visualstudio.com/features/azure-tools-vs.aspx) é um componente opcional que permite que você trabalhe com repositórios de dados do Azure diretamente do Visual Studio. A maioria dos outros SQL e NoSQL banco de dados produtos listados aqui pode ser hospedada em um computador local, em uma rede local ou no Microsoft Azure em uma máquina virtual. Nesse cenário, você é responsável por gerenciar o próprio banco de dados.

**Microsoft Azure**

||||
|-|-|-|
|Banco de dados SQL|DocumentDB|Armazenamento (blobs, tabelas, filas, arquivos)|
|SQL Data Warehouse|SQL Server Stretch Database|StorSimple|

E muito mais...

**SQL**

||||
|-|-|-|
|SQL Server 2005-2016, incluindo Express e LocalDB|Firebird|MariaDB|
|MySQL|Oracle|PostgreSQL|
|SQLite|||

E muito mais...

**NoSQL**

||||
|-|-|-|
|Apache Cassandra|CouchDB|MongoDB|
|NDatabase|OrientDB|RavenDB|
|VelocityDB|||

E muito mais...

Muitos fornecedores de banco de dados e de terceiros dão suporte à integração do Visual Studio pacotes do NuGet. Você pode explorar as ofertas em nuget.org ou por meio do Gerenciador de pacotes do NuGet no Visual Studio (**ferramentas** > **NuGet Package Manager** > **gerenciar NuGet Pacotes de solução**). Outros produtos de banco de dados se integram ao Visual Studio como uma extensão. Você pode procurar essas ofertas no Visual Studio Marketplace navegando até **ferramentas**, **extensões e atualizações** e, em seguida, selecionando **Online** no painel esquerdo das caixa de diálogo. Para obter mais informações, consulte [sistemas de banco de dados compatível para o Visual Studio](../data-tools/installing-database-systems-tools-and-samples.md).

> [!NOTE]
> Suporte estendido para o SQL Server 2005 terminou em 12 de abril de 2016. Não há nenhuma garantia de que as ferramentas de dados no Visual Studio 2015 e posteriores continuem a funcionar com o SQL Server 2005 após essa data. Para obter mais informações, consulte o [anúncio de fim do suporte para o SQL Server 2005](https://www.microsoft.com/server-cloud/products/sql-server-2005/).

## <a name="net-languages"></a>Linguagens .NET

Qualquer acesso a dados .NET, incluindo no núcleo do .NET, é baseado no ADO.NET, um conjunto de classes que define uma interface para acessar qualquer tipo de fonte de dados relacional e não relacionais. O Visual Studio tem várias ferramentas e designers que funcionam com o ADO.NET para ajudá-lo a se conectar a bancos de dados, manipular os dados e apresentar os dados para o usuário. A documentação nesta seção descreve como usar essas ferramentas. Você pode também programar diretamente os objetos de comando do ADO.NET. Para obter mais informações sobre como chamar as APIs do ADO.NET diretamente, consulte [ADO.NET](/dotnet/framework/data/adonet/index).

Para obter a documentação de acesso a dados relacionada especificamente ao ASP.NET, consulte [trabalhando com dados](http://www.asp.net/web-forms/overview/presenting-and-managing-data) no site do ASP.NET. Para obter um tutorial sobre como usar o Entity Framework com o ASP.NET MVC, consulte [guia de Introdução ao Entity Framework 6 Code First usando MVC 5](http://www.asp.net/mvc/overview/getting-started/getting-started-with-ef-using-mvc/creating-an-entity-framework-data-model-for-an-asp-net-mvc-application).

Aplicativos universais do Windows UWP (plataforma) no c# ou Visual Basic podem usar o SDK do Microsoft Azure para .NET para acessar o armazenamento do Azure e outros serviços do Azure. A classe Windows.Web.HttpClient permite a comunicação com todos os serviços RESTful. Para obter mais informações, consulte [como se conectar a um servidor HTTP usando Windows.Web.Http](https://msdn.microsoft.com/library/windows/apps/dn469430.aspx).

Para o armazenamento de dados no computador local, a abordagem recomendada é usar SQLite, que é executado no mesmo processo que o aplicativo. Se uma camada de mapeamento relacional de objeto (ORM) for necessária, você pode usar o Entity Framework. Para obter mais informações, consulte [acesso a dados](https://msdn.microsoft.com/windows/uwp/data-access/index) no Centro de desenvolvedores do Windows.

Se você estiver se conectando aos serviços do Azure, certifique-se de baixar a versão mais recente [ferramentas do SDK do Azure](https://azure.microsoft.com/downloads/).

### <a name="data-providers"></a>Provedores de dados

Para um banco de dados ser consumível no ADO.NET, ele deverá ter um personalizado *provedor de dados ADO.NET* ou else deve expor uma interface ODBC ou OLE DB. A Microsoft fornece um [lista de provedores de dados ADO.NET](https://msdn.microsoft.com/data/dd363565) para produtos do SQL Server, bem como provedores de ODBC e OLE DB.

### <a name="data-modeling"></a>Modelagem de dados

No .NET, você tem três opções de modelagem e manipulação de dados na memória depois de recuperá-lo de uma fonte de dados:

[Entity Framework](../data-tools/entity-data-model-tools-in-visual-studio.md) a tecnologia Microsoft ORM preferencial. Você pode usar isso para programar em dados relacionais como objetos de primeira classe .NET. Para novos aplicativos, ele deve ser a primeira opção padrão quando um modelo é necessário. Ele requer suporte personalizado do provedor de ADO.NET subjacente.

[O LINQ to SQL](../data-tools/linq-to-sql-tools-in-visual-studio2.md) um mapeador relacional de objetos da geração anterior. Ele funciona bem para cenários menos complexos, mas não está em desenvolvimento ativo.

[Conjuntos de dados](../data-tools/dataset-tools-in-visual-studio.md)  
O mais antigo dos três tecnologias de modelagem. Ele foi projetado principalmente para rápido desenvolvimento de aplicativos "formulários sobre dados" em que você não é processar grandes volumes de dados ou executar consultas complexas ou transformações. Um objeto de conjunto de dados consiste em objetos de DataTable e DataRow que lembram logicamente objetos de banco de dados do SQL muito mais objetos do .NET Framework. Para aplicativos relativamente simples com base em fontes de dados do SQL, os conjuntos de dados ainda podem ser uma boa opção.

Não há nenhum requisito para usar qualquer uma dessas tecnologias. Em alguns cenários, especialmente quando o desempenho for crítico, você pode simplesmente usar um objeto DataReader para ler do banco de dados e copiar os valores que você precisa para um objeto de coleção como lista\<T >.

## <a name="native-c"></a>C++ Nativo

Aplicativos C++ que se conectar ao SQL Server devem usar o [Microsoft® ODBC Driver 13.1 para SQL Server](https://www.microsoft.com/download/details.aspx?id=53339) na maioria dos casos. Se os servidores estiverem vinculados, em seguida, o OLE DB é necessário e para que você use o [SQL Server Native Client](/sql/relational-databases/native-client/sql-server-native-client). Você pode acessar outros bancos de dados usando [ODBC](https://msdn.microsoft.com/library/ms710252\(v=vs.85\).aspx) ou drivers de OLE DB diretamente. ODBC é a interface padrão do banco de dados atual, mas a maioria dos sistemas de banco de dados fornecem funcionalidade personalizada que não pode ser acessada por meio da interface do ODBC. OLE DB é uma tecnologia de acesso a dados COM herdado que é ainda tem suporte mas não recomendada para novos aplicativos. Para obter mais informações, consulte [acesso a dados no Visual C++](/cpp/data/data-access-in-cpp).

Programas C++ que consumirem serviços REST podem usar o [C++ REST SDK](https://github.com/Microsoft/cpprestsdk).

Programas em C++ que funcionam com o armazenamento do Microsoft Azure podem usar o [cliente de armazenamento do Microsoft Azure](http://www.nuget.org/packages/wastorage).

Modelagem de dados&mdash;Visual Studio não fornecem uma camada ORM para C++. [ODB](http://www.codesynthesis.com/products/odb/) é um ORM popular do código-fonte aberto para C++.

Para saber mais sobre como conectar aos bancos de dados de aplicativos em C++, consulte [ferramentas de dados do Visual Studio para C++](../data-tools/visual-studio-data-tools-for-cpp.md). Para obter mais informações sobre tecnologias de acesso a dados herdadas do Visual C++, consulte [acesso a dados](/cpp/data/data-access-in-cpp).

## <a name="javascript"></a>JavaScript

[JavaScript no Visual Studio](/scripting/javascript/javascript-language-reference) é uma linguagem de primeira classe para a criação de aplicativos de plataforma cruzada, aplicativos UWP, serviços de nuvem, sites e aplicativos web. Você pode usar o Bower, Grunt, Gulp, npm e NuGet de dentro do Visual Studio para instalar bibliotecas de JavaScript favoritas e produtos de banco de dados. Conecte-se ao armazenamento do Azure e serviços baixando SDKs do [site do Azure](https://azure.microsoft.com/). Edge.js é uma biblioteca JavaScript do lado do servidor (Node. js) conecta-se a fontes de dados do ADO.NET.

## <a name="python"></a>Python

Instalar [suporte a Python no Visual Studio](../python/python-in-visual-studio.md) para criar aplicativos de Python. Documentação do Azure tem vários tutoriais sobre como se conectar a dados, inclusive o seguinte:
- [Django e banco de dados do SQL Azure](/azure/app-service/app-service-web-get-started-python)
- [Django e MySQL no Azure](/azure/app-service-web/web-sites-python-ptvs-django-mysql)
- Trabalhar com [blobs](/azure/storage/blobs/storage-quickstart-blobs-python), [arquivos](/azure/storage/files/storage-python-how-to-use-file-storage), [filas](/azure/storage/queues/storage-python-how-to-use-queue-storage), e [tabelas (DB Cosmo)](/azure/cosmos-db/table-storage-how-to-use-python).

## <a name="related-topics"></a>Tópicos relacionados

[Análise, dispositivos e dados](https://msdn.microsoft.com/data-and-devices) fornece uma introdução à nuvem inteligente da Microsoft, incluindo suporte para Internet das coisas e Cortana Analytics Suite.

[Armazenamento do Microsoft Azure](https://azure.microCsoft.com/documentation/services/storage/) descreve o armazenamento do Azure e como criar aplicativos com o uso de blobs do Azure, tabelas, filas e arquivos.

[Banco de dados do SQL Azure](https://azure.microsoft.com/documentation/services/sql-database/) descreve como se conectar ao banco de dados do SQL Azure, um banco de dados relacional como um serviço.

[SQL Server Data Tools](/sql/ssdt/download-sql-server-data-tools-ssdt) descreve as ferramentas que simplificam o design, a exploração, teste e implantação de aplicativos de dados conectados e bancos de dados.

[ADO.NET](/dotnet/framework/data/adonet/index) descreve a arquitetura ADO.NET e como usar as classes ADO.NET para gerenciar dados de aplicativo e interagir com fontes de dados e XML.

[ADO.NET Entity Framework](https://msdn.microsoft.com/data/ef) descreve como criar aplicativos de dados que permitem aos desenvolvedores de programas em um modelo conceitual em vez de diretamente em um banco de dados relacional.

[WCF Data Services 4.5](/dotnet/framework/data/wcf/index) descreve como usar [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] para implantar serviços de dados na web ou em uma intranet que implementam o [Open Data Protocol (OData)](http://go.microsoft.com/fwlink/?LinkID=182204).

[Dados em soluções do Office](../vsto/data-in-office-solutions.md) contém links para tópicos que explicam como dados funcionam em soluções do Office. Isso inclui informações sobre programação orientada a esquema, o cache de dados e o acesso a dados do lado do servidor.

[LINQ (consulta integrada à linguagem)](/dotnet/csharp/linq/) descreve os recursos de consulta compilados em c# e Visual Basic e o modelo comum para consultar bancos de dados relacionais, documentos XML, conjuntos de dados e coleções na memória.

[Ferramentas de XML no Visual Studio](../xml-tools/xml-tools-in-visual-studio.md) discute trabalhar com recursos de XML do .NET Framework de dados, depuração XSLT, XML e a arquitetura de consulta XML.

[Documentos e dados XML](/dotnet/standard/data/xml/index) fornece uma visão geral para um conjunto abrangente e integrado de classes que trabalham com documentos XML e dados do .NET Framework.