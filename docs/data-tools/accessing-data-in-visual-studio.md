---
title: Acessando dados no Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: "80025080"
helpviewer_keywords:
- data [Visual Studio]
- data access [Visual Studio]
- data [C#]
- ADO.NET, data access
ms.assetid: 9812a6d5-23d2-4427-8b98-70a2abfec3bc
caps.latest.revision: "100"
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.technology: vs-data-tools
ms.openlocfilehash: 585f021bf88dd6005a82643c5d182bd1fcbf8e91
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/09/2017
---
# <a name="accessing-data-in-visual-studio"></a>Acesso a dados no Visual Studio
No Visual Studio, você pode criar aplicativos que se conectam aos dados em praticamente qualquer produto de banco de dados ou um serviço, em qualquer formato, em qualquer lugar — em um computador local, em uma rede local ou em uma nuvem pública, privada ou híbrida.  
  
Para aplicativos em JavaScript, Python, PHP, Ruby ou C++, você se conectar aos dados que você pode fazer qualquer outra coisa, obtendo bibliotecas e escrever código. Para aplicativos .NET, o Visual Studio fornece ferramentas que você pode usar para explorar a fontes de dados, criar modelos de objeto para armazenar e manipular os dados na memória e associar os dados para a interface do usuário. Microsoft Azure fornece SDKs para .NET, Java, Node.js, PHP, Python, Ruby e aplicativos móveis e ferramentas no Visual Studio para se conectar ao armazenamento do Azure.  
  
A lista a seguir mostra apenas alguns os muitos sistemas de banco de dados e armazenamento que podem ser usados no Visual Studio. O [Microsoft Azure](https://azure.microsoft.com/) ofertas são serviços de dados que incluem todos os provisionamento e administração de armazenamento de dados subjacente.  [Ferramentas do Azure para Visual Studio](https://www.visualstudio.com/features/azure-tools-vs.aspx) é um componente opcional que permite que você trabalhe com repositórios de dados do Azure diretamente do Visual Studio. A maioria dos outros SQL e NoSQL banco de dados produtos listados aqui pode ser hospedada em um computador local, em uma rede local ou no Microsoft Azure em uma máquina virtual. Nesse cenário, você é responsável por gerenciar o próprio banco de dados.  
  
**Microsoft Azure**  
  
||||  
|-|-|-|  
|Banco de dados SQL|Documentos|Armazenamento (blobs, tabelas, filas, arquivos)|  
|SQL Data Warehouse|Banco de dados do SQL Server Stretch|StorSimple|  
  
e muito mais...  
  
**SQL**  
  
||||  
|-|-|-|  
|SQL Server 2005-2016, incluindo Express e LocalDB|Firebird|MariaDB|  
|MySQL|Oracle|PostgreSQL|  
|SQLite|||  
  
e muito mais...  
  
**NoSQL**  
  
||||  
|-|-|-|  
|Apache Cassandra|CouchDB|MongoDB|  
|NDatabase|OrientDB|RavenDB|  
|VelocityDB|||  
  
e muito mais...  
  
Muitos fornecedores de banco de dados e de terceiros dão suporte à integração do Visual Studio pacotes do NuGet. Você pode explorar as ofertas em nuget.org ou por meio do Gerenciador de pacotes do NuGet no Visual Studio (**ferramentas** > **NuGet Package Manager** > **gerenciar NuGet Pacotes de solução**). Outros produtos de banco de dados se integram ao Visual Studio como uma extensão. Você pode procurar essas ofertas na Galeria do Visual Studio, navegando para **ferramentas** > **extensões e atualizações** e, em seguida, selecionando **Online** à esquerda painel da caixa de diálogo. Para obter mais informações, consulte [instalar sistemas de banco de dados, ferramentas e exemplos de](../data-tools/installing-database-systems-tools-and-samples.md).  
  
> [!NOTE]
> Suporte estendido para o SQL Server 2005 terminou em 12 de abril de 2016. Não há nenhuma garantia de que as ferramentas de dados no Visual Studio 2015 e posteriores continuem a funcionar com o SQL Server 2005 após essa data. Para obter mais informações, consulte o [anúncio de fim do suporte para o SQL Server 2005](https://www.microsoft.com/server-cloud/products/sql-server-2005/).  
  
### <a name="net-languages"></a>Linguagens .NET  
Qualquer acesso a dados .NET, incluindo no núcleo do .NET, é baseado no ADO.NET, um conjunto de classes que define uma interface para acessar qualquer tipo de fonte de dados relacional e não relacionais. O Visual Studio tem várias ferramentas e designers que funcionam com o ADO.NET para ajudá-lo a se conectar a bancos de dados, manipular os dados e apresentar os dados para o usuário. A documentação nesta seção descreve como usar essas ferramentas. Você pode também programar diretamente os objetos de comando do ADO.NET. Para obter mais informações sobre como chamar as APIs do ADO.NET diretamente, consulte [ADO.NET](https://msdn.microsoft.com/library/e80y5yhx\(v=vs.110\).aspx) na biblioteca MSDN.  
  
Para obter a documentação de acesso a dados relacionada especificamente ao ASP.NET, consulte [trabalhando com dados](http://www.asp.net/web-forms/overview/presenting-and-managing-data) no site do ASP.NET. Para obter um tutorial sobre como usar o Entity Framework com o ASP.NET MVC, consulte [guia de Introdução ao Entity Framework 6 Code First usando MVC 5](http://www.asp.net/mvc/overview/getting-started/getting-started-with-ef-using-mvc/creating-an-entity-framework-data-model-for-an-asp-net-mvc-application).  
  
Aplicativos universais do Windows UWP (plataforma) no c# ou Visual Basic podem usar o SDK do Microsoft Azure para .NET para acessar o armazenamento do Azure e outros serviços do Azure. A classe Windows.Web.HttpClient permite a comunicação com todos os serviços RESTful. Para obter mais informações, consulte [como se conectar a um servidor HTTP usando Windows.Web.Http](https://msdn.microsoft.com/library/windows/apps/dn469430.aspx).  
  
Para o armazenamento de dados no computador local, a abordagem recomendada é usar SQLite, que é executado no mesmo processo que o aplicativo. Se uma camada de mapeamento relacional de objeto (ORM) for necessária, você pode usar o Entity Framework. Para obter mais informações, consulte [acesso a dados](https://msdn.microsoft.com/windows/uwp/data-access/index) no Centro de desenvolvedores do Windows.  
  
Se você estiver se conectando aos serviços do Azure, certifique-se de baixar a versão mais recente [ferramentas do SDK do Azure](https://azure.microsoft.com/downloads/).  
  
#### <a name="data-providers"></a>Provedores de dados  
Para um banco de dados ser consumível no ADO.NET, ele deverá ter um personalizado *provedor de dados ADO.NET* ou else deve expor uma interface ODBC ou OLE DB. A Microsoft fornece um [lista de provedores de dados ADO.NET](https://msdn.microsoft.com/data/dd363565) para produtos do SQL Server, bem como provedores de ODBC e OLE DB.  
  
#### <a name="data-modeling"></a>Modelagem de dados  
No .NET, você tem três opções de modelagem e manipulação de dados na memória depois de recuperá-lo de uma fonte de dados:  
  
[Entity Framework](../data-tools/entity-data-model-tools-in-visual-studio.md)  
A tecnologia Microsoft ORM preferencial. Você pode usar isso para programar em dados relacionais como objetos de primeira classe .NET. Para novos aplicativos, ele deve ser a primeira opção padrão quando um modelo é necessário. Ele requer suporte personalizado do provedor de ADO.NET subjacente.  
  
[LINQ to SQL](../data-tools/linq-to-sql-tools-in-visual-studio2.md)  
Um mapeador relacional de objetos da geração anterior. Ele funciona bem para cenários menos complexos, mas não está em desenvolvimento ativo.  
  
[Conjuntos de dados](../data-tools/dataset-tools-in-visual-studio.md)  
O mais antigo dos três tecnologias de modelagem. Ele foi projetado principalmente para rápido desenvolvimento de aplicativos "formulários sobre dados" em que você não é processar grandes volumes de dados ou executar consultas complexas ou transformações. Um objeto de conjunto de dados consiste em objetos de DataTable e DataRow que lembram logicamente objetos de banco de dados do SQL muito mais objetos do .NET Framework. Para aplicativos relativamente simples com base em fontes de dados do SQL, os conjuntos de dados ainda podem ser uma boa opção.  
  
Não há nenhum requisito para usar qualquer uma dessas tecnologias. Em alguns cenários, especialmente quando o desempenho for crítico, você pode simplesmente usar um objeto DataReader para ler do banco de dados e copiar os valores que você precisa para um objeto de coleção como lista\<T >.  
  
### <a name="native-c"></a>C++ Nativo  
Aplicativos C++ que se conectar ao SQL Server devem usar o [Microsoft® ODBC Driver 13.1 para SQL Server](https://www.microsoft.com/download/details.aspx?id=53339) na maioria dos casos. Se os servidores estiverem vinculados, em seguida, o OLE DB é necessário e para que você use o [SQL Server Native Client](https://msdn.microsoft.com/sqlserver/aa937733.aspx). Você pode acessar outros bancos de dados usando [ODBC](https://msdn.microsoft.com/library/ms710252\(v=vs.85\).aspx) ou drivers de OLE DB diretamente. ODBC é a interface padrão do banco de dados atual, mas a maioria dos sistemas de banco de dados fornecem funcionalidade personalizada que não pode ser acessada por meio da interface do ODBC. OLE DB é uma tecnologia de acesso a dados COM herdado que é ainda tem suporte mas não recomendada para novos aplicativos. Para obter mais informações, consulte [acesso a dados no Visual C++](https://docs.microsoft.com/cpp/data/).  
  
Programas C++ que consumirem serviços REST podem usar o [C++ REST SDK](https://github.com/Microsoft/cpprestsdk).  
  
Programas em C++ que funcionam com o armazenamento do Microsoft Azure podem usar o [cliente de armazenamento do Microsoft Azure](http://www.nuget.org/packages/wastorage).
  
Modelagem de dados &mdash; Visual Studio não fornecem uma camada ORM para C++. [ODB](http://www.codesynthesis.com/products/odb/) é um ORM popular do código-fonte aberto para C++.  

Para saber mais sobre como conectar aos bancos de dados de aplicativos em C++, consulte [ferramentas de dados do Visual Studio para C++](../data-tools/visual-studio-data-tools-for-cpp.md). Para obter mais informações sobre tecnologias de acesso a dados herdadas do Visual C++, consulte [acesso a dados](http://msdn.microsoft.com/Library/a9455752-39c4-4457-b14e-197772d3df0b).
  
### <a name="javascript"></a>JavaScript  
[JavaScript no Visual Studio](https://msdn.microsoft.com/library/hh334522.aspx) é uma linguagem de primeira classe para a criação de aplicativos de plataforma cruzada, aplicativos UWP, serviços de nuvem, sites e aplicativos web. Você pode usar o Bower, Grunt, Gulp, npm e NuGet de dentro do Visual Studio para instalar bibliotecas de JavaScript favoritas e produtos de banco de dados. Conecte-se ao armazenamento do Azure e serviços baixando SDKs do [site do Azure](https://azure.microsoft.com/). Edge.js é uma biblioteca JavaScript do lado do servidor (Node. js) conecta-se a fontes de dados do ADO.NET.  
  
### <a name="python"></a>Python  
Instalar [ferramentas Python para Visual Studio](http://microsoft.github.io/PTVS/) juntamente com a estrutura de Python favorita para criar aplicativos CPython ou IronPython (.NET). As ferramentas Python para o site do Visual Studio tem vários tutoriais sobre como se conectar a dados, inclusive [Django e banco de dados do SQL Azure](https://github.com/Microsoft/PTVS/wiki/Django-and-SQL-Database-on-Azure), [Django e MySQL no Azure](https://github.com/Microsoft/PTVS/wiki/Django-and-MySQL-on-Azure) e [garrafa e MongoDB em Azure](https://github.com/Microsoft/PTVS/wiki/Bottle-and-MongoDB-on-Azure).
  
## <a name="related-topics"></a>Tópicos relacionados  
 [Análise, dispositivos e dados](https://msdn.microsoft.com/data-and-devices)  
 Fornece uma introdução à nuvem inteligente da Microsoft, incluindo suporte para Internet das coisas e Cortana Analytics Suite.  
  
 [Armazenamento do Microsoft Azure](https://azure.microCsoft.com/documentation/services/storage/)  
 Descreve o armazenamento do Azure e como criar aplicativos com o uso de arquivos, tabelas, filas e blobs do Azure.  
  
 [Banco de dados SQL do Azure](https://azure.microsoft.com/documentation/services/sql-database/)  
 Descreve como se conectar ao banco de dados do SQL Azure, um banco de dados relacional como um serviço.  
  
 [SQL Server Data Tools](https://msdn.microsoft.com/library/hh272686\(v=vs.103\).aspx)  
 Descreve as ferramentas que simplificam o design, a exploração, teste e implantação de bancos de dados e aplicativos de dados conectados.  
  
 [ADO.NET](/dotnet/framework/data/adonet/index)  
 Descreve a arquitetura ADO.NET e como usar as classes ADO.NET para gerenciar dados de aplicativo e interagir com fontes de dados e XML.  
  
 [ADO.NET Entity Framework](https://msdn.microsoft.com/data/ef)  
 Descreve como criar aplicativos de dados que permitem aos desenvolvedores de programas em um modelo conceitual em vez de diretamente em um banco de dados relacional.  
  
 [WCF Data Services 4.5](/dotnet/framework/data/wcf/index)  
 Descreve como usar [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] para implantar serviços de dados na web ou em uma intranet que implementam o [Open Data Protocol (OData)](http://go.microsoft.com/fwlink/?LinkID=182204).  
  
 [Dados em soluções do Office](/office-dev/office-dev/data-in-office-solutions)  
 Contém links para tópicos que explicam como dados funcionam em soluções do Office. Isso inclui informações sobre programação orientada a esquema, o cache de dados e o acesso a dados do lado do servidor.  
  
 [LINQ (Consulta Integrada à Linguagem)](http://msdn.microsoft.com/Library/a73c4aec-5d15-4e98-b962-1274021ea93d)  
 Descreve os recursos de consulta compilados em c# e Visual Basic e o modelo comum para consultar bancos de dados relacionais, documentos XML, conjuntos de dados e coleções na memória.
  
 [Ferramentas XML no Visual Studio](../xml-tools/xml-tools-in-visual-studio.md)  
 Discute a trabalhar com recursos de XML do .NET Framework de dados, depuração XSLT, XML e a arquitetura de consulta XML.  
  
 [Documentos e dados XML](/dotnet/standard/data/xml/index)  
 Fornece uma visão geral sobre um conjunto abrangente e integrado de classes que funcionam com documentos e dados XML no .NET Framework.