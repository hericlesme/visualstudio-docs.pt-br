---
title: Ferramentas do conjunto de dados no Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.data.DataSet
helpviewer_keywords:
- untyped datasets
- datasets [Visual Basic], extended properties
- typed datasets
- current record in dataset
- XML [Visual Basic], datasets
- DataSet class, about datasets
- unique constraints (datasets)
- data relationships
- parent records in datasets
- extended properties, in typed datasets
- datasets [Visual Basic]
- schemas [Visual Basic], datasets
- datasets [Visual Basic], msprop
- master-detail tables, datasets
- databases [Visual Basic], updating
- msprop
- foreign keys, datasets
- DataSet class
- datasets [Visual Basic], filling
- case sensitivity, datasets
- constraints [Visual Basic], datasets
- child records
- related tables, datasets
- updating datasets, about dataset updates
- data caching, datasets
- DataRelation object, datasets
- untyped datasets, compared to typed datasets
- cache [Visual Studio], datasets
- datasets [Visual Basic], relationships
- related tables
- XML schemas, about XML schemas and datasets
- relationships, datasets
- typed datasets, compared to untyped datasets
- datasets [Visual Basic], populating
- datasets [Visual Basic], namespace
- data adapters, populating datasets
ms.assetid: ee57f4f6-9fe1-4e0a-be9a-955c486ff427
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: a8c8660fbc489dd8c4926bb09b8b42006da0897a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="dataset-tools-in-visual-studio"></a>Ferramentas do conjunto de dados no Visual Studio
> [!NOTE]
>  Conjuntos de dados e classes relacionadas são herdadas tecnologias .NET de início dos anos 2000 que habilitam aplicativos para trabalhar com dados na memória, enquanto os aplicativos são desconectados do banco de dados. Eles são especialmente úteis para aplicativos que os usuários possam modificar dados e manter as alterações no banco de dados. Embora os conjuntos de dados são comprovadamente uma tecnologia muito bem-sucedida, é recomendável novos aplicativos .NET usam Entity Framework. O Entity Framework oferece uma forma mais natural para trabalhar com dados de tabela como modelos de objeto, e ele tem uma interface de programação mais simples.  
  
 Um objeto de conjunto de dados é um objeto de memória que é essencialmente um banco de dados simplificado. Ele contém objetos DataRow, DataTable e DataColumn em que você pode armazenar e modificar dados de um ou mais bancos de dados sem a necessidade de manter uma conexão aberta. O conjunto de dados mantém informações sobre as alterações nos seus dados, para que as atualizações podem ser controladas e enviadas de volta para o banco de dados quando seu aplicativo se torna reconectado.  
  
 Conjuntos de dados e classes relacionadas são definidos no namespace System. Data na biblioteca de classes do .NET Framework. Você pode criar e modificar os conjuntos de dados dinamicamente no código. Para obter mais informações sobre como fazer isso, consulte ADO.NET. A documentação nesta seção mostra como trabalhar com conjuntos de dados usando os designers do Visual Studio. Uma coisa a saber: conjuntos de dados que são feitos por meio de designers de usam objetos de TableAdapter para interagir com o banco de dados, enquanto que conjuntos de dados que são feitos por meio de programação usam objetos de DataAdapter. Para obter informações sobre como criar conjuntos de dados programaticamente, consulte [DataAdapters e DataReaders](/dotnet/framework/data/adonet/dataadapters-and-datareaders).  
  
 Se seu aplicativo precisa apenas ler dados de um banco de dados e não executar atualizações, adiciona ou exclui, você geralmente pode obter um melhor desempenho usando um objeto DataReader para recuperar dados em um objeto de lista genérico ou outro objeto da coleção. Se você estiver exibindo os dados, você pode associar dados a interface do usuário à coleção.  
  
## <a name="dataset-workflow"></a>Fluxo de trabalho do conjunto de dados  
 O Visual Studio fornece muitas ferramentas para simplificar o trabalho com conjuntos de dados. O fluxo de trabalho de ponta a ponta básico é:  
  
-   Use o **fonte de dados** janela para criar um novo conjunto de dados de uma ou mais fontes de dados. Use o **Dataset Designer** para configurar o conjunto de dados e definir suas propriedades. Por exemplo, você precisa especificar quais tabelas da fonte de dados para incluir e quais colunas de cada tabela. Escolha cuidadosamente reduzir a quantidade de memória que exigirá que o conjunto de dados. Para obter mais informações, consulte [Create and configure datasets (Criar e configurar conjuntos de dados)](../data-tools/create-and-configure-datasets-in-visual-studio.md).  
  
-   Especifica as relações entre as tabelas para que as chaves estrangeiras são tratadas corretamente. Para obter mais informações, consulte [preencher conjuntos de dados usando TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md).  
  
-   Use o **Assistente de configuração TableAdapter** para especificar a consulta ou procedimento armazenado que preencherá o conjunto de dados e que operações de banco de dados (update, delete e assim por diante) para implementar. Para saber mais, consulte estes tópicos:  
  
    -   [Preencher conjuntos de dados usando TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)  
  
    -   [Editar dados em conjuntos de dados](../data-tools/edit-data-in-datasets.md)  
  
    -   [Validando dados em conjuntos de dados](../data-tools/validate-data-in-datasets.md)  
  
    -   [Salvar dados de volta no banco de dados](../data-tools/save-data-back-to-the-database.md)  
  
-   Consultar e pesquisar os dados no conjunto de dados. Para obter mais informações, consulte [conjuntos de dados de consulta](../data-tools/query-datasets.md). [!INCLUDE[linq_dataset](../data-tools/includes/linq_dataset_md.md)]permite [LINQ (consulta integrada à linguagem)](/dotnet/csharp/linq/) sobre os dados em um <xref:System.Data.DataSet> objeto. Para obter mais informações, consulte [LINQ to DataSet](/dotnet/framework/data/adonet/linq-to-dataset).  
  
-   Use o **fontes de dados** janela para associar a controles de interface do usuário para o conjunto de dados ou de suas colunas individuais e para especificar quais colunas são editáveis pelo usuário. Para obter mais informações, consulte [associar controles a dados no Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).  
  
## <a name="datasets-and-n-tier-architecture"></a>Arquitetura de conjuntos de dados e de N camadas  
 Para obter informações sobre conjuntos de dados em aplicativos de N camadas, consulte [trabalhar com conjuntos de dados em aplicativos de n camadas](../data-tools/work-with-datasets-in-n-tier-applications.md).  
  
## <a name="datasets-and-xml"></a>Conjuntos de dados e XML  
 Para obter informações sobre a conversão de conjuntos de dados para e de XML, consulte [dados XML de leitura em um conjunto de dados](../data-tools/read-xml-data-into-a-dataset.md) e [salvar um conjunto de dados como XML](../data-tools/save-a-dataset-as-xml.md).  
  
## <a name="see-also"></a>Consulte também  
 [Ferramentas de dados do Visual Studio para .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)